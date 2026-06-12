---
title: "nsswitch.conf vs host.conf question"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by kidders on 2008-04-05
Hi there,

> **Auston said:**
> Does nsswitch.conf and host.conf do the same job?More or less ... nsswitch.conf is a newer, more powerful implementation, but they are both resolver configuration files.

> **Auston said:**
> Which file gets called first, if there is a request?That depends on what's making the request. Afaik, they are never *both* used ... I've always assumed that requests handled by glibc's newer resolver library ignore host.conf completely.

---

