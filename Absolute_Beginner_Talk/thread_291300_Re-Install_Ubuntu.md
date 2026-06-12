---
title: "Re-Install Ubuntu"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by ubbu on 2006-11-02
Hi,
I messed up things in my installed ubuntu and had some specific errors at the beginning of some programs. So I want to re-install my ubuntu.

The thing is I have running it with XP and dual boot. I want to keep it as it is now.

How can I re-install ubuntu where it is located now without damaging any partition and dual boot option.

THanks very much in advance

---

### Post by Kateikyoushi on 2006-11-02
Well it is almost the same when you installed it in the first place.
Use manual partitioning select your existing / partition and swap partition for the installer, you can also delete the exisiting partitions and create new ones if you like then finish the install.

Just keep in mind that ntfs is you windows partition do not delete that and the installer will set up dual boot automagically for you.

Here is a dualboot installation guide. [LINK]("http://www.psychocats.net/ubuntu/installing")

---

### Post by Bartender on 2006-11-02
As long as your partitions are set up correctly, you'd just spin the install CD, go thru the steps, and install Ubuntu to the same partition that you set aside for it the first time.  Thats in Step 5 of the LiveCD.
Any idea what happened the first time?  Maybe someone can help.

---

### Post by pattymnaish on 2006-11-02
If you just run the installer again (better to use the alternate CD) it will not need to change your partitions or booting setup. I have had to re-install recently, and had no problems with it. My partitions were still intact after doing so, and the boot options were preserved (although I do use the Windows bootloader, not GRUB).

EDIT: Hmm. I typed too slowly there. Two people got in before me :P

---

### Post by ubbu on 2006-11-02
Thanks for the responds, I'll do it as you wrote. There are important files in the windows partititon so a damage would be crucial for me. But as long as you tried and had no problems nothing to worry about

> **Bartender said:**
> As long as your partitions are set up correctly, you'd just spin the install CD, go thru the steps, and install Ubuntu to the same partition that you set aside for it the first time.  Thats in Step 5 of the LiveCD.
Any idea what happened the first time?  Maybe someone can help.
It started with my WINE installing, had some error messages in terminal, I disgard those as they had no affect to any other thing. Than I mistakenly installed a winamp-like program (can't remember the exact name bt starting with an "a") for KDE desktops, and it turns with too many error messages, and after all most of the programs started to give errors like "kde" for example when I try to start Kooka:
```
 There was an error setting-up inter-process communications for KDE. The Message returned by the system was:

................."
```

As long as I know, I am using Gnome desktop but the error message is about KDE?
dunno
But this program doesn't work properly as I was scanning files with it but no more.

Things like that.

---

### Post by Bartender on 2006-11-02
ubbu -
I'm sort of a conservative type (with my PC's anyway) so take my advice for what it's worth...
You're kind of new to this Linux thing, right?  Rather than trying to make non-native programs work, I think you'd be happier installing some of the Ubuntu-supported app's, then following [these]("http://www.ubuntuforums.org/showthread.php?t=182902") directions for making them work better.  Also try Automatix for a wider selection of music players, etc.
Just my 2 cents
Also, take hand-written notes of any changes you make or progams you install.  It's just too darn easy to change some setting one day, then a week later you want to reverse it and can't remember what the heck you did.  My Linux binder keeps getting thicker.  I had to add more tabs to keep it organized.

---

### Post by ubbu on 2006-11-02
Right, I am new to it and want to learn/experience it fully to remove Windows from my pc forever. But quite early I guess. Thanks for your words, I ll take them as an advice.

---

