---
title: "GTKpod and iPod Classic Problem"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by dwilson08 on 2008-03-05
So, bit of a problem here. I decided to hook up my 80 gig Classic to my laptop the other day and decided that nothing bad could happen in linux to it right? Wrong. 

I opened GTKpod, it screwed something up and now my iPod thinks that all my music files are "other files". I thought this was a bit weird considering the GTKpod wiki even says the Classic is supported. Any ideas of how to fix this? I don't wanna go back to windows and reinstall the firmware, I don't have all the music that was on my ipod anymore... plus I have some movies on here because I don't have space on any hard drive for all of it.... 

Any help or ideas would be appreciated, thanks!

Derek.

---

### Post by misterfrad on 2008-03-08
the new 80gig ipods have an encryption on them that prevents them from being used in linux and media players other than itunes. i had the same problem, and ended up having to move all my music to windows and reinstalling my firmware.

I read somewhere that the encrytion had been cracked, but i had already moved all my music so i didnt really look into it. you might want to google it if you really want to use it on ubuntu

---

### Post by jubxie on 2008-03-08
[http://ubuntuforums.org/showthread.php?t=619615&highlight=ipod+classic](http://ubuntuforums.org/showthread.php?t=619615&highlight=ipod+classic)

This is how to do it. However, i couldn't get it to work until i used some .deb packages for libgpod-0.6.  I would restore my ipod in itunes first, as i don't know how well the ipod works going back and forth between windows/mac and linux. I think this may be a linux only solution.

Replace the compiling of libgpod-0.6 with the install of these .deb files (in order). I finally got my ipod classic 80g working, so it can be done. Don't give up!!!

Download from here: [ftp://64.22.103.45/packages/ubuntu/gutsy/libgpod/](ftp://64.22.103.45/packages/ubuntu/gutsy/libgpod/) the following packages:

libgpod2_0.5.3+actually0.6.0-0.1_i386.deb 
libgpod-dev_0.5.3+actually0.6.0-0.1_i386.deb

---

