---
title: "dual boot question"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by viergeame on 2007-03-27
Maybe this is a stupid question, but bear with me.  I am working on installing Ubuntu on my second computer, I'm setting that one up as a dual boot for gaming reasons.  I have two hard drives and I am putting Ubuntu on the second one.  My question is, will I still be able to access things on the Windows drive with Ubuntu and vice versa?  If so, is there anything special I will have to do for this?  I don't want to get too far into installing and getting everything set up and find out that I did something wrong and won't be able to access the media I kept on the other drive.

---

### Post by kittyhawk63 on 2007-03-27
> **viergeame said:**
> Maybe this is a stupid question, but bear with me.  I am working on installing Ubuntu on my second computer, I'm setting that one up as a dual boot for gaming reasons.  I have two hard drives and I am putting Ubuntu on the second one.  My question is, will I still be able to access things on the Windows drive with Ubuntu and vice versa?  If so, is there anything special I will have to do for this?  I don't want to get too far into installing and getting everything set up and find out that I did something wrong and won't be able to access the media I kept on the other drive.

The simple answer is yes. You can boot to either drive and use them as you have set them up. One will not affect the other. If you have any problems, post them here.
kh

---

### Post by nickoli_02 on 2007-03-27
Since Ubuntu uses the ext3 filesystem, you'll need a special program for windows to be able to read your Ubuntu partition. Sorry, I can't remember the program, but you should find it by searching google/forums. Linux currently offers read support of NTFS partitions, and is working on the write support. Last I heard, write support just moved out of the experimental stage, so you might want to wait a bit for write support to improve, unless you don't mind the risk of corrupting your NTFS partition. 

Many dual booters create a FAT32 partition to be used as media storage so that both windows and linux can access the files easily, you might want to look at going this route. Or, if you install the program to enable windows to see ext3 filesystems, you wouldn't really need the FAT32 partition. You also wouldn't have to worry about fragmentation ;)

---

### Post by kittyhawk63 on 2007-03-27
[FONT=monospace]If you have any problems getting dual boot to work follow these steps. They helped me to resolve my dual booting problem.

In terminal:
sudo update-grub

and then followed the instructions given here:
[http://www.ubuntuforums.org/showthre...light=dualboot]("http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot")

[/FONT]Be sure to remove the # before  hiddenmenu or hidden, whichever you have.

---

### Post by sirkism on 2007-03-27
here you go

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by nickoli_02 on 2007-03-27
ah there it is! thanks sirkism :popcorn:

---

### Post by viergeame on 2007-03-27
> **nickoli_02 said:**
> Since Ubuntu uses the ext3 filesystem, you'll need a special program for windows to be able to read your Ubuntu partition. Sorry, I can't remember the program, but you should find it by searching google/forums. Linux currently offers read support of NTFS partitions, and is working on the write support. Last I heard, write support just moved out of the experimental stage, so you might want to wait a bit for write support to improve, unless you don't mind the risk of corrupting your NTFS partition. 

Many dual booters create a FAT32 partition to be used as media storage so that both windows and linux can access the files easily, you might want to look at going this route. Or, if you install the program to enable windows to see ext3 filesystems, you wouldn't really need the FAT32 partition. You also wouldn't have to worry about fragmentation ;)

It seems like this is going to be a lot less difficult than I expected.  For some reason I expected that the answer would be either a straight out no, or something insanely complicated, not because I find Ubuntu to be complicated but because I seem to have terrible luck with things like this.

---

