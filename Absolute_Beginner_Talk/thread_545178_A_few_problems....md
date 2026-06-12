---
title: "A few problems..."
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by count_zero on 2007-09-07
Hi all.
I'm afraid I have a few problems with Ubuntu that I was after some help with. Most of it's minor stuff, but annoying none the less.
I'm new to linux, and so far have only played with two live CDs of Slax. Then I got virused up to the eyeballs with Windoze, so...

The problems I have are:

When Grub loads it offers me several options, including two versions of Ubuntu, 2.6.20-15 and 2.6.20-16. Not a big problem, but is there a way I can clean up this menu?

Secondly, when I installed I followed several online guides, and one suggested creating a 'shared' partition (I'm dual booting at the moment), which I did. However, now I can't find it (I haven't fired up windys yes tho') and was wondering how I go about finding it and using it.

Next, I added GTKPod because of it's iPod Video support, but I can't see the videos I have on the ipod. Any ideas? (I'm going to check the GTKPod website (if there is one) but decided to throw it in here too.)

I saw kworldclock on synaptic package manager and decided to try it as it could be used as a wallpaper, but I can't get that bit to work. Is it because I'm not running Kubuntu?

Another add-on I've got if Firestarter, but it doesn't start up when everything else does. I've tried looking for Startup, but it's not there...:)

Lastly, I've got an underwater digital camera called a Sealife DC500 which works as a webcam with Windows, but I can't find it let alone use it with Linux. Suggestions?

Sorry this is a bit of a long post, I promise to try not to do it again!!

BTW, I'm not (too) afraid of the command line, but I am still a n00b to the language. Please be patient with me!!

---

### Post by dca on 2007-09-07
Firestarter does load at start-up, however, for some reason it doesn't show in the tray after reboot.
 
The grub is located at /boot/grub/menu.lst
 
I usually shorten the display message time and leave it alone...

---

### Post by chrome307 on 2007-09-07
Here's a great walk-through with instructions for setting up Firestarter :)

[http://ubuntuforums.org/showthread.php?p=3314238#post3314238](http://ubuntuforums.org/showthread.php?p=3314238#post3314238)

---

### Post by finer recliner on 2007-09-07
a shared partition (to share files between windows and linux) isnt really necessary anymore, since there is now support for NTFS partitions (the format windows uses)

to read/write NTFS from linux, install ntfs-3g
to read/write ext2/3 from windows, install the driver from here: [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

if you're camera uses removable memory (i.e. SD card, compact flash, etc) get USB compatable reader for it. they're fairly cheap and it will be much more likely to work in linux this way.

---

### Post by ajgreeny on 2007-09-07
I agree and accept everything others above have said, but just wonder why you want firestarter to start up at boot.  Firestarter is just a gui for the linux firewall, iptables, and is not really needed in 99% of desktop situations.  I suspect your paranoia from previously using windows has made you presume that you must have something running for the firewall to be active, but that's not so.  You could uninstall firestarter and you would still be as safe as you can be; ubuntu has no open ports by default and nothing is listening.  Go to [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) and check your system for open ports.   All mine are stealthed and not visible.

Similarly you don't really need a virus checker, though so as to avoid possibly sending a virus to other windows users I do have clamav installed and check in the terminal every month or so.

---

### Post by count_zero on 2007-09-07
Wow, thanks guys!!

Yes I am rather paranoid after windows, I'll try harder in future and not worry about not seeing the icon in the tray.

I take it I can remove the alternative kernels from grub without affecting anything adversely?

Now I'm not sure of what I can do with the spare partition on my hard drive. I've already got a large swap file!! Oh well...

As for the camera, it has a menu when connected via USB of either printer, PC or PC webcam. I can access it fine when it's just connected to the PC for download, but I was hoping to use it for something like Gaim in it's webcam mode.

---

### Post by Campingman on 2007-09-07
Here is a link for info on editing various aspects of your grub configuration:

[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

Have fun

---

