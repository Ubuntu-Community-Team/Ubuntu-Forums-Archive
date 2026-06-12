---
title: "ubuntu 7.04 probelms"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by tyman1180 on 2007-05-23
iv recently downloaded the Ubuntu 7.04 live cd and i got it burned and checked it right it will boot up to the Ubuntu screen i will hit start or install and it says its loading. Now people tell me it will take a while for Ubuntu to boot up but it shouldn't take 24 hours yes i left my computer run  24hrs and when i came back it still said loading. Iv wanted to try Ubuntu so bad iv been trying for 3 months (internet is kinda slow so it takes a while to download things) iv tried the new xp install thing that took like 3 tries and when i finally thought i got it right their was an error that i couldn't fix and now i just downloaded this thought it was going to work since i got the ubuntu screen to come up BUT NO IT WONT LOAD!!!! 

PLZ any help id really love to give ubuntu a go but obviously it hates me

---

### Post by lazyart on 2007-05-23
what are your system specs?  Especially how much memory?

---

### Post by homergreg on 2007-05-23
the iso could be corrupt.  did you do an md5 sum against it?

---

### Post by tyman1180 on 2007-05-23
Pentium 4, 2.80 GHz,512 MB of Ram, Nivida GeForce 4 Mx420, Samsung DVD-Rom SD-616T and HL-DT-ST CD-RW GCE-8481B, and no actually i was goiing to do a md5sum but forgot and ran crapcleaner so it deleted my download so how can i rescan the disk

---

### Post by drowner on 2007-05-23
It is possible that your computer is not quite powerful enough to run the liveCD.

---

### Post by tyman1180 on 2007-05-23
why wouldnt it be powerful enough iv read about tons of other people that run ubuntu on crappier pc's then me

---

### Post by drowner on 2007-05-23
> **tyman1180 said:**
> why wouldnt it be powerful enough iv read about tons of other people that run ubuntu on crappier pc's then me

I run ubuntu on a crappier PC than you.

But i can't run a liveCD. THe live cd runs the operating system from the RAM and the CD, and is very heavy of your computers resources.

THere is an option when you first boot the CD to check the integrity of the disk. Try that.

---

### Post by tyman1180 on 2007-05-23
is there any other way i can try it out then???? and i already tried that and it did the same thing as the start or install thing did is their any way i can like import the iso or files back in to do a md5sum i have the disc in right now and everything looks ok

---

### Post by drowner on 2007-05-23
> **tyman1180 said:**
> is there any other way i can try it out then???? and i already tried that and it did the same thing as the start or install thing did 


I would assume the disc is corrupted then.

Download a new .iso, maybe.

---

### Post by icechen1 on 2007-05-23
> **drowner said:**
> I would assume the disc is corrupted then.

Download a new .iso, maybe.

INPORTANT:burn the cd at a slower speed(like 4X or slower)

---

### Post by tyman1180 on 2007-05-23
great this could take a whole day cuz my internet isnt the fastest :(

---

### Post by lamalex on 2007-05-23
> **drowner said:**
> It is possible that your computer is not quite powerful enough to run the liveCD.

are you kidding? 2.8 ghz? 512mb? That should run the cd fine.

---

### Post by drowner on 2007-05-23
> **Iamalex said:**
> are you kidding? 2.8 ghz? 512mb? That should run the cd fine.

Yeah, probably. I said it was POSSIBLE, looking back, its not very likely.

I'm going with the CD is corrupted... as it hung when trying to ananlyse it's integrity.

---

### Post by tyman1180 on 2007-05-23
ahh ur kidding me i really dont want to spend a whole day downloading again i wonder what could of went wrong with the burn i burned it at 1x and everything looks fine and when i insert the cd while windows in running a splash screen pops up

---

### Post by leafs555 on 2007-05-23
i have a problem installing programs i get this...,

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What should i do? i tried to run it, but nothing happens!!!

Someone help, im kinda new to this

---

### Post by bone43 on 2007-05-23
> **tyman1180 said:**
> is there any other way i can try it out then???? and i already tried that and it did the same thing as the start or install thing did is their any way i can like import the iso or files back in to do a md5sum i have the disc in right now and everything looks ok

Down load the alternate CD its a text base install should work fine.

[http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/)

A how to just skip the dual boot part...

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by medicineman24 on 2007-05-23
I have almost the same hardware, live cd works great.  Try buning the cd again.  If no such luck, you may have to re-download the iso.  BTW for some reason i burned my live disk at 4x and it burned horribly with so many errors, I then tried the fastest speed and it worked almost perfect.  WTF?

---

### Post by jerrylamos on 2007-05-23
> **tyman1180 said:**
> Pentium 4, 2.80 GHz,512 MB of Ram, Nivida GeForce 4 Mx420, Samsung DVD-Rom SD-616T and HL-DT-ST CD-RW GCE-8481B 

Ubuntu 7.04 Feisty runs just fine, fast, and crisp with 1.0 GHz pentium, 512 MB Ram.  Actually ran almost that well with 384 MB Ram.  That's for applications, internet, Office, photos, file sharing, yata yata. I don't do games nor 3D desktop so those can probably use as fast a hardware is made and more.

I'd think the situation hinges on the Nivida GeForce 4 Mx420.  I don't have one, so do a search on the forums for Nivida GeForce (make sure spelling is right) since in passing I've seen a number of people mention problems with Ubuntu and the Nivida driver.

There are some things to try right off, for example on the CD Live Boot Options, do "Safe Graphics Mode" which uses the very conservative video driver VESA.

Another thing to try is at the CD Live Boot Options, push F6 and delete the word "quiet" which should get you a lot more on the screen, and try to post what the last few lines say.

Also on boot at CD Live Boot Options screen, push F1 and look at some of the boot options; I don't have that screen up, however F4 may give some options like noacpi.

Cheers, Jerry

---

### Post by Hobo Joe on 2007-05-23
> **medicineman24 said:**
> I have almost the same hardware, live cd works great.  Try buning the cd again.  If no such luck, you may have to re-download the iso.  BTW for some reason i burned my live disk at 4x and it burned horribly with so many errors, I then tried the fastest speed and it worked almost perfect.  WTF?

Are you sure? Cuase that would be crazy! :o

---

### Post by medicineman24 on 2007-05-24
Yea I'm sure.  Maybe some nero software issues?  Or an act of god.

---

### Post by tyman1180 on 2007-05-25
hey i finally got ubuntu to work and im posting on it right now the only problem now is i want to save everything iv done iv read some different tutorials and my usb thing is a little different it looks like this 

Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 252M   33M  219M  14% /lib/modules/2.6.20-15-generic/volatile
tmpfs                 252M   33M  219M  14% /lib/modules/2.6.20-15-generic/volatile
varrun                252M  104K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M  116K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
tmpfs                 252M   72K  252M   1% /tmp
/dev/sdc1             236M   89M  148M  38% /media/My 256MB
ubuntu@ubuntu:~$ 
 and where it says /dev/sdc1 on mine it says sda1 on others and tutorials so i was wondering what to do ???? any help

---

### Post by jerrylamos on 2007-05-25
Ubuntu Feisty has some "new features" which include having different /dev/s??? from one system to the next, from one install to the next, and even from one boot to the next.  You pretty much have to take it as it is and always check if you need to.  For example, I never know what the USB pen drive is going to be, but it is formatted ext3 so I could change the label like so:
df -h 
to see what Ubuntu called it this time, could be /dev/sda1 or /dev/sda3 or who knows what
umount /dev/s???     (use whatever df -h showed it as)
sudo e2label /dev/s??? casper-rw       use whatever you want for a label

That way every time I boot the USB pen drive is /media/casper-rw 
and I don't have to care what the /dev/s??? turned out to be.  Cheers, Jerry;)

---

### Post by tyman1180 on 2007-05-25
so could you give me some step by step instructions to go by for this it would be greatly appreciated since im just learning all these sudo commands and stuff.

---

### Post by tyman1180 on 2007-05-26
Anyone got any instructions on backing up my data on a usb

---

