---
title: "Ubuntu Duel Booting.. Taking the Leap"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-10-18
I currently have Windows Xp Professional and am using Ubuntu 7.04 in Virtual Box....
Well, it's time to reverse the roles and put windows where it needs to be which is
the Back seat.  I haven't decided if I want to put Windows in Virtual Box or Duel
boot and run it Natively but I need to ask these questions before I make the
decision. 

If I do the Duel Boot I plan to set up my Partitions like this

**Windows XP:**

C:  OS Partition
D:  Program Partition

**Ubuntu**

/                   
Swap
Home

Now, in the past I have always let Ubuntu do everything for me
as far as partitioning. If I do it manually what questions is it going to
ask me. I know I want ext3 file systems for sure. I also plan to give 10 gigs 
to / , 1 gig to Swap and the majority of the space to the Home partition. 

Since I have never done a Duel Boot before what should I do about the MBR?
Where does that go? Does it go on Windows or Ubuntu?

Never done a Duel Boot before so I want to be prepared and zip through it
without worry....

---

### Post by earobinson on 2007-10-18
If you follow the steps during the install everything should go well. This should tell you all about it [http://ubuntuforums.org/showthread.php?t=16287](http://ubuntuforums.org/showthread.php?t=16287).

As for the MBR you will most likley want to let grub (ubuntu) handle that, this way when you boot your computer grub will let you pick what os you want to boot into.

---

### Post by Paul820 on 2007-10-18
You should be fine with that, ubuntu won't really ask you any questions it just lets you choose the sizes you want for each patition. MBR (Master Boot Record ), you won't be able to do anything with the MBR, ubuntu will make the bootloader for you. Just make sure you have everything done correctly before hitting the commit button. BACK UP your data.

---

### Post by Orbital75 on 2007-10-18
Sounds pretty simple..... I just remember years ago I tried this with RedHat 9 and it asked
questions I didn't understand like What partition would you like to place the MBR on.
I had no idea.  It also asked if I wanted to use lilo or Grub?  I just always chose Grub.

Is it true that If I make a separate Home partition that I can upgrade and even
install another version of Linux and use that same home folder to keep all my files
and conf settings to programs?

---

