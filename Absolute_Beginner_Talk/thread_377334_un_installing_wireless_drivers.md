---
title: "un installing wireless drivers"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by the.eagle on 2007-03-06
Hello all

 Can anyone help. I have been trying to uninstall the native wireless drivers' bcm43xx' and having no luck. Read all the help files I could, but they all seem to differ slightly each time. Can someone give me the exact string incl sudo etc so I can be rid of this thing. Also do you know when there will be a generic driver generator included in linux? Perhaps that could be a project.  Thanks in advance.....:)

---

### Post by zanglang on 2007-03-06
You can't really uninstall drivers per se... Everytime there's a kernel modules upgrade it gets installed anyway. If you'd like to *prevent* it from being used though, you can add a line
```
blacklist bcm43xx
```
to /etc/modprobe.d/blacklist (sp?) and it should fallback to Ndiswrapper or whatever driver you'll be using next.

---

