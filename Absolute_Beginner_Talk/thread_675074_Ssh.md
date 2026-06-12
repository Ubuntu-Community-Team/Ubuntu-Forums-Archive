---
title: "Ssh"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2008-01-22
Whenever i try to SSH to any server, which is not sshed before, it asked me that Yes/No/Always question about their keys, is there a way to get rid of this, i mean set it Always automatically?

---

### Post by p_quarles on 2008-01-22
Doesn't sound to me like the best idea, but if that's what you want, edit /etc/ssh/ssh_config and change the "StrictHostKeyChecking" setting to "no."

---

