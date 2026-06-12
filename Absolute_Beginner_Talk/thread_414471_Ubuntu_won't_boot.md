---
title: "Ubuntu won't boot"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by jwh on 2007-04-19
Hi there.  A couple of days ago I installed Unbuntu from the LiveCD to a second harddrive.  I edited the GRUB menu using the guide found here:

[http://tinyurl.com/33dezp](http://tinyurl.com/33dezp)

Well, it didn't work and I couldn't boot XP but I could Ubuntu.  So, in lieu of correcting this, I decided to play around a bit with Ubuntu. ( I figured I could always make the XP drive the master again, so I didn't worry too much about it.)

Playing around with Ubuntu, I got all the updates and downloaded a bunch of stuff from the Synaptic package manager.   I wanted also to install QuickFox as I thought Firefox was performing too slowly.  I was able to do this and felt pretty good about things.

Well, today I figured out what I did wrong with the GRUB edit; (I simply included a space where I shouldn't have).  So, I started up Ubuntu to re-edit Grub -- Lo and behold Ubuntu  gave me errors and wouldn't load.  

After dicking around with it with no results I decided that perhaps some of the things I downloaded had changed something.  So I thought perhaps a fresh install from the LiveCD would get me where I needed to go. So, I re-installed Ubuntu - which, of course, reformatted the harddrive. 

Once into Ubuntu again, I re-edited the GRUB menu.lst and restarted the computer to see if it would boot XP.   It Worked!   Great.  Now, I restarted the computer to reboot Ubuntu. 

Ubuntu would not load again. Same problem as before.  This is what I get on the screen:

Uncompressing Linux... OK, booting the kernel.
MOUNT: Mounting /dev/hda1 on /root  failed: Invalid argument
MOUNT: Mounting .rootdev on /dev/.static/dev  failed: No such file or directory
MOUNT: Mounting /sys on /root/sys  failed: No such file or directory
MOUNT: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbi/init

Busybox V1.01 (Debian 1:1 or4ubuntuv3) Built-in shell (ash)
Enter 'help' for a list of built-in commands
/bin/sh:  can't access TTY;  job control turned off
#

Well my guess is that Busybox is some kind of DOS like tool but I'm inexperienced in this so can't diagnose anything.  It's also my guess that the first /root failure is the problem, but don't really know.

I did try to do a repair from the GRUB menu but I just get the same.

Can someone help me out, here?  Much appreciated. Thanks.

---

### Post by jwh on 2007-04-20
Well, I've been doing some looking around and doing some thinking.

There are a few other threads I have found where people had this very same problem, (or at least very close to it.  I'm using two harddrives, they were using one.)

In every instance there was a dual boot with some version of Windows. Either xp or vista.

Some have speculated that the M$ did something to the other partition, (in my case the other harddrive).

I do know that I did not have the problem until I switched the Windows harddrive back to the master drive for the purposes of accessing windows.  Then when I the Ubuntu drive the master again, it would not load.

Again, when I reformatted for a new install,  Ubuntu worked again and I could load it. But then I opted to load Windows.  After that I again could not load Ubuntu.

In the other threads I looked at:

[http://tinyurl.com/2ubj77](http://tinyurl.com/2ubj77)

none of the other people could resolve this problem other than to reformat their drive. IOW, do a fresh install of Ubuntu.

But this makes me wonder then;  how are you supposed to do a dual boot so that this does not occur?

---

### Post by freebird54 on 2007-04-20
Normally the install will set up without needing to change the master drive. Ubuntu is quite happy not being on the first drive, or even on a primary partition for that matter.  Ubuntu (and Linux in general) play nice with others.

There should be no reason to switch which boots, that is what grub is for!  When you boot Windows - does it go directly in?

---

### Post by jwh on 2007-04-20
Hello Freebird.  The reason I made Ubuntu the master drive was simply because that was how it was laid out in the forum post that told me how to do an easy dual boot:  [http://tinyurl.com/33dezp](http://tinyurl.com/33dezp)

So, the way it was set up when I turned on the computer it would give me 10 seconds to select GRUB or would automatically go into XP.  

If I now re-install Ubuntu on a slave drive after previously having it on a master drive isn't that going to mess up GRUB?  

The reason I think for putting Ubuntu on the master was so you could completely remove the WINXP drive to ensure that XP would be unaffected by the install.  Then, once the install was complete you would hook up the XP as the slave.   Now if you used XP instead as the master, you would be installing Ubuntu on the slave and have no guarantee that XP would be unaffected by the install.

But after looking through some of the previous posts that shared my problem, I notice that a couple of these people did not have a dual boot.  They were using Ubuntu as their sole OS.  So, it seems that this is really an Ubuntu problem unrelated to sharing with Windows. 

Anyway, since I figure I have to do a fresh install, I'm downloading Kubuntu's Feisty Fawn. 

But I sure would like to see an answer to this problem, because there seems to be no solution and therefore no guarantee that the OS will screw up and leave your files in jeopardy.  

I guess that means a tenacious backup.

---

### Post by freebird54 on 2007-04-20
Actually, when you swap them so that Linux is the master, you should have a choice, as you say -and it does indeed leave the Win drive untouched.  But, then you should have no need to switch again unless you remove the Ubuntu drive completely -as Grub gives you a choice a boot time.

The other way is to put ONLY grub on the win drive, and leave it as the boot drive - bu you have to replace grub with a win MBR in that case to get win to work.  so.. I better re-read what your problem is again.. <pause>  OK.  I Now suspect that you missed the partitions correct GRUB names when editing.  If you can post the following from a terminal in Live CD, I am sure we can get it dual booting quite quickly.

sudo fdisk -l

This wil tell us what's where, and then we can find the rest of the fixes.  Got 1/2 an hour?

---

### Post by jwh on 2007-04-21
Sorry Freebird for not getting back, but I did a new install with Kubuntu Feisty Fawn.  I removed the windows drive prior to the install and still haven't hooked it back up.

However, many others that I mentioned in those threads did perform the fdisk function you mention and posted their results,  to no avail.  I think a couple of them were able to at least mount their drive to a temporary place so they could back up their valuable files before they did the fresh install.

Anyway, I'm enjoying Kubuntu too much to risk screwing things up with a second boot. But I will get around to it eventually.

I do appreciate your help though. Thanks.

---

### Post by freebird54 on 2007-04-21
I am impresses you got through (or had to patience to wait out the slow speed) !  I have not even booted my Feisty for a couple of days now - to let things settle down before I upgrade it!

Keeping the system separate is perfectly fine if you have easy access to the connections - dual boot is a little more convenient - but I am going to try running Windows in Virtual Box I think - if I do happen to want it, it seems like too much trouble to reboot!  That probably explains why I haven't seen it for almost 2 weeks again :)

Enjoy your Feisty!

BTW - the sudo fdisk -l just does a listing of the partitions in your system.  Try opening a terminal window and do **man fdisk** to see why :)  ( The man command displays a manual for the thing described after it. try **man man** for more)  We wouldn't trash your system intentionally!

---

### Post by antoz on 2007-04-21
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

the above link is very helpfull

---

