---
title: "Tri-boot, XP and Ubuntu, Adding vista"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Bohlio on 2007-07-03
I currently have a dual boot set up with XP and Ubuntu. My XP partition is huge and mostly unused, so i want to shrink that and fit Vista Ultimate in there (dont ridicule me for buying it, Im getting it for free). I need someone to help me through the process and correct me if I'm wrong.
1. Defrag in XP
2. Using the live CD and gparted, shrink my XP partition the desired amount.
3. Out of the empty space, Create a new NTFS partition.
4. Reboot and pop in the Vista CD.
5. Point Vista to install onto the newly created NTFS partition (can I do this?)
6. Somehow set up grub correctly....

Vista will override my MBR correct? So then I would use the live CD and do this...
```
sudo grub

> find /boot/grub/stage1
(enter output '(hdx,y)' in next command)
> root (hdx,y)
> setup (hdx)
> quit
```
Im I am understanding this right, That will set grub back up to boot XP and Ubuntu. But how do I add an entry for windows Vista?

Any help is great, and please, point out the smallest of mistakes in my plan, I'd rather do this well prepared then blindly.

Thank you :D

---

### Post by FunkyJack on 2007-07-03
Read this for setting up grub.
[http://www.pctipsbox.com/dual-boot-vista-and-linux/]("http://www.pctipsbox.com/dual-boot-vista-and-linux/")

---

### Post by FunkyJack on 2007-07-03
File you need to edit is:
/boot/grub/menu.lst

---

### Post by Bohlio on 2007-07-03
I already have grub set up to dual boot XP and Ubuntu...

All I need to know is what entries to put into menu.lst

---

### Post by Benoone on 2007-07-03
Billy Gates does not want you to do this so he had his coders change all the rules for Vista just to tick you off and drive ya nuts.

You just can't shoe-horn in Vista like you could w2k or xp and this thread is just too short to explain why.  Right now a lot of peeps are pulling their hair out because they don't understand that Billy only wants Microsh!t products on your computer and will go to any length to ensure that happens.

Suggest highly that you visit multibooters.co.uk and spend some time there.  When done get the free program boot-us and give it a try.   Also get some real tools to partition your drive and Acronis9 to archive your disk data before you start the project.  

Sorry but Grub and Lilo are underpowered for your project.  Yes it can be done but expect it to be a full time job and a general pain in the butt.

Vista... the best thing that ever happened for Linux  :popcorn:

My friend, I do wish you well.

Regards

Benoone

---

