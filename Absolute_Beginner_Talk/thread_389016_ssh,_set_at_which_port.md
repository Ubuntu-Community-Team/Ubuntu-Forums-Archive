---
title: "ssh, set at which port?"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-03-20
Hi there,

I need to know at what port the ssh server on a pc is set to use? I can login from a computer screen but the previous owner changed the SSH from the default port to something else, so now I can't ssh into the thing.

Thanks,

Rudolf

---

### Post by Bachstelze on 2007-03-20
```
cat /etc/ssh/sshd_config | grep Port
```

---

### Post by RudolfMDLT on 2007-03-20
thank you very much!

---

