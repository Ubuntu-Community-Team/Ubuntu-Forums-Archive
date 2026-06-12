---
title: "apt-get remove -y ???"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-11-01
Can someone please tell me what does the apt-get remove "-y" switch do?

Cheers.

---

### Post by matthewv on 2006-11-01
> **zugu said:**
> Can someone please tell me what does the apt-get remove "-y" switch do?

Cheers.
According to ```
man apt-get
```
**-y, --yes, --assume-yes**
[INDENT]Automatic  yes to prompts; assume "yes" as answer to all prompts and run non-interactively. If an undesirable situation, such  as              changing  a  held  package,  trying to install a unauthenticated              package or removing an essential  package  occurs  then  apt-get              will abort. Configuration Item: APT::Get::Assume-Yes.[/INDENT]

---

### Post by zugu on 2006-11-01
Thank you.

---

