---
title: "[SOLVED] Stupid mistake: Edited ls command in nano"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Smatt454 on 2007-10-09
So I'm completely new to linux. So i decided to have some fun and make the ls file in /bin/ writable.

I edited with nano..put something stupid in the first line like "mkdir /home/smatt/Desktop/newfolder"

then I tried the ls command....it didnt work. I dont remember the error.

So i went back in nano and took the line i added out, and i took the writable option off of ls.

Now whenever I log in it stats a failsafe xterm session.  Now when I try ls, it says "Segmentation fault (core dumped)"

I know I did something really stupid, I'm a n00b to linux and it's fun messing around with stuff

guess they make it read-only for a reason huh?

I don't know if there's any way to fix it. And if my only option is an uninstall... well...that's a problem. I'll explain that if I don't get any other options

So if anyone has any ideas...I'd greatly appreciate them. Thanks :guitar:

---

### Post by bodhi.zazen on 2007-10-09
boot a live CD and try copying /bin/ls to your ubuntu partition /bin/ls :twisted:

---

### Post by rsambuca on 2007-10-09
I think I would just re-install.

---

### Post by milosz.galazka on 2007-10-09
*sudo aptitude reinstall coreutils*
run this from command line, it should solve this problem :)

---

### Post by Smatt454 on 2007-10-09
It said it wasnt able to locate files coreutils , then asked me if i was root. I'm in recovery mode right now.

I dont have an Internet connection on the computer with ubuntu, in case that matters.

Also, i've been trying to boot from a live cd, the same one i did to install ubuntu, it wont boot from cd (yes i checked the priority in the bios)

i put the like cd in this computer (running windows xp) and it works just fine. 

I'd like to fix the cd problem...but fixing my ls problem and getting it to stop starting a failsafe xterm session first

---

### Post by Adramelech on 2007-10-09
hummmm have you checked if nano left a backup copy? the backup is normally named with a '~' at the end, go check and replace the one u got messed with that one.

---

### Post by Smatt454 on 2007-10-09
no backup was left

=(

---

### Post by Lord Illidan on 2007-10-09
I attached my /bin/ls file in this archive. Perhaps you can try using a flash drive to copy it to /bin.

---

### Post by milosz.galazka on 2007-10-09
You could for example download using windows [coreutils]("http://pl.archive.ubuntu.com/ubuntu/pool/main/c/coreutils/coreutils_5.97-5.3ubuntu3_i386.deb")
and then from ubuntu copy it to new empty directory and in this directory run command (to extract package)
```
dpkg -x coreutils_5.97-5.3ubuntu3_i386.deb .
```
then you can copy *ls* command to */bin*

---

### Post by bodhi.zazen on 2007-10-09
LOL 

/bodhi hands milosz.galazka wget :

```
wget http://pl.archive.ubuntu.com/ubuntu/pool/main/c/coreutils/coreutils_5.97-5.3ubuntu3_i386.deb
```

No need to download in windows ...

:lolflag:

---

### Post by Smatt454 on 2007-10-09
> **milosz.galazka said:**
> You could for example download using windows [coreutils]("http://pl.archive.ubuntu.com/ubuntu/pool/main/c/coreutils/coreutils_5.97-5.3ubuntu3_i386.deb")
and then from ubuntu copy it to new empty directory and in this directory run command (to extract package)
```
dpkg -x coreutils_5.97-5.3ubuntu3_i386.deb .
```
then you can copy *ls* command to */bin*

dont i need an internet connection for that?

---

### Post by Smatt454 on 2007-10-09
> **Lord Illidan said:**
> I attached my /bin/ls file in this archive. Perhaps you can try using a flash drive to copy it to /bin.

how do u copy it over to bin (what would be the location of the flash drive?)

---

### Post by bodhi.zazen on 2007-10-09
> **Smatt454 said:**
> dont i need an internet connection for that?

Is you network working ?

You can bring it on line with 

(still in recovery mode)

/etc/init.d/network start

You can also get a X session with :

startx

---

### Post by Smatt454 on 2007-10-09
> **Smatt454 said:**
> how do u copy it over to bin (what would be the location of the flash drive?)

i stated earlier in my thread that I do not have an internet connection on my computer with linux

do you know a way that i can find the location of a thumbdrive with the bin/ls file on it?

---

### Post by bodhi.zazen on 2007-10-09
Usually thumb drives mount in /media

you can enter 

```
sudo fsdisk -l
```

to list your partitions

```
mount
``` to show mount points

---

### Post by Smatt454 on 2007-10-09
> **bodhi.zazen said:**
> Usually thumb drives mount in /media

you can enter 

```
sudo fsdisk -l
```

to list your partitions

```
mount
``` to show mount points

i'm still confused how to find the location of the USB thumb drive

---

### Post by bodhi.zazen on 2007-10-09
Plug the drive in, then from the command line :

```
ls /media
```

---

### Post by Smatt454 on 2007-10-09
my whole problem is the fact that ls doesnt work.....

---

### Post by bodhi.zazen on 2007-10-09
Use tab completion

cd /media/<tab><tab>

---

### Post by Smatt454 on 2007-10-09
.hal-mtab-lock     cdrom0/          floppy/             floppy1/
cdrom/                 cdrom1/          floppy0/

---

### Post by Smatt454 on 2007-10-09
don't know where to go from there :(

---

### Post by bodhi.zazen on 2007-10-09
Your flash drive is not recognized.

You will have to try something else, what about copying /bin/ls from the live CD, I think that woudl be easiest at this point.

---

### Post by Smatt454 on 2007-10-09
i assume that would be in the media directory too? something like /media/cdrom/bin/ls ?

---

### Post by bodhi.zazen on 2007-10-09
You will have to boot the live CD, then mount your Ubuntu partition.

Then

sudo cp /bin/ls /media/ubuntu/bin/ls

where "/media/ubuntu" is the mount point of the Ubuntu partition.

---

### Post by Smatt454 on 2007-10-09
it would be so much easier if i could check what's in directories by using the ls command

but since i screwed that up...i'm pretty much lost

like i said...i'm a complete linux n00b

---

### Post by Smatt454 on 2007-10-09
> **Smatt454 said:**
> I

Also, i've been trying to boot from a live cd, the same one i did to install ubuntu, it wont boot from cd (yes i checked the priority in the bios)

i put the like cd in this computer (running windows xp) and it works just fine. 



yeah...that's a problem :(

i wouldnt mind reinstalling....but my computer wont boot from the cd

---

### Post by bodhi.zazen on 2007-10-09
Odd that you can not boot the CD ... It obviously booted earlier ...

You will have to boot windows, install the fs-driver (to access you linux partition from windows)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

Download the zip from  Lord Illidan

[http://ubuntuforums.org/showpost.php?p=3505545&postcount=8](http://ubuntuforums.org/showpost.php?p=3505545&postcount=8)

Extract (un zip) ls and copy it from windows to your ubutnu partition, in /bin/ls

---

### Post by Smatt454 on 2007-10-09
i dont have windows on that computer...and it wont boot from cd =/

---

### Post by bodhi.zazen on 2007-10-09
Game over

---

### Post by Smatt454 on 2007-10-09
> **bodhi.zazen said:**
> Game over

there has to be something i can do =/ any ideas how i can fix it so it boots from the cd?

---

### Post by rsambuca on 2007-10-09
Try updating your bios.

---

### Post by Smatt454 on 2007-10-09
how?

---

### Post by rsambuca on 2007-10-09
I don't know, but some motherboards have a bios that can be 'flashed' back to factory setting.  Check the manual of your motherboard - you can usually find it on the manufacturer website.

---

### Post by bodhi.zazen on 2007-10-09
> **Smatt454 said:**
> there has to be something i can do =/ any ideas how i can fix it so it boots from the cd?

1. Just do what ever you did to boot from CD the first time ???

2. Download a boot floppy.

[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

---

### Post by Smatt454 on 2007-10-09
okay i'll try that. thanks for the help.

---

### Post by llamakc on 2007-10-09
Why update the BIOS? Just SET the BIOS to boot from the CD first. 

Do you know how to GET into BIOS at boot?

EDIT: I'm late to this party. Good luck, OP.

---

### Post by rsambuca on 2007-10-09
> **llamakc said:**
> Why update the BIOS? Just SET the BIOS to boot from the CD first. 

Do you know how to GET into BIOS at boot?

EDIT: I'm late to this party. Good luck, OP.

'cause he said it is set to boot from the Cd drive first, and that he had already used the CD to install Ubuntu in the first place.  Something is borked here.

---

### Post by Smatt454 on 2007-10-09
> **bodhi.zazen said:**
> 1. Just do what ever you did to boot from CD the first time ???

2. Download a boot floppy.

[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

 i did do what i did what i did to boot with the cd the first time

it wont boot. i dont know why

i did open up my computer and attempt to add in an old network card...but it was bad.I checked the ribbon wires and they all seem to be fine...but I could have messed up something with the hardware =/

also..i dont have a floppy drive on this computer (my only internet access)

---

### Post by Smatt454 on 2007-10-09
well i'm just going to go off to bed for now (i'm in high school...got to get up at 4:30)

so i'd appreciate if anyone has any more ideas how i could fix my problems. if not...i'll just check my motherboard..i'm thinking CMOS is corrupted or something

---

### Post by llamakc on 2007-10-09
> **rsambuca said:**
> 'cause he said it is set to boot from the Cd drive first, and that he had already used the CD to install Ubuntu in the first place.  Something is borked here.

Yeah, that's why I edited my post after going back through all of the pages. 

Why hasn't the OP just reinstalled 'ls' from the coreutils package that's already in /var/cache/apt/archives? 

```

cd /var/cache/apt/archives && cp coreutils.deb /tmp && cd /tmp && sudo dpkg -x coreutils.deb /tmp/coreutils && cd /tmp/coreutils/bin/ && sudo mv /tmp/coreutils/bin/ls /bin
```[COLOR=Red]**PS: You'll have to use the actual filename for the coreutils package in the above example.**[/COLOR]

---

### Post by Lord Illidan on 2007-10-10
A good solution. But if he did  		*sudo aptitude reinstall coreutils *wouldn't it have worked as well? Because it didn't. But, anyway, try it and see what happens. Things can't really go worse now.

However, I'd investigate why it can't boot from CD anymore.

---

### Post by llamakc on 2007-10-10
> **Lord Illidan said:**
> A good solution. But if he did          *sudo aptitude reinstall coreutils *wouldn't it have worked as well? Because it didn't. But, anyway, try it and see what happens. Things can't really go worse now.

However, I'd investigate why it can't boot from CD anymore.

I believe that was tried already (have to go back up and read again). Perhaps the preinst and postinst scripts have a call to "ls" in them somewhere?

---

### Post by Smatt454 on 2007-10-10
> **llamakc said:**
> Yeah, that's why I edited my post after going back through all of the pages. 

Why hasn't the OP just reinstalled 'ls' from the coreutils package that's already in /var/cache/apt/archives? 

```

cd /var/cache/apt/archives && cp coreutils.deb /tmp && cd /tmp && sudo dpkg -x coreutils.deb /tmp/coreutils && cd /tmp/coreutils/bin/ && sudo mv /tmp/coreutils/bin/ls /bin
```[COLOR=Red]**PS: You'll have to use the actual filename for the coreutils package in the above example.**[/COLOR]

how do i figure out the filename for the coreutils?

---

### Post by Smatt454 on 2007-10-10
the tab completion says 

lock
partial/

in archives

---

### Post by dannyboy79 on 2007-10-10
I myself don't have coreutils located within /var/cache/apt/archives/, so it's possible that you don't either. You can see if it's anywhere on your machine with either 
locate coreutils
or
sudo find / -name coreutils
if it doesn't show up with a  .deb on the end, you don't have it and you'll have to either figure out why your cd isnt' booting on your machine anymore (scratch, dirty cd-drive lens, etc etc) or do what I suggest below:

to be honest the easiest thing to do is (if nothing else is working), use the ls.zip that the guy has uploaded for you on page 1 of this thread. To use it, I mean, go to any internet accessable location, a library, a friends house, your windows computer if it's online or whereever you can get to the ubuntu forums and this thread, page 1. Download the ls.zip to a removable media source. this can be a thumb drive, an external hard drive, heck, you could even burn it to a cd.

Now, go home, and  plug in your media stick. It should just show up as an icon on your desktop. Do you have admin privileges on this computer? Meaning, you're the first account on the computer right? If so, then the password you used when installing ubuntu is also the same password that will give you root privileges using "sudo".
Double click the media stick and it'll open nautilus window (nautilus is a file browser), now navigate to where you "saved" that ls.zip file, then just double click it. Now, if you are on a  recent version of ubuntu, another little window opens, that means ubuntu has a GUI driven archive extraction tool (i forget what it's called)  to "unzip" the zip file. You should see an extract button at the top of the gui window, click that and it should ask you where to save the file. Now just chose /home/username/Desktop. So you should now have a ls file on your desktop. 
Now to overwrite the existing WRONG ls command, just issue this command.
sudo mv /home/username/Desktop/ls /bin/ls
(note: username should be YOUR username) it'll ask you for a password, this is that sudo password that I mentioned earlier.

THen you should be done.

If you had to burn the ls.zip to a cd, then instead of a little icon showing up on your desktop that looks like a usb drive, a little disc should show up on your desktop and you would just follow the same instructions.

I would perform a restart and see if ls works again.

I do have to ask, ls is a binary file, why would you open it in nano to edit it? Didn't you notice that it was a bunch of gibberish?? Are you aware of what the ls command does, why were you trying to put something in there and make the file writable? Word to the wise for next time, don't mess with system files/utilities next time unless you know what you're doing. Not trying to be rude, just trying to be real.

---

### Post by Lord Illidan on 2007-10-10
> **dannyboy79 said:**
> to be honest the easiest thing to do is (if nothing else is working), use the ls.zip that the guy has uploaded for you on page 1 of this thread. To use it, I mean, go to any internet accessable location, a library, a friends house, your windows computer if it's online or whereever you can get to the ubuntu forums and this thread, page 1. Download the ls.zip to a removable media source. this can be a thumb drive, an external hard drive, heck, you could even burn it to a cd.

Now, go home, and  plug in your media stick. It should just show up as an icon on your desktop. Do you have admin privileges on this computer? Meaning, you're the first account on the computer right? If so, then the password you used when installing ubuntu is also the same password that will give you root privileges using "sudo".
Double click the media stick and it'll open nautilus window (nautilus is a file browser), now navigate to where you "saved" that ls.zip file, then just double click it. Now, if you are on a  recent version of ubuntu, another little window opens, that means ubuntu has a GUI driven archive extraction tool (i forget what it's called)  to "unzip" the zip file. You should see an extract button at the top of the gui window, click that and it should ask you where to save the file. Now just chose /home/username/Desktop. So you should now have a ls file on your desktop. 
Now to overwrite the existing WRONG ls command, just issue this command.
sudo mv /home/username/Desktop/ls /bin/ls
(note: username should be YOUR username) it'll ask you for a password, this is that sudo password that I mentioned earlier.

THen you should be done.

If you had to burn the ls.zip to a cd, then instead of a little icon showing up on your desktop that looks like a usb drive, a little disc should show up on your desktop and you would just follow the same instructions.

I would perform a restart and see if ls works again.

I do have to ask, ls is a binary file, why would you open it in nano to edit it? Didn't you notice that it was a bunch of gibberish?? Are you aware of what the ls command does, why were you trying to put something in there and make the file writable? Word to the wise for next time, don't mess with system files/utilities next time unless you know what you're doing. Not trying to be rude, just trying to be real.

The problem is that he can't even go on the gui.

However, I have to second what you said here. Never, EVER edit binary files in text editors. To edit binary files, you need hex editors, and even those are used rarely.

I'd do a reinstall right now, but it seems as if he can't even boot from the cd.

---

### Post by Smatt454 on 2007-10-10
ugh...no .deb file

and yeah i cant go into the gui....=(

yeah i know editing binary files is stupid.....i just was having fun messing around.

I'm smart...yet I lack command sense.

Ugh....I've tried everything to get the cd to boot...and to get into the gui. No such luck.

:(

---

### Post by dannyboy79 on 2007-10-10
ok, fine. here's the instructions if you can't get into a gui but I never read that he said that. I only read that he was in recovery mode, which I thought he thought he needed to do that but most likely not. Just enter ubuntu as normal.

from recovery mode. (i found out that unzip isn't installed by default, so what you should do is unzip it on the machine that you used to download it from the inernet. So you would just have a file called ls on your usb stick or on the cd that you burned.

when you plug in your media stick, it may or may not get automounted. To find out if the media stick is seen by ubuntu issue this command

sudo fdisk -l

this will return stuff like this as an example:

Disk /dev/hdd: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       36483   293049666   83  Linux

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48641   390708801   83  Linux

You'll want to see which one of the Disk /dev/foo is closest to the size of the media stick that you used. Whether it's 256mb or 1gb or what. It's most likely going to be a /dev/sdX versus /dev/hdX (x represents a number of the partition if the media stick is even partitioned) because USB sticks are emulated as SCSI devices.

So now for example you say you know the drive that you plugged in is at /dev/sda or /dev/sda1

You'll want to mount that to a location so that you can access the files on it. You would issue this command
sudo mount /dev/sda (or /dev/sda1) /mnt/
it should automount it without having to tell it the Filesystem type (because I am assuming it's FAT32)
this will mount the data that's on the media stick to the /mnt/ folder. Now you will want to copy the ls command to the proper location which will overwrite the WRONG ls command

sudo mv /mnt/ls /bin/ls

then unmount your media stick with
sudo umount /mnt/
then issue
sudo shutdown -r now
to restart your machine. you should be able to login to a gui now.

---

### Post by Smatt454 on 2007-10-10
i'm only getting hda1 hda2 and hda5

---

### Post by Smatt454 on 2007-10-10
if i were to burn the working ls file on a cd...wut directory would i find it in on linux?

---

### Post by milosz.galazka on 2007-10-10
If you insert cd then you should look into directories like */mnt/* or */media/* (like */media/cdrom/*) but there will probably appear cdrom icon on desktop

---

### Post by Smatt454 on 2007-10-10
i cant get into the gui

---

### Post by milosz.galazka on 2007-10-10
```
cat /etc/fstab
```
and you will see line similar to this (second column is a mount directory)
```
/dev/scd0       /media/cdrom0   auto user,noauto     0       0
```
then after you inserted cd
```
mount /media/cdrom0
cd /media/cdrom0
```

You can list files in directory by using command
```
echo *
```
or even if files does not contain spaces in their names
```
echo * | sed s/\ /\\n/g
```

---

### Post by Smatt454 on 2007-10-10
well i finally got it to boot from cd...so i'm just reinstalling ubuntu

thanks for all the help everyone

i'll but more careful when "messing around" on ubuntu

:guitar:

---

### Post by rsambuca on 2007-10-10
> **Smatt454 said:**
> well i finally got it to boot from cd...so i'm just reinstalling ubuntu

thanks for all the help everyone

i'll but more careful when "messing around" on ubuntu

:guitar:

Well tell us what you did to fix it.  To help others in the future.

---

### Post by Smatt454 on 2007-10-10
well...i didnt really want to because it's embarrassing.....
but it turns out one of the ribbon wires were loose  :oops:

---

### Post by rsambuca on 2007-10-10
Too funny!!!

Oh, well, don't sweat it.  These things happen on occasion, although I am surprised no one suggested checking the cables a while ago.

---

### Post by Smatt454 on 2007-10-10
well i said i had checked the cables....i double..even triple checked...but i opened my computer again and sure enough it was lose

---

