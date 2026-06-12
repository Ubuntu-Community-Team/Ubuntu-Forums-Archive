---
title: "Wireless and Dual Boot Issues"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by cshelley on 2008-02-23
Alrighty! So I'm completely new to Ubuntu and apparently thought this would be easier than it actually is! I'm running into a few problems with my wireless card (I'm on a wired connection right now). From what I can tell, my wireless card is being read just fine, since I'm getting a "wireless network" option within Networks, as well as it seems to recognize my wireless card when I type in "ifconfig" into Terminal.  I've tried configuring it to my router's settings, including the WEP, however it's still not working.

Also, I believe I should've partitioned this off myself before I began installing. It appears that I'm unable to dual-boot like I believed I was going to be able to. When I was installing Ubuntu, it said it was partitioning, just like the guide I was checking out said...however I can't find a way to get back into XP.

Please help! I follow directions nicely, I'm just kind of without them right now.

---

### Post by richaoj on 2008-02-23
It would be helpful to know what kind of wireless cards you are using.  I suspect that it is a Broadcom, as with alot (all?) Broadcom chipsets, they will show up as being there but will not work without a little work.  

There are two options you can use with Broadcom wireless .. .
(1)bcm43xx - which will in essence take the firmware from your device and use it to make a driver.  I have not preferred this method in the past because last time I used it, it was limeted to a wireless B connection at 11 MB/s

(2) ndiswrapper - which will allow you to use the windows driver for your wireless card.  Some people have had trouble with ndiswrapper, but it has never failed for me.

When you find out exactly what kind of wireless card you have, we can be of more assistance and provide more detailed instructions.  I would also suggest you search the forums for either solution above with the name of your wireless card, as there is much documentation on the forums of people trying to figure out wireless problems . . . 

good luck.  it will be worth it when you get everything working

---

### Post by richaoj on 2008-02-23
also, for the dual boot, you should have an option at boot time -- grub should pop up and ask you what operating system you want to boot into if everything was installed correctly.  you may have to hit esc or something to get to the GRUB menu.  just pay attention when your computer boots -- it will tell you what to press to get to the grub menu...

---

### Post by cshelley on 2008-02-23
I believe I'm running a Broadcom 802.11 b/g wireless card. I was just now looking at bcm43xx...but I'm not exactly sure how to run it. I'd rather not be restricted to 11mbps, so how would I go about getting ndiswrapper?

When I hit escape when booting, I see about 3 different Ubuntu types of boots, but no Windows. I could be hitting it too late.

---

### Post by neurostu on 2008-02-23
When you installed ubuntu grub should have detected the XP install. Check the file system size to see if it is the same size are your original HDD, if it is then the partition didn't work and you formatted your entire HDD.

If this didn't happen, and you correctly partitioned then you need to tell grub what partition contains your windows install. There are plenty of posts in this forum that will explain how to do that...

To get ndiswrapper try:
```
 sudo apt-get install ndiswrapper 
```  
again there are plenty of posts in this forum on how to configure it.

Good luck!

---

### Post by cshelley on 2008-02-23
When I do that, I get the following > ubuntu-desktop@ubuntu-desktop-laptop:~$ sudo apt-get install ndiswrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper


Where to next?

---

### Post by richaoj on 2008-02-23
first off, you will need to find the appropriate windows driver for your wireless card.  you can often get them from the manufacturer of your machine or you can just do a google search for the SPECIFIC name of your device with "driver" and you will be able to find it fairly readily.  the best place to look will be the website of your manufacturer.

find the file, unpack it and find the actual driver file, and be sure you know what directory it is in.

the rest of the instructions are good here, if not a bit technical.  if you have any trouble with these instructions let us know, and we'll be here to help you.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Good luck.  it's not too bad - just follow the instructions carefully.

---

### Post by cshelley on 2008-02-23
As for the dual boot...I think I either 1) formatted my HDD or 2) erased one of my partitions. I looked beforehand and there were 3. One being 11.7 Gb, another being 99-ish (Which is the file size Ubuntu) and another, much smaller one being around 1 gb. Looks as if Ubuntu took over my 3rd partition.

---

### Post by richaoj on 2008-02-23
Hope you didn't lose any important data.  Trust me, i have learned the hard way to backup data regularly and especially before i try anything major like insalling an os.

---

### Post by cshelley on 2008-02-25
Alright, I've come to the conclusion that Windows is pretty much gone. I'm okay with that...since i was kind of getting tired of it anyways. I'm liking the interface with Ubuntu a lot, but i'm still having issues getting things loaded.

I've searched and searched and have yet to find a step-by-step version that gets me to the end result of an installed wireless driver. I see a lot of stuff involving terminal, but operating from a command prompt is about like reading Greek to me. Also, i think I was wrong and I'm actually using a BCM94311 wireless adapter. I've messed around with ndiswrapper but to no avail, and I can't even figure out how to install b43-fwcutter.

Another question: Would i have better luck with something like Fedora or Mandrake Linux?

---

### Post by neurostu on 2008-02-25
Probably not, ubuntu seems to have some of the best hardware support.  I have put several different distros on my laptop and by far ubuntu has worked the best. 

The command prompt can be really challenging, but its actually a feature that a lot of people love about linux.  Just give it some time and don't be afraid to try new things!

---

### Post by cshelley on 2008-02-26
Well if that's the case, is there a spot where I can find a guide on the commands used in Terminal?

---

### Post by myddewji13 on 2008-02-26
if u have probs using the terminal....go to synaptic manager...search for ndiswrapper...install...search for ndisgtk..install...u now have a gui for ndiswrapper....under system-administration-windows wireless drivers

now this is the important part....once u find drivers (the hardest part)....open the gui window... drag in the .sys file...it will tell u to put in the .inf file...do so...if you have the right driver it should work.... if not....just remove and keep trying (thats how i did it... best thing ever...all my frustration was due to the wrong driver) .... then once thats workin...to make it startup:

Make permanent:To load the module at boot time , add "ndiswrapper" to your /etc/modules file ,
```
sudo gedit /etc/modules
```

oh yea dont forget to run:

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

in terminal...pref before installing ndiswrapper driver...

---

### Post by dstew on 2008-02-26
> I've come to the conclusion that Windows is pretty much gone.Are you sure? Post the output of sudo fdisk -l and we'll see if the partition is still there. If so, you can probably boot it by reconfiguring grub.

---

### Post by neurostu on 2008-02-26
Here is a great list of commands: [http://www.ss64.com/bash/](http://www.ss64.com/bash/)

Also you might want to check out the different linux books, Anything by o'reilly tends to be good.

---

### Post by cshelley on 2008-02-26
After typing sudo fdisk -l I get.....
> ubuntu-desktop@ubuntu-desktop-laptop:~$ sudo fdisk -l
[sudo] password for ubuntu-desktop:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x282d282d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14242   114398833+  83  Linux
/dev/sda2           14243       14593     2819407+   5  Extended
/dev/sda5           14243       14593     2819376   82  Linux swap / Solaris


---

### Post by dstew on 2008-02-27
Yes, it looks like Windows is gone. Probably the Windows partition was deleted during the partitioning phase of the installation.

---

### Post by TheDilettante on 2008-02-27
Terminal scare you, cshell?  Well, I'd recommend following this tutorial: [http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)  Try to finish it in a week or two, as it really makes you feel comfortable with the way Linux does things.

After that, you might also look at [http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php) which will show in more detail how you can use the terminal well.  I promise that after you get comfortable, you'll roll your eyes at the thought of a GUI-dependent system...

Regarding Windows, it does in fact sound as if you accidentally erased the Windows partition.  Sorry.  Wifi, as everyone has said, will require you to find a driver either for ndiswrapper or the restricted drivers manager.  Start with googling "[device name] ubuntu"  to see if anyone has already posted the solution, as often it's been solved before you personally have the problem (as I learned while making my card work.)  If not, then look for the driver (someone else made the template "[device name] driver", which you should try, as well as "[device name] ndiswrapper.")

Half of learning Linux is learning the terminal, but the other half is learning to find an answer....  Good luck.

---

### Post by jbalazs on 2008-02-27
I have Broadcom 802.11 b/g wireless card only thing I did is download wifi radar

and it will connect you wireless card

---

