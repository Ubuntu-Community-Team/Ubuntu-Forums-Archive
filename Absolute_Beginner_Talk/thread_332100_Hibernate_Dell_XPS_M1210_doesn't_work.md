---
title: "Hibernate Dell XPS M1210 doesn't work"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by gardara on 2007-01-05
IHibernate doesn't seem to work on my dell XPS m1210. When I choose Hibernate the laptop doesn't hibernate. 
What happens is this: The screen goes blank, then there appear some text messages (I can't read it it's too fast), then the screen goes black again and nothing more happens. Now when I move my mouse I'm asked for my password. So it looks like the computer just went to some black screensaver. 
I have been looking for solution. The wiki tells that hibernate on M1210 does work out of the box, but the wiki is written for dapper and some of the things reported not woking there work with edgy so.... 

I also noticed in the wiki something about ubuntu needing SMP kernel for the core duo to work... do  I need this SMP kernel? Or was that only for dapper? How can I check if my CPU is working properly?
Maby that's the reason why the hibernate doesn't work?

I did read something about hibernate not to be working on other dell laptops, might this be the same problem? And will the same solution work?

Does anyone know what's wrong? Why I can't hibernate?

btw, the link to the M1210 wiki: [https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1210?highlight=%28m1210%29](https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1210?highlight=%28m1210%29)

---

### Post by gborzi on 2007-01-05
One possible problem that prevents hibernation on your laptop is the image_size setting. If you look under /sys/power, there is a file named image_size, that specifies the maximum amount (bytes) of swap area that can be used for hibernation. By default it is set to 512 MB. You should set it to the amount of RAM you have (get it with "free -b"). Obviously, your swap area must be at least equal to the amount of RAM you have.
To have the right value set at each startup put a line like this in your /etc/rc.local file: > echo XXXX > /sys/power/image_size
As for the kernel, the default 2.6.17-10-generic supports SMP, the 2.6.17-10-386 doesn't.

---

### Post by gardara on 2007-01-05
Thanks for your reply.

I tried looking at the image_setting file... but both with sudo and not sudo it wouldn't allow me to open the file... so I can't see what's inside it.

I have 1gb ram and did choose to have 2gb for swap when I set up ubuntu.

"free -b" gave me:

```
                 total              used                free     shared        buffers          cached
Mem:    1050959872  930160640  120799232               0   54784000  475824128
-/+ buffers/cache:      399552512  651407360
Swap:                      0                      0                     0

```

I'm pretty surprised that "Swap:" has 0 in everything.

I'm not sure how to use echo XXXX > /sys/power/image_size to change the image_setting.


And for the kernel then according to conky I have Linux 2.6.17-10-386 on i686. 
I'm not sure what SMP is. Should I move to 2.6.17-10-generic to get SMP?

---

### Post by gborzi on 2007-01-05
> **gardara said:**
> Thanks for your reply.

I tried looking at the image_setting file... but both with sudo and not sudo it wouldn't allow me to open the file... so I can't see what's inside it.
The file is /sys/power/image_size and it should be in 644 mode. To use the echo command do this > sudo -i
echo 1050959872 > /sys/power/image_size
the first command "sudo -i" make you as root, so after echo you need to exit (i.e. type exit or ctrl-D).

> **gardara said:**
> 
I have 1gb ram and did choose to have 2gb for swap when I set up ubuntu.

"free -b" gave me:

```
                 total              used                free     shared        buffers          cached
Mem:    1050959872  930160640  120799232               0   54784000  475824128
-/+ buffers/cache:      399552512  651407360
Swap:                      0                      0                     0

```

I'm pretty surprised that "Swap:" has 0 in everything.


I've read of similar problems for the swap partition in edgy. It seems to be due to the UUID used to identify partitions. Check the forum, there are some fixes.

> **gardara said:**
> 
And for the kernel then according to conky I have Linux 2.6.17-10-386 on i686. 
I'm not sure what SMP is. Should I move to 2.6.17-10-generic to get SMP?
SMP stands for symmetric multi processor (or processing ?), i.e. it's the kernel for computer having two or more identical CPU, like your multicore processor. You need to install linux-image-generic (if it isn't already installed) and select it at the grub menu.

---

### Post by gardara on 2007-01-06
Allright I did 

sudo -i
echo 1050959872 > /sys/power/image_size

but it didn't change anything.

I haven't found anything about my swap problems... I did some searching but didn't find any good solutions.

I tried the generic kernel. But I have some problems with it.... it doesn't find my wireless network card..... is that normal?

When I tried to make a hibernate with the generic kernel it didn't work but the message that appears on my screen did stay on the screen a little longer (the message that appears right after I click the hibernate button and right before the screensaver or blank screen appears.) I think I saw something mentioned about "cannot find swap"... so maby my swap problem is also my hibernate problem. 

btw. I also tried 2.6.15-23 kernel but the hibernate didn't work with it.... but another thing worked, the brightness... the brightness buttons on my screen don't work with 2.6.17-10 but they seemed to work fine with 2.6.15-23. Pretty strange :-k

---

### Post by gborzi on 2007-01-06
Until you fix the swap issue the image_size will be meaningless. As for the wireless, have you installed the linux-restricted-modules-generic package ? Without the restricted modules most wireless devices won't work.

---

### Post by gardara on 2007-01-06
ok I managed to get swap working, thanks to taurus in this thread: [http://ubuntuforums.org/showthread.php?p=1976187#post1976187](http://ubuntuforums.org/showthread.php?p=1976187#post1976187)

However when I try to hibernate it seems that hibernate kills my swap. 

(quoted from the other thread)
[quote=gardara]ok I did a reboot, everything seemed fine, the swap was still there.
Then I tried to hibernate. The computer didn't hibernate, because when I started my laptop again there didn't anything resume like it's supposed to be when hibernating, the folders and stuff I had open were closed all, so it was more like I had just turned the laptop off and then on again. Except for that the swap is gone. Free looks like this after the hibernate:

```


total used free shared buffers cached Mem: 1026328 491372 534956 0 21648 216488 -/+ buffers/cache: 253236 773092 Swap: 0 0 0

```[/quote]

I also managed to write down the error message I sometimes get when trying to hibernate.

```
17179948.94800 hda_intel azx_get_response timeout switching to single_cmd mode
```

do you know what this error message means?

And yes, I set up linux-restricted-modules-generic so now everything seems to work fine with the generic kernel.

---

### Post by gborzi on 2007-01-07
I don't know what's the meaning of that error message. But I'm sure you need to adjust your initrd configuration to fit the "new" swap partition. Since you made an mkswap, the UUID for this partition surely changed, so the initrd images for your kernels do not contain the correct swap partition. Open the /etc/initramfs-tools/conf.d/resume file, it should contain a line like this > RESUME=UUID=ae8c4db5-9cc9-44d3-a5c7-68bbc9252a79
where the string after the UUID= should be the old UUID of your swap partition. Change it to > RESUME=/dev/sda3 and update your initrds like this > sudo dpkg-reconfigure linux-image-2.6.17-10-generic
sudo dpkg-reconfigure linux-image-2.6.17-10-386 I think it is possible to regenerate the initrds with > sudo update-initramfs -k 2.6.17-10-generic
sudo update-initramfs -k 2.6.17-10-386
please note that when you resume from hibernation you need the same kernel you used before the hibernation. I mean, let's suppose that your default kernel is 386, but you started with the generic one and then put your laptop in hibernation. When you resume, you have to select the generic kernel at the grub prompt.

Let me know if this works for you.

---

### Post by gardara on 2007-01-07
```
sudo update-initramfs -k 2.6.17-10-generic
sudo update-initramfs -k 2.6.17-10-386
```

doesn't seem to work.

```
sudo update-initramfs -k 2.6.17-10-generic
You must specify at least one of -c, -u, or -d.

Usage: /usr/sbin/update-initramfs [OPTION]...

Options:
 -k [version]   Specify kernel version or all
 -c             Create a new initramfs
 -u             Update an existing initramfs
 -d             Remove an existing initramfs
 -t             Take over a custom initramfs with this one
 -b             Set alternate boot directory
 -v             Be verbose
 -h             This message

gardar@glappi:~$ sudo update-initramfs -k -u 2.6.17-10-generic
You must specify at least one of -c, -u, or -d.

Usage: /usr/sbin/update-initramfs [OPTION]...

```

---

### Post by gborzi on 2007-01-07
Have you tried the dpkg-reconfigure commands ? I'm sure these will work, I have used them. As for the update-initramfs, I wrote "I think" meaning I wasn't sure about them. Perhaps you can try the -u option, i.e. > sudo update-initramfs -k 2.6.17-10-generic -u
or the -c option.

---

### Post by gardara on 2007-01-07
> **gborzi said:**
> Have you tried the dpkg-reconfigure commands.

It seems to work after the dpkg-reconfigure commands. I haven't regenerated the initrds, do I need to do that? 

Hibernate seems to be working now. But I still get a message when trying to hibernate, but with different code in front.

17181217.132000 hda_intel azx_get_response timeout switching to single_cmd mode

Maby I don't need to worrie about this message?

---

### Post by gborzi on 2007-01-07
The initrds were regenerated by the dpkg-reconfigure commands. Perhaps I didn't stated it clearly, but the dpkg-reconfigure and the update-initramfs are two alternatives ways to do the same thing, i.e. regenerate the initrd files under /boot. Actually, dpkg-reconfigure uses the update-initramfs command with the right arguments. So you don't need to regenerate the initrds, you have already done it.
As for the error message, a google search shows some links related to kernel development, maybe to some sound related problems. After resuming, does your laptop works properly ? I mean, sound, network, video are all OK ?

---

### Post by gardara on 2007-01-07
> **gborzi said:**
> The initrds were regenerated by the dpkg-reconfigure commands. Perhaps I didn't stated it clearly, but the dpkg-reconfigure and the update-initramfs are two alternatives ways to do the same thing, i.e. regenerate the initrd files under /boot. Actually, dpkg-reconfigure uses the update-initramfs command with the right arguments. So you don't need to regenerate the initrds, you have already done it.

Ah, yes I see it now... I must have been too tired to notice that.


Everything seems to be working fine, video, audio, and wifi. I'll post here if I will notice something not working.

I am wondering if I can select the generic kernel as the default kernel in grub, so I don't have to manually select it every time I start my laptop.

---

### Post by gborzi on 2007-01-07
> **gardara said:**
> Ah, yes I see it now... I must have been too tired to notice that.


Everything seems to be working fine, video, audio, and wifi. I'll post here if I will notice something not working.
Nice to know it's working.

> **gardara said:**
> 
I am wondering if I can select the generic kernel as the default kernel in grub, so I don't have to manually select it every time I start my laptop.
Yes, you can make it the default kernel in two ways:
[LIST=1]
[*]open /boot/grub/menu.lst and change the > default         0
to > default         X where X is the entry for the generic kernel, i.e. that with the title equal to "Ubuntu, kernel 2.6.17-10-generic". On your system it should be 2.
[*]open /boot/grub/menu.lst and move the entry for the generic kernel to the first position.
[/LIST]
There is an interesting alternative, from the grub info file, that i copy and paste here: ```
Command: savedefault num
     Save the current menu entry or NUM if specified as a default
     entry. Here is an example:

          default saved
          timeout 10

          title GNU/Linux
          root (hd0,0)
          kernel /boot/vmlinuz root=/dev/sda1 vga=ext
          initrd /boot/initrd
          savedefault

          title FreeBSD
          root (hd0,a)
          kernel /boot/loader
          savedefault

With this configuration, GRUB will choose the entry booted
previously as the default entry.
```

---

### Post by gardara on 2007-01-07
> **gborzi said:**
> ```
Command: savedefault num
     Save the current menu entry or NUM if specified as a default
     entry. Here is an example:

          default saved
          timeout 10

          title GNU/Linux
          root (hd0,0)
          kernel /boot/vmlinuz root=/dev/sda1 vga=ext
          initrd /boot/initrd
          savedefault

          title FreeBSD
          root (hd0,a)
          kernel /boot/loader
          savedefault

With this configuration, GRUB will choose the entry booted
previously as the default entry.
```

This is a really nice way... But just to be sure, by this way I get some seconds to choose to boot up some other kernel/os... might be a noobish question but I don't want to screw anything up...
And also where should I paste this in my menu.lst?

here is my menu.lst

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=87a30623-c163-477c-a28d-5cc101a526e5 ro

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

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

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

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=87a30623-c163-477c-a28d-5cc101a526e5 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=87a30623-c163-477c-a28d-5cc101a526e5 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=87a30623-c163-477c-a28d-5cc101a526e5 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=87a30623-c163-477c-a28d-5cc101a526e5 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=87a30623-c163-477c-a28d-5cc101a526e5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=87a30623-c163-477c-a28d-5cc101a526e5 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

---

### Post by gborzi on 2007-01-08
You need only to change the "default 0" line to "default saved" and you are done. This change won't affect the ability to choose a different kernel at startup. It is controlled by the timeout line, which by default is set to 3 seconds.
Finally, as the americans would say, better noobish than sorry. Don't worry to appear a newby, everyone has been a newby and still is a newby in some specific area.

---

### Post by gardara on 2007-01-08
changed it from 0 to 2 and now it's working :)

However hibernate hasn't worked so good today ](*,) ... I tried to hibernate this morning and only the screensaver appeared.
And about an hour ago I tried to hibernate, the screen went blank and the only thing that showed was a blinking white dash. That was the only thing that showed for about 10 minutes so I gave up and did hold the power button down until it turned off.
Now when I put my laptop back on the sound isn't working :( and my wireless connection was disabled but I was able to turn it back on... The sound doesn't come back after 2 reboots and I tried  

```
sudo /etc/init.d/alsa-utils restart
``` 

but it didn't change anything.

Can you help me out?

---

### Post by gborzi on 2007-01-08
Have you modified the image_size file as I suggested at the start of this thread ? I have had similar problems that were fixed once I put the right value for image_size. Please note that every time you reboot your system the image_size value is reverted to the default value of 512MB. As for the sound, do you get any error message when restarting alsa-utils ? Or can you see any sound related error message in /var/log/messages ?

---

### Post by gardara on 2007-01-08
I didn't look at the image_size, I just looked at the swap and assumed that everything was the same as the swap hadn't gone to zero. I still have to try but I guess it will work now.
Is there a way to change the default to 1gb?

I don't see any error messages regarding the sound, the log shows nothing and alsa utils restart gives me OK.
I have tried opening amarok, totem, and mplayer. and I can't hear sound in any of them.

My girlfriend told me that she had booted windows, that was after I had tried to hibernate and held down the power button to turn the laptop off, I thought this might have something to do with the sound not working... failing to hibernate correctly and then boot another os (sound works in windows btw - but I don't want to use windows, I'm trying to get rid of it out of my life :p )

[quote=gaborzi]everyone has been a newby and still is a newby in some specific area[/quote]

You are exactly right, I have been working with computers for some years now (I know I'm young). And I'm pretty good with windows and have ran some redhat servers, been sharing information and helping people out on forums with windows and symbian os. Then I had got enough with windows so I decided to switch to ubuntu, there are many things here to learn and I'm quite exited about it. :)

---

### Post by gborzi on 2007-01-08
> **gardara said:**
> I didn't look at the image_size, I just looked at the swap and assumed that everything was the same as the swap hadn't gone to zero. I still have to try but I guess it will work now.
Is there a way to change the default to 1gb?
image_size is the amount of swap the system use at hibernation. Obviously it cannot be greater than the swap area itself. IIRC the 512MB default is "hard coded" in the kernel, so to have the correct value use a small trick, i.e. open the /etc/rc.local file and add a line like this > echo 1073741824 > /sys/power/image_size
where 1073741824 should be 1gb in bytes. The correct number will be shown by *free -b*.

> **gardara said:**
> 
I don't see any error messages regarding the sound, the log shows nothing and alsa utils restart gives me OK.
I have tried opening amarok, totem, and mplayer. and I can't hear sound in any of them.


Perhaps the failed hibernation set the volume to 0 or toggled some switch. Open the volume control (you can do this from the volume applet) and check the various channels.

> **gardara said:**
> 
You are exactly right, I have been working with computers for some years now (I know I'm young). And I'm pretty good with windows and have ran some redhat servers, been sharing information and helping people out on forums with windows and symbian os. Then I had got enough with windows so I decided to switch to ubuntu, there are many things here to learn and I'm quite exited about it. :)
I understand what you are saying. I too started with Windows... well to say the truth I started with DOS, then windows and in 1995 for the first time I installed a Slackware. At the time it was barely usable (at least to me) but nevertheless I continued to use it and learn, gradually changing my computer habits. In 1998 (or 99 ? I don't remember exactly) with a RedHat I completely stopped using windows. Even after all the years that have passed since '95, I still find Linux and the free software world exiting.

---

### Post by gardara on 2007-01-08
> **gborzi said:**
> 

Perhaps the failed hibernation set the volume to 0 or toggled some switch. Open the volume control (you can do this from the volume applet) and check the various channels.

PCM volume was muted... see I'm still learning :)


[quote=gborzi]I understand what you are saying. I too started with Windows... well to say the truth I started with DOS, then windows and in 1995 for the first time I installed a Slackware. At the time it was barely usable (at least to me) but nevertheless I continued to use it and learn, gradually changing my computer habits. In 1998 (or 99 ? I don't remember exactly) with a RedHat I completely stopped using windows. Even after all the years that have passed since '95, I still find Linux and the free software world exiting.[/QUOTE]

I looked at your website and see you've got quite a lot of knowledge... Hopefully I'll reach you some day... :)

btw, do you mind if I contact you sometime if no one else seems to be able to help me out with linux questions/issues?

---

### Post by gborzi on 2007-01-09
Sure, feel free to contact me by email or pm when you need help.

---

