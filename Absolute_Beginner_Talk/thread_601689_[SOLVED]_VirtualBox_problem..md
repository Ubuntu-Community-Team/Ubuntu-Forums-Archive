---
title: "[SOLVED] VirtualBox problem."
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by eXeCuTeR+ on 2007-11-03
Anytime I try to start Windows I get this message:
```

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).
Result Code: 
0x80004005
Component: Console
Interface: Console {1dea5c4b-0753-4193-b909-22330f64ec45}

```

How do I fix this?

Thanks.

---

### Post by overdrank on 2007-11-03
> **eXeCuTeR+ said:**
> Anytime I try to start Windows I get this message:
```

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).
Result Code: 
0x80004005
Component: Console
Interface: Console {1dea5c4b-0753-4193-b909-22330f64ec45}

```

How do I fix this?

Thanks.

Hi if you use this command in the terminal ```
sudo chmod 666 /dev/vboxdrv

``` that should solve that issue. And if you will check out the user manual it has great info
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
Good luck!

---

### Post by eXeCuTeR+ on 2007-11-03
> **overdrank said:**
> Hi if you use this command in the terminal ```
sudo chmod 666 /dev/vboxdrv

``` that should solve that issue. And if you will check out the user manual it has great info
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
Good luck!

Thanks but now it shows after it loads the innotek:
```

FATAL: No bootable medium found! system halted.

```

---

### Post by overdrank on 2007-11-03
> **eXeCuTeR+ said:**
> Thanks but now it shows after it loads the innotek:

FATAL: No bootable medium found! system halted.

Ok I did this once, :oops: make sure you have the disc in the right cd drive that you have set up for VB.

---

### Post by eXeCuTeR+ on 2007-11-03
> **overdrank said:**
> Ok I did this once, :oops: make sure you have the disc in the right cd drive that you have set up for VB.

There's no disc in in my cd drive.
And what's VB?

---

### Post by overdrank on 2007-11-03
> **eXeCuTeR+ said:**
> There's no disc in in my cd drive.
And what's VB?

Ok sorry I must be confused. I thought you were trying to install windows on the Virtual Box ( VB) :)

---

### Post by eXeCuTeR+ on 2007-11-03
> **overdrank said:**
> Ok sorry I must be confused. I thought you were trying to install windows on the Virtual Box ( VB) :)

I am trying to run windows on VB although windows is already installed in my computer as another OS.
I haven't installed windows on VB yet although I allocated enough memory and stuff for it in the VB itself.

Edit;
Oh! I have to install Windows on VB now, do I?
If I do, please tell me what to do lol.

---

### Post by overdrank on 2007-11-03
> **eXeCuTeR+ said:**
> I am trying to run windows on VB although windows is already installed in my computer as another OS.
I haven't installed windows on VB yet although I allocated enough memory and stuff for it in the VB itself.

Ok please excuse me but I have a tooth ache and the pain pills must have me confused :confused:
You have windows and ubuntu dual boot system now correct?
You have VB installed on Ubuntu and are wanting to install windows on the VB correct?

---

### Post by eXeCuTeR+ on 2007-11-03
> **overdrank said:**
> Ok please excuse me but I have a tooth ache and the pain pills must have me confused :confused:
You have windows and ubuntu dual boot system now correct?
You have VB installed on Ubuntu and are wanting to install windows on the VB correct?

Yeah, I have VB installed atm on Ubuntu, and I want windows to run on it.
How do I run it now?
Well, here's a screenshot of my VirtualBox:
[IMG]http://img218.imageshack.us/img218/5563/screenshotinnotekvirtuafr5.png[/IMG]

btw,
feel good :)

---

### Post by MarshallClan on 2007-11-03
Dude... 
 You need to Install Windows in your VirtualBox system jkust as if it were a real live stystem. As in pop in the install disc and walk through the whole good old install process to establish your "Virtual Windows System". You do have an install disc correct? That's your next step. Good Luck!

---

### Post by eXeCuTeR+ on 2007-11-03
Yeah I do have an install disc for windows.
But I already installed it once on my computer will it install now again?

EDIT:
I entered the windows install disc to the cd drive.
What should I do now?

---

### Post by overdrank on 2007-11-03
> **eXeCuTeR+ said:**
> Yeah I do have an install disc for windows.
But I already installed it once on my computer will it install now again?

Hi and as far as I know yes you will have to install it on or in VB. If you have windows on your system and its a dual boot with ubuntu on the same drive it would be impossible to use at the same time you are using Ubuntu. At least I think ( the way this day is going I am sure I will be proven wrong :) )

---

### Post by overdrank on 2007-11-03
> **eXeCuTeR+ said:**
> Yeah I do have an install disc for windows.
But I already installed it once on my computer will it install now again?

EDIT:
I entered the windows install disc to the cd drive.
What should I do now?

Hi and please have a look at the user manual
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
:KS

---

### Post by eXeCuTeR+ on 2007-11-03
> **overdrank said:**
> Hi and please have a look at the user manual
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
:KS

Oh man, I have no time to read this manual, please tell me what to do or send me a tutorial that explains what to do =[

---

### Post by overdrank on 2007-11-03
> **eXeCuTeR+ said:**
> guys please help me =[

Ok you have set it up once in VB so delete the first one and then go through the same steps as you did the first time and this time install it with the cd that you have. :KS

---

### Post by PogMoThoin on 2007-11-03
I have a dual boot set-up also, but on seperate hd's, Vista & ubuntu. Can i load vista from the other hd with virtualbox?

---

### Post by eXeCuTeR+ on 2007-11-03
> **overdrank said:**
> Ok you have set it up once in VB so delete the first one and then go through the same steps as you did the first time and this time install it with the cd that you have. :KS

But how do I load the installation now through the VirtualBox?

---

### Post by eXeCuTeR+ on 2007-11-03
HElp guys?

---

### Post by P4man on 2007-11-03
AFAIK you can not migrate an existing windows installation to virtualbox. I believe VMware lets you do this, but not VB.

Executer, you have to install windows as you would on a new pc. You have to make sure you have configured the CDrom drive; in the settings page of your VM, enable "mount CD/DVD drive". Then insert your windows disc, and power on the VM so it boots from it.

BTW, make sure you make your harddisk large enough. By default it will only propose 4 GB or something, and you can not make it larger later on!  Give  it 100 or so GB, unused space will not take away space from your real harddisk anyway.

---

### Post by zmjjmz on 2007-11-03
Ok, I've been trying to get Mac OS X.4.6 installed in VB, but whenever I start up the VM (the OSX install disk is in there), and selecet it to boot from the CD drive, It says it can't read it...
And PogMoThoin, you could try getting it to boot from the other HD, and run it in there...
I think you can do that...

---

### Post by eXeCuTeR+ on 2007-11-03
to click on Setup.exe and install it somewhere?

---

### Post by RKCole on 2007-11-03
Hey guys.

PogMoThoin and others asking:  Unfortunately, you are unable to run your current Windows dual boot installation within VirtualBox.  You will have to go through a full windows installation to run it within VirtualBox.

Basically, the purpose of virtualization is this:  a person who solely runs a Linux system can use virtualization software (such as VirtualBox) to run an OS such as Windows without having to dual boot it.  this could be necessary for tasks such as using Internet Explorer and other applications which do not have Linux ports or applications which do not run under Wine.

For example, I solely use Ubuntu here at home.  I have a Windows XP virtual machine under VirtualBox as there will be some things in college which will require me to have Windows XP.  I do not want to dual boot Windows XP (anymore), so I use VirtualBox to work around this.

Now..I'll try to (briefly) give instructions on how to get Windows installed in VirtualBox.  Please keep in mind that this is brief, but I'll try to keep things streamlined and clear.  If you have any questions please feel free to ask.

1)  Install VirtualBox. (this is probably already done, but I just wanted to list it for the sake of this all :) )

2)  Open VirtualBox and click on the **New** option to create a new virtual machine.

3)  Go through the steps to create your virtual machine, putting in appropriate values for RAM (memory) and such.

4)  Most likely you'll need to create a **virtual drive**; this will be the virtual hard drive that Windows (or your OS of choice) will be installed on.

5)  After completing the Virtual machine creation, go through the settings for the virtual machine, enabling the host CD/DVD drive, floppy drive, and other things that you may wish to have.

6)  Insert your Windows (or other OS's) installation CD. (NOTE:  I don't think that recovery CDs work for this procedure.  You would have to have a Windows installation CD for this.)

7)  **Start** your virtual machine.  It SHOULD boot from the installation CD.

**********************************************************************************************************************
You may encounter the same problem I did in this step, as my CD-ROM drive (for some odd reason) is seen by Ubuntu as scd (a SCSI device) rather than hdc (an IDE device); if this happens, you'll receive some FATAL: No Boot Device error or something of the like.  If this happens, just shut down the virtual machine, and follow the below procedure.  I am sure there is a workaround for this, but my way around it was to create an ISO image of my Windows installation CD and boot from the ISO image.  This also makes the installation much faster than it would be from the actual CD.

To do this, simply insert your Windows XP (or other OS's) installation CD and open up a terminal (**Applications->Accessories->Terminal** in Ubuntu (GNOME).  Your CD should be mounted somewhere in the **/media** directory.  

Use the **mount** command to find out what your CD/DVD drive is called (mine is /dev/scd1).  This entry should be at the end of the output from the mount command, and will show something like this:

```

/dev/scd1 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=bob)

```

Once you find this out, execute the following command to create an ISO image of your installation CD:

```

dd if=<location_of_cd> of=xppro.iso (or a name of your choice, without spaces)

EXAMPLE:
dd if=/dev/scd1 of=windowsxppro.iso

```

In VirtualBox, change the CD/DVD mount option so that it mounts from the ISO image.  By default, the ISO you created will be saved in the directory where you executed the command in terminal.  Most likely this will be /home/<your_username>.

Start your virtual machine again.
**********************************************************************************************************************

8)  Go through the OS installation, and get ready to use your OS when it's done.

Enjoy!

Hope this helps some.

Take care...going to go spell check this...

---

### Post by haldean on 2007-11-03
Also: your original problem stems from the fact that your user is not part of the vboxusers group - make sure that you're a member of that group (do it from the Users and Groups menu under Administration)

---

### Post by zmjjmz on 2007-11-03
I've actually taken a closer look at my problem...
two things that might help here....
a). When I pop in my OSX install disc, it says that it can't mount it
b). When I startup settings in VB, it says it failed to access the USB subsystem....
(I'm using a MacBook, if that helps...)

---

### Post by eXeCuTeR+ on 2007-11-03
Im getting this FATAL thing.
What to do, I didn't understand =[

---

### Post by overdrank on 2007-11-03
> **zmjjmz said:**
> I've actually taken a closer look at my problem...
two things that might help here....
a). When I pop in my OSX install disc, it says that it can't mount it
b). When I startup settings in VB, it says it failed to access the USB subsystem....
(I'm using a MacBook, if that helps...)

Please lets stay on the topic on hand. You would be better starting a new thread with your issue's and maybe get better support in another forum, [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

---

### Post by PogMoThoin on 2007-11-03
I get this error when i try to make an iso of the cd
> colm@l33t-str33t-PC:~$ mount
/dev/sdc1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sde1 on /media/Media type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=colm)
colm@l33t-str33t-PC:~$ dd if=/dev/scd0 of windowsvista.iso
dd: unrecognized operand `of'
Try `dd --help' for more information.

---

### Post by eXeCuTeR+ on 2007-11-03
After I typed mount I got this:
```

niv@niv-desktop:~$ mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/hdd on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=niv)


```

and after i typed this:
```

niv@niv-desktop:~$ dd if=/media/cdrom0 of=windowsxppro.iso
dd: reading `/media/cdrom0': Is a directory
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000791767 seconds, 0.0 kB/s
niv@niv-desktop:~$ dd if=/media/cdrom0/ of=windowsxppro.iso
dd: reading `/media/cdrom0/': Is a directory
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000801545 seconds, 0.0 kB/s


```

---

### Post by RKCole on 2007-11-03
Sorry, eXeCuTeR+, I made an error...just figured it out.

Rather than running the **dd** command on /media/cdrom0, run it on /dev/hdd, where ti appears your CD/DVD drive is on your system.  This should hopefully solve yoru problem for you.

Going to go edit my other post.

---

### Post by eXeCuTeR+ on 2007-11-03
> **RKCole said:**
> Sorry, eXeCuTeR+, I made an error...just figured it out.

Rather than running the **dd** command on /media/cdrom0, run it on /dev/hdd, where ti appears your CD/DVD drive is on your system.  This should hopefully solve yoru problem for you.

Going to go edit my other post.

Ok, ill try and edit

---

### Post by PogMoThoin on 2007-11-03
I've done this, created an iso image, set it 2 boot from iso but i get this error:
> 
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 


Help

---

### Post by eXeCuTeR+ on 2007-11-03
it shows me a black screen now if i press f12 fast and then 3 (cd-rom).

---

### Post by DeepNoob on 2007-11-03
"Now what to do?"

I don't read fast at all, but it took me less than three hours -- the length of time you've been begging for help on this thread) -- to RTFM, install XP in VB and take it for a trial run.

---

### Post by eXeCuTeR+ on 2007-11-03
But how can I install XP in VB? :OOO
I did what RKCole told me and now it just shows me a black screen.

---

### Post by RKCole on 2007-11-03
PogMoThoin:  May need to run:

```

sudo apt-get install virtualbox-ose-modules

```

Then run:

```

sudo /etc/init.d/vboxdrv start

```

Then proceed.

Hope this helps.

Please take care.

---

### Post by eXeCuTeR+ on 2007-11-03
RKCole, would you please help me, mate?
After I did what you told me it just now loads the innotek screen and shows a black screen.
What to do, please man!!

---

### Post by RKCole on 2007-11-03
eXeCuTeR+,

Is your CD the actual Wndwos installation CD, or is it a recovery CD?

I need to go for a bit, but I will try to check back later.

Take care.

---

### Post by PogMoThoin on 2007-11-03
Ok, i reinstalled the package in synaptics but i now get this error:
> 
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 

i have used the command you gave me "sudo /etc/init.d/vboxdrv start" to start virtualbox

---

### Post by zmjjmz on 2007-11-03
You have to run
```
sudo chmod 666 /dev/vboxdrv
```
then restart

---

### Post by eXeCuTeR+ on 2007-11-03
FINALLY! INSTALLATION!!!
But now it says that the size I allocated is too small and somehow I can't get it bigger!!!
I type 1500 and then it changes it back to 245 as it set before and it doesn't let me procced.
H-E-L-P!

---

### Post by zmjjmz on 2007-11-03
is the virtual hard disk being used dynamic or static?

---

### Post by eXeCuTeR+ on 2007-11-03
FINALLY!
Thank you all!!!

Especially you, RKCole, you are the best!

---

### Post by Maestro23 on 2007-11-03
> **eXeCuTeR+ said:**
> FINALLY!
Thank you all!!!

Especially you, RKCole, you are the best!

Congrats. Please mark this SOLVED using Thread Tools.

:guitar:

---

### Post by PogMoThoin on 2007-11-03
ok got mine 2 boot from iso image but unfortunately its 64bit which wont work, gonna try xp now & sort out vista 2morro

Thanks all

---

### Post by eXeCuTeR+ on 2007-11-03
how do i mark it as SOLVED?

and btw
how do I set the microphone and audio settings so I could hear my buddies on the ventrilo? :)
thanks.

btw 2,
sometimes it just turns off and restarts... =/ wtf?

---

### Post by Maestro23 on 2007-11-03
> **eXeCuTeR+ said:**
> how do i mark it as SOLVED?

and btw
how do I set the microphone and audio settings so I could hear my buddies on the ventrilo? :)
thanks.

btw 2,
sometimes it just turns off and restarts... =/ wtf?

THREAD TOOLS. Top of the page.

---

### Post by PogMoThoin on 2007-11-03
Right, have XP running fine, but after i restart i got 2 use > sudo chmod 666 /dev/vboxdrv to get it 2 run, is there nay way i can have it launched @ startup?

---

### Post by overdrank on 2007-11-03
> **PogMoThoin said:**
> Right, have XP running fine, but after i restart i got 2 use  to get it 2 run, is there nay way i can have it launched @ startup?

Hi and you can find the user manual here
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by PogMoThoin on 2007-11-03
Check out my [vid]("http://ie.youtube.com/watch?v=BjGxINg5MkQ")

Cant find anything in manual to help me with my last post, does any1 have any ideas?

Its not really bothering me tho, i know how get it going.


Thanks all

Pog

---

### Post by RKCole on 2007-11-03
eXeCuTeR+:  Thank you for your compliment.  However, I'm not the best...just someone who wants to help when I am able.

PogMoThoin:  Check under **System->Administratoin->Users and Groups**.  In the resulting dialog that will display, click on the **Manage Groups** option.  scroll down until you see the group **vboxusers**; highlight this entry and then click on the **Properties** button.  In the dialog that will appear, look for the area labeled **Group Members**.  If you do not see a checkmark next to your name/username for this, make sure to check it.  Close out of these dialogs, logout, and then log back in.  I think this may resolve your issue in having to run the chmod command each time you restart your system.

I noticed that (on Ubuntu Gutsy) after installing VirtualBox, none of the users on my system were added to the vboxusers group.

Hope this helps you some.

Take care.

EDIT:  My apologies, PogMoThoin.  I can't make too much of your video.  Itisi clear and all, but my vision is too bad to really perceive anything of it.  I only hope that this post helps to solve your problem.

---

### Post by P4man on 2007-11-04
> **PogMoThoin said:**
> Right, have XP running fine, but after i restart i got 2 use  to get it 2 run, is there nay way i can have it launched @ startup?

system>administration>users and groups>manage groups

select vboxusers > properties

check your own name.

(edit, oops, RKCole already explained that :D). Nice desktop btw

---

### Post by PogMoThoin on 2007-11-04
> **P4man said:**
>  Nice desktop btw

Desktop is Vancouver, can get it [[COLOR="Red"]here[/COLOR]]("http://www.penny-farthing.net/gallery2/main.php?g2_itemId=49")

Thanks all, workin lovely now. Owe ye all a beer, I'll have 1 for ye 2day :p

Pog

---

### Post by RKCole on 2007-11-04
PogMoThoin:  Not a beer drinker, but if you like root beer, have one for me one day down the road, eh? :)

Glad it's all up and going.  

Take care.

---

### Post by bratliff on 2007-11-04
I shared a new partition ext3. But I can't add a virtual drive except under my existing ubuntu drive. I do not have enough disk space to install in the default drive. How do I install xp to a shared drive?

Robert Ratliff
Retired in Panama

---

### Post by bourrinlepoulpe on 2007-11-06
sudo apt-get install build-essential linux-source
sudo su
/etc/init.d/vboxdrv setup
exit
sudo chmod 666 /dev/vboxdrv
sudo usermod -G vboxusers -a <your userid>
sudo /etc/init.d/gdm restart (or kdm restart if using kde)

if it says it can't find your kernel sources try

sudo apt-get install linux-headers-`uname -r`
sudo su
/etc/init.d/vboxdrv setup KERN_DIR=/usr/src/linux-headers-`uname -r`
chmod 666 /dev/vboxdr
usermod -G vboxusers -a <your userid>
exit
sudo /etc/init.d/gdm restart (or kdm restart if using kde)

---

### Post by gatewayasteroid on 2007-11-06
> **eXeCuTeR+ said:**
> Anytime I try to start Windows I get this message:
```

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).
Result Code: 
0x80004005
Component: Console
Interface: Console {1dea5c4b-0753-4193-b909-22330f64ec45}

```

How do I fix this?

Thanks.

sudo usermod -a -G vboxusers <your login name here>

then logout and login

---

### Post by carusoswi on 2007-12-08
> **DeepNoob said:**
> "Now what to do?"

I don't read fast at all, but it took me less than three hours -- the length of time you've been begging for help on this thread) -- to RTFM, install XP in VB and take it for a trial run.

Anyone so smart as you should stick to reading manuals and refrain from offering your helpful comments to others less smart than you.

Most forums, but especially those in this community, exist to help members who are having a difficult time finding their way.  It could be because they didn't read the manual, or it could be for some other reason, including the possibility that those members are not as smart as you or that they simply don't feel like RTFM . . . none of which deserves or is helped by your snotty reply.

If you find reading questions for which the answer is obvious to you so bothersome, why don't you just skip the thread.

Caruso

---

