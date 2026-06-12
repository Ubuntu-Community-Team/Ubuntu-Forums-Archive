---
title: "backup image of win7 install using ubuntu"
date: 2011-08-23
forum: Any Other OS
---

### Post by m.fjerbaek on 2011-08-23
Hi ubuntuforums. New user here, but have been using Ubuntu on/off since version 6ish. 
My GF just recently had her Win 7 install crash and burn in an virus/malware induced shitstorm. I cant convince her to make the switch to ubuntu, so its up to me to fix her win7 install.

Thing is, its and upgraded win7 from vista, installed on a laptop with no DVD drive. I have had a long day with bootable usb sticks and confusing different types of win7 installation types. Now i'm done with that I want a much faster way to do this again.

So the plan is to:

1 ) Boot the win laptop on a bootable ubuntu usb stick
2 ) Connect to a smb share on my ubuntu box
3 ) Make a clone of the whole windows drive BEFORE malware destroys it again
4) Next time this happens, reverse the above and recover the installation much easier over LAN. 

I think _dd_ would work for the image? Is there any problems with this plan that i can't foresee? Any trouble with windows registration or other stuff?? 

Comments and/or other suggestions would be greatly appreciated.

(the usb stick could really be anything that has dd and samba. no need for 11.04 and unity for that:)) 

M. Fjerbaek

---

### Post by mips on 2011-08-23
Will work fine.

Look at [Clonezilla]("http://clonezilla.org/") and [FOG]("http://www.fogproject.org/")

You don't have to use SAMBA, NFS or a external drive will also work fine.

Be careful when using dd, it's not called 'disk destroyer' for nothing ;)

---

### Post by m.fjerbaek on 2011-08-23
Thank you mips for the quick reply, clonezilla looks fine. 
And yes. I'll do a quick man dd, can't say i use that command all the time

---

### Post by mips on 2011-08-23
> **m.fjerbaek said:**
> 
And yes. I'll do a quick man dd, can't say i use that command all the time

Just make sure you don't switch the source and destination around etc.

---

### Post by m.fjerbaek on 2011-08-24
Okay, first try didn't go to well.

Decided to do try just with dd and a random distro. 
Installed puppylinux on a usb stick. no problems there.
Booted and connected the laptop to my computer with a LAN cable.
Mounted a folder from the computer with ubuntu on the laptop under puppylinux.

Next i ran 
```
dd if=/dev/sdX bs=64k conv=noerror,sync gzip -c -9 > /mnt/networkshare/sdX.img.gz
```

After many hours the backup file is ~80gb and as i aborted the laptop was only a third through the harddrive.

So a few more questions.
1) The bs=64k parameter might be wrong? Can you speed up the process changing it? 
2) Is it possible to make sure the empty parts of the new win7 partition is just zeroes so it will compress better?

Or maybe just go with one of the other options.

---

### Post by mips on 2011-08-24
> **m.fjerbaek said:**
> 
So a few more questions.
1) The bs=64k parameter might be wrong? Can you speed up the process changing it? 
2) Is it possible to make sure the empty parts of the new win7 partition is just zeroes so it will compress better?


1) Use **bs=1M** to make it faster
2) Not as far as I'm aware. dd makes bit for bit copy (hence being used in forensics as it makes an exact image). Check out one of these suggestion to zero free space [http://answers.yahoo.com/question/index?qid=20091107183839AAY7nkd](http://answers.yahoo.com/question/index?qid=20091107183839AAY7nkd) **but first defrag the drive**.

I would suggest you don't gzip the image during the dd process to speed things up. Once you have a completed image run whatever compression algorithm you want on it for backup purposes, bz2 is pretty efficient I think.

---

