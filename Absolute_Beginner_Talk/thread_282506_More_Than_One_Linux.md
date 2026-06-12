---
title: "More Than One Linux"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by mengd2002 on 2006-10-22
Hi,

I have WIN XP Pro and Ubuntu 6.06 on my machine.  Given that I have a rather large second disk drive, I'd like to install Freespire as well.  What ramifications will this have for the GRUB bootloader?  And will this cause me much grief?  Thanks.

Don

---

### Post by mengd2002 on 2006-10-22
Hi,

I have WIN XP Pro and Ubuntu 6.06 on my machine.  Given that I have a rather large second disk drive, I'd like to install Freespire as well.  What ramifications will this have for the GRUB bootloader?  And will this cause me much grief?  :( Thanks.

Don

---

### Post by H.E. Pennypacker on 2006-10-22
I don't know how GRUB deals with two different harddrives, but I do know GRUBs over a hundred operating systems.  If you, for the sake of illustration, were to install all three operating systems (XP, Ubuntu, and Freespire) on one harddrive, that would definitely work.  

Using two different drives is another story, because GRUB would be located on the MBR of a single harddrive.  I can't be of much help there.

---

### Post by ReaderRat on 2006-10-22
GRUB - HowTo set/change the default OS in GRUB
          **[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)**
GRUB - How To Do Most Anything With GRUB
          **[http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu](http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu)**

       [[color=BLUE]**GRUB HowTo**[/color]](https://help.ubuntu.com/community/GrubHowto)

---

### Post by skirkpatrick on 2006-10-22
Should still work fine.  I've got XP on one drive and Ubuntu on another.

---

### Post by ReaderRat on 2006-10-22
> **mengd2002 said:**
> Hi,

I have WIN XP Pro and Ubuntu 6.06 on my machine.  Given that I have a rather large second disk drive, I'd like to install Freespire as well.  What ramifications will this have for the GRUB bootloader?  And will this cause me much grief?  :( Thanks.

Don
 A double-post is frowned on in the forum, but feel free to ask another question.

---

### Post by aysiu on 2006-10-22
> **ReaderRat said:**
> A double-post is frowned on in the forum, but feel free to ask another question.
I've merged the two threads. In the future, the best thing to do is click the "report post" button (red octagon, white X inside).

---

