---
title: "another newb story"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by tekwarren on 2005-12-31
hello folks, i'm giving ubunut a whirl as step back into learning some linux.

My issues:

I'm dual booting with grub - XP and ubuntu. Durring installation I don't know if went about it the wrong way but I never got anything about the installer "detecting" my windows installation. Not a big deal after some searching here I was able to add the appropriate entries into menu.lst. Windows was able to load no problem...that time. Now it seems like every time I boot into windows it messes up grub. When trying to boot into ubuntu after a windows session I keep running into reboot cycle as soon as grub starts to try and load. I see the message about hitting escape to choose what I want to boot for a split second and then the system reboots. This continues over and over and I have use the ubuntu install disk to re-install grub. 

-This is a major hassle to say the least, but maybe I did something foobar and will learn from it.

Also this last time I wanted to get into windows without having to do the whole grub reinstall dance so I put the xp cd in to restore/rebuild the mbr and really foo'd something up and was getting the "missing ntldr" message and nothing would fix it and I know the files are there. I tried every method suggested in these forums and some found via google. Finally a reinstall of grub once again and the entry for windows again...and I was able to get windows to load again. Something strange though when I chose windows this time I got another menu (nt boot loader?) giving me additional options lf "1" and the regular Windows XP...I'm not sure where the "1" is coming from but I may poke around the nt boot loader and see if its in there. I'd like it to just go right to XP and load when I chose it from the grub menu.

I think these are enough questions for now and I appreciate any help offered.

---

### Post by tekwarren on 2005-12-31
Well once again after a windows session i shutdown for a time and came back and yippee!! :( grub is freaking out AGAIN with the reboots. I took notes this time for some more specific info.

When booting up with the install cd I have noticed my partition information has been changing and finally wrote it down:

The root (/) partition is constantly be changed so that it is NOT flagged as bootable, and its changed from root (/) to /media/hda3

I don't know what the deal is here. I'm thinking about trying to run the XP cd and re-creating the MBR so it boots into windows and using the nt boot loader...but as I posted above when I tried to rebuild the MBR with XP cd before I kept getting ntldr missing (which it is not) and could not load windows again untill reinstalling grub. Its a very annoying cycle to keep having to do this.

Should I wax ubuntu and try again...or forget it alltogether? When I first setup ubunu I followed a guide on the net and only created 2 partitions: a swap and / with the appropriate settings so that / was flagged bootable and actually set as root.

:confused:

---

### Post by prizrak on 2005-12-31
Hmm interestingly enough that is the same exact issue my dad is having on his work machine. Do you run a RAID controller? That's what he had.

---

### Post by d1337 on 2005-12-31
Are your partitions on the same HD or seperate (XP on one, your Ubuntu on another).  During install, what filesystem did you choose?

Well, it's New Years Eve and I've already indulged in a beverage, but I think since you haven't done much in Ubuntu yet, a clean install maybe just what you need.  It sounds to me that Grub is botched and maybe hasn't taken over the MBR  as it should have and quite possibly your partitions are crossed up a bit.  Considering that the install didn't detect your XP install, something may have gone afoul.  If you have a good internet connection, a clean install shouldn't take too long.  While I know that it can likely be fixed and that it would likely be a learning experience, it can also be quite frustrating.

With that being said, maybe you'd like to post you /boot/grub/menu.list here first to see if we can pick it apart some.

d1337

---

### Post by tekwarren on 2005-12-31
I do not have a raid setup its just a single hard drive in a laptop.

Here is my current menu.lst from grub. Bear in mind I know it doesn't have the entry for windows as its the default "re-installed" grub that I am forced to do everytime I restart after a windows session.

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

Reinstalling ubuntu wouldn't deter me much from trying it again if that is what you guys think will help my issues. I don't know much about the setup of linux but would my partitions be wrong in some way? In the free space I created a swap partition (512mb) and then the main partition / for linux. Only those two partitions and in that order would that be causing some issus?

---

### Post by vasudevank on 2005-12-31
have you tried grub interactive mode

---

### Post by tekwarren on 2005-12-31
no I haven't...honestly I don't even know what that is how to do it. I finally just blew away the partitions I created for linux. I still had a heck of a time trying to get windows to boot back to normal. For some reason I couldn't fix the mbr with the cd using the usual commands. I tried rebuilding the mbr, and a couple other commands that should have restored or recreated the mbr. All of the commands completed successfully but I kept getting the ntldr error message. Finally I just did the automated repair which basically reinstalled windows and I didn't lose any of my programs or data just had to reinstall all the windows updates (thanks  to autopatcher for making that painless). So I guess I might re-try the ubunto install again later. Still curious as to where I may have gone wrong though.

---

### Post by tekwarren on 2006-01-03
If/when I go to try the install again any tips? I have an existing windows partition, so I thought the only way to save that was to do the manual partition setup for Ubuntu. Any suggestions for the next round?

---

### Post by carlosqueso on 2006-01-03
If manual partitioning isn't working for you, I'd try installing Mandriva first.  Their installer has a great partitioning utility called DiskDrake, which should get you set up.  Then you can just install Ubuntu over Mandriva's partitions.  That worked for me, and didn't require thought (a big plus for a n00b like me).

---

### Post by Luke on 2006-01-03
i'm very new to linux but so far my setup has worked perfectly. my first experience with linux was with fc4 but for various reasons, i ended up not using it much and when i decided (again) that i wanted to learn how to use linux i decided to go with ubuntu. when using fc4, i'd decided (for reasons i'd read somewhere on the interweb) to use GAG as my bootloader. i had a very positive experience with it and decided it would be my bootloader of choice from then on. 

so, before i installed ubuntu, i installed GAG to my mbr and then installed GRUB to my linux partition. ideally i wouldn't have installed GRUB at all since i now have two bootloaders but ubuntu seemed to complain when there was no grub. GAG boots windows xp with no problems (not that i've used xp in a while on my main machine but i also have GAG on my other laptop which only has xp on it at the moment).

[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

not sure if this will help but you might want to give it a shot on your next go 'round

also, i had an existing windows partition when i installed. i let the ubuntu installer automatically parition the "free space". i think i may have manually adjusted the sizes after that but it at least took care of creating the proper mount points and what not.

---

### Post by tekwarren on 2006-01-03
thanks guys, I think i'll try again and just let ubuntu do its thing with the partitions rather than me pretending to know what I'm doing :rolleyes: if that doesn't work I'll try the suggestions here.

---

### Post by Sef on 2006-01-04
If you have a dual boot, the windows partition should be set to bootable, and Ubuntu root should not set to not bootable.

---

### Post by Luke on 2006-01-04
[QUOTE=Sef]If you have a dual boot, the windows partition should be set to bootable, and Ubuntu root should not set to not bootable.[/QUOTE]
is that double negative intentional?

---

### Post by tekwarren on 2006-01-04
I don't see a double negative there its quite clear what he stated... Anyways I just did another install using the guided mode and once again grub did did not pick up my XP install. I'm going to add it to the menu and test it by booting into windows and seeing if it freaks out again.

---

### Post by tekwarren on 2006-01-04
ok guys frustration is really starting to get to me. I tested booting into windows again then rebooted and YEP...I get consistent reboots after Loading GRUB 1.5... displays. The ONLY way I can get back to a usable OS is to reset the linux partion back to "/" turning on the bootable flag...AND reinstalling GRUB which still fails to see that there is XP on another partition.

I tried setting the windows partition to bootable and no go it only works if I set the linux to bootable and reinstall GRUB...I can then as stated above add the windows entry into menu.lst for another ONE time use to boot into XP after which this damn cycle starts all over.

It has to be something in windows right? Is something protecting the MBR or trying re-write it? I'm at a loss and not quite ready to go full on into Ubuntu just yet :confused:

---

### Post by thekiller on 2006-01-04
if u are currently in ubuntu, post the output of :

```

more /etc/fstab

```

and if you can also repost your menu.lst, it would be great. Lets attack the problem one by one.

---

### Post by tekwarren on 2006-01-04
fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```


and the current menu.lst with no windows entries:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```


Thanks for your time and efforts!

---

### Post by Lord Illidan on 2006-01-04
Try adding this :



title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1

---

### Post by tekwarren on 2006-01-04
[QUOTE=Lord Illidan]Try adding this :



title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1[/QUOTE]


doesn't help, if you read the whole thread you would see the problem is not that I don't know how to add the option for windows...but that after a windows session something (grub?) gets toasted.

---

### Post by thekiller on 2006-01-04
i noticed you have an ntfs filesystem, now when u were in ubuntu did you try to write something over to windows ? I know some ppl think its dangerous/risky to write over an ntfs filesystem from a linux partition, but it might have done something nastier in your case. 

See this thread : [http://www.ubuntuforums.org/showthread.php?t=42632](http://www.ubuntuforums.org/showthread.php?t=42632)

I personally use a FAT32 filesystem for my windows, and i havent had any problems with it. Everything is still working like charm (keepin my fingers crossed) :)

---

### Post by tekwarren on 2006-01-04
Honestly I have spent very little time exploring ubuntu and really doing much of anything as I want to solve this problem first. I have made no attempts to mount the windows partition or do any sort of writing to it. I still have a notion that "something" is happening from windows each time I am able to load it. I just can't think of what. I thought maybe I had system restore turned on (which I still may) but I don't think that does anything the MBR. Also I asked my supervisor here at work and he recently setup fedora/XP and his XP has system restore on and he has no issues.

I'll have to do some poking around in windows tonight and see if I come with anything. I am anxious to explore Ubuntu and linux more if I can get past this issue.

---

### Post by tekwarren on 2006-01-04
It just clicked that I should add this I did use Partition Magic to resize my main partition to make another for ubuntu...does this help troubleshoot?

---

### Post by thekiller on 2006-01-04
nopes, partition magic is a good tool. That cant be the problem. And windows cant corrupt your linux partition. I cant trace what the problem is, if it still exists than I would suggest you to wipe out everything, and do a fresh install of windows and ubuntu. Remember to use FAT32 as your filesystem in windows. You can go either way, install ubuntu first and then xp or vice versa. If you do plan to install ubuntu first, then remember to leave first partition for windows. And use the second partition for ubuntu.

---

### Post by Luke on 2006-01-05
did you try GAG as i suggested earlier?
[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

### Post by tekwarren on 2006-01-05
the issue isn't that the ubuntu partition is being corrupted...its something happening to GRUB and the master boot record. If I reboot and keep going into ubuntu i'm fine but one time boot into windows...from grub and the next reboot grub is f'd up. I have not tried the other boot loader suggested. I'm going to image the windows data and then just manually creat the partions (without partition magic) and after doing a full format on the hard drive. I'll lay the image of windows back down on the first one and then try the ubuntu install again and see what happens. Course my laptop took a dump again this morning so it might be a bit before I can try this again (ongoing hardware issue with HP/compaq NX9500...POS!).

---

### Post by tekwarren on 2006-01-26
Ok so I get my laptop back from HP after being in for repair for nearly 3 weeks and system board replacement #5...but that's a long and aggrivating story...

I boot up with the xp cd yesterday and split the HD into two partitions. I re-image partition 1 with my existing xp installation. Then last night I get Ubuntu installed and everything went perfect. I used the guided mode and used the longest continious free space and everything is partitioned automatically. The install goes smoothly and quickly and it DID "detect" XP on the other partition and GRUB installed with no issues including the entry for XP. I had ubuntu up doing a few things and thinking all was good. My wireless wasn't working so I boot into windows right before I'm about to head to bed as I can't remember what brand the wireless is (broadcomm). I shutdown and done for the night.

This morning I get to work...start up the laptop and guess what....YEP...I get to the "GRUB loading stage 1.5" (or whatever it says) and then REBOOT and its constant it will keep rebooting and get to the GRUB loading stage and reboot again.

As posted above the ONLY way I have been able to get around this is by repairing/reinstalling GRUB OR doing the FIXMBR/FIXBOOT from the xp cd. SOMETHING is happening when I boot into XP to cause this. I can reboot (on my own) over and over and as long as I keep going into Ubuntu I'm fine but as soon as I load windows once GRUB gets toasted.


Need Advice!

---

### Post by void_false on 2006-01-26
Try booting with XP cd in drive. Yes you heard it right. Put CD into the drive and  try booting grub. I dont know why but GRUB didnt work for my friend until he inserted this damn cd.

---

### Post by tekwarren on 2006-01-26
I over joyed to announce that I think I have solved the issue. It never occured to me to mention anything about zenworks being in the windows install. We have a novell network here at work. 

I started googling my initial issue once again and came across an article/post about a bug with grub. Apparently there is a registry key related to zenworks that does something to the mbr and is known to screw up grub. The note stated to remove the key from the windows registry which I did.

The next part was tedious but a great learning experience. I needed to reload grub...easy right? Well I didn't bring my ubuntu install cd with me to work! So after more google searching an reading I found out how to reload from a knoppix live cd I keep on hand. 

I just did a test with booting into linux and then windows...AND...I have successfully rebooted into Ubuntu AFTER a windows session! WOOOHOOO now I can get back to experiencing ubuntu!

Thanks for all the suggestions, my next journey will probably getting my broadcomm wireless up...but I think I've seen some posts on that around here in my searches. :wink:

---

### Post by mips on 2006-01-26
tekwarren,

I'll give you 10/10 for perseverance =D>

I think you'll take to linux like a fish to water...

---

### Post by tekwarren on 2006-01-26
Thank you :KS  Its to easy to give up, I knew it had to be something I could overcome! I do have a question though, I was thinking since I reloaded grub from the knoppix cd (not sure how old it is but not current) should I update grub or isn't that necessary?

---

### Post by mips on 2006-01-26
I honestly dont know, they might be different versions. Me i'd simply upgrade.

---

### Post by mips on 2006-01-26
lol, it just occurred to me that this wasn't actually a linux problem...

---

### Post by tekwarren on 2006-01-27
I'm all about being up to date is there an apt-get way to update grub?


And you are right my issue was in no way a Linux problem :)

---

### Post by tekwarren on 2006-01-28
Well amazingly enough I crossed two more bridges yesterday! I got my broadcom wireless working on this laptop in the afternoon and last night I installed the latest nvidia drivers!\\:D/

---

