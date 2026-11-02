# 芒格式盘问 · grillme-munger

> 三轮，九个盲区，只问不答。  
> 不给你答案，只帮你发现哪里没想清楚。

一个给 Claude Code 用的认知盘问 Skill。适用于决策前压力测试、拆解伪概念、检验判断依据，以及任何「我以为我想清楚了」的时刻。

---

## 它是什么

普通盘问容易变成两种东西：要么抬杠，要么聊天。

这个 Skill 用一套固定的三层诊断框架，把「感觉没想清楚」变成「具体卡在哪个盲区」：

- **本体论**：你看到的是静态的「是什么」，还是动态的「怎么变」？
- **认识论**：你的判断有依据，还是只有感觉？
- **语言哲学**：你用的词，能换成可测量的事实吗？

九个盲区，三轮扫描；问完给一份诊断报告：主盲区、证据、治疗方案、今天能做的三件事、待验证清单，以及「我没法判断的」。

---

## 特点

- **只问不答**：盘问结束前不给建议、不给结论、不给方案。唯一例外：用户说「别问了，直接说」。
- **一次只问 1–2 个**：不一次抛五个问题；从轻到重，答不上来先换角度。
- **九个盲区，最多 2 个**：主盲区说透，次盲区点到；给多了记不住。
- **六个模型，最多 2 个**：逆向、第一性原理、机会成本、概率、复利、系统；语言层不硬套模型。
- **报告有证据**：每条判定必须引用用户原话；最后必须有「我没法判断的」，不能装。
- **有安全边界**：情绪危机、医疗/法律/投资等高风险决策，不盘问，建议找专业人士。

---

## 安装

### 用户级（所有项目可用）

```bash
git clone https://github.com/pangolin-aigc/grillme-munger.git
mkdir -p ~/.claude/skills
cp -r grillme-munger ~/.claude/skills/grillme-munger
```

Windows PowerShell：

```powershell
git clone https://github.com/pangolin-aigc/grillme-munger.git
New-Item -ItemType Directory -Force "$env:USERPROFILE\.claude\skills" | Out-Null
Copy-Item -Recurse -Force ".\grillme-munger" "$env:USERPROFILE\.claude\skills\grillme-munger"
```

### 项目级（只对当前仓库生效）

把 `grillme-munger/` 放到项目根目录的 `.claude/skills/` 下：

```
your-project/
└── .claude/
    └── skills/
        └── grillme-munger/
            ├── SKILL.md
            └── references/
```

---

## 使用

在 Claude Code 里直接说：

```
盘问我：我想辞职做独立开发，现在的工作太没意思了。
```

也可以：

```
用芒格视角审一下我这个决策：要不要把房子卖了去创业。
帮我找一下认知盲区：我为什么总是想不清楚这件事。
决策前压力测试：我准备把全部积蓄投进这个项目。
```

Skill 会一次问一个问题，三轮结束后给诊断报告。

---

## 一个最小示例

> **你**：盘问我：我想辞职做独立开发。
>
> **Skill**：先问一个——你说「现在的工作没意思」，是最近才这样，还是一直如此？
>
> **你**：最近半年吧，之前还行。
>
> **Skill**：半年前发生了什么？
>
> **你**：换了领导，项目方向也变了。
>
> **Skill**：所以「没意思」是这份工作的问题，还是这个阶段的问题？
>
> **你**：……可能是阶段。
>
> **Skill**：如果半年后换回原来的方向，你还会想走吗？
>
> **你**：那可能不会。

三轮之后，报告会指出主盲区（比如「实体思维」：把当前阶段的状态当成了这份工作的本质），并给出对应的模型和今天能做的验证动作。

---

## 目录结构

```
grillme-munger/
├── SKILL.md                     # 技能入口：原则、节奏、三轮结构、报告模板
├── references/
│   ├── 盲区问题库.md            # 九个盲区 × 5–8 个问法 + 快速版 8 问
│   ├── 思维模型详解.md          # 六个模型的用法、失效场景、常见误用
│   └── 诊断报告模板.md          # 完整模板 + 示例 + 输出注意事项
├── LICENSE                      # MIT
├── NOTICE.md                    # 第三方参考与授权说明
└── README.md
```

---

## 设计原则

1. **问，不要替他想。** 人只有被追问到答不上来，才会意识到自己没想清楚。
2. **一次一个。** 盘问是对话，不是问卷。
3. **先轻后重。** 先铺垫，再致命；答不上来先换角度。
4. **最多 2 个盲区、2 个模型。** 给多了等于没给。
5. **报告必须有证据、有动作、有边界。** 只列问题不给方案，是最差的报告。

---

## 它不做什么

- 不替你做决定
- 不判断某个决策「对不对」，只判断「想清楚了没有」
- 不预测结果
- 不在完全不了解的领域硬给建议
- 不用于情绪危机、医疗/法律/投资等高风险决策

---

## 版权与致谢

- 盘问结构参考 [Jekudy/grillme-skill](https://github.com/Jekudy/grillme-skill)（MIT License）。
- 三层诊断框架与思维模型为二次整理，受《穷查理宝典》及芒格公开演讲启发。**「芒格」是风格指代，不是原话；本项目与 Charlie Munger 及其家族无关联。**
- 盲区问题库与报告模板为原创整理。
- 本项目使用 MIT License，详见 [LICENSE](LICENSE) 与 [NOTICE.md](NOTICE.md)。

---

## English

**grillme-munger** is a Claude Code skill for Munger-style cognitive grilling: three rounds (ontology / epistemology / philosophy of language), nine blind spots, and one rule — ask, don't answer.

It is for decision stress-testing, concept dismantling, and evidence checks. It ends with a diagnosis report: primary blind spot, evidence, one or two mental models, concrete actions, and an honest "what I can't judge" section.

Install by copying the folder into `~/.claude/skills/grillme-munger/`. Trigger with "grill me", "review this decision from Munger's perspective", or "find my blind spots".

MIT licensed. Not affiliated with Charlie Munger.
