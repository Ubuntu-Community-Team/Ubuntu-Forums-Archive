---
title: "Don't use reset button?"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-09-13
I recently saw this 

> 
Don´t ever use the reset-button in Linux ! 
[http://www.brunolinux.com/01-First_Things_To_Know/The_Reset_Button.html](http://www.brunolinux.com/01-First_Things_To_Know/The_Reset_Button.html)


It's quite an old page - last updated 2005, but is it still valid? I've been having system lockups recently that defy CTRL+Alt+Backspace - no mouse, no keyboard; I've had to hit reset. Now I'm wondering if I've made things worse. :(

Being a long-time Windows user, the reset button is second nature to me. :)

TIA

---

### Post by Nulifier on 2007-09-13
It can mess up some file systems if it is writing data to it, so it is not recommended for normal usage.

However if the system is locked up there is not very many alternatives. Most likely the worst that can happen is that the file system gives you warnings on boot.

I have had to use the reset button several times in linux and so far I have had not even and error on boot caused by the file system.

---

### Post by mcduck on 2007-09-13
> **freesitebuilder said:**
> I recently saw this 



It's quite an old page - last updated 2005, but is it still valid? I've been having system lockups recently that defy CTRL+Alt+Backspace - no mouse, no keyboard; I've had to hit reset. Now I'm wondering if I've made things worse. :(

Being a long-time Windows user, the reset button is second nature to me. :)

TIA

It's not a Linux think. It's a computer thing. You should always shut the machine down properly, just using the power or reset button might cause data loss or corruption, and in worst case break your operating system so you need to do a complete reinstall.

Anyway, as long as the keyboard is working you can do a fairly safe reboot this way: hold Alt and SysRq (the same key that has PrtSc on it). Then press R-E-I-S-U-B slowly. Alt-SysRq-R takes your keyboard out of raw mode, Alt-SysRq-E ends all running programs, Alt-SysRq-I kills all processes that failed to end properly, Alt-SysRq-S syncs the disks to avoid data loss, Alt-SysRq-U remounts disks as read-only and finally Alt-SysRq-B boots the machine.

edit: More info about SysRq: [http://en.wikipedia.org/wiki/Magic_SysRq_key]("http://en.wikipedia.org/wiki/Magic_SysRq_key")

---

### Post by steve.horsley on 2007-09-13
Yay! Alt-SysRq-R, Ctrl-Alt-Del works nicely on Feisty. Now, that one is simple enough to remember.

---

