# Contribution [#]: ]: Duplicate entry in rule one of list after payee name merge

**Contribution Number:** [1]  
**Student:** Trang Doan  
**Issue:** [GitHub issue link](https://github.com/actualbudget/actual/issues/6486)
**Status:** [Phase I] [Complete]

---

## Why I Chose This Issue

I chose issue #6486 — "Duplicate entry in rule one of list after payee name merge" — because it fits my TypeScript and React experience and gives me a clear, bounded first contribution. The issue has 0 comments, no assignee, no open PR, and a numbered repro with obvious expected behavior, which made it stand out during issue selection.

I'm interested in this because:

- The tech stack is clearly within my area of expertise (Typescript, Shell)
- The bug sits at the intersection of rules and payee merge. It seems contained enough to learn one area without taking on the whole app
- I've already left a comment on the issue to introduce myself and ask to claim it. Actual also has a devcontainer and contributing docs, which should make local setup manageable.
---

## Understanding the Issue

### Problem Description

When a user merges two payees that both appear in a rule's "one of" payee list, the merged rule ends up showing the same payee twice. If the user removes what looks like a duplicate and saves, both entries are removed — so the payee condition disappears from the rule entirely.


### Expected Behavior

After merging payee B into payee A, a rule that previously matched "one of Payee A, Payee B" should show one entry for the surviving payee. Editing the rule should not create duplicates, and removing an entry should only remove that single condition — not wipe the whole payee match.


### Current Behavior

- User creates a rule with payee one of "Burger Drops Montreal", "Burger Drops Toronto", etc.
- User merges those payees into a single "Burger Drops" payee via a PRE rename rule.
- Reopening the category rule shows "Burger Drops" twice in the one-of list.
- Removing one duplicate and saving removes both entries; reopening the rule shows the payee gone entirely.

### Affected Components

the fix likely touches:
- Payee merge flow — packages/loot-core/src/server/payees/app.ts (mergePayees) and packages/loot-core/src/server/db/index.ts (payee merge DB updates)
- Rules engine — packages/loot-core/src/server/transactions/transaction-rules.ts and packages/loot-core/src/server/rules/condition.ts (oneOf / notOneOf handling for payee fields)
- Rule UI — packages/desktop-client/src/components/rules/RuleEditor.tsx and related modals (EditRuleModal, ConfirmPayeesMergeModal) where one-of lists are displayed and saved

---

## Reproduction Process

### Environment Setup

[Notes on setting up your local development environment - challenges you faced, how you solved them]

### Steps to Reproduce

1. [Step 1]
2. [Step 2]
3. [Observed result]

### Reproduction Evidence

- **Commit showing reproduction:** [Link to commit in your fork]
- **Screenshots/logs:** [If applicable]
- **My findings:** [What you discovered during reproduction]

---

## Solution Approach

### Analysis

[Your analysis of the root cause - what's causing the issue?]

### Proposed Solution

[High-level description of your fix approach]

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** [Restate the problem]

**Match:** [What similar patterns/solutions exist in the codebase?]

**Plan:** [Step-by-step implementation plan]
1. [Modify file X to do Y]
2. [Add function Z]
3. [Update tests]

**Implement:** [Link to your branch/commits as you work]

**Review:** [Self-review checklist - does it follow the project's contribution guidelines?]

**Evaluate:** [How will you verify it works?]

---

## Testing Strategy

### Unit Tests

- [ ] Test case 1: [Description]
- [ ] Test case 2: [Description]
- [ ] Test case 3: [Description]

### Integration Tests

- [ ] Integration scenario 1
- [ ] Integration scenario 2

### Manual Testing

[What you tested manually and results]

---

## Implementation Notes

### Week [X] Progress

[What you built this week, challenges faced, decisions made]

### Week [Y] Progress

[Continue documenting as you work]

### Code Changes

- **Files modified:** [List]
- **Key commits:** [Links to important commits]
- **Approach decisions:** [Why you chose certain approaches]

---

## Pull Request

**PR Link:** [GitHub PR URL when submitted]

**PR Description:** [Draft or final PR description - much of the content above can be adapted]

**Maintainer Feedback:**
- [Date]: [Summary of feedback received]
- [Date]: [How you addressed it]

**Status:** [Awaiting review / Iterating / Approved / Merged]

---

## Learnings & Reflections

### Technical Skills Gained

[What you learned technically]

### Challenges Overcome

[What was hard and how you solved it]

### What I'd Do Differently Next Time

[Reflection on your process]

---

## Resources Used

- [Link to helpful documentation]
- [Tutorial or Stack Overflow post that helped]
- [GitHub issues or discussions that helped]
