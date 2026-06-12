---
title: "Re-installing windows, need help to get grub back on"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Bohlio on 2007-06-10
< I apologize in advance for all the questions and the mass of Info, I just wanna provide all the information I can so I know exactly what i will be doing. Thank you>

After being with Ubuntu for a couple weeks and enjoying its lightning fast speed, then booting into windows to watch TV or play C&C3, I've realized that I'm sick off all the crap that is slowing my windows partition down. So, Ive decided that I'm going to re-install Windows on my computer, But i want to keep Ubunutu still. So, after I back up the data I want, then run the installation CD, Im pretty sure Grub wont load :-(. So how do i go and re-install grub, or reactivate it or whatever to get it to come up when i boot? Heres the output of "fdisk -l" if that helps...
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9       16289   130777132+   7  HPFS/NTFS
/dev/sda3           18847       19452     4867695   db  CP/M / CTOS / ...
/dev/sda4           16290       18846    20539102+   5  Extended
/dev/sda5   *       16290       18734    19639431   83  Linux
/dev/sda6           18735       18846      899608+  82  Linux swap / Solaris
```
1 is the Dell Utilitys, I dont think the windows install will screw with that.
2 Is my windows parition
I have no clue what 3 Is
4&5 are linux... But why do the two partitions overlap?? can someone explain that quickly
and 6 is my swap...

So when i install Windows, I don't know if It will allow me to choose to install to partition 2, but i hope to god it does because i don't wanna loose anything except for what currently is in sda2. I know that windows will override my MBR (by the way, where is that). Grub is stored on my sda5 correct?? just something in the MBR points to grub right? Yah So if anyone knows how to get me to boot with Grub after i install windows that would be great :-)
Thanks very very much.

---

### Post by atlfalcons866 on 2007-06-10
use the super grub disk     [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

havent tried it myself but i hear it works

---

### Post by Bohlio on 2007-06-10
I cant use the liveCD? Thats how grub got on there in the first place...

---

### Post by atlfalcons866 on 2007-06-10
did you try super grub disk?

---

### Post by taurus on 2007-06-10
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

### Post by logos34 on 2007-06-10
> **Bohlio said:**
> I cant use the liveCD? Thats how grub got on there in the first place...

you can.

sudo grub
find /boot/grub/stage1
root (hdx,y)       --> replace 'x,y' w/output from preceding command
setup (hdx)
quit

---

### Post by Bohlio on 2007-06-10
Thanks Taurus and logos34, Thats exactly what I needed. Sorry, I guess i coulda searched. But i want this to go without a hitch :-) Alright, time to attempt to re-install!. Cross your fingers for me :-P

---

### Post by Bohlio on 2007-06-11
This makes me wanna cry...  Hours later and I am still setting up windows. I hate the restarts, I hate the updates, and i hate that i cant find the Cineplayer that has DVD support that is supposed to be on my dell cd... Now i know why Ubuntu is so great in comparison.

---

