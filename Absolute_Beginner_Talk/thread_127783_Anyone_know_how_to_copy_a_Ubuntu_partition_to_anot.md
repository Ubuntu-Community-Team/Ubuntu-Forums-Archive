---
title: "Anyone know how to copy a Ubuntu partition to another HD?"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by gigi1234 on 2006-02-09
OK I have spent the last 6 weeks trying to get Ubuntu working for me and my machine (a Thinkpad laptop). Things are finally getting peachy. The problem is I installed Ubuntu on my "experimental" hard drive. I would like to use Ubuntu on my main hard drive, which I would use with XP running a dual boot. It was so difficult to set everything up once I am not even sure I could do it again. So, is there any way I can just copy my Ubuntu partition to the new hard drive? I tried MKCDREC and also a method of tar-ing the whole partition, but I couldn't get either method to work. 

Is there any easy, straightforward way to do this? Thanks everyone...

---

### Post by Herman on 2006-02-09
The simplest and easiest way to copy and paste partitions around these days is with [GParted livecd-0.2.]("http://gparted.sourceforge.net/livecd.php")
I only have computers with single hard-disks though, I don't know what it's like running GParted in a two disk machine. I presume it will work. Please let me know for sure, I am interested.
If that doesn't work, then I know where to find a 'dd' command we can modify to do it. Also, the install CD should be able to, or 'parted' (CLI), or GParted installed in your operating system.
But I think GParted livecd will be the easiest. Download yourself a copy and burn it and try it out -you won't look back, it's great. Honest!
Don't forget to edit /etc/fstab afterwards if you need to (most likely) :D (Herman).
Edit: and GRUB, you'll need to re-install GRUB too, I believe, and/or at least edit /boot/grub/menu.lst.

---

### Post by blair on 2006-02-10
You may also want to check out the System Rescue CD as  it includes GParted ghosting utilities and other very handy tools, such as partition managers, etc. Download the ISO and burn a CD-R.

[http://www.sysresccd.org/](http://www.sysresccd.org/)

---

### Post by atoponce on 2006-02-10
[quote=Herman]The simplest and easiest way to copy and paste partitions around these days is with [GParted livecd-0.2.]("http://gparted.sourceforge.net/livecd.php")
I only have computers with single hard-disks though, I don't know what it's like running GParted in a two disk machine. I presume it will work. Please let me know for sure, I am interested.
If that doesn't work, then I know where to find a 'dd' command we can modify to do it. Also, the install CD should be able to, or 'parted' (CLI), or GParted installed in your operating system.
But I think GParted livecd will be the easiest. Download yourself a copy and burn it and try it out -you won't look back, it's great. Honest!
Don't forget to edit /etc/fstab afterwards if you need to (most likely) :D (Herman).
Edit: and GRUB, you'll need to re-install GRUB too, I believe, and/or at least edit /boot/grub/menu.lst.[/quote]

I haven't played with GParted.  Is it any good?  How does it compare with Norton Ghost?

---

### Post by Herman on 2006-02-10
> I haven't played with GParted. Is it any good? How does it compare with Norton Ghost? I'm sorry but I don't know very much about Norton Ghost, and also I'll have to try blair's link and download the latest 'System Rescue CD', my copy is old and way out of date, I don't think I have GParted on mine at all, mine still has QTParted. I guess it's time to update. Thanks, blair! :D 

GParted is an open source partitioning software based on Gnu Parted. It comes on the Ubuntu Breezy live CD, and you can also easily install it in your Ubuntu hard disk install using either synaptic, or 'add applications' on the 'Applications' menu, or apt-get in 'terminal'. These are sufficient to get the job done for most people.

I really like using GParted on its own Live CD though, it seems to work much better that way for me. The best idea is to download yourself a copy of the latest .iso and try it out for yourself. It makes jobs that used to be slow and tedious quick and easy instead. Jobs that used to be 'not recommended for newbies' like resizing ext3 and reiserfs (filesystem) partitions are simple now. 
One trick I like is to shrink my Ubuntu partition as small as I can and paste it to the last three or four GB at the end of my disk. Then if I do anything silly and 'bork' an install, I just restore it again from the spare copy at the end of my disk. (I am the inquisitive type and I'm not afraid to take risks, mainly just in my test computer though, but occasionally even with my 'good' computers). That's a heck of a lot faster than an ordinary re-install. It's easier too. 
That's my test computer in my avatar, I sometimes use it for testing possible solutions to help people with a question on the forums. GParted livecd is an extremely help to me in this regard. I use it a lot.
I have been using it through Alpha3 0.09, then livecd-0.1 and now I have the current GParted livecd-0.2 . I think it's great!
 Several people who I have given the link to have posted back to thank me for recommending it to them.
Plors is the one I found out about it from. Thanks Plors! 

Try it, you'll like it, it's only about 33.4 mb download. :-D (Herman)

---

### Post by gigi1234 on 2006-02-10
Actually I running a laptop that has ONE hard drive. But I have two hard drives that I swap back and forth, depending on my mood. It is a way to play around on one drive but have one that works as backup.

I will try the system rescue cd, which I actually think I have somewhere. 

Thanks people.

---

