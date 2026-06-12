---
title: "What is happening? MULTIBOOT?"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by lfmasieri on 2006-02-14
I just installed the ubuntu and when I tried to start it it just say me an errorreffering to the video card or something like that, and it appera a black scrren like widnows DOS, what should I do? I actually reinstalled windows on my other partition and I cant boot, what shoudl I do?

---

### Post by Clark Nova on 2006-02-14
I'm still a novice myself when it comes to Linux but I'll help with the Windows installation if I can. Which version of Windows do you have installed? What happens when you try to boot, do you get the GRUB bootloader at all?

If you have a full install disc for XP (I'll assume that's what you have installed) you can boot from that and choose the option to "fix an existing installing using Recovery Console". If you choose your installation of XP and then type "fixmbr" it will rewrite your boot record and you'll be able to get back into Windows again without having lost your data.

Sorry I can't help with the Linux stuff but perhaps you can at least get your Windows partition working again :)

---

### Post by Pavel Kraynov on 2006-02-15
[QUOTE=lfmasieri]I just installed the ubuntu and when I tried to start it it just say me an errorreffering to the video card or something like that, and it appera a black scrren like widnows DOS, what should I do? I actually reinstalled windows on my other partition and I cant boot, what shoudl I do?[/QUOTE]

if you could start recovery console (from install disk), try 
fixboot
fixmbr

and reboot

---

