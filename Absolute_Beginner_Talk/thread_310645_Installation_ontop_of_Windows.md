---
title: "Installation ontop of Windows?"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by rachael on 2006-12-01
I'm having problems with Windows and cannot access any of my files because it won't boot properly. I was told that I could install Ubuntu ontop of Windows, access my files, back them up and then install Windows again. But I only have one hard drive and I'm worrying about losing my files. 

If I install Ubuntu, it will be over the top of Windows right? So it won't delete my files? And will I be able to have both Windows and Ubuntu installed and the chose which one I want to boot from?

Sorry, have no idea about how Ubuntu works so any help will be soooo great. I am terrified of losing my data! :???:

---

### Post by nickburns on 2006-12-01
It sounds like you want to boot up the Ubuntu live CD and try to recover your files.  If you only boot, and not install Ubuntu the windows partition will be left untouched.  You can mount your windows partition and get to the files you need to recover.

---

### Post by RChickenMan on 2006-12-01
Yeah, once you boot up the live cd, check out the ubuntu wiki, which has a great guide on how to mount your windows partition.  I've used this technique as well to attempt data recovery.  Have you tried fixing your windows installation first?

---

### Post by rachael on 2006-12-01
Yeah I've tried everything to fix the problem so now the only option is to completley restore everything. But I want to back up my files first which is the only problem really.

---

### Post by nickburns on 2006-12-01
Is you HD completely shot? can you mount it with the live CD?

---

### Post by rachael on 2006-12-01
It's not working so far. Does this mean I've lost all my data and need a new hard drive?

---

### Post by nickburns on 2006-12-01
What error do you get on trying to boot to windows?

Is it the dreaded 'Cannot find system file...'  ?

Do you get the windows splash screen?

Does the bios see the HD (if you press delete / f2 on bootup do you see your hd in the list? )

---

### Post by rachael on 2006-12-01
Yeah it gives me the option to boot from the hard drive but it just hangs at the Windows logo and the scroll thing that goes back and forth as it loads. And then after ages I get - the file user32.dll cannot be found, installing it again might fix the problem. But of course it won't let me install it...

---

### Post by SyvanX on 2006-12-01
Have you tried safe mode? 
Press F8 a bunch before you get to the windows logo.  You can probably choose the 'with networking' option if you need to transfer some files.

---

### Post by nickburns on 2006-12-01
So your HD might be ok, it is spinning up and getting some data, hopefully you can get out what you need.

So Boot up the Ubuntu disc, mount your HD and copy everthing you need to a USB drive, or email it out, or ftp or burn to CD the files that you need.

---

### Post by rachael on 2006-12-01
Ubuntu won't load either! Arg...it's just one problem after another!!!

---

### Post by nickburns on 2006-12-01
We will get through this, don't get too frustrated.  If ubuntu is not booting check first,

That your bios is set to boot CD before HD

Usually, you hit delete or F2 when the bios first shows on the monitor, go to boot options and make the appropriate settings. 

On one of my motherboards I have to hit the space bar to boot to CD, it asks if I want to boot to cd and you just hit any key.

Make sure you burned the ISO file for ubuntu properly, you need to burn the image to CD not just burn the ISO file on a CD

---

### Post by rachael on 2006-12-01
Ok, it is definatly booting from the CD.

And I get the Ubuntu screen with all the options, install, run memory check and whatnot. So I selected 'boot from first hard disk' and it asked me whether I wanted to start normally, safe mode etc. And it just ends up hanging at the Windows logo before going to the user32 error message again. I can hear the hard drive making noises so I know it's doing something

---

### Post by SyvanX on 2006-12-01
> **rachael said:**
> Ok, it is definatly booting from the CD.
So I selected 'boot from first hard disk' 

You need to select boot from cdrom.

---

### Post by rachael on 2006-12-01
That's not one of the options.

I boot from the CDROM which gets me to the Ubuntu menu which has these options:

Start or install Ubuntu
Start Ubuntu in safe graphics mode
Check CD for defects
Memory Test
Boot from the first hard disk

---

### Post by mushroom on 2006-12-01
"Start or install Ubuntu" will bring you to the Live CD.

---

### Post by rachael on 2006-12-01
Oooh right...but that won't affect any of my files or Windows stuff??

---

### Post by mushroom on 2006-12-01
Nope, unless you double-click the icon on the desktop that says "Install" and then actually go through with the installation procedure. Stay away from that icon, and nothing will be affected.

---

### Post by shuRe on 2006-12-01
i have tried option one on 2 of my computers, but at the last moment when loading ubuntu, it dreezes and the ubuntu logo gets a little distorted and small green lines appear around the loading bar, any ideas how to fix this problem, i have done that md5 checksum thing, downloaded different copier and versions of ubuntu, and used different cd's and nothing seems to work :(

---

### Post by nickburns on 2006-12-01
Once you get up and booted to Ubuntu --

go to Applications >> Acessories >> Termainal

then type in

sudo mkdir /media/windows
(this makes a folder that we will mount your windows partition)

then type 

sudo mount /dev/**** /media/windows
you need to replace the **** with hda1 or sda1 -- the best way to figure out which one is to type:

sudo mount /dev/s 
and then press tab, if it autofills with sda1 then your good otherwise type

sudo mount /dev/h
and then press tab, if it autofills with hda1 then we are good


either way this will mount your HD so you can get to the files.

to get to a file browser, go to Places >> Computer and then you windows directory is found in /media/windows

let us know how it goes...

---

### Post by mushroom on 2006-12-01
have you tried "Safe graphics mode"?

---

### Post by rachael on 2006-12-01
Woah I've just got a whole load of error messages and now its saying its been 'respawning too fast' and has been disabled for 5 minutes!! After 5 mins it just displays the same message again, and again...

---

### Post by jingo811 on 2006-12-01
I tried to simulate the whole process that you will probably go through from the point where you booted up the Ubuntu Screen.
Note that I'm using **Dapper Draker 6.06 Live CD**

**1.)** Go drink some water first.
**2.)** Then get back to your 'puter, and simultaneously close your eyes and take 3 deep breaths before you sit down. ;) 
**3.)** Boot your 'puter with the Ubuntu Live CD like you did before.
**4.)** Select **Start Ubuntu in Safe mode Graphics**!
**5.)_** Applications > Accessories > **Terminal**_

It's back to the stone age from here on :KS type as follows:
**6.)** sudo fdisk -l
**7.)** Look at column _Boot_ and locate where the ***** is.
**8.)** Look at column _Device_ and locate which device it is next to *. (for instance it might look like this: **/dev/hda1** )
**9.)** Look at column _System_ what does your * designated device say?
HPFS/**NTFS** or VFAT (something with **FAT** will do fine!).
> 
If **FAT** then type as follows... 
if not then jump to the **NTFS** section!

([COLOR="Red"]hda1[/COLOR] might not be your designated device, you put whatever ID you got on step **8**!)
**[COLOR="DarkOrange"]----------------FAT----------------[/COLOR]**
**10.)** sudo mkdir /media/windows
**11.)** sudo mount /dev/[COLOR="Red"]hda1[/COLOR] /media/windows/ -t vfat -o iocharset=utf8,umask=000

-**[COLOR="DarkOrange"]---------------NTFS----------------[/COLOR]**
**10.)** sudo mkdir /media/windows
**11.)** sudo mount /dev/[COLOR="Red"]hda1[/COLOR] /media/windows/ -t ntfs -o nls=utf8,umask=0222

Now the moment of truth [-o< (If you believe in GOD this would be a good time to pray) :twisted: 
**12.)** Go up to menu and click _Places > **Computer**_

Can you find your mounted Windows disk?  If not then you must have miss typed during step 11.  You might have gotten a message saying "unable to mount or access denied".  Then you will have to unmount the disk even though it didn't got mounted right!

**13.)** sudo umount /media/windows/
**14.)** Try step 11 again and make sure you're using the right section.  It's either **FAT** or **NTFS**.  Then make sure you typed the long complicated commands in **step 11** correctly.

---

### Post by PotOfVB on 2006-12-01
Another solution to recover windows files: 

This will allow you to keep all your existing files, and will install windows onto the same drive. 
You may be able to fix the old windows from here. I don't think it is worth the effort.
Also your programs,drivers etc will need to be reinstalled

from [http://pcworld.about.com/magazine/2109p156id111652.htm]("http://pcworld.about.com/magazine/2109p156id111652.htm")

Boot your computer with your Windows CD-ROM inserted. When you get the 'Press any key to boot from CD' message, do so. 
(If you don't see that message before Windows starts, restart Windows, press the key you're prompted to enter for your PC Setup program, and change the boot order so your CD drive is first.)
At the 'Welcome to Setup' screen, press Enter. 
The R (repair) option takes you to the Recovery Module, which is useful if Windows won't boot, but it's no help with a reinstallation. 
Soon you'll be told that there's already a Windows installation on the computer.
Press r for a repair reinstall or Esc to begin a complete, destructive one. 
For a complete restore, select your C: partition and press Enter. When you get the warning that says an operating system is on that partition, press c.
When you are asked your partition preference, select Leave the current file system intact (no changes). 
When you're told that a Windows folder (or Winnt folder for Windows 2000) already exists, press l ('ell') to delete it and create a new one. 
Follow the series of prompts. When the installation program asks for your name, enter temp.
Once the installation is complete, your system will reboot into Windows, and you'll be logged on as user Temp. If the screen is difficult to read, reinstall your graphics card driver.

To install ubuntu you will need to partition the drive, the drive will need to be split into 3 partitions. An example: 
1. _win xp_       * C: *                ntfs
2._ ubuntu_       */ (root)*          ext3
3. _swap_                               linux swap

if you get windows working try something like _partition magic_ to partition drive non-destructively

Lastly install ubuntu, what ubuntu live cd have you got 6.06, 6.10?
I couldn't get 6.06 to boot, kept locking up due some driver support for my pata controller, but could get 6.10 to boot,

is your bios set to boot from cd first?

---

### Post by binselam on 2006-12-01
Hi,
First, what type computer do you have? and Did it come with Windows  Operating System/System Recovery Disks? If you have any one of those disks, you migh be able to repair your OS and backup your files. Than, you can install an Operating System. 
Or as suggested, you can boot from a LiveCD , mount the disk and recover your data.
NOTE: if you realy need the data and you don't wanna risk loosing the data, you should take your computer to a computer repair shop. 
GOOD LUCK

---

### Post by binselam on 2006-12-01
Hi,
First, what type computer do you have? and Did it come with Windows  Operating System/System Recovery Disks? If you have any one of those disks, you migh be able to repair your OS and backup your files. Than, you can install an Operating System. 
Or as suggested, you can boot from a LiveCD , mount the disk and recover your data.
NOTE: if you realy need the data and you don't wanna risk loosing the data, you should take your computer to a computer repair shop. 
GOOD LUCK

---

### Post by rachael on 2006-12-01
Stupid question I'm sure but...how do you get that line at the end of step six?!?!?

---

### Post by rachael on 2006-12-01
I can see it on my keyboard but there are three other symbols on the same key and I can only toggle between two with the shift button!!

---

### Post by jingo811 on 2006-12-01
It's next to your [right-Shift] button \\:D/ -------------------- I slipped, honestly!

---

### Post by rachael on 2006-12-01
No it's not!! Seriously!!! I'm not being blind!! It's next to the alt button but there are 3 other symbols on the same button and I can only type two of them!

Would you believe I'm doing Computing A-Level this year! :-|

---

### Post by rachael on 2006-12-01
Woo scratch that last part, I've worked it out

Well, that's the hard bit done :p

---

### Post by jingo811 on 2006-12-01
Computer level A :confused: what's that. hehe, I'm from not the same country as you.  May I ask how old you are?

---

### Post by rachael on 2006-12-01
I'm from England and A-Levels are the last level of school before university. I'm 17 :)

Also, after I type 'sudo fdisk -|' all i get is this:

>




By the way, thank you so much for all of your help!!!

---

### Post by jingo811 on 2006-12-01
17?! :mrgreen: 
Well miss 17 prepare for a little information overload l = L

you typed: sudo fdisk -|
me  types: sudo fdisk -l   

I might have misinterpreted your question last time around I thought you couldn't find "-" but now I see what you meant.  The last one is a small letter "L".

Well hope you'll manage by yourself from here on, me sleepy time....zzz

---

### Post by rachael on 2006-12-01
It worked!!!!!

Thank you all soooo much!!!

All my data is there!!! I feel soo happy now :D 

Am off to bed now I can sleep peacfully :D :D :D 

And again, thank you, I know this has taken a while :p

---

