---
title: "Installing windows over Ubuntu (Dual-boot system)"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by christof53 on 2005-12-28
Hi! I already have Ubuntu Breezy Badger installed on my system, and it works great! The only problem is that I can't play any of the games I want because I need windows to play them. I have a windows 98 cd and boot disk that came with my PC (Dell) and I was wondering if I could put both Ubuntu and Windows 98 on my PC, and get to choose what one to use in the BIOS. Dual-Boot system I think is what it's called. I already tried installing windows 98 and no luck, I can't do it. Do I have to uninstall Ubuntu (and if so, how do I do that?)?, or can I just install windows 98 over Ubuntu and make a dual-boot system? I hope this wasn't too confusing or anything, thanks for your time and help!

---

### Post by Dr. Nick on 2005-12-28
**[COLOR=Red]This method will delete all of your data[/COLOR]**
Windows 98 doesnt have a partition program in the installer. If you have a startup floppy use it to get a dos prompt. Then run fdisk and delete all partitions and then make 2 or 3 new ones and format them.

Then install win 98 first, then install ubuntu and it will set up dual boot automatically

[B][COLOR=Red]This method will delete all of your data
[/COLOR][/B][COLOR=Red][COLOR=Black]
I havent done this in a long time so I am a bit rusty with some of it ,but thats the general idea, If you need help with specifics just ask. [/COLOR][/COLOR][B][COLOR=Red]
[/COLOR][/B]

---

### Post by christof53 on 2005-12-28
I have a boot floppy, and whenever I try to use it I get an error. So I put in the Windows 98 CD, and continued without using the cd, and that runs DOS. I tried using fdisk with that, and it just freezes up. Am I screwed completely? or is there hope?

---

### Post by Dr. Nick on 2005-12-28
Thats weird, but their could be a solution. Have you tried to boot off your ubuntu cd and do a custom partition?

If you do a custom partition delete all partitions and make some new ones. Format the first partition fat32 and leave the rest unpartitioned. Save changes to disk and then quit the installation then try to install windows 98.

If I recall windows 98 wants a partition of type fat32 preprared before it will install, it wont make one itself. Since you have ubuntu already, windows cant "See" the harddrive since it doesnt recgonize the linux filesystems.

If  this doesnt solve your problesms post the error that windows gives you and it will help some.

The only catch about dual booting windows and linux is that windows has to be installed first

---

### Post by christof53 on 2005-12-28
That makes a lot more sense now! Windows uses FAT and I think Linux uses ext3 or something. I'm a little hazy on the partitioning to CD bit though. I used the guided partitioning so I have little knowledge on how to do this. Sorry for all these questions, I just want to get this right the first time. Thanks for your help by the way!

---

### Post by Dr. Nick on 2005-12-28
Just boot off your ubuntu cd and take it to the partitioning section. Choose custom and it should tell you what to do. Just delete all the partitions now and make one new one and you can choose the partition type for it which would be fat32, just make sure you make it big enough for windows + all games you want so you dont have to try and resize it later. I would just leave the rest of it as free space and you could probably used the guided partition on it later when you install ubuntu.

Its been awhile since ive installed ubuntu so I forgot exactly how its set up, but I remember that it had some help onscreen.

EDIT
You could possibly use the fdisk for linux to do this aswell. When you get into the installer look for the Shell option I believe (something to get you into command line basically) And using that you can delete the partitions and make a new one. If you can get their run 
fdisk /dev/hda and then choose "m" for help.

The end result should be the same, jsut a different way to do it

---

