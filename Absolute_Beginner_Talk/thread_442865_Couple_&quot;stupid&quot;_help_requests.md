---
title: "Couple &quot;stupid&quot; help requests"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by johnnyphive on 2007-05-13
Alright, just got Ubuntu studio installed and am loving it so far.  Just a couple minor quarks i'm trying to iron out

1.  I'm running a dual display setup.  Nvidia dual head card with twinview enabled.  When i boot the computer up, my login screen pops up on my right monitor, but i'd like it on my left as that is my "main" monitor.  Is this possible?

2.  I've got xdcmp running (can only access it locally right now, but thats a different topic)
For some reason, whenever i do log in from my windows box using xming, my taskbars all jump from my left  (main) monitor to my right (secondary) monitor.  Is there someway to prevent this?  FYI, i'm logging in as the some user that is logged in on the desktop currently.

3.  Whenever I switch work spaces, i loose my taskbars and main menu.  Why is this happening?  Can it be fixed?

4.  Since the release of Studio, the site has been down.  I'm trying to find a list of all the preinstalled packages and what exactly they all do.  Does one exist somewhere other than ubuntustudio.org?

5.  Should i have 4 different kernel options in my grub menu?  I previously had straight feisty installed and didn't know if something got left behind.  How can i edit this menu?

Like i said nothing major, just trying to figure out how to "make it my own"

Thanks in advance for any and all suggestions.

---

### Post by finer recliner on 2007-05-14
1) [http://ubuntuforums.org/showthread.php?t=221174&highlight=dual+monitors](http://ubuntuforums.org/showthread.php?t=221174&highlight=dual+monitors)
start reading old posts. your question cant be original.

5) open synaptic package manager. search 'linux'. remove any kernels not needed anymore.

---

### Post by johnnyphive on 2007-05-14
Thanks for the reply

Anybody got ideas on the other stuff?

---

### Post by johnnyphive on 2007-05-14
I did what you said but can't seem to find anything on moving the login screen to my other moniter.  Could you give me some suggestions on what to search for?  I'm wondering if I'm using the correct terminology.

As for the other questions, i'm still stumped on #2

I think i figured out #3 had something to do with "Desktop Effects" being turn on.  I turned them off, and all works now.

The site is back up so #4 fixed itself

As for #5, are the 4 different kernel options there for studio, or did something get left behind from a previous install?  What is the difference between the low latency and the regular?

---

### Post by finer recliner on 2007-05-15
1) try reading this thread. it may help you: [http://ubuntuforums.org/showthread.php?t=409840](http://ubuntuforums.org/showthread.php?t=409840)

5) linux kernels show up as "linux-image-<version>" in synamptec. or if you want to play it safe, you can leave the extra kernels installed and just take them off the the GRUB list at boot up. 
the latter option can be done by:

```
$sudo gedit /boot/grub/menu.lst
```

make sure to back up the file first though!
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.list.bck
```

once the file is opened for editing, just comment out any entries you dont want by placing an '#' at the beginning of the line. next time you load GRUB, those entries will not appear as a choice (but the kernel still exists on your system). if something happens to your current kernel, you could always reenable one of these kernels and boot from it to fix your other problem. 

read here for more info about the GRUB config file: 
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

---

### Post by leeley on 2007-05-15
> **johnnyphive said:**
> Alright, just got Ubuntu studio installed and am loving it so far.  Just a couple minor quarks i'm trying to iron out

1.  I'm running a dual display setup.  Nvidia dual head card with twinview enabled.  When i boot the computer up, my login screen pops up on my right monitor, but i'd like it on my left as that is my "main" monitor.  Is this possible?

2.  I've got xdcmp running (can only access it locally right now, but thats a different topic)
For some reason, whenever i do log in from my windows box using xming, my taskbars all jump from my left  (main) monitor to my right (secondary) monitor.  Is there someway to prevent this?  FYI, i'm logging in as the some user that is logged in on the desktop currently.

3.  Whenever I switch work spaces, i loose my taskbars and main menu.  Why is this happening?  Can it be fixed?

4.  Since the release of Studio, the site has been down.  I'm trying to find a list of all the preinstalled packages and what exactly they all do.  Does one exist somewhere other than ubuntustudio.org?

5.  Should i have 4 different kernel options in my grub menu?  I previously had straight feisty installed and didn't know if something got left behind.  How can i edit this menu?

Like i said nothing major, just trying to figure out how to "make it my own"

Thanks in advance for any and all suggestions.

The answet #1 is I think first look at your xorg.conf file and see where you have your second monitor set up to be. Do you have it on the left or the right this will determin which monitor is the the default one? If you have said in twinview to the right of the default monitor is the left  one if you said to the left of then the right on e id the default.

---

### Post by leeley on 2007-05-15
> **johnnyphive said:**
> Alright, just got Ubuntu studio installed and am loving it so far.  Just a couple minor quarks i'm trying to iron out

1.  I'm running a dual display setup.  Nvidia dual head card with twinview enabled.  When i boot the computer up, my login screen pops up on my right monitor, but i'd like it on my left as that is my "main" monitor.  Is this possible?

2.  I've got xdcmp running (can only access it locally right now, but thats a different topic)
For some reason, whenever i do log in from my windows box using xming, my taskbars all jump from my left  (main) monitor to my right (secondary) monitor.  Is there someway to prevent this?  FYI, i'm logging in as the some user that is logged in on the desktop currently.

3.  Whenever I switch work spaces, i loose my taskbars and main menu.  Why is this happening?  Can it be fixed?

4.  Since the release of Studio, the site has been down.  I'm trying to find a list of all the preinstalled packages and what exactly they all do.  Does one exist somewhere other than ubuntustudio.org?

5.  Should i have 4 different kernel options in my grub menu?  I previously had straight feisty installed and didn't know if something got left behind.  How can i edit this menu?

Like i said nothing major, just trying to figure out how to "make it my own"

Thanks in advance for any and all suggestions.

The reason that you have four different kernel options in Grub is that everytime you upgrade the kernel grubregates the old kernel down one so that if the new kernel does not work you can a least boot into on that works. I would not under any surcumstance remove the kernels from previous upgrades untill you know for certtian that the new kernel works. And for all of the room that it takes in grub I would not edit out the last 2 at least. It is like windows restore to last good image if you have problems. If you are new to Linux then leave alone for now and wait till you  better aquainted with it.

---

### Post by johnnyphive on 2007-05-15
> **leeley said:**
> The reason that you have four different kernel options in Grub is that everytime you upgrade the kernel grubregates the old kernel down one so that if the new kernel does not work you can a least boot into on that works. I would not under any surcumstance remove the kernels from previous upgrades untill you know for certtian that the new kernel works. And for all of the room that it takes in grub I would not edit out the last 2 at least. It is like windows restore to last good image if you have problems. If you are new to Linux then leave alone for now and wait till you  better aquainted with it.

that much i understand, but i actually wiped, repartitioned, reformatted my original 20gb / partition into 2 small 10gb partitions and installed studio from scratch (sorry is i was unclear earlier).  i was thinking doing the above would have wiped my original grub a kernels, but i guess i was wrong?????

---

