---
title: "Grub Error 15"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by KGB42 on 2007-10-31
I loaded Ubuntu Feisty Fawn from a download cd with no problems and was astonished by how fast it was compared to windows on the same computer. Then I hit the hibernate button and everything went wrong.

Rebooting brings up the message Grub Error 15, Please Wait, I have no command line, and I can't reinstall. What do I do? Answers in layman's terms please - I'm keen to get away from the awful Microsoft, but definitely a Newbie...

---

### Post by jusmurph on 2007-10-31
> **KGB42 said:**
> I loaded Ubuntu Feisty Fawn from a download cd with no problems and was astonished by how fast it was compared to windows on the same computer. Then I hit the hibernate button and everything went wrong.

Rebooting brings up the message Grub Error 15, Please Wait, I have no command line, and I can't reinstall. What do I do? Answers in layman's terms please - I'm keen to get away from the awful Microsoft, but definitely a Newbie...

My first question is why did you go Fiesty over the Newer Gutsy?

If you wanted to install Gutsy assuming you had the means to download it you could, the cd boot step comes before grub, so you should be able to fiddle your BIOS to allow you ot boot from cd.

---

### Post by the badger on 2007-10-31
> **KGB42 said:**
> Rebooting brings up the message Grub Error 15,..

one newbie to another: if you have an installation cd, and your boot sequence is set to boot first from cd (adjustable in GRUB at startup by pressing "del" or some F button - it will say), you should still be able to use this as a live cd.

anyhow, i can point you to [http://users.bigpond.net...#15]("http://users.bigpond.net.au/hermanzone/p15.htm#15") and the [super grub disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") pages.

(and re: feisty/gutsy - i just installed gutsy from dapper and it's all go. i'd recommend it).

---

### Post by KGB42 on 2007-11-01
Thanks for replies - I downloaded Fawn because Gutsy hadn't been released, and I didn't realise it was imminent. 

I think what's happening is that the pc is trying to boot from the hard disk and for some reason is unable to find the fight file. I'll try hitting del and the various F keys and see if I can adjust it to boot from the cd, which would then allow me to access the command line.

---

### Post by geeree on 2007-11-01
> **KGB42 said:**
> Rebooting brings up the message Grub Error 15, Please Wait, I have no command line, and I can't reinstall. What do I do? Answers in layman's terms please - I'm keen to get away from the awful Microsoft, but definitely a Newbie...

Hey KGB42, sorry I can't help by explaining in layman's terms but if you want to understand  the Error 15 see this:

[http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors](http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors)

It basically means that everything (the hard disk partitioning, etc.) is okay but GRUB cannot find the required files, which in this case could be your /boot/grub/menu.lst. To solve this problem you could open a GRUB shell (how to do this is explained in the above document) and see what is wrong with this file or whether it is even present or not. We had a similar problem on a friend's Dell Inspiron 1420 and which had Windows Vista pre-installed. We solved it by restarting the computer, booting it on the Gutsy installation disk and reinstalling the operating system. This brute force method corrected any errors in the /boot/grub directory. 

HTH,
Girish.

---

### Post by adrian15 on 2007-11-06
> **KGB42 said:**
> I loaded Ubuntu Feisty Fawn from a download cd with no problems and was astonished by how fast it was compared to windows on the same computer. Then I hit the hibernate button and everything went wrong.

Rebooting brings up the message Grub Error 15, Please Wait, I have no command line, and I can't reinstall. What do I do? Answers in layman's terms please - I'm keen to get away from the awful Microsoft, but definitely a Newbie...

Do you perhaps have two hard disks?

adrian15

---

