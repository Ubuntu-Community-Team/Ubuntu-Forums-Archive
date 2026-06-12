---
title: "Can't fully install Ubuntu on G5, won't reboot into Linux"
date: 2007-09-28
forum: Apple PPC Users
---

### Post by soundhead on 2007-09-28
Hello, when I try to install Ubuntu on my G5, I get as far as installing off the CD then the CD rom ejects. Upon rebooting it initially booted into OS X immediately, no yaboot option. I then restarted with the alt key held down and got yaboot. However it still would not restart into Linux for the second half of the installation. I tried selecting the Linux drive icon, pressing the right arrow and then pressing L when prompted, still nothing. (Although pressing x did boot back into OS X) Eventually I got a grey screen with nothing to do but turn the power off.
I am sure I am doing something incredibly stoopid, but hey it does say that Linux is really easy to install and I have not found this to be the case!
My G5 has 1.5gb ram, Dual 2 ghz processor. I have partitioned my second internal drive for Linux.
Can anybody help?

---

### Post by soundhead on 2007-10-01
Please can anybody help?:)

---

### Post by stmiller on 2007-10-01
What version of Ubuntu? And what specific iMac do you have? ( [www.apple-history.com](www.apple-history.com) )

Are you installing with the alternative CD? If not, try the Feisty PowerPC Alternative CD and reinstall, choosing install-powerpc64 at the boot prompt.

[http://cdimage.ubuntu.com/ports/releases/feisty/release/](http://cdimage.ubuntu.com/ports/releases/feisty/release/)

If it barfs when trying to install yaboot at the end, you may have to run rescue mode from that alternative CD and choose the 'repair yaboot' option. This has come up for a few Powermac G5 folks with Feisty.

---

### Post by soundhead on 2007-10-02
Thanks Stmiller, I'm using a desktop G5, not an iMac or a MacPro. I am downloading the feisty alternative cd and will let you know how I get on with it. Thanks again!

---

### Post by soundhead on 2007-10-03
That worked, though not in the way I expected. I downloaded a file called ubuntu-7.04-alternate-powerpc.iso from the link supplied [http://cdimage.ubuntu.com/ports/rele...eisty/release/](http://cdimage.ubuntu.com/ports/rele...eisty/release/)
This however makes a Live CD. Therefore using the prompt install-powerpc64 does nothing. However on booting into the live CD it gives you the option to Install, using the Install wizard. This worked after a few goes as I made some mistakes in partitioning. I am now writing this from within Firefox in Ubuntu, looking forward to the whole Linux experience.
By the way I have done this while keeping my Mac OS X system and files, if anyone needs help in how to do that without reinstalling OS X I can offer you some advice.
Thanks again.

---

### Post by markfiend on 2007-10-03
> **soundhead said:**
> By the way I have done this while keeping my Mac OS X system and files, if anyone needs help in how to do that without reinstalling OS X I can offer you some advice.
Thanks again.

I'd like that advice. :) Thanks

---

### Post by soundhead on 2007-10-03
OK this is the way I did it, bear in mind it may be different on your system. I have a second hard drive in my G5 upright which I installed Linux on to, you may not have this. 
First I copied everything off this second internal drive on to a USB external. 
In Disk Utility in Applications/Utilities/Disk Utility I partitioned this drive, using 20 gb for Linux and the rest for my OS X files. You can use more or less but at least 2gb. I selected the drive and clicked on the partition tab. I clicked split at the bottom left and dragged to make the partition size. There is not much point in renaming your Linux partition. I selected Free Space from the Format drop down menu, this allows the Linux partitioner to use this drive space. (Incidentally my first mistake with partitioning was to neglect to select this as free space, by default OS X sets it as Mac OS X Extended which means Linux cannot use it.) 
Once I booted into the Live CD I double clicked the Install icon. When prompted I selected the partitioner to use the biggest free space on my second internal drive, i.e. the one I had made in OS X Disk Utility. After that the installer went through ok, though I still have a problem with yaboot which means I still need to hold down alt at startup etc. But that's another story. 
The only other problem as I recall was taking out the live CD, if I want to restart after installing from the linux CD, how do I take the CD out when I need it to shut down from Linux?!! I can't remember what I did but maybe I booted into OS X, not sure!
Finally once I had got up and running in Ubuntu I booted back in to OS X to check all was well and I copied the files back on to my second internal from the USB drive.
I hope this all helps, feel free to ask any other questions.

---

### Post by markfiend on 2007-10-04
Thanks!

I don't have a second HD though, so I guess I'd have to back up my HD to a USB external drive and repartition my HD (I'm right in thinking I'd do both from Disk Utility on the OSX install DVD?), and then restore the OSX partition from backup.

---

### Post by soundhead on 2007-10-04
I'm not the expert in reinstalling a Mac OS X system so I'm not sure, it sounds feasible though.

---

### Post by markfiend on 2007-10-05
It worked. :D 

There was nothing vital on there which I couldn't have restored from other DVD-R backups, so I figured it was worth the risk; I could always have done a clean OSX install on the partition if it had gone ****-up.

It took about three hours to backup and restore though, finished by about midnight! I just need to put Ubuntu on the empty partition now...

---

### Post by soundhead on 2007-10-05
Nice one. Let me know if you have any problems with the Ubuntu install and if you figure out the whole yaboot thing.

---

### Post by markfiend on 2007-10-05
Will do. I won't be able to post until Monday now; I'm posting from work and my home Internet connection is off at the moment.

---

### Post by markfiend on 2007-10-08
The installer froze 68% of the way into the installation process.  I didn't have time to try again.

---

### Post by markfiend on 2007-10-18
Got it all working. As I knew the backup was OK, just as an experiment, I wiped the HD and installed Ubuntu as the only OS; it kept losing the time/date settings going back to Jan 1904 every time I started up. Now I've gone back to dual-boot it's working fine. Strange but not a big problem; I intend keeping the machine as dual-boot for the forseeable future.

---

### Post by soundhead on 2007-10-18
Good to hear all is well. No idea about that date time thing. Dual boot is good, OS X rocks and I still haven't managed to get much out of Linux, I wanted it for the audio tools but so far haven't found anything too spectacular. I will keep trying however.

---

