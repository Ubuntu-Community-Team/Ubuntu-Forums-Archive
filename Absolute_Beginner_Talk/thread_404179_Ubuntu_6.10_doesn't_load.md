---
title: "Ubuntu 6.10 doesn't load"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by j2edwards on 2007-04-08
OK.  I feel like an idiot, but I'm new to the Ubuntu flavor.  I've got a Dell Dimension 2350, 1.8GHz, 256MB RAM, 40GB HDD.  This should be a piece of cake, but I can't get the Ubuntu desktop to load for anything.  For a while I was getting the Ubuntu startup screen, and then the progress bar, but then I would get 2 errors, HDC: timeout waiting for DMA and HDC: drive not ready for command.  I see these errors repeated 3 times, and then I get a whole lot of garbage on the scree, which I've now noticed changes every time.  I had an ATI PCI vid card, so I tried taking that out thinking this might solve the problem.  I attach the monitor to the onboard VGA and I get stil get the Ubuntu startup screen, but then I get nothing except for a flashing cursor in the top left corner, no progress bar, but I do hear the CD working away.  If I leave it sit, I do finally get *Activating Swap, * Checking File System, and then after about another 1-2min everything goes quite.  Nothing, no cursor, no screen flash, nothing.  I've checked for bios upgrades, but I'm up to date.  I've turned off DMA on the motherboard, but still no luck.  I've swapped out the CDROM.  I've swapped out the HDD.  If anyone has any thoughts I would be grateful.  I have verified the MD5Sum, burned the iso at 4x, and loaded the Ubuntu live on a laptopthe.  The PC does work as I have loaded XP and Fedora on this machine today with no issues whatsoever just to verify that there shouldn't be an issue.  I'm sick of using XP, and Fedora just bores me for some reason.  Thanks for any help.

---

### Post by HereInOz on 2007-04-08
This may not bring you any joy, but I have had a few issues with some machines where the CD drive is set to either cable select or secondary slave.  I have had more success setting the CD/DVD drive to Secondary master.  Try that, and see what happens.

---

### Post by j2edwards on 2007-04-08
Thanks for the note HereInOz.  Sorry I left that bit out of my original.  I had read somewhere in the forum about similar problems.  Here's my IDE setup.  Primary Master = 40GB HDD, Primary Slave = Nothing, Secondary Master = CDRW Drive, Secondary Slave = 250GB HDD.  Please if someone can help that would be great.  I lost 8 hours of my life just trying to get Ubuntu to load on a stupid Dell Dimension.  This shouldn't be that hard.

---

### Post by oilchangeguy on 2007-04-08
the problem may be the 256mb of ram your computer has. as this is the min. amount needed. yes it should still load, but if you can increase the amount of ram your computer would be much happier, whatever os you decide to use.

---

### Post by overdrank on 2007-04-08
> **j2edwards said:**
> Thanks for the note HereInOz.  Sorry I left that bit out of my original.  I had read somewhere in the forum about similar problems.  Here's my IDE setup.  Primary Master = 40GB HDD, Primary Slave = Nothing, Secondary Master = CDRW Drive, Secondary Slave = 250GB HDD.  Please if someone can help that would be great.  I lost 8 hours of my life just trying to get Ubuntu to load on a stupid Dell Dimension.  This shouldn't be that hard.

Hi you might try the _**alternate cd**_ found here
[http://releases.ubuntu.com/edgy/](http://releases.ubuntu.com/edgy/)
Scroll down to the *alternate cd* this is a good how to burn
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
and install with that cd. Hope this helps and good luck!:)

---

### Post by j2edwards on 2007-04-08
Thanks oilchangeguy and Paul for the suggestions.  I'm not one to buy into the philosophy of when a PC doesn't work, throw more ram at it.  I did try putting another 256MB chip in, but still the same errors.  The hardware runs XP with no troubles, and runs Fedora great, with only 256MB ram.  I'm going to try the alternate image Paul suggested and see if that gets me anywhere.  This should be so hard!

---

### Post by ihavenoname on 2007-04-08
[http://lists.debian.org/debian-user/2001/03/msg04638.html](http://lists.debian.org/debian-user/2001/03/msg04638.html)

this guy had a similar problem. And he was given the suggestion that he should remove some disks in order to lessen the burden on his power supply or get a more" powerful" power supply. Not sure if this helps. 
The alternate install cd is probably a good bet.

Edit: In general you should unplug any unnecessary things from the computer. Just to minimize the change for problems.

---

### Post by j2edwards on 2007-04-11
Hey,

So here's a quick update.  I'm fairly sure that it's the video card.  I took overdrank advice using the alternative CD.  The text mode install worked great!  It recognized my partitions, XP install, and everything went just as planned.  I rebooted, and picked the option to load Ubuntu, and then nothing.  I can't see anything.  I tried a different ATI video card, and I do get the Ubuntu name with a scrolling bar, but then it locks up cold.  So, does anyone know where to find a list of approved Ubuntu hardware?  Seems as though I need a new vid card.

---

### Post by oilchangeguy on 2007-04-11
try this:
[http://www.linuxcompatible.org/compatibility.html](http://www.linuxcompatible.org/compatibility.html)

---

### Post by dstew on 2007-04-11
Try the boot option for recovery mode. This should get you to a text login window. From there, we can try different things to see why your system won't boot properly. If it doesn't boot in recovery mode, then you have issues other than the video card. If it does boot in recovery mode, then we can make configuration/driver changes to get it going.

---

### Post by ihavenoname on 2007-04-11
> **j2edwards said:**
> Hey,

So here's a quick update.  I'm fairly sure that it's the video card.  I took overdrank advice using the alternative CD.  The text mode install worked great!  It recognized my partitions, XP install, and everything went just as planned.  I rebooted, and picked the option to load Ubuntu, and then nothing.  I can't see anything.  I tried a different ATI video card, and I do get the Ubuntu name with a scrolling bar, but then it locks up cold.  So, does anyone know where to find a list of approved Ubuntu hardware?  Seems as though I need a new vid card.

Before you get another card try one more thing for me. When you get to grub stop the count down. (press the down arrow). Then either scroll to the selection for your kernel that says recovery. OR while your on the Ubuntu selection hit e. Then scroll to the line that starts with kernel and type e again. At the very end of that line hit space then type the number 1. hit enter. The b. Wait for the boot up. It SHOULD take you to a console log in.  Login with your user name and password. Then type this command in.

```

sudo cat /etc/X11/xorg.conf |grep Driver
```The output should look something like this 
```

        Driver          "kbd"
        Driver          "mouse"
  Driver        "wacom"
  Driver        "wacom"
  Driver        "wacom"
        Driver          "nvidia"


```It won't be the exact same but should be similar. Tell us what you have listed  there. You see under mine it says nvidia. This is because I am runing the proprietary nvidia driver. IF I was using the oss one it would say nv.

If the the sudo cat... command doesn't work for you, you can type ```
sudo nano /etc/X11/xorg.conf. 
```What you want to do is scroll though the xorg.conf (it is long). Now what you can do is if you find that you have an ati driver listed (or anything besides vesa) is go into the device section of your xorg.conf and change the driver to "vesa". Then save it (ctrl+x and then type y and the enter) and type 
```
sudo /etc/init.d/gdm restart
```Good luck.

Fyi: the sudo cat |grep  command will only display the driver it won't change anything you will have to go in there afterwards and change the drive to vesa. It's only useful in that it lets you know what you are looking for. Generally for me the last driver listed after the cat grep command is the video card driver.

---

### Post by Goodkimchee on 2007-04-11
Heh.  I had this problem a few weeks ago.  Did a quick google and found this link: 

[http://students.mypha.org/wiki/Solving_the_Buffer_I/O_Error](http://students.mypha.org/wiki/Solving_the_Buffer_I/O_Error)

To sum up what he says, there are two options you can try: 

1) replace your cd drive.  For some reason, the Ubuntu dics really, really dislike whatever cd drive Dell is using.
2) try burning your Ubuntu cd at 4x or the slowest speed your burner can burn.  I've read that people with Dells have had success with that.  

I personally replaced the cd drive; actually, I just unplugged the cd drive & left it in the cage & put the "new" cd drive on top, plugged everything in, and it loaded up perfectly without a hitch.  

I hope that helps.

---

### Post by Jhongy on 2007-04-18
i second the idea to re-burn your Ubuntu CD at as slow a speed as possible, on the best media you can find, optionally wrapping the computer in eggshells while the CD is burning.

---

### Post by brianglass on 2007-04-26
j2edwards,

Did you ever solve this problem. I have a friend who has a Dimension 2350 and he is having problems installing Feisty Fawn. I'm going to be going over to his house to help him get it going and could use any advice you have.

Thanks.

---

### Post by j2edwards on 2007-05-10
Hey,
Just wanted everyone to know I haven't given up.  Got a little sidetracked with my wife having a child, you know, the little things in life.  Thanks for all the posts.  I'm going to work on this again over the weekend.  I tried burning 7.04 at 2x.  We'll see if that helps.

---

### Post by ihavenoname on 2007-05-10
CONGRATULATIONS!!!!!!:popcorn::KS:guitar:\\:D/:-D8):D Hopefully this child has a wonderful life!

---

### Post by jerrylamos on 2007-05-10
One of my systems gets the message "can't access tty" which turns out to be an fsck failure when during boot it tries to check the file system which hasn't been mounted yet.  This is a result of Ubuntu picking up Debian scripts to do functions in parallel, and in a number of cases time dependencies result in one function failing because another hadn't gotten far enough yet.

In my case I put the CD Rom on IDE1 and 1 or 2 IDE hard drives on IDE2.  It boots that way O.K.  You will have to look at the master/slave or cable select plugging; cable select doesn't work for me.  Here's some more.  Ben Collin's fix I didn't understand, but other people have found it useful.

[https://bugs.launchpad.net/ubuntu/+s...20/+bug/106864](https://bugs.launchpad.net/ubuntu/+s...20/+bug/106864)
There was a "fsck failed, see /var/log/checkfs" buried in the middle of the messages that roar up the screen. My interpretation, the bug came in when hard drive code was changed to support both IDE and SATA. Along with this came change of device name from hda to sda, complex UUID's, and all that. fsck failed to process the IDE hard drive.
My fix: put in an extra cable to put the IDE hard drive on IDE2, while the CDROM is on IDE1. Ubuntu booted right up, no "can't access tty" errors.

Ben Collins said on 2007-04-18: (permalink)
The quick workaround for this on an installed system is to add "piix" to /etc/initramfs-tools/modules, and run "sudo update-initramfs -u"
For installing a system, add break=top to the kernel cmdline via the bootgfx menu. Once at a busybox prompt, run "modprobe piix". Then "exit" the shell. Once the system is installed, the above work around will also be needed.

Cheers, Jerry:confused:

---

### Post by commonplace on 2007-07-23
Replacing the CD-ROM drive worked when I had this problem. Thanks!

/Kevin

---

