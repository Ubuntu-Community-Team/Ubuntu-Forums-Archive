---
title: "Booting Pretty"
date: 2008-03-27
forum: Apple PPC Users
---

### Post by LinuxRT on 2008-03-27
Hello there,

Out of the storm, and enjoying my xubuntish experience. 

Quick question. Is it possible to bypass the yaboot/ first stage bootstrap straight to the Xubuntu loading window?

If so, how?


As well, I would like to thank the Ubuntu PPC community and its outstanding patience. 

Thanks

RT

---

### Post by adelahunty on 2008-03-27
Hi LinuxRT,

Glad you got it all running... :)

Yaboot - as I recall from somewhere, anyhow - is the glue that exists between the Open Firmware and the Linux system, so the first answer is that you need it.  Hard cheese... ;)

The one thing you can do is to edit your /etc/yaboot.conf file.  Have a look at the 'delay' and 'timeout' options.  If you set those to something really small, like zero, then it will effectively run so quickly it will go straight to your Xubuntu loading screen.  Well, there'll be a small delay as it does it's thing, but not so that you would really notice.  Even on my G3 it runs through this very quickly.

Oh, and when you're done making changes, you need to type ybin at the prompt for it all to do it's thang.

---

### Post by LinuxRT on 2008-03-28
Done it, Thank you.

---

