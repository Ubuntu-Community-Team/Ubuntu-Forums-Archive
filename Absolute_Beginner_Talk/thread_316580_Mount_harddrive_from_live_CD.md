---
title: "Mount harddrive from live CD"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by faraazs on 2006-12-11
I did some stupid things (not worth saying and making myself look like an idiot :) ) and now when I boot up Ubuntu on my harddrive, I get the *Grub Error 21* and Ubuntu wont boot. I have some files that I cant lose at all so what I thought I would do is load up the live cd, mount the harddrive, move all important files and settings over to another computer and then reinstall ubuntu and move them back.

Is there any better way than this? What does Grub Error 21 mean? How can I mount my old harddrive with my files on it so I can back them up?

Any help on this issue is greatly appreciated!

Thanks.

---

### Post by bodhi.zazen on 2006-12-11
> **faraazs said:**
> I did some stupid things (not worth saying and making myself look like an idiot :) ) and now when I boot up Ubuntu on my harddrive, I get the *Grub Error 21* and Ubuntu wont boot. I have some files that I cant lose at all so what I thought I would do is load up the live cd, mount the harddrive, move all important files and settings over to another computer and then reinstall ubuntu and move them back.

Is there any better way than this? What does Grub Error 21 mean? How can I mount my old harddrive with my files on it so I can back them up?

Any help on this issue is greatly appreciated!

Thanks.

To mount fro the live CD:

[list=number][*]make a mount point.[*]Mount[/list]

To list your partitons:```
sudo fdisk -l
```

To mount say /dev/hda1:

```
sudo mkdir /media/hda1
sudo mount /dev/hda1 /media/hda1
```

Now you can copy away....

Do you need help with grub ?

---

### Post by faraazs on 2006-12-11
Thanks! That worked! If GRUB could load up the disk then a few hours of work would be saved but your method of mounting worked for me! Thank you so much!

---

### Post by Famicommie on 2006-12-11
Have you tried to [reinstall GRUB](http://www.ubuntuforums.org/showthread.php?t=224351)?

---

### Post by bodhi.zazen on 2006-12-11
> **faraazs said:**
> Thanks! That worked! If GRUB could load up the disk then a few hours of work would be saved but your method of mounting worked for me! Thank you so much!

What partition is Ubuntu (in grub speak)

/dev/hda2 = (hd0,1) in grub speak.....

From the live CD:

```
sudo grub
```

This will bring up the grub prompt whcih looks like this;> grub>

Type:```
root (hdx,y)
setup (hd0)
quit
```

Where hdx,y is your ubuntu partition......

and re-boot....

---

### Post by faraazs on 2006-12-11
The correct drive was hdb1 for the mount. What would the grub speak be for this?

---

### Post by bodhi.zazen on 2006-12-11
> **faraazs said:**
> The correct drive was hdb1 for the mount. What would the grub speak be for this?

If your ubuntu root is /dev/hdb1 this translates into (hd1,0) in grub speak

Grub starts numbering with "0"

hdx,y
x=drive
y=partition on drive x

---

### Post by faraazs on 2006-12-11
I tried that. The error does not come any longer and GRUB is no longer the issue...I get a new error like this after I see the ubuntu logo and the progress bar come up:```
cannot access tty: job control turned off
``` or something to that effect...

Is my best bet just reinstalling after backing up?

---

### Post by bodhi.zazen on 2006-12-11
This is a common problem and I do not know if it has been solved.

Start here: [http://ubuntuforums.org/showthread.php?t=292533](http://ubuntuforums.org/showthread.php?t=292533)

This looks like a problem with the desktop CD install. If you re-install I would advise the alternate CD. The alternate CD is a text installer, but it is not too difficult....

[Alternate install](http://users.bigpond.net.au/hermanzone/)

---

### Post by faraazs on 2006-12-11
I read all of that...I dont think the error has to do with installation as the error came up after I have had ubuntu installed and have been using it on this drive for a few months now.

Today I upgraded my CPU to a faster CPU, installed a new DVD+/-RW drive with lighscribe technology and added a second 80gb harddrive as the slave. I did all of this in one go rather than turn ubuntu on after each installation. One of the hardware upgrades probably caused something to go wrong.

With this information, is there anything I can do?

---

### Post by bodhi.zazen on 2006-12-11
> **faraazs said:**
> I read all of that...I dont think the error has to do with installation as the error came up after I have had ubuntu installed and have been using it on this drive for a few months now.

Today I upgraded my CPU to a faster CPU, installed a new DVD+/-RW drive with lighscribe technology and added a second 80gb harddrive as the slave. I did all of this in one go rather than turn ubuntu on after each installation. One of the hardware upgrades probably caused something to go wrong.

With this information, is there anything I can do?

Hard to see how your 80 Gb slave drive or DVD caused this. I am nto sure about the CPU....

My only other thought is will the ubuntu partition boot from CD?

When you boot the live CD you get an option to boot a HD install...

Sorry I do not know more, good luck to you.

---

### Post by faraazs on 2006-12-11
> **bodhi.zazen said:**
> Hard to see how your 80 Gb slave drive or DVD caused this. I am nto sure about the CPU....

My only other thought is will the ubuntu partition boot from CD?

When you boot the live CD you get an option to boot a HD install...

Sorry I do not know more, good luck to you.Thanks for all of your help then :). I think I'll just reinstall after backing up my files. Thanks again.

---

I just reinstalled and everything is going fine now :). Thanks for all the help.

---

