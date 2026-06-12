---
title: "Ubuntu Partition help"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by `danny on 2007-07-11
I want to take some space off my Vista partition and give it to my Ubuntu Install but I do not know how. Is there any way to do this without screwing up either partition?

---

### Post by dhughes on 2007-07-11
Gparted it's a partitioning application that comes with Ubuntu but it's also available as a LiveCD. Download it and burn it to a CD, reboot and see if you like it, at the very least you can look around and see what it detects of you setup.

 It's pretty easy to use, it's graphical and pretty much point and click, slide sliders then press OK.

 Make sure you backup your data before use just in case something goes wrong or you goof up.

 [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

 Here's what it looks like.
 [[IMG]http://img388.imageshack.us/img388/1226/gparted1bigva1.jpg[/IMG]](http://imageshack.us)

---

### Post by bren on 2007-07-11
some others have mentioned that it is better to partion using vistas own partion tool rather than gparted....
don't know if this is true

type resize partition into vista help and see where you get to

---

### Post by kavon89 on 2007-07-12
Yeah, I've heard Vista + Ubuntu don't get along. Vista likes to take control of what boots on your system, and sometimes messes your Ubuntu partitions up if you install Vista after Ubuntu.

---

### Post by hyper_ch on 2007-07-12
Why do you have ext2 partitions and not ext3?

---

### Post by loomee on 2007-07-12
Hello,
I have a similar but devastating problem.
I installed ubuntu 7.04 and when I ran the installation I clicked on GNOME format then I got an error message so I decided to leave that section and proceed with installation. I was able to install Ubuntu which I am using right now to write this post. The problem is my windows OS is gone, I can not access it, all I see is disk1 in the desktop with an empty 73GB storage which is the size of my HD. My question is, did I really lose my windows OS and all my files? and is there away to restore or recover my OS and files?

I would appreciate any help.

---

### Post by `danny on 2007-07-12
Gpart worked very nicely, thanks for the help guys.

---

### Post by dhughes on 2007-07-29
> **hyper_ch said:**
> Why do you have ext2 partitions and not ext3?

 It's just a screen shot off the Gparted website. It must be an old photo.



 Glad to hear it worked `danny.

---

### Post by ev5unleash1 on 2007-07-29
By the looks of it you have Ubuntu installed twice on the system with the EXT 2 and 3 or you have one for linux storge. I'm not sure how to get Ubuntu to boot you may try clicking F8 or ESC right before the Windows Vista Boot screen comes up you may have a function to let Ubuntu start up first like another boot to let go first. You should also delete that other partition that is taking up space unless it's something you need.

---

