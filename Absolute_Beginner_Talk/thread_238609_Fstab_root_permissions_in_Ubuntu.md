---
title: "Fstab root permissions in Ubuntu?"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by dragonlor20 on 2006-08-17
Hi, this is my first post. I have been running solely Ubuntu for a couple of weeks now and there are of course kinks to work out:

My Music directory has it's own hard drive and it refuses to mount automatically. I changed my fstab to include it, but I believe I did some little detail wrong. It tells me that only root can perform that action. Here is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb5	/media/music	vfat	defaults	0	0	


/dev/hdb5 is the music harddrive. I have a couple of other ones that I want to mount automatically too, but I think I could do it with the solution from this one.

Thanks for any help in advance!

P.S. If anyone could point me in the direction of how to set up my ATI 9200SE graphics card, it would be a great help! It seems to have been detected by Ubuntu on install, but the 3d graphics aren't the smoothest... I have an NVIDIA card lying around here that is the equal of my card from NVIDIA, would it be worth it to just change out the cards? Thanks again!

---

### Post by meng on 2006-08-17
One assumes that the /media/music directory already exists. I imagine there would be an error if the mountpoint didn't exist.

---

### Post by bodhi.zazen on 2006-08-17
Change 

/dev/hdb5 /media/music vfat defaults 0 0

to

/dev/hdb5 /media/music vfat user,auto,rw 0 0

and in a terminal:
sudo mkdir /media/music
sudo chown root:user /media/music
sudo chmod 770 /media/music

You music partition should now mount on boot.
You can mount it as a user (without a reboot):
mount /media/music

Same format with other drives.

---

### Post by dragonlor20 on 2006-08-18
> **meng said:**
> One assumes that the /media/music directory already exists. I imagine there would be an error if the mountpoint didn't exist.

I have made that mistake on many an occasion. But on this particular occasion I remembered ;-) Thanks though...

---

### Post by dragonlor20 on 2006-08-18
> **bodhi.zazen said:**
> Change 

/dev/hdb5 /media/music vfat defaults 0 0

to

/dev/hdb5 /media/music vfat user,auto,rw 0 0

and in a terminal:
sudo mkdir /media/music
sudo chown root:user /media/music
sudo chmod 770 /media/music

You music partition should now mount on boot.
You can mount it as a user (without a reboot):
mount /media/music

Same format with other drives.


That definitely solved it. Thanks a lot, I know that once you know an OS that well they seem like easy questions, but it helps the rest of us out a whole lot for you guys to answer the easy questions.

Much appreciated!

---

### Post by bodhi.zazen on 2006-08-18
Glad to be of help. Thank you for letting me know your problem was solved.

---

### Post by Tom Brokaw on 2006-08-18
> **dragonlor20 said:**
> Hi, this is my first post. I have been running solely Ubuntu for a couple of weeks now and there are of course kinks to work out:

P.S. If anyone could point me in the direction of how to set up my ATI 9200SE graphics card, it would be a great help! It seems to have been detected by Ubuntu on install, but the 3d graphics aren't the smoothest... I have an NVIDIA card lying around here that is the equal of my card from NVIDIA, would it be worth it to just change out the cards? Thanks again!

From what I've found here and on the net, ATI's driver implementation is no good.  I can't vouch for that, but I can say I had no troubles related to my Nvidia card that weren't due to my own ignorance.  In other words, once I did what I was supposed to, it worked as it was supposed to.  I've heard that ATI's cards are less likely to do so.

---

### Post by meng on 2006-08-18
I followed the instructions here to set up my ATI Radeon Mobility, using Method 2.
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
Worked for me, YMMV of course.

---

