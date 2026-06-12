---
title: "Oops... I deleted my Windows partition."
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by transparent9 on 2007-05-22
I'm sorry if this has been covered, but I don't even know how to begin searching for this type of problem...

Basically, I was trying to follow the How To to get my existing dual-boot Windows XP partition to run under VMWare Player.  

Usually I'm pretty good at following directions... but I fear I've made a grave mistake.  

At one point, the How To says to reboot into Windows to set up a hardware config, but suggests that I copy the VMWare Tools to the Windows partition for easy access later.

Stupidly, I was in "sudo -i" mode, and typed: cp windows.iso /dev/sda1, as /dev/sda1 is my Windows partition.

Now I realize two things.  One, my drive is mounted as /media/sda1.  Two, I should have done something more like "cp windows.iso /media/sda1/windows.iso"  Such are the consequences of carelessness while in sudo.

Anyway... now it appears my partition is gone?  It's still there of course, parted sees it, but it doesn't recognize it.  a VMWare Tools volume is mounted in "Computer" view, and the hardware info applet shows my 20gb Windows partition as "VMWare Tools".

Is there any way to recover from this, or am I screwed?

Thanks in advance...

---

### Post by Mr.Beast on 2007-05-22
Hi, 
it sounds to me like you have made a big of an error there.
Firstly, how grave is it to you, what was in the XP partition that you need or want deparately.  music, pictures, documents?
What I think you need to do is download and burn to CD some system recovery tools, preferably with a different computer. (Leave your current one on if possible, do not switch it off.)

I'm sure that there are knoppix based system rescue CD's with file recovery utilities based on it.

Realistically, you stand a pretty good chance of getting back some, if not all of your data.  But you might have to reinstall XP.

I'd give you more advice if I had the experience directly with this area but I haven't done file recovery under linux (yet!)

hope you get on allright

---

### Post by AnRa on 2007-05-22
If you don't find a better answer than this, you should try TestDisk using the [System Rescue CD](http://www.sysresccd.org/). Good luck! ;)

---

### Post by transparent9 on 2007-05-22
One thing I forgot to mention: when I click on the VMWare Tools volume, it appears to be the contents of the windows.iso file.  

I'm just wondering, if I really replaced my Windows partition with this file, or if I just messed up some linking somewhere, or if it appended that file to the beginning of my partition.  

If it's the middle one, I'm hoping there's a way to reset/repair things so everything's back the way it was.

If it's the others, then I guess it's file recovery time...

---

### Post by transparent9 on 2007-05-22
Is there anyone that knows what exactly happened when I executed as root the command:

sudo cp windows.iso /dev/sda1

?

---

### Post by weatherman1293 on 2007-05-22
CP means copy, so you copied windows.iso to /dev/sda1.

When you remove a partition, or reformat, all you really do is delete the index on the hard disk (at least with NFTS). There are some companies around that can get you at least some of your data back, but, the cost isn't the cheapest around.

---

### Post by LaRoza on 2007-05-22
It looks like you replaced the entire contents of /dev/sda1 with windows.iso.

---

### Post by annda on 2007-05-22
sorry, i don't. but it looks like you have overwritten the device file only. have you tried rebooting into windows?

oh, it might not be possible, since grub will look for the /dev/sda1 file/link to device, which is probably damaged (i.e. replaced with an .iso file). but try to see if it has really been changed.

---

### Post by annda on 2007-05-22
you can check if your partition has actually been overwritten by booting from ubuntu live cd and seeing what it shows in sda1

---

### Post by brennydoogles on 2007-05-22
> **transparent9 said:**
> I'm sorry if this has been covered, but I don't even know how to begin searching for this type of problem...

Basically, I was trying to follow the How To to get my existing dual-boot Windows XP partition to run under VMWare Player.  

Usually I'm pretty good at following directions... but I fear I've made a grave mistake.  

At one point, the How To says to reboot into Windows to set up a hardware config, but suggests that I copy the VMWare Tools to the Windows partition for easy access later.

Stupidly, I was in "sudo -i" mode, and typed: cp windows.iso /dev/sda1, as /dev/sda1 is my Windows partition.

Now I realize two things.  One, my drive is mounted as /media/sda1.  Two, I should have done something more like "cp windows.iso /media/sda1/windows.iso"  Such are the consequences of carelessness while in sudo.

Anyway... now it appears my partition is gone?  It's still there of course, parted sees it, but it doesn't recognize it.  a VMWare Tools volume is mounted in "Computer" view, and the hardware info applet shows my 20gb Windows partition as "VMWare Tools".

Is there any way to recover from this, or am I screwed?

Thanks in advance...

TestDisk looks like it is the way to go for you. I don't know if it can restore bootability to the partition, but I know that PhotoRec (which is included in TestDisk) can recover your files. There is a great link for testdisk [here]("http://www.cgsecurity.org/wiki/TestDisk"), a great link for PhotoRec [here]("http://www.cgsecurity.org/wiki/PhotoRec"), and a great thread for what to do after using PhotoRec [here]("http://ubuntuforums.org/showthread.php?t=447849"). TestDisk is available through the repositories, and I would make it your first bet!!

---

### Post by louieb on 2007-05-22
> **annda said:**
> sorry, i don't. but it looks like you have overwritten the device file only. have you tried rebooting into windows?...file). but try to see if it has really been changed.

I'm  with annda : /dev/sda1 is a device file so its trashed. My wild as guess of the day XP will boot and you will get some very strange errors when you boot Ubuntu.

---

### Post by transparent9 on 2007-05-22
Thanks for explaining what's happening here everyone.  That's what I get for having twitchy fingers...!

Tried testdisk, and booting from grub doesn't work.

I'll see about file recovery with some other tools.

---

### Post by brennydoogles on 2007-05-22
> **transparent9 said:**
> Thanks for explaining what's happening here everyone.  That's what I get for having twitchy fingers...!

Tried testdisk, and booting from grub doesn't work.

I'll see about file recovery with some other tools.

Did you use PhotoRec, which comes with TestDisk?? That will most likely be your way to go.

---

### Post by transparent9 on 2007-05-22
Just wanted to share my progress, in case anyone ever types "sudo cp windows.iso /dev/sda1" again by accident.

I used testdisk to rebuild the boot sector, then repair the MFT.  Then I adjusted my geometry a little, it appeared that the heads were listed as 16, testdisk thought it should be 255.  After this, the drive showed up in parted as an NTFS drive.  

Then I booted off a Windows XP install CD, dropped into the recovery consol, and did chkdsk then fixboot.  

Upon reboot, I was able to start up Windows again, though things were slightly broken (taskbar stuck not showing any icons or start bar, just a few grey pixels line at the bottom of the screen, login taking forever, etc) so I booted off the Windows install CD again and did a repair install, which to my understanding replaces all the system files.  My applications, documents and settings were left intact.

Now my Windows partition seems fine. 

I then edited my /etc/fstab information so that there was an entry like such:
```

/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1

```

After a reboot, I can now browse the volume and it sees my windows partition files.

However, the volume properties show this volume still as "vmware tools", with a joliet filesystem, like it was still the iso.

Where do I go to fix this?

---

