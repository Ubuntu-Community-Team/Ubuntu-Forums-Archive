---
title: "Dual Booting"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Haruko147 on 2007-06-17
Hey all!

So I installed ubuntu and got it running fine, but then when I tried to get WoW working, I ran into so many issues that I shrunk my hardrive, repartitioned and installed windows on a new partition.

Windows is working fine, but how do I get back to ubuntu? I think that my windows partition is marked active now, anyone know how to unactivate it?

Thanks in advance! And if there are any guides available to fix it I wouldn't mind a link over, searched myself but came up empty.

---

### Post by sharke on 2007-06-17
There lies the problem Windows rewrites the mbr ad ignores other operating systems. Save all your data do a fresh install of ubuntu and you are okay for go. In other windows must be installed first.
Regards
Sharke

---

### Post by Haruko147 on 2007-06-17
ugh....lol

I also happened to find [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) while waiting for a reply, I'm going to give it a shot and hopefully that will work before I have to reinstall. But thanks for the help, at least I know how to fix it in a last case resort. ^^

---

### Post by sharke on 2007-06-17
Supergrub disc is a great asset but i have never been able to get it to give dual boot only one os.
Let me know how it goes.
Regards
Sharke

---

### Post by alienexplorers on 2007-06-17
Supergrub should work fine if not try the manual approach.  Insert your Ubuntu live cd, boot up, and enter terminal.  Type in sudo grub and enter the grub editor.
Enter
> find /boot/grub/stage1
it will give an output like (hd#,#)
Enter
> root (hd#,#)
setup (hd#)
exit grub editor
reboot and you should have dual boot again.

---

### Post by Haruko147 on 2007-06-17
just an update

I got supergrub running but I got scared because it was slightly confused as to which partition I needed to select.

The manual fix worked perfect (I love hands on more ^^) 

Now I'm back into ubuntu, and I know I can get back and forth via supergrub, but I didn't see anything in particular that I could select a partition from. Is there something else I'm missing, or would I have to install something else/reinstall ubuntu to load something to give me the choice without a cd?

---

