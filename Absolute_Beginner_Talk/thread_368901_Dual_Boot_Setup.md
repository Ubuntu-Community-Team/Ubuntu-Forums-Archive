---
title: "Dual Boot Setup"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by TheMono on 2007-02-23
OK... I bet this question doesn't get asked very often:

I'm trying to set up a dual boot environment for Ubuntu Feisty and Win XP. I'm using feisty more because of hardware support for my new PC than anything else. Having said that, I've been using ubuntu as my primary OS for a long time now, and I'm certainly not scared of partitioning or the command line.

The catch is, feisty is already installed, and now I want to add XP... Every howto I could fine was the other way round. Ideally, I want to have GRUB in the MBR and allow me to chainload XP. I know that if I install XP, it will kill my MBR copy of GRUB - what is the trick to restoring it?

Thanks a lot

---

### Post by islander_810 on 2007-02-23
Use grub-install. Type grub-install --help for all the options.

The option which is reqd is "root-directory"

Once you install WinXP, use Ubuntu as Live CD and run it. Then open the terminal and type

sudo grub-install --root-directory="your root directory here"

Well, you've to mount ur root partition first.

---

### Post by TheMono on 2007-02-23
Is it possible to do this from the alternate install disc? I don't have the feisty live CD, but I do have the alternate one sitting round.

---

### Post by rsambuca on 2007-02-23
It doesn't have to be the feisty cd to restore grub.  If you have an older live CD it will work as well.

---

### Post by TheMono on 2007-02-23
Great then. I've got a Kubuntu dapper live disc sitting round, so lets give this a go... Wish me luck lol.

---

### Post by islander_810 on 2007-02-23
Any Live CD having grub should do

---

