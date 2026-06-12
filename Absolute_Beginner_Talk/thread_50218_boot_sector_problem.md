---
title: "boot sector problem"
date: 2005-07-19
forum: Absolute Beginner Talk
---

### Post by Patrick Egan on 2005-07-19
i'm new to linux and not very computer savvy. i got a copy of fedora 3 and installed it on my laptop with win xp. it dual booted fine (grub) read about Ubuntu and thought it sounded better. got cd install seemed no problem but now can't boot - message boot sector invalid. live cd booting fine. any advice ??? thanks
patrick

---

### Post by odin on 2005-07-20
If what you want is to haveboth (ubuntu and xp working) I think you should do this.

First restore try to restore te boot sector so you can boot normally with your xp.

For restoring the boot sector just put the windows xp cd.Boot to the cd and choose recovery console and when you get to the command prompt type:

fixmbr

You have to use the windows cd not the recovery cd.
After that reboot and you should be able to boot your windows.Then proceed to install ubuntu.

Remember that (at least I had to do it like that) you have to partition your hard disk before you start installing ubuntu.I've read some people saying that it is possible to do the partitioning in the ubuntu installation but i couldnt.I used partition magic for that.If you are a newbie you should use that because is graphical and even though there other tools they are text-based and you may find them more difficult.

Good luck

---

### Post by Patrick Egan on 2005-07-20
thanks, I'll try that - patrick

---

