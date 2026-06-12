---
title: "Does the -rt kernel save power?"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Megatog615 on 2007-10-21
I was thinking of switching to the -rt kernel for the 1000Hz tick rate since a higher tick rate apparently helps save power. Is this true?

Also, what are some examples of how it would affect performance?

---

### Post by dave-5B on 2007-10-21
i would assume that prioritising response time over everything else would reduce battery life

also i thought dynticks was implemented in both the generic and -rt gutsy kernels making tick rates a non-issue

EDIT: and how would having more ticks reduce power consumption?

---

