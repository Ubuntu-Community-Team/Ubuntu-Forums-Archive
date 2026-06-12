---
title: "Booting linux or windows"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by Entase on 2006-11-15
Hey, new question,

in my other mpost, i was under the assumption I was going to run ubuntu on my Powermate VP75, old piece of crap, but Im think about particianing, ( typo I know,) my brothers hard drive ( 200 GB), and dual booting or w/e, but I know it candle it, its nice computer, how do I make it where I can install ubuntu, and then, at boot, choos whether I want to boot Windows or Ubuntu?

(Lead me through it step-by-step, please)

Entase

---

### Post by Tomosaur on 2006-11-15
Depending on which version of Ubuntu you're going to try, you will either be asked to install Grub, or Grub will be automatically installed. This is a program which displays a list of your Operating System at boot-up, allowing you to select which one to use.

---

### Post by joshsherman on 2006-11-15
Assuming the drive's already partitioned, ubuntu will install Grub and add your Windows partition automatically.

I'm going to assume there are guides out there so I'm not going to go into full details.

-j

---

### Post by Entase on 2006-11-15
if anything with ubuntu goes wrong, are there measures in place, to allow you to boot windows at start?

---

### Post by Esben Kramer on 2006-11-15
When running the Ubuntu-installer, it will ask you to partition the harddrive with a GUI. It's quite simple, and it will tell you if you are doing something completely wrong. After choosing how much size you want for Ubuntu and how much for Windows, it does the rest for you. When you boot the computer, it will ask you which system you want to start. Very simple and intuitive.

Edit: So yes. If Ubuntu doesn't work out for you, you can just boot Windows. Just remember not to overwrite Windows under the install, but the installer will help you there.

---

### Post by alinuxfan on 2006-11-15
check out [this link]("http://www.psychocats.net/ubuntu/installing") and read through it.  After getting into the installer there will be an option to resize the HD partitions.  follow the guide and you are set

---

### Post by Tomosaur on 2006-11-15
> **Entase said:**
> if anything with ubuntu goes wrong, are there measures in place, to allow you to boot windows at start?

As with any disk operation, partitioning and generally messing around with your hard drive can cause problems. Although the chances of anything going wrong DURING installation are slim, it is not unheard of. You should back up the stuff you want to keep before installing.

If Ubuntu fails to install, then Grub won't install either, since Grub is only installed at the very end of the installation process. If it's Grub which fails to install, this could cause problems, but these should be easily fixed if you have a windows recovery CD (or just install grub again, or a different bootloader).

If all installation is successful, but Ubuntu refuses to work, then you can just select Windows at bootup.

If grub won't work (again, unlikely, but not unheard of), then again you may need your windows recovery disk handy.

---

### Post by ReaderRat on 2006-11-15
Some 'stuff':
[**Partitioning (XP & Ubuntu)**](http://psychocats.net/ubuntu/partitioning)
[**Installing Ubuntu**](http://www.psychocats.net/ubuntu/installing)
For future Reference:  [**[color=blue]Psychocats Tutorials[/color]**](http://www.psychocats.net/ubuntu/index)

---

