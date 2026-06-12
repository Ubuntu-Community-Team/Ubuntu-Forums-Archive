---
title: "dual boot Vista and Ubuntu (an instruction page)"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by molly_001 on 2006-07-02
For this thread, please, no OS bashing.  That's already been hashed out :-)
 
I've put together a page displaying instructions on how to dual boot Vista and Linux (in this case, Ubuntu 6.06).   (27 July 2006: There are now also instructions for triple boot; also, for adding Vista without messing up a previous Ubuntu install; also, for dual booting over two physical hard drives.)
 
There are other pages out there explaining broadly how to accomplish this, but those pages didn't seem to be geared towards the Linux beginner.
 
Please note these are instructions for a machine containing only a GNU/Linux distro which uses GRUB (such as Ubuntu 6.06) and Vista Beta 2.  No Windows XP or salient leftovers from XP are included in the instructions on my page.
 
Thanks and here it is:
[http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx](http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx)

---

### Post by molly_001 on 2006-07-03
Here's a 24-hour bump.
 
Also, since the forum breaks up the original URL, here
is the TinyURL for the page:
**[http://tinyurl.com/hrbhy](http://tinyurl.com/hrbhy)**

---

### Post by molly_001 on 2006-07-04
Here's a 36 hour bump (my final bump) since my 24 hour bump merely recycled it for the same part of the world as the day before (doh!)
 
Dual Boot Vista and Linux (Ubuntu 6.06)
:
**[http://tinyurl.com/hrbhy]("http://tinyurl.com/hrbhy")**

---

### Post by ProjectGod on 2006-07-04
coolies! cheers! add the link to commonmancomputing in your signature... right now its just plain text.

---

### Post by Loffe_ on 2006-07-07
Is there a way of installing Vista Beta witout reinstalling Ubuntu?

---

### Post by jordanmthomas on 2006-07-07
If you have a livecd version of Ubuntu handy, you can install Vista without reinstalling Ubuntu.

Boot up with the livecd and resize your partitions.
Install Vista to your new free space.

Reboot with livecd again and from a terminal run
```

sudo grub-install /dev/sda1

```

You may need to change the sda1 to the proper location.

---

### Post by Loffe_ on 2006-07-07
```

ubuntu@ubuntu:~$ sudo grub-install /dev/sda7
Could not find device for /boot: Not found or not a block device.

```

Nope, it doesn't work...

---

### Post by richbarna on 2006-07-07
> **jordanmthomas said:**
> 
Reboot with livecd again and from a terminal run
```

sudo grub-install /dev/sda1

``` 


Have you actually tried this? (from the live cd I mean).
Or do you mean that you use the live cd to boot to the operating system on the first harddrive (ubuntu hopefully), and then open the terminal from THERE?

Otherwise it won't work.

---

### Post by molly_001 on 2006-07-07
> **Loffe_ said:**
> Is there a way of installing Vista Beta witout reinstalling Ubuntu?

This is a great question.

I'm certainly still a Linux beginner, but it was my impression that installing Vista Beta 2 at anytime would overwrite the MBR on the volume.  

This would wipe out access through GRUB to your existing Ubuntu installation.  So I wrote my instructions for dual boot of Vista and Ubuntu (link below) to start out with the Vista install first chronologically.

---

### Post by jordanmthomas on 2006-07-07
> **richbarna said:**
> Have you actually tried this? (from the live cd I mean).
Or do you mean that you use the live cd to boot to the operating system on the first harddrive (ubuntu hopefully), and then open the terminal from THERE?

Otherwise it won't work.


It worked when I wanted to give Vista a try.  Vista put its stuff on the MBR and then I just replaced it with Ubuntu's off the CD.  At least I think that's how I did it...it's been a while now.

---

### Post by RIS on 2006-07-07
Since it's about dualboot Ubuntu and Vista:
I had Vista installed on one hd and installed Ubuntu 6.06 on another hd. Grub did not discover Vista, and now I can't boot Vista. It's not an option in the boot menu.
Is there a simple way to fix this problem? 
(Linuxnewbee)

---

### Post by molly_001 on 2006-07-07
> **RIS said:**
> Since it's about dualboot Ubuntu and Vista:
I had Vista installed on one hd and installed Ubuntu 6.06 on another hd. Grub did not discover Vista, and now I can't boot Vista. It's not an option in the boot menu.
Is there a simple way to fix this problem? 
(Linuxnewbee)

RIS --

You should be able to do this as you described, but you would need to the edit GRUB and it (GRUB) would need to be on the primary boot drive.

For instance, with Vista is on a secondary hard drive (second of two, in this scenario) you would edit the GRUB menu.lst file, in the 'title' section of menu.lst file, so that it would point to root (hd1,0) for secondary drive Vista.

For much more, read all of this page below, but in particular the section called " Quick Guide to Grub's Numbering System"
site: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Loffe_ on 2006-07-08
I solved the problem using the live-cd and this page :D 
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub)

//Loffe

---

### Post by cjm5229 on 2006-07-08
You will have to put Vista in the first partition on your hdd, just like any other windows install, then after you reinstall grub, you have to boot into Ubuntu and edit the menu.lst to add Vista.

---

### Post by seshomaru samma on 2006-07-08
> **RIS said:**
> Since it's about dualboot Ubuntu and Vista:
I had Vista installed on one hd and installed Ubuntu 6.06 on another hd. Grub did not discover Vista, and now I can't boot Vista. It's not an option in the boot menu.
Is there a simple way to fix this problem? 
(Linuxnewbee)


In the terminal put 
```
sudo gedit /boot/grub/menu.lst
```

then add these 3 lines at the bottom of the document
```
title vista 
rootnoverify (hd0,2) 
chainloader +1


```
and save

you might need to adjut the (hd0,2) part of the second line according to where Vista is on your harddisk
If you dont know , i think running fdisk would help 
```
sudo fdisk -l
```

hope this helps

---

### Post by molly_001 on 2006-07-08
Loffe --

Re: putting Vista on an Ubuntu machine, and saving/keeping your previous Ubuntu install
 
If you managed to do that above, it would be very helpful to allow everyone to borrow from your experience.  Herman this weekend is going to link his dual boot site to my existing Vista+Ubuntu page.  As you have read, my instruction page is for those starting fresh with a previously clean, dedicated Vista/Ubuntu machine.  Please consider working on a Loffe-credited page, I will host the page (or link to it) and create it according to your desire, if you wish.   Then  the page will be helpful to much more folks, too.

Thank you.

P.S.  There is a lot of cross-posting in this thread due to various situations.  Posters, if you can remember, please address your further posts to the specific person you are replying to.  Thanks!

---

### Post by Loffe_ on 2006-07-08
> **molly_001 said:**
> Loffe --

Re: putting Vista on an Ubuntu machine, and saving/keeping your previous Ubuntu install
 
If you managed to do that above, it would be very helpful to allow everyone to borrow from your experience.  Herman this weekend is going to link his dual boot site to my existing Vista+Ubuntu page.  As you have read, my instruction page is for those starting fresh with a previously clean, dedicated Vista/Ubuntu machine.  Please consider working on a Loffe-credited page, I will host the page (or link to it) and create it according to your desire, if you wish.   Then  the page will be helpful to much more folks, too.

Thank you.

P.S.  There is a lot of cross-posting in this thread due to various situations.  Posters, if you can remember, please address your further posts to the specific person you are replying to.  Thanks!


Ok, i'll write together a tutorial...

---

### Post by RIS on 2006-07-08
I just want to say Thank You to all, helping me out with the problems I had with the dualboot Ubuntu/Vista. Problem fixed!

---

### Post by testube_babies on 2006-07-08
I, too, just want to say thanks.  Thanks in part to this thread I am now triple-booting Vista, Dapper, and XP.

---

### Post by molly_001 on 2006-07-09
I'm glad this thread and the dual boot page at my site was able to help.

testube-babies ... If you are now triple-booting, you might consider writing up a set of instructions for this accomplishment.  Then we can your testube_babies-credited page to the dual boot Vista page.  That would help a lot more people.  Thanks!

---

### Post by molly_001 on 2006-07-09
Herman --

Thanks very much for adding the links to the Dual Boot Vista page when you get the chance.

Loffe is writing a page for "Dual Boot Vista and Ubuntu on a single drive with previous Ubuntu instal; -- and Saving/Keeping your Ubuntu install in the process."

Perhaps testube_babies can contribute towards a triple boot page, then we'll really have a lot of bases covered.

Thanks again.

---

### Post by testube_babies on 2006-07-09
I'm planning on creating a triple-boot tutorial.  But don't expect to see it for a while.  I should hopefully be able to get a good start on it next week.

---

### Post by molly_001 on 2006-07-09
Thank you, testube_babies.  Looking forward to it!

---

### Post by Loffe_ on 2006-07-11
Now I have written a tutorial on how to dual boot Ubuntu / Vista WITHOUT reinstalling Ubuntu!

You can read it on [http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot](http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot)

Reards
Loffe

---

### Post by testube_babies on 2006-07-21
The triple-boot tutorial is now up!

[http://www.ubuntuforums.org/showthread.php?t=220452](http://www.ubuntuforums.org/showthread.php?t=220452)

It's kind of wordy.  Sorry.  ;)

---

### Post by molly_001 on 2006-07-27
The site in my signature now includes instructions and/or links to:

* dual boot Vista and Ubuntu 6.06

* dual boot XP and Ubuntu 6.06

* triple boot XP, Vista, and Ubuntu 6.06 (thanks testube_babies)

* dual boot Vista or XP and Ubuntu over a previous Ubuntu install, without the need to reinstall Ubuntu (thanks Loffe)

* dual boot over two physical hard drives  (thanks confused57)

---

### Post by homrJ on 2006-09-04
> **Loffe_ said:**
> Now I have written a tutorial on how to dual boot Ubuntu / Vista WITHOUT reinstalling Ubuntu!

You can read it on [http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot](http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot)

You say in your tutorial that i will need the Dapper-cd, but unfortunately, I  don't have it at hand. Will I be able to do this with the breezy-livecd instead?

Anyways, i tried, and followed the exact instructions. When rebooting, however, all that comes up is the text "GRUB", and the computer freezes.

Do you know what i've done wrong?

homrJ

---

### Post by Loffe_ on 2006-09-04
> **homrJ said:**
> You say in your tutorial that i will need the Dapper-cd, but unfortunately, I  don't have it at hand. Will I be able to do this with the breezy-livecd instead?

Anyways, i tried, and followed the exact instructions. When rebooting, however, all that comes up is the text "GRUB", and the computer freezes.

Do you know what i've done wrong?

homrJ

I think the Breezy disc will work, haven't tried it though.

I am in no way an expert of GRUB, but I think GRUB can't find the all it files. Did you set GRUB's root to your Ubuntu disc?

In my example i used: root(hd0,2)
But that may be something totally different on your machine...

---

### Post by homrJ on 2006-09-04
I have Vista on hd(0,0) and ubuntu at hd(1,0).

I type:
grub> root hd(1,0)
grub> setup hd(1,0)

Everything apparently installs correctly. That's the way it's supposed to be right?

Before attempting this guide, I simply got an "error loading os" at startup, now it freezes after printing "GRUB ".

Any idea?

---

### Post by Athanasius on 2007-03-02
Just popping in the live cd doesn't work.  Ubuntu doesn't recognize the hard drive, I think Vista does this on purpose though

---

### Post by Levitation on 2007-03-09
Will this work on a system that *already *has Vista on it?

---

### Post by rudolfbj on 2007-04-12
Hi.

I just bought a new PC, a dell inspiron 1501. And without telling me they had pre-installed Vista home basic. Now, my problem is that there isn't any partition created for Ubuntu and the partition magic 8 are not compatible with Vista. So could anyone tell me if there is a way to create a partition for linux from vista, if there is any partition tools that works? I have already installed some programs on vista so I would prefer if I didn't have to reinstall it. Btw, I'm a first-timer with Linux.

---

### Post by dmorris68 on 2007-04-13
> **rudolfbj said:**
> Hi.

I just bought a new PC, a dell inspiron 1501. And without telling me they had pre-installed Vista home basic. Now, my problem is that there isn't any partition created for Ubuntu and the partition magic 8 are not compatible with Vista. So could anyone tell me if there is a way to create a partition for linux from vista, if there is any partition tools that works? I have already installed some programs on vista so I would prefer if I didn't have to reinstall it. Btw, I'm a first-timer with Linux.

GParted.  Burn the bootable ISO and go to town, it supports Vista's flavor of NTFS and works as well or better than any commercial product.

[http://gparted.sourceforge.net](http://gparted.sourceforge.net)

---

### Post by jpyanowski on 2007-06-08
> **rudolfbj said:**
> Hi.

I just bought a new PC, a dell inspiron 1501. And without telling me they had pre-installed Vista home basic. Now, my problem is that there isn't any partition created for Ubuntu and the partition magic 8 are not compatible with Vista. So could anyone tell me if there is a way to create a partition for linux from vista, if there is any partition tools that works? I have already installed some programs on vista so I would prefer if I didn't have to reinstall it. Btw, I'm a first-timer with Linux.

Bring up the start panel. Right click on computer and click on manage. You should see the computer management  program. On the left side click on disk managemet. This will show all the disks on the computer. Right click on your C: dirve and click shring volume. Set the new size (reduced by the size of your new ubuntu volume. Make your ubuntu volume a simple volume with fat 32 file system. Install ubuntu....enjoy.;)

---

### Post by neilneil2000 on 2007-07-04
Hi,

I am having problems with triple booting XP, Vista and Ubuntu 7.04.

My situation is this:

1. I have had Windows XP Pro 32 bit installed for about a year
2. I got a copy of Windows Vista Business 32 bit a couple of months ago and installed that on another partition on the same drive.  When I boot I get the Vista boot loader and can choose between the two.
3. I installed Ubuntu 7.04 64 bit on another partition on the same drive with the swap file also on this drive.  The install went fine without a hitch

BUT...
When I turn the computer on I still see the Vista boot loader and only entries for XP and Vista.

**Any ideas?**

Just to confirm, my primary hard drive has 5 partitions

1 - XP Install Parition (active) - ntfs
2 - 700MB scratch drive - ntfs
3 - Ubuntu 7.04 Install partition - ext3
4 - Ubuntu 7.04 Swap - swap
5 - Vista install partition - ntfs

Any help would be much appriciated!

---

