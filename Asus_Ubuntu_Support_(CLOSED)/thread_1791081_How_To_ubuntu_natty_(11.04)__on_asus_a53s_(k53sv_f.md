---
title: "How To: ubuntu natty (11.04)  on asus a53s (k53sv family)"
date: 2011-06-26
forum: Asus Ubuntu Support (CLOSED)
---

### Post by cucisan on 2011-06-26
hiya,

i just got my asus 2 days ago and wanted to share my findings with you how to get nearly everthing working:

its an asus a53s which is nearly the same as a k53sv:
core i5, 4gb, 500gb wd scorpio blue, gt 540m 2gb vram, cardreader, **NO bluetooth**

just for the record:
it originally came with BIOS version 208, i updated it to 210 and then to version 300 (i thought it would fix fan issues, but it didn't)


**still not working:**

 * camera is upside-down (you can find solutions using google easily or here on the forums / NOT every asus laptop has this problem!)
 * **stability issue #2** (heavy lags resulting in **freeze**)
 * harddisk clicking with WD scorpio blue -> **[try post #33]("http://ubuntuforums.org/showpost.php?p=11018654&postcount=33")** and report back please :) -this **works for me!**

**what will work after doing these steps:**

* **stable** WLAN (ath9k driver in 2.6.38 natty is buggy)
* Touchpad (**2 Finger Scrolling/disable on typing**) (will actually get detected as touchpad, not as mouse on default natty install)
* Nvidia offloading through bumblebee **WITHOUT the fan going mad** (uploaded scripts to bumblebee to fix fan issues)
* fn keys like **volume up/down - play/pause/next/prev** (see post [#9]("http://ubuntuforums.org/showpost.php?p=10997488&postcount=9"))
* **stability issue #1** (related to **intel sandybridge** drivers - update to patched kernel to **fix GUI hangs**, **[try post #25]("http://ubuntuforums.org/showpost.php?p=11014764&postcount=25")** - works for me | **fixed in 2.6.38-11**)
* **cardreader** fix (follow _byrons_ [post]("http://ubuntuforums.org/showpost.php?p=11122123&postcount=103"))
* **BLUETOOTH** (follow _byrons_ [post]("http://ubuntuforums.org/showpost.php?p=11163434&postcount=110") again :))

**not confirmed by anyone expect me**
* hdd performance issues (repartition whole drive cause its a 4k advanced format hdd, aligning partition table will fix those small lags - if you don't have 'em, nevermind ;) [#5]("http://ubuntuforums.org/showpost.php?p=11018654&postcount=5"))


**WLAN:**
my hardware:
```
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```

symptoms:
slow wlan connection, copying files over LAN normally will work for 5-10 minutes then it will drop completely.. you had to disconnect and connect again to get it working for another 5-10 minutes

one of many bugreports to this problem:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/761176]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/761176")

speed before: 120-170kb/s max.

as 2.6.39 seems to bring new bugs, lets just update (dirty way) the ath9k driver (based on this guide [http://ubuntuforums.org/showthread.php?t=1481983]("http://ubuntuforums.org/showthread.php?t=1481983"))

```

wget http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.39/compat-wireless-2.6.39-1.tar.bz2
tar xfvj compat-wireless-2.6.39-1.tar.bz2
cd compat-wireless-2.6.39-1
./scripts/driver-select ath9k
make
sudo make install
sudo make unload
sudo modprobe ath9k

```

or just reboot insteat of the last 2 steps

after driver update: 2500-3000kb/s on g-wlan... same situation :)

**Touchpad:**

gets detected as mouse so no scrolling etc..

to get it detected and working (can be configured in the "mouse" preferences):

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/681904/comments/64]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/681904/comments/64")

after following these steps
reboot or unload old module and load new one:

```
sudo rmmod psmouse && sudo modprobe psmouse
```

**Nvidia offloading/disabling NVIDIA card** to get over 4hrs of battery life:

you will need git:
```
sudo aptitude install git
```

after its finished do these steps:
```

git clone http://github.com/MrMEEE/bumblebee.git
cd bumblebee/
sudo ./install.sh

```

**if you get asked which config you want to use, choose the one from "Thomas Krutz" - this will fix any fan issues**

be aware, this will add another xorg ppa to install a newer nvidia driver.
but it should work

reboot

you can now try if it worked:

```
optirun glxgears
``` to use the nvidia card
and
```
glxgears
``` to use intel card

any change to the GL libraries (like bumblebee PPA or xorg-edgers PPA will break intel DRI after installing/setting up bumblebee, so be aware! i think the bumblebee install.sh moves around some files)

hope this helps someone :)





[COLOR="Red"]obsolete as of 4.7.2011

i submitted my enable/disable scripts
when you get asked which config you want to use, just choose the one from "Thomas Krutz"
[/COLOR]


to disable the nvidia card you can use the following commands:

```
bumblebee-enablecard, bumblebee-disablecard, ...
```

if you get caught by the same bug as me that after installing bumbleebee and the fan starts spinning at full speed 
i did this to fix it

in /usr/src/acpi_call-1.0 i modified asus1215n.sh:

```

#!/bin/sh
# Power control for Asus 1215N Optimus
# by Pete Eberlein

if ! lsmod | grep -q acpi_call; then
    echo "Error: acpi_call module not loaded"
    exit
fi

acpi_call () {
    echo "$*" > /proc/acpi/call
    cat /proc/acpi/call
}


case "$1" in
off)
    echo _DSM $(acpi_call "\_SB.PCI0.PEGR.GFX0._DSM" \
	"{0xF8,0xD8,0x86,0xA4,0xDA,0x0B,0x1B,0x47," \
	 "0xA7,0x2B,0x60,0x42,0xA6,0xB5,0xBE,0xE0}" \
	 "0x100 0x1A {0x1,0x0,0x0,0x3}")
	# ok to turn off: Buffer {0x59 0x0 0x0 0x11}
	# is already off: Buffer {0x41 0x0 0x0 0x11}
    echo _PS3 $(acpi_call "\_SB.PCI0.PEGR.GFX0._PS3")
;;
on)
    echo _PS0 $(acpi_call "\_SB.PCI0.PEGR.GFX0._PS0")
;;
*)
    echo "Usage: $0 [on|off]"
esac


#echo P3MO $(acpi_call "\_SB.PCI0.PEGR.GFX0.P3MO")
echo DGPS $(acpi_call "\_SB.PCI0.PEGR.GFX0.DGPS")
PSC=$(acpi_call "\_SB.PCI0.PEGR.GFX0._PSC")
echo _PSC ${PSC}
case "$PSC" in
0x0)
    PSC="on"
;;
0x3)
    PSC="off"
;;
esac
echo "Asus 1215N Optimus appears to be ${PSC}"

```


now you have to edit bumblebee-enablecard and bumblebee-disablecard to use this file:
in enablecard: find the last lines
```

#echo _PS0 $(acpi_call "\_SB.PCI0.PEG1.GFX0.DON")
#echo _PS0 $(acpi_call "\_SB.PCI0.PEGR.GFX0.DON")
modprobe nvidia-current
``` and put a # before the echos

write this right after the commented echo lines in the enablecard script: ```
/full/path/to/asus1215n-modified.sh on
```
in the disablecard script do the same, put a # on the last line and add
```
/full/path/to/asus1215n-modified.sh off
```

et voila, turn the pc off to get rid of the full speed fan (reboot wont help) and then boot your ubuntu again.. everything should work now .. at least it does work for me.

---

### Post by Triton Yurin on 2011-06-26
Sorry, but i think that you aren't right about K53SV.
As for me, I can't get Bluetooth in that laptop working almost for two weeks.
I don't know what is inside A53SV, but mine K53SV has an Atheros AR5B195 combo card (hybrid of ar9285 wlan and ar3011 bt)installed there - wlan works fine, bluetooth - not:(. 
Everything except bluetooth is working out of the box. Thanks for the graphics switching manual.
Please tell me if bluetooth is working/not working for you in A53SV.
Thanks.

---

### Post by cucisan on 2011-06-26
hm i dont have bluetooth in my A53SV :)

on my notebook a label says: modell a53s / mainboard: k53sv

but thx for your post, ill update the topic

---

### Post by Twigman on 2011-06-28
FINALLY! Thankyou! I no longer get my fan running at full speed as soon as my nvidia card is powered off.

---

### Post by cucisan on 2011-06-29
another thing i noticed, that the system is considerable laggy when generating normal IO activity like starting firefox while watching a movie.

i read somewhere that ppl who changed the harddrive got rid of those lags (windows users on amazon)

i opened the notebook to see whats inside and found out its a relativly good harddrive: western digital scorpio blue 500gb model WD5000BPVT which means it uses 4K advanced format.

a quick peak on the partition table with
```
fdisk -l -u
```
showed me this :confused:

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    45062324    22531131   1c  Hidden W95 FAT32 (LBA)
Partition 1 does not start on physical sector boundary.
/dev/sda2   *    45062325   289251773   122094724+   7  HPFS/NTFS
Partition 2 does not start on physical sector boundary.
/dev/sda3       289253374   976771071   343758849    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       289253376   297439231     4092928   82  Linux swap / Solaris
/dev/sda6       297441280   976771071   339664896   83  Linux

```


sidenote: sda3 was the data drive (d:) on windows when i first turned it on

afaik partitions on a 4K harddrive have to start on sectors which are dividable by 8 (without remainders) - or otherwise it will be slower/more fragmented...

well, im now in the process to backup the contents of the recovery partition (sda1) and reformat the whole drive... i dont care for windows right now (as i use it only 2-3times a year or to flash a bios - which you should consider as there are 2 newer versions online than the one that was on the board - though i didnt notice any difference ;) but risking a brick is fun, isnt it?)

i will report back if it changes anything (IO lags are gone... that would be awesome! ;))

---

### Post by cucisan on 2011-06-29
well that worked out quite well.... not noticing any lags on normal IO usage... strike

---

### Post by qmater001 on 2011-06-30
Hello. did u also get the functions key working?
i found a patched kernele here, but the download link is not working
[http://ubuntuforums.org/showthread.php?t=1752900&highlight=asus-nb-wmi](http://ubuntuforums.org/showthread.php?t=1752900&highlight=asus-nb-wmi)

also, i have a minor issue with the touchpad. for some reason, it`s working at the login screen, and after login, it`s disabled. using sudo rmmod psmouse && sudo modprobe psmouse,  does the trick but i have to do it every time. I applied the patch, for detecting the touchpad, as you mentioned in the post, but i was getting a shaky, jittery cursor, so i upgraded to xserver-xorg-input-synaptics_1.4.0-1+b1_amd64.deb, and now is fine, but it`s getting disabled after login. any ideas? thx.

---

### Post by cucisan on 2011-06-30
hrm strange... not all function keys are working:

working:
brightness controls
calculator key
wlan on/off

not working:
volume up/down
media controls (play/pause/stop/next/prev)

others:
not tested because useless for me


what kinda touchpad do you have?
after elantech dkms module install, it gets detected as

```
[    18.846] (II) XINPUT: Adding extended input device "ETPS/2 Elantech ETF1059 Click-Pad" (type: TOUCHPAD)
```

in Xorg.0.log

and i must say it works quite well...

---

### Post by cucisan on 2011-06-30
```

git clone git://git.iksaif.net/acpi4asus-dkms.git
cd acpi4asus-dkms
make
sudo make install
sudo modprobe asus-nb-wmi

```

all keys are working :) strike

with natty default kernel...

*edit*:

as soon as a kernel update is coming, the files installed will be overwritten.
but being the dkms branch is quite easy to make it "stick"

```

sudo aptitude install debhelper
cd acpi4asus-dkms
dpkg-buildpackage
sudo dpkg -i [newlycreated-package].deb

```

---

### Post by cucisan on 2011-06-30
another thing:

intel sandy bridge support in natty is well.. quite bad

symptoms: lockups/garbled screen (errors in dmesg)

you can try if this fix helps you for now:

in /etc/rc.local add this line before "exit 0"
```

echo 1 > /sys/module/i915/parameters/semaphores

```

when i have time i will try to find a way to update mesa/kernel to get better sandybridge support ... without breaking bumblebee (which i currently ran into)

also performance of some steam games through wine 1.3 (wine ppa) is bad like css (which was twice as fast on much older laptop with nvidia card)

---

### Post by qmater001 on 2011-06-30
great. the most important functions are working. thank u very much. the one that are not working are the mouse disable fn +f9, insert and scrl lock, but, those i never use. 99% funcitonability. i`ve noticed some weird freezings, like starting ffox, and libreoffice, skype and banshee at the same time. do u think is related to the processor or hdd? i still have the factory default windows partitions.
thanx again and good luck

---

### Post by cucisan on 2011-06-30
well, when i did something IO-wise (copy, tar/zip or starting a big program like libreoffice) and like started to type in firefox (so it would search my bookmarks/history) firefox got stuck for 2seconds until the other programm or whatever was loaded... after repartitioning my drive, i never experienced this ever again...

you could look at your partition table and see if is like mine was (see some posts before)

---

### Post by qmater001 on 2011-07-02
well, for me it`s a bit worse. sometimes the system is almost frozen,  having only the mouse moving, but without any response frome any  aplication. and sometimes it just hangs, frozen, so i have to restart  manually. also when searching in the unity dashboard, it used to hang  for 2-3 seconds, after every letter i typed, but, after the upgrade to  kernel 2.6.39 it`s working ok. still i have the hanging, and freezing of  the whole system problem.

---

### Post by qmater001 on 2011-07-02
bad bad bad. it keeps freezing for no reason. today twice. total hang. any ideas?

---

### Post by F3R on 2011-07-02
Thanks a lot for this Thread Cucisan, everything was working for me as a charm!!!! i have a Asus a53s (k53sj) as well.

I have the same problem than qmater001 my laptop sometimes freezes suddenly, but i don't feel any lag on running several apps. (my partitions table looks exactly than yours)
but due to my work i will not format th Hd for the moment.)

By the way i am facing issues with the webcam which works upside-down :S
and my SDcard reader doesn't detect any memory when it's inserted. Do you know guys somthing about?

It's funny I was not aware that my wifi card was working under its possibilities, i was thinking was the shitty bandwidth i have) but after installing that wifi driver my speed was the double...greattt!!!!

I face the same problem with the CPU fan running at full speed and i solved as you mentioned! greatttt!!!

Thanks!!!

---

### Post by qmater001 on 2011-07-02
...so it seems i face 2 issues. first total freeze, brain dead; 
and second, where actually i think only the keyboard is affected, because i can still listen to music (if playing), i can even use the function media keys to play pause stop, or skip to next track. i can also alt + ctrl+ backspace but other then this, keyboard is unresponsive. touchpad is still working, but i can`t click on anything...

so... any suggestions?

---

### Post by qmater001 on 2011-07-02
@F3R skype video fix
open the terminal an type in:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

hope it works.

---

### Post by cucisan on 2011-07-03
hi guys,

F3R: i'm glad i could help you with my little howto ;)

webcam upside-down is a common issue on many laptops... but using the LD_PRELOAD method is not working for us... has something todo with the libv4l... as far as i know that we have to report our hw to the libv4l-tools maintainer and he will update it (and for now we would have to patch it) - i did not so much research on this one, as i'm planning to just exchange my cam.. cause 0.3MP is really bad for a new laptop :) (but you can find information on this pretty easy through google)

the cardreader is currently not supported (its a realtek cardreader connectected via usb)... i guess we could try to patch some kernel modules here and see if that works... but for now no cure here.

touchpad: it works quite good... sometimes it becomes completely slow or jittery when scrolling... for now: just release your fingers.. and then scroll again.. this works for me (but im not a touchpad poweruser as i use a mouse 90% of the time ;))

to the freezes:

there are 2 completely different ones - i think:
1, complete lockup -> only powercycle works
2, X screen does not refresh but sound etc continues to work...

ad 1: currently i have no clue.. it only happens very seldom for me... i use standby a lot.. and maybe after a uptime of 16-20hrs its likely to happen.. have to investigate further..

there are many possibilities, we have to narrow down the issue:
i have read somewhere (dont remember the link) that ath9k driver could possibly freeze the complete system... maybe someone of you can test this for like 2-3 days with only using ethernet and rmmod ath9k to see if thats the cause? :)
i don't have this possibilty :(

ad 2: i think this is caused by the crappy intel sandybridge driver or a combination of xorg-driver and mesa7.0...

when this happens, you can - without problem - switch to the console and login from there (strg+alt+f1) and you will see in dmesg something like:

[i915] IRQ hangcheck error / semaphore blabla

i think the echo 1 > /sys/module/i915/parameters/semaphores helps here, but does not fix it -> the screen hangs for like... 1 minute and then it will "refresh" and will continue to work.

changing anything related to mesa/xorg will break intel DRI with bumblebee installed... i guess it has something todo with the install.sh.. which moves around some files... this is my no.1 priority for now as i think it may fix both freezing issues...

but i currently have my exams and not much time for playing around...

if you find new informations on these things or did work out a cure, just post it here.. please :)

---

### Post by 4Foot on 2011-07-03
> **Triton Yurin said:**
> Sorry, but i think that you aren't right about K53SV.
As for me, I can't get Bluetooth in that laptop working almost for two weeks.
I don't know what is inside A53SV, but mine K53SV has an Atheros AR5B195 combo card (hybrid of ar9285 wlan and ar3011 bt)installed there - wlan works fine, bluetooth - not:(. 
Everything except bluetooth is working out of the box. Thanks for the graphics switching manual.
Please tell me if bluetooth is working/not working for you in A53SV.
Thanks.

Triton:

I have just purchased a K53S and it did not come with Bluetooth installed. I had to buy a dongle, which works perfectly.It seemed odd to me to not have Bluetooth but I checked it out and it was not spec on my box anyway.

I hope this helps you sleep.
Cheers
4Foot

---

### Post by cucisan on 2011-07-04
freezes:

im currently trying out this [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/761065/comments/38]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/761065/comments/38") kernel... it has an upstream patch from kernel 3.0 which seems to make things better reported in the bugreport...

well lets wait and bleed :) (ill report back)

---

### Post by Ench on 2011-07-04
Hey cucisan,

Thanks for this thread, it helped me a lot. I have Asus K53SV and I was getting very annoyed by all the things that were not working (explained in this thread) that I was considering going to windows just to relax a little.

I still didn't apply the bumblebee because first I want to try it on a new installation to see how it will act on my machine. Also, the HDD needs to be reformatted so that the sectors are correctly aligned etc. But all at it's time :)

I was getting the freeze/stuck screen a lot lately, that was my main concern and major drive force for windows. I applied what was explained earlier for the /etc/rc.local file and so far after 24 hours and it works ok.

Thank you and all who are contributing in this thread!

ench

---

### Post by cucisan on 2011-07-05
first of all, the kernel with intel upstream patch from 3.0 seems to work fine.. i also get better speed from the intel card. no freezes for hours while on AC power.

but there is a new problem i noticed with the hardware for me:

when running on battery, the system soon (but not always) will start to lag like hell: typing something gets stuck every now and then, watching a movie from harddisk gets stuck etc... i can hear the harddrive clicking which actually means it tries to park its head but somehow is confused :( and after some time of heavy lag, the system froze instantly... so maybe this is another cause/only cause of the freezing problem I am currently having..

little bit of explanation and workaround found [here]("http://http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking#Possible_solutions_.28Linux.29")

also the WD FAQ mentions disabling power management for some harddrives in certain conditions to let it work "normally"... oh oh... sounds like a complete f*ckup to me.

i came across some reports of clicking/apm issues with this type of hard drive (WD5000BPVT) (mostly windows7).

find out harddrive type without opening the laptop:
```
sudo hdparm -I /dev/sda | grep Model
```

these are just thoughts based on recent observations.. so as long as nobody can confirm it don't take them to serious :) i invite you to observe for yourself and maybe we will find a cure ;)

---

### Post by qmater001 on 2011-07-05
nice.... looking forward to it.

---

### Post by qmater001 on 2011-07-05
Mine is WDC WD6400BPVT-80HXZT1. 
did you try disabling "Spin down harddisk when possible" from power management?
since i`m still begginer with linux, could you please provide the commands for upgrading to "the kernel with intel upstream patch from 3." thx

---

### Post by cucisan on 2011-07-05
just download the files from [http://kernel.ubuntu.com/~sarvatt/lp761065/natty/]("http://kernel.ubuntu.com/~sarvatt/lp761065/natty/").

use the amd64 files on an 64bit install and the i386 files on 32bit install

e.g. 64bit you need these files:
	linux-headers-2.6.38-10-generic_2.6.38-10.44+lp761065_amd64.deb
	linux-headers-2.6.38-10_2.6.38-10.44+lp761065_all.deb
	linux-image-2.6.38-10-generic_2.6.38-10.44+lp761065_amd64.deb

and then install them by double clicking via GUI or open a terminal, change to the directory where the files are and type ```
sudo dpkg -i linux*.deb
```

it should rebuild all dkms modules... so the only thing you need to do after reboot is doing the ath9k wlan module thingie again (first post)

as for the harddisk stuff.. didn't have time but will try it soon, you could do these tests too and observe.. :)



P.S. when using the patched kernel, there should be no need for "echo 1 > /sys/module/i915/parameters/semaphores" any longer.

so you can just comment that one out in /etc/rc.local

with natty kernel and semaphore=1 i get ~400fps with ```
optirun glxgears
```, with kernel from the link above and semaphore=0 i get ~800fps and no gfx issues any longer (at least no errors in dmesg ;)).

but to get the best out of the sandybridge intel card we would need mesa7.11 (natty uses 7.10)... but thats a different and not so easy story ;)

---

### Post by qmater001 on 2011-07-05
thx, i`ll try it out.
do u get your coursor jittery if you keep one finger on the touchpad?
if so, i may have a fix for that. at least it worked for me:
[http://pkgs.org/download/debian-wheezy/debian-main-amd64/xserver-xorg-input-synaptics_1.4.0-1+b1_amd64.deb.html](http://pkgs.org/download/debian-wheezy/debian-main-amd64/xserver-xorg-input-synaptics_1.4.0-1+b1_amd64.deb.html)
download and install
but i may say that afterwards i face the touchpad disabling after login, and then i have to go to terminal and
sudo rmmod psmouse && sudo modprobe psmouse

---

### Post by qmater001 on 2011-07-05
by the way, isn`t there a patched 2.6.39 ? i noticed some improvements with 2.6.39 compared with 2.6.38.

---

### Post by qmater001 on 2011-07-05
well, i did the update... and as a test i did opened firefox, chrome, pidgin, skype, libreoffice at the sime time, and it`s getting laggy, not frozen, but really not going anywhere, hanging and lagging. i still have the original windows on the hdd, but i dont think that`s the issue.
also, any ideea how do i set grup to load default 2.6.38.10 insted of 2.6.39 ?

---

### Post by cucisan on 2011-07-06
todays update should also bring some more stability... although since using the patched kernel i have not a single issue with gfx..

```

xserver-xorg-video-intel (2:2.14.0-4ubuntu7.1) natty-proposed; urgency=low

  * Add 119_disable_relaxed_fencing.patch: The relaxed fencing
    optimization is suspected as the cause for various i915/945 gpu lockup
    issues.  This disables the optimization by default but adds an
    xorg.conf parameter to let people experiment with it turned on.
    (LP: #727594, #761143, #761632, #755693)

```


enforcing hdparm -B 254 /dev/sda on battery seems to help.. not a single lockup yesterday... from 9a.m to 24p.m (also no clicking..)

but this produces more heat on the harddrive and also shortens battery life as the harddrive will not go to sleep too often.. 

qmater: the issue for the small but constant lags is not windows or the windows partition itself, but the partition table which is not aligned to the physical sector boundries of the harddrive! (google: 4k advanced format - this can and will impact performance)
also starting many applications at once will be slow on a notebook harddrive or any harddrive (hello SSD ;)), but starting to copy something while trying to use firefox (search a huge history on my machine) will get firefox completely stuck for 2-5seconds, which is NOT normal... even on a single core atom netbook (which is so much slower) this never happend to me.

proof: since i repartitioned my whole harddrive.. those constant lags are completely gone! firefox never ever got stuck again, i tested that one very well and this issue is fixed for me - if you believe me or not :). the only lags that remained for me was when running on battery (with harddrive clicking, which is due a shitty harddisk firmware -> WD_IntelliPark, wdidle3.exe not working on this harddrive to change the parameters of this) and after some time of heavy lag the system freezed. (when those heavy lags occur.. there is no way out.. the clicking wont stop no matter what you do with hdparm) my guess that those 2 things are related.

yesterday the notebook did not freeze or lag in any way, using the hdparm cmd(see above) when on battery...

will test more the next days.. if the problems are gone for me, i will exchange my harddrive as i want maximum battery performance :)

---

### Post by qmater001 on 2011-07-06
thx for the reply cucisan, but. i dont get any constant lags. On 10.10, i used to boot, and once i was logged in, i just clicked on my "usual apps" (firefox, skype, pidgin, chrome, and libre office), well if i do the same on 11.04, thinks are getting stuck/laggy, to the point where there`s nothing but lag lag lag and the apps will not load (or crash), for minutes, and then i have to restart. if i just open the appes one by one, giving them some time to load until i start the other, then everything works smooth.
i have another hdd so i`ll try to use that one to see if it makes any difference. 
and in regars to grub? any ideea how can i set 2.6.38.10 as default to be loaded instead of 2.6.39 ?

---

### Post by cucisan on 2011-07-06
hm why didnt you mention earlier that it worked without lags/crash on 10.10 ..? :) guess i would have searched for changes between those two versions which could lead to IO lag im experiencing... also, when it does crash or lag heavily, do you hear the harddrive clicking? what does hdparm -B /dev/sda say when on AC power/battery power? does it always crash or just when on battery power? how long do you need to produce a crash? 4hrs uptime? 10hrs uptime? more?

for me there is no crash or lag since yesterday 9a.m. but im trying hard to get it crashed as im not 100% about the harddrive issues... but comments on amazon etc make me feel right about the harddrive... someone changed his harddrive without doing any tweaks to the original HDD, and he says everything is fast and snappy after doing so using win7...

do you have lags or performance problems under win7? some ppl complain/confirm about lags on windows7 on amazon (german site)...

as i mentioned earlier.. i dont have a single lag on AC (always) and on battery power (since i issued the hdparm -B 254 cmd)... but it can also be just a coincidence


the only problem i currently have is: sometimes after standby, i have a garbled screen... but no problem: i switch to console (strg+alt+f1) and then back to X... and the garbled screen is gone :)


as for grub: you will find it easily with google, i don't know it by heart

---

### Post by qmater001 on 2011-07-06
wait... i was talking about 10.10, but i didn`t mentioned that it was on my previous notebook. :D so i didnt tried 10.10 on a53s yet. but i think i`ll give it a shot, tough i kind of got used with 11.04. everything was working fine for me too, no freezings all night long, and today also. but after an update (also running on battery) it froze 2 times... so i`m not sure yet if it was just beacause of the battery or update...

---

### Post by cucisan on 2011-07-06
ah ok... :/

does it always crash when on battery? or after you used the battery and returned to AC?
the harddrive clicking only occurs on battery power (it may get triggered because of the powermanagement).. but NOT always..
when it starts clicking.. it wont stop, no matter what you do with hdparm parameters.. until it freezes...

well, if it happens so often on battery for you, just try this and see if you can make the battery empty without crashing (its just temporary, so no worries!):

1, pull the AC cable
2, powermangement will kick in and set the APM level to 128 (default value, also lowest value possible; you can check that in terminal with "sudo hdparm -B /dev/sda")
3, open a terminal and type the following:
   ```
sudo hdparm -B 254 /dev/sda
```

(or 255 to disable APM for the harddrive completely!)

4, use your laptop normally and see if its crashing (i guess it wont)
5, REPORT BACK :P

---

### Post by qmater001 on 2011-07-06
OK. i`ll try that.
btw, how`s glxgears for you?

mine with optirun64, the first time after i updated to the patched kernel (2.6.38.10) gave me 800fps. (and ofcourse i was amazed); then i ran it a second time, and 350-400fps. and every time now the same (350-400). ?

---

### Post by cucisan on 2011-07-06
for me its not constantly at the same speed...

but remember, glxgears is not a good benchmark.. only on the same system you could try to use it as a benchmark..

i play many 3d games via steam (using wine) and they all work quite well.

remember: the intel card is used to display those graphics so if the framerate is low, that may be also be the cause...

```

optirun glxgears
 * Starting Bumblebee X server bumblebee
_PS0 Enabling nVidia Card Succeded.
DGPS Enabling nVidia Card Succeded.
 *       [ OK ] 
4144 frames in 5.0 seconds = 828.725 FPS
2962 frames in 5.0 seconds = 592.322 FPS
3043 frames in 5.0 seconds = 608.477 FPS
3148 frames in 5.0 seconds = 629.556 FPS
2295 frames in 5.0 seconds = 459.000 FPS
 * Stopping Bumblebee X server bumblebee                                                   * .
_DSM Disabling nVidia Card Succeded.
_PS3 Disabling nVidia Card Succeded.
DGPS Disabling nVidia Card Succeded.
   [ OK ]

```


sidenote:
on my old laptop with a geforce 9600 i get 8000 fps from glxgears, but the games i play via steam didnt work that good as they work now...

---

### Post by qmater001 on 2011-07-06
it`s ok the same for me.. i hade it install offline, and probably went wrong. now it` seems to be fine, i get the same results as you. still i`m wondering, why is oscilating so much? from 400 -800 ?

---

### Post by qmater001 on 2011-07-06
i`ll tell you what. i`ll put a different hdd (i have another 500gb), and see if it`s the hdd or not.
the only thing that i got (in the past 3 hours of use) is the laggy freezing (laggs untils is frozen). how` yours working?

---

### Post by cucisan on 2011-07-06
no problems so far, over 30hrs uptime on AC and many times on battery (using hdparm for apm adjustment). no freeze no lag.

it seems there are many WD caviar blue 2.5" with apm issues.. just googled a bit lately :) but on win7 there are no freezes :)

---

### Post by cucisan on 2011-07-07
hm, another day and no freeze on battery :)

i wonder if someone who has freezes und reads this thread will acutally confirm this ;)

---

### Post by qmater001 on 2011-07-07
well i changed the hdd and with a seagate momentus (the one the i had on my previous notebook). and i ran glxgears in a loop for 5 hours. se everything seems OK. one thing though, The search function in Unity Dashboard is very laggy, and it wasnt on my previous instalation. any ideas?

---

### Post by cucisan on 2011-07-07
so no more freezing/lagging with the new harddrive? (tested on battery?)

unity: no idea, its beta so i don't expect much from it ;)

---

### Post by qmater001 on 2011-07-07
yes. i`m on battery now, and no problems. 
i also found the issues with unity. it was the dock. after installing ccsm, i disabled autohide, and now the search works fine.
by the way, ur camera is not working properly? mine is just fine.

---

### Post by cucisan on 2011-07-07
i'm glad we finally found the freezing issue, solutions: change harddrive or just tweak powermanagment of the harddrive (if its wd scorpio blue)

my cam works too, but its upside down like many "sonix" webcams are, what did you change to make it work correctly with skype etc? i tried the LD_PRELOAD method but it didn't work

---

### Post by cucisan on 2011-07-07
another sidenote on the used harddrive:

this WD_IntelliPark feature, which tries to park the head every 6-8seconds results in a high "Load_Cycle_Count", a normal laptop harddrive is built for 300.000-600.000 of such "load cycles" aka. "head parks".

my asus has a wd scorpio blue from 2011 (printed on a label on the harddrive). i've been using it for **over a week now** and

```

sudo smartctl -A /dev/sda | grep "193 Load_"
193 Load_Cycle_Count        0x0032   198   198   000    Old_age   Always       -       8006

```

its **at 8006 load cycles**.

(changing the APM settings see posts above, did only increase this number by ~20 load cycles in the last 2 days, which i guess is normal :))


looking on **another** wd scorpio blue i have **from 2009**:

```

sudo smartctl -A /dev/sdb | grep "193 Load_"
193 Load_Cycle_Count        0x0032   195   195   000    Old_age   Always       -       15509

```

is **at 15509** load cycles, and i used that for over 1 year, often over 10 hours a day.



you can do the math yourself i believe. also load cycle counts are not the only reasons for harddrive failures, BUT they are 1 possible reason when reaching a certain amount. (see your harddrive manufactorers specs/warranties or google for SMART values)

you can also do some googling around, you will find many discussions etc on this issue and also specific to the WD IntelliPark.

i'm glad this freezing issue turned up, so i know i wont use the harddrive any longer as my main harddisk in my asus.

JUST FOR YOUR INFO ;)

/sidenote

besides that, everything is NOW (except cardreader) working perfectly on my asus :)

---

### Post by qmater001 on 2011-07-08
well my cam just worked out of the box, maybe it`s a different one?
card reader i haven`t tested.

thank you for all the help.

---

### Post by qmater001 on 2011-07-08
well... i guess i was too soon happy. the problem is still here.. lagging till freezing. this problem becomes very obvious especially when i start a lot of programs one after another in a very short time.. i tried even sudo "hdparm -B 255 /dev/sda", on battery, also with the plug on. it`s persistent in both cases... so back to square one :)

the difference from yesterday, when everything seemed fine, is that i downloaded a lot of apps with ubuntu tweak. maybe it`s a memory leak??

---

### Post by cucisan on 2011-07-08
> **qmater001 said:**
> well... i guess i was too soon happy. the problem is still here.. lagging till freezing. this problem becomes very obvious especially when i start a lot of programs one after another in a very short time.. i tried even sudo "hdparm -B 255 /dev/sda", on battery, also with the plug on. it`s persistent in both cases... so back to square one :)

aaaaaaaaaaaaaaaaaaaaaaargl... ok thats where i don't get it. the hdparm "workaround" works for me 100000%, my asus runs completely stable without any issues at all. running for days now... also with short periods of standby each day.


i don't know if it does change anything, but the only thing i did was updating my bios. in the first place, i thought it would cure the fan issue i was having (see changelog on asus website). my notebook came with version 208, i updated it to version 300 (there is also version 210 available). but if you are unsure how to update a bios, **DONT** do it, cause it can brick your laptop completely :)

i did that update on the same day i got it.. but i didnt notice any difference from it (also ditched windows on the second day, so never used that one expect for "winflash" ;))

> 
the difference from yesterday, when everything seemed fine, is that i downloaded a lot of apps with ubuntu tweak. maybe it`s a memory leak??

i also use ubuntu tweak and havent had a single issue. also RAM is there to be used (be it a memleak or not ;)).. i wouldnt worry about that.


sorry that it doesnt work for you. mine is just like i wished it was in the first place running natty :)

maybe some of the other posted their "thanks" here can tell us more if they have issues and how they fixed it. -> YES, YOU! :)

---

### Post by cucisan on 2011-07-08
ARGH, another issue turned up, as i mentioned in my first post, updating nvidia driver AFTER installing bumblebee will break INTEL DRI -> no unity.

today the x-swat ppa (added by bumblebee) updated its nvidia driver... so far no problem

uninstall then install again will fix that. (or see bumblebee issue [#414]("https://github.com/MrMEEE/bumblebee/issues/414"))

but using kernel 2.6.38-10 which seems to fix any gui hangs with intel sandybridge, completely breaks graphic output for intel when updating driver to nvidia 275.xxx.xxx

no problem with original natty kernel (2.6.38-8 )

can anyone confirm this?

*EDIT*
ok another reboot fixed this... maybe spoke too soon :)


(what a troublesome piece of hardware... grrrrrrrrrrrr)

---

### Post by cucisan on 2011-07-08
qmater001: its just a hunch, but... could you just try to disable wireless for 2-3 days and see if its freezing again? (i know it suxx on a laptop ;))

it did just freeze after ~3days. the only difference was today i was using wlan instead of lan. and i used it a lot (X11 ssh tunneling etc...), first symptoms after ~2hrs was extrem lagging over ssh, then suddenly freeze of complete system :(

i will try to reproduce this... my nerves are already on edge...

---

### Post by cucisan on 2011-07-08
or you could try rmmod'ing the ath9k module if the lagging starts and see if it stops.. maybe more convenient :)

---

### Post by qmater001 on 2011-07-08
try to run a memtest from grub menu. mine is "frozen" meaning that after i hit enter in grub menu of memtest86, it loads the blue&white screen, and nothing happens, any key wont work, i have to power off from the power button. i still think it might me related to the memory, give it a try see if it works or not.

---

### Post by silentbang on 2011-07-09
Anyone experienced the laggy keyboard? I usually get trouble with it. For example, when browsing Opera, the keys doesn't react my pressing, I have to click on the Search textbox and then can press key normally. This also happens with Netbeans. I keep typing and nothing appear. Don't know this is the popular problem of Ubuntu or only for these series of Asus laptop (SAndybridge). My laptop is K53SV.
Another question, I'm using Bumblebee, but still don't know how to enable desktop effects. It seems that my onboard graphic card isn't recognized ?

---

### Post by cucisan on 2011-07-09
qmater: memtest v4.1 seems to have troubles with intel sandybrdige, see [http://forum.canardpc.com/threads/53258-Memtest86-V4.20-Released-!]("http://forum.canardpc.com/threads/53258-Memtest86-V4.20-Released-!")

silentbang: for qmater and me, there is also heavy lagging but not that easy reproducable for the moment...
i guessed it was the harddisk, which has some issues but is not the only reason. yesterday i discovered it seems to be related to wlan drivers...

i start copying things over wlan with full speed for some hours and i feel it starts lagging.. do you also experience that?


can anyone of you - when lagging starts and doesnt go away - do:
```
sudo rmmod ath9k
``` to see if it stops?

there have been issues with ath9k in the past.. i just want to rule that out.
i guess everyone must/will use wlan on his laptop.. but a few days ago i was NOT using wlan cause there was none available to me and i didnt experience any lags or stability issues for exact THESE 3 days on LAN... i just want to try everything now ;)

i don't have the possibility to use a LAN connection for the next days :(

---

### Post by cucisan on 2011-07-09
@silentbang: did it work before installing bumblebee ? have you updated nvidia driver recently? if nvidia driver gets updated AFTER installing bumblebee, unity will stop to work (know problem -> see post [#48]("http://ubuntuforums.org/showpost.php?p=11026156&postcount=48")

---

### Post by AureiAnimus on 2011-07-09
cucisan, thank you very much! I managed to get fn keys, bumblebee and touchpad features working properly. I have an Asus K53SV (K53SV-SX146V). Bumblebee recently added an ppa ( [https://launchpad.net/~mj-casalogic/+archive/bumblebee/](https://launchpad.net/~mj-casalogic/+archive/bumblebee/) ), which worked perfectly for me. I am not experiencing wlan/instability issues, so i think i'm pretty much all set :D Again, thank you very much!

---

### Post by silentbang on 2011-07-09
> **cucisan said:**
> @silentbang: did it work before installing bumblebee ? have you updated nvidia driver recently? if nvidia driver gets updated AFTER installing bumblebee, unity will stop to work (know problem -> see post [#48]("http://ubuntuforums.org/showpost.php?p=11026156&postcount=48")

I experienced unable to use unity since the very first time installing Ubuntu. Everytime trying to click on Extra or NOrmal effect, it searched for Additional Driver and ended up "Desktop effects could not be enabled ". After installing Bumblebee, nvidia_current "is activated but not currently in used", which is normal as other's situation.

---

### Post by cucisan on 2011-07-09
everyone with WLAN issues of any kind PLEASE post your hardware, as there seem to be different wlan adapters (bluetooth, no bluetooth etc)

```

~$ lspci | grep Network
**03:00.0** Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

~$ lspci -s **03:00.0** -vvnn
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: AzureWave Device [1a3b:1089]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at de200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k


```

change the **bold** letters in case its different for you.


sidenote: im currently using my umts stick, and no lags at all.... but i will not speak too soon.. need more time to observe...

---

### Post by cucisan on 2011-07-09
> **silentbang said:**
> I experienced unable to use unity since the very first time installing Ubuntu. Everytime trying to click on Extra or NOrmal effect, it searched for Additional Driver and ended up "Desktop effects could not be enabled ". After installing Bumblebee, nvidia_current "is activated but not currently in used", which is normal as other's situation.

thats strange... it worked for me without bumblebee..

please post your hardware.

what does ```
glxgears
``` do? (type in terminal)

if it moans about DRI/GLX missing uninstall bumblebee and try again

also do not use the gui to enable desktop effects - it will try to install nvidia driver...

just open a terminal and type:

```
compiz --replace &
```

this will start unity, there may be more error output to see there

---

### Post by cucisan on 2011-07-09
> **AureiAnimus said:**
> cucisan, thank you very much! I managed to get fn keys, bumblebee and touchpad features working properly. I have an Asus K53SV (K53SV-SX146V). Bumblebee recently added an ppa ( [https://launchpad.net/~mj-casalogic/+archive/bumblebee/](https://launchpad.net/~mj-casalogic/+archive/bumblebee/) ), which worked perfectly for me. I am not experiencing wlan/instability issues, so i think i'm pretty much all set :D Again, thank you very much!

im glad at least some ppl have no stability issues :)

the last time i checked on the bumblebee ppa there was no bumblebee package there (so no way to install without the scripts from git)

guess i will switch soon and update the my post accordingly as soon as those stability issues are gone.

care to share you wireless hardware? see commands above...

---

### Post by silentbang on 2011-07-09
Srr. I didn't mean Unity. As I'm using Ubuntu 10.10. I meant desktop effects.
Here is my hardware info: 
$lspci

```
00:00.0 Host bridge: Intel Corporation Sandy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
00:1c.5 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Cougar Point LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation Cougar Point 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation Cougar Point 2 port SATA IDE Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev ff)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
```

$lspci | grep Network
```
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```

$lspci -s 03:00.0 -vvnn
```
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Device [1a3b:2c37]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at de200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k
```


$glxgears
```
Mesa: Initializing x86-64 optimizations
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
3 frames in 6.8 seconds =  0.441 FPS
301 frames in 5.0 seconds = 60.069 FPS
301 frames in 5.0 seconds = 60.011 FPS
300 frames in 5.0 seconds = 59.991 FPS
301 frames in 5.0 seconds = 60.003 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.002 FPS
300 frames in 5.0 seconds = 59.999 FPS
301 frames in 5.0 seconds = 60.003 FPS
301 frames in 5.0 seconds = 60.002 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.002 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.003 FPS
301 frames in 5.0 seconds = 60.002 FPS
300 frames in 5.0 seconds = 59.999 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.003 FPS
300 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.002 FPS
301 frames in 5.0 seconds = 60.003 FPS
300 frames in 5.0 seconds = 60.000 FPS
300 frames in 5.0 seconds = 59.996 FPS
301 frames in 5.0 seconds = 60.007 FPS
301 frames in 5.0 seconds = 59.991 FPS
301 frames in 5.0 seconds = 60.010 FPS
301 frames in 5.0 seconds = 60.005 FPS
300 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.003 FPS
301 frames in 5.0 seconds = 59.997 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.002 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.002 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.004 FPS
300 frames in 5.0 seconds = 59.999 FPS
300 frames in 5.0 seconds = 59.990 FPS
301 frames in 5.0 seconds = 60.012 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.003 FPS
300 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.005 FPS
301 frames in 5.0 seconds = 60.001 FPS
300 frames in 5.0 seconds = 59.997 FPS
301 frames in 5.0 seconds = 60.005 FPS
300 frames in 5.0 seconds = 59.998 FPS
301 frames in 5.0 seconds = 60.003 FPS
300 frames in 5.0 seconds = 59.998 FPS
300 frames in 5.0 seconds = 59.805 FPS
300 frames in 5.0 seconds = 59.999 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.005 FPS
300 frames in 5.0 seconds = 59.995 FPS
301 frames in 5.0 seconds = 60.005 FPS
300 frames in 5.0 seconds = 59.998 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 59.997 FPS
301 frames in 5.0 seconds = 60.010 FPS
301 frames in 5.0 seconds = 59.997 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.002 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.005 FPS
300 frames in 5.0 seconds = 59.997 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.002 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.003 FPS
300 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.004 FPS
300 frames in 5.0 seconds = 59.998 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.006 FPS
300 frames in 5.0 seconds = 59.996 FPS
300 frames in 5.0 seconds = 59.999 FPS
301 frames in 5.0 seconds = 60.003 FPS
301 frames in 5.0 seconds = 60.003 FPS
300 frames in 5.0 seconds = 59.999 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.003 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.002 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.002 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.003 FPS
301 frames in 5.0 seconds = 60.001 FPS
300 frames in 5.0 seconds = 59.998 FPS
301 frames in 5.0 seconds = 60.003 FPS
301 frames in 5.0 seconds = 59.999 FPS
301 frames in 5.0 seconds = 60.002 FPS
301 frames in 5.0 seconds = 60.002 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.005 FPS
300 frames in 5.0 seconds = 59.995 FPS
301 frames in 5.0 seconds = 60.006 FPS
301 frames in 5.0 seconds = 60.003 FPS
300 frames in 5.0 seconds = 59.997 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.009 FPS
300 frames in 5.0 seconds = 59.992 FPS
301 frames in 5.0 seconds = 60.003 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.003 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 59.998 FPS
301 frames in 5.0 seconds = 60.007 FPS
300 frames in 5.0 seconds = 59.998 FPS
301 frames in 5.0 seconds = 60.002 FPS
301 frames in 5.0 seconds = 60.003 FPS
301 frames in 5.0 seconds = 59.999 FPS
301 frames in 5.0 seconds = 60.005 FPS
300 frames in 5.0 seconds = 59.996 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.002 FPS
301 frames in 5.0 seconds = 60.005 FPS
301 frames in 5.0 seconds = 59.997 FPS
301 frames in 5.0 seconds = 59.970 FPS
301 frames in 5.0 seconds = 60.036 FPS
301 frames in 5.0 seconds = 60.000 FPS
300 frames in 5.0 seconds = 60.000 FPS
300 frames in 5.0 seconds = 59.999 FPS
301 frames in 5.0 seconds = 60.004 FPS
300 frames in 5.0 seconds = 59.998 FPS
301 frames in 5.0 seconds = 60.002 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.003 FPS
300 frames in 5.0 seconds = 59.997 FPS
301 frames in 5.0 seconds = 60.004 FPS
301 frames in 5.0 seconds = 60.002 FPS
301 frames in 5.0 seconds = 60.005 FPS
300 frames in 5.0 seconds = 59.996 FPS
301 frames in 5.0 seconds = 60.002 FPS
301 frames in 5.0 seconds = 60.002 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.004 FPS
301 frames in 5.0 seconds = 60.000 FPS
300 frames in 5.0 seconds = 59.999 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.005 FPS
300 frames in 5.0 seconds = 59.998 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.002 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.005 FPS
301 frames in 5.0 seconds = 59.996 FPS
301 frames in 5.0 seconds = 60.002 FPS
301 frames in 5.0 seconds = 60.003 FPS
301 frames in 5.0 seconds = 59.999 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.012 FPS
300 frames in 5.0 seconds = 59.992 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.006 FPS
300 frames in 5.0 seconds = 59.990 FPS
301 frames in 5.0 seconds = 60.010 FPS
300 frames in 5.0 seconds = 59.999 FPS
301 frames in 5.0 seconds = 60.004 FPS
300 frames in 5.0 seconds = 59.999 FPS
301 frames in 5.0 seconds = 60.004 FPS
300 frames in 5.0 seconds = 59.998 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.003 FPS
301 frames in 5.0 seconds = 60.005 FPS
301 frames in 5.0 seconds = 60.030 FPS
301 frames in 5.0 seconds = 60.032 FPS
301 frames in 5.0 seconds = 59.984 FPS
```

$compiz --replace
```
Blacklisted PCI ID 8086:0116 detected

Launching fallback window manager
Window manager warning: "" found in configuration database is not a valid value for keybinding "run_command_10"
```

---

### Post by AureiAnimus on 2011-07-09
> **cucisan said:**
> im glad at least some ppl have no stability issues :)

the last time i checked on the bumblebee ppa there was no bumblebee package there (so no way to install without the scripts from git)

guess i will switch soon and update the my post accordingly as soon as those stability issues are gone.

care to share you wireless hardware? see commands above...

I have the same wireless hardware as you. However, I don't actually have a wireless access point in my house, so I use a lan cable. When the cable is unavailable, i sometimes borrow neighbouring networks, which don't seem to give me any real instability, but i tend to do that very little, so i have no real reference whether or not it works. I do have massive instability when trying to use Connectify, which turns my desktop into a wireless access point, but i'm pretty sure that is largely a connectify problem.

---

### Post by qmater001 on 2011-07-09
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
qmt@qmater-OS:~$ lspci -s 03:00.0 -vvnn
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: AzureWave Device [1a3b:2c37]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at de200000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k


how about the original driver that came with natty? how about trying it out, see if it makes the same troublem (i remember that i still had the lagging/freezing issues, even before puting the new driver that you recomended, but you can give it a try). for me.. the problem appears only when i boot in ubuntu, i let a few seconds, in between every app to load, everything is OK. still... it maybe be ralated to sandybridge

---

### Post by qmater001 on 2011-07-09
....And, coming back to the sandybridge issue. it says here...
 [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/761065](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/761065)

"SRU Justification:
 Fixes a constant stream of hangcheck errors flooding dmesg, and
removes the visible stuttering that was caused by it when using 3D
applications.
Impact:
 Fixes missed interrupts on sandybridge GPU's. It doesn't affect any
other GPU generation.
Fix:
 Upstream commit 498e720b96379d8ee9c294950a01534a73defcf3.
Testcase:
 1) Install mesa-utils on a system using sandybridge graphics on 11.04
 2) run vblank_mode=0 glxgears and let it run for 30 seconds or so
 3) kill it then check dmesg
 4) Without fix: hangcheck messages every ~5 seconds, massive
stuttering of the whole desktop observed. With fix: no hangcheck
messages, able to continue using the desktop."


i ran the test and i got:
[ 8398.647057] [drm:i915_hangcheck_ring_idle] *ERROR* Hangcheck timer elapsed... blt ring idle [waiting on 17517045, at 17517045], missed IRQ?
[ 8403.864403] [drm:i915_hangcheck_ring_idle] *ERROR* Hangcheck timer elapsed... blt ring idle [waiting on 17533018, at 17533018], missed IRQ?
[ 8408.322110] [drm:i915_hangcheck_ring_idle] *ERROR* Hangcheck timer elapsed... blt ring idle [waiting on 17545348, at 17545348], missed IRQ?
[ 8417.627339] [drm:i915_hangcheck_ring_idle] *ERROR* Hangcheck timer elapsed... blt ring idle [waiting on 17578156, at 17578156], missed IRQ?



but the things is that i have already 2.6.38.10 patched. (one thing though... after i installed the 2.6.38.10 patched kernel, i also updated the whole system, and i remember seeing something like downloading 2.6.38.10.... does that mean that it might have overwritten the patched kernel?


in any case, RUN THE TEST:
Testcase:
 1) Install mesa-utils on a system using sandybridge graphics on 11.04
 2) run vblank_mode=0 glxgears and let it run for 30 seconds or so
 3) kill it then check dmesg
 4) Without fix: hangcheck messages every ~5 seconds, massive
stuttering of the whole desktop observed. With fix: no hangcheck
messages, able to continue using the desktop.

---

### Post by qmater001 on 2011-07-09
Digging more, it seems to be 2 patches for the Random GPS Hangs. take a look here

[https://bugzilla.redhat.com/show_bug.cgi?id=684097#c33](https://bugzilla.redhat.com/show_bug.cgi?id=684097#c33)

---

### Post by cucisan on 2011-07-09
there it is: "Blacklisted PCI ID 8086:0116 detected"

seems you gfx hardware is blacklisted by compiz in 10.10

sorry don't have 10.10 so i cant help you much here :)

---

### Post by cucisan on 2011-07-09
> **qmater001 said:**
> ....And, coming back to the sandybridge issue. it says here...
 [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/761065](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/761065)

[...]

in any case, RUN THE TEST:
Testcase:
 1) Install mesa-utils on a system using sandybridge graphics on 11.04
 2) run vblank_mode=0 glxgears and let it run for 30 seconds or so
 3) kill it then check dmesg
 4) Without fix: hangcheck messages every ~5 seconds, massive
stuttering of the whole desktop observed. With fix: no hangcheck
messages, able to continue using the desktop.

yeah, thats why i suggested updating to kernel 2.6.38-10 from the bugreport... i had those hangchecks too.

one could also use the echo 1 > semaphores stuff to get stabler intel output.. but using -10 was the better result for me in the end..

---

### Post by cucisan on 2011-07-09
> **qmater001 said:**
> 03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
qmt@qmater-OS:~$ lspci -s 03:00.0 -vvnn
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: AzureWave Device [1a3b:2c37]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at de200000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k


how about the original driver that came with natty? how about trying it out, see if it makes the same troublem (i remember that i still had the lagging/freezing issues, even before puting the new driver that you recomended, but you can give it a try). for me.. the problem appears only when i boot in ubuntu, i let a few seconds, in between every app to load, everything is OK. still... it maybe be ralated to sandybridge



hmmmmmmmmmmmmmm...

for me there where massive issues with the original driver... very slow download rates, complete driver shutdown after 5minutes of copying files over wlan. had to re-connect to get it working again...

yes, it may still be related to sandybridge, but i dont know why its so random. i had 3 days with over 12hrs using the pc (playing, surfing, idling, watching movies, watching tv via usbstick, etcetc, idling around, copying stuff from/to usb drives) - all without a freeze.. and now it starts freezing again... and the only difference i remembered was actually i did not use wlan in those 3days.. :)
also when i copy stuff (making backup via scp, over 50gb of data) via wlan, i get those lags.. they are small but still there...


it also may neither ath9k nor sandybridge (but both are known to freeze a system :))... without the proper knowledge on debugging such things, i can only trial-on-error and observe... thats why im hoping to get more informations from other ppl :)

---

### Post by cucisan on 2011-07-10
as i switched my harddrive now im in the process of reinstalling.

out of curiosity i installed kernel 3.0 latest rc from mainline kernel ppa...

as soon as i install bumblebee it crashes on boot :) seems to be acpi_call - using default natty kernel works without problems with bumblebee installed.

*edit*

i will now stay on natty default kernel with blacklisting ath9k and only using my umts stick and see for how long it takes to freeze...

so no sandybridge fixes (irq hangs here we go) and no wlan fixes.

---

### Post by goldshirt9 on 2011-07-10
excellent thread.
very helpful :D

---

### Post by cucisan on 2011-07-10
> **AureiAnimus said:**
> I have the same wireless hardware as you. However, I don't actually have a wireless access point in my house, so I use a lan cable. When the cable is unavailable, i sometimes borrow neighbouring networks, which don't seem to give me any real instability, but i tend to do that very little, so i have no real reference whether or not it works. I do have massive instability when trying to use Connectify, which turns my desktop into a wireless access point, but i'm pretty sure that is largely a connectify problem.

funny you mention that. connectify is a windows program as far as i could find out. this features is also available through network manager (under ipv4 settings -> share to other computers; just in case you don't know)

what kind of instability issues are you talking about? which OS (as connectify turns out to be a win program).

---

### Post by cucisan on 2011-07-10
> **goldshirt9 said:**
> excellent thread.
very helpful :D

hello goldshirt9!

please tell us what your hardware is, what problems you have fixed and what still doesn'T work :)

as qmater & i have problems with the whole system freezing which nobody else seems to have? :)

thankyou!

---

### Post by cucisan on 2011-07-10
[https://bugzilla.kernel.org/buglist.cgi?quicksearch=freeze+ath9k](https://bugzilla.kernel.org/buglist.cgi?quicksearch=freeze+ath9k)
[https://bugzilla.kernel.org/show_bug.cgi?id=37082](https://bugzilla.kernel.org/show_bug.cgi?id=37082)
[http://marc.info/?l=linux-wireless&m=130768848626799&w=2](http://marc.info/?l=linux-wireless&m=130768848626799&w=2)

these are things im currently watching...

---

### Post by qmater001 on 2011-07-10
> **qmater001 said:**
> Digging more, it seems to be 2 patches for the Random GPS Hangs. take a look here

[https://bugzilla.redhat.com/show_bug.cgi?id=684097#c33](https://bugzilla.redhat.com/show_bug.cgi?id=684097#c33)

did you check this post?

"                   Alex W. Jackson                                                  2011-06-24 01:05:07 EDT                                I've compiled and am currently running a custom kernel based on 2.6.38.8-32.fc15 with the following two patches applied, and I get no more random GPU hangs. Please consider adding both patches to the next kernel update for F15."

how about this kernel? is it possible to use it with ubuntu?

folow post 33 on the above link, maybe you can try the 2 patches.
i know that 2.6.38-10 patched kernel used only the first patch. not the second.


....as its mentioned here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/761065/comments/45](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/761065/comments/45)
                 "After using the kernel from #38 for a few days I got a GPU hang again:
 Jun 25 10:58:05 x220 kernel: [154505.782665] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Jun 25 10:58:05 x220 kernel: [154505.782788] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -11 (awaiting 79090 at 79089, next 79117)
 This, however:
 [https://bugzilla.redhat.com/show_bug.cgi?id=684097](https://bugzilla.redhat.com/show_bug.cgi?id=684097)
 indicates that this needs to be applied for the BSD ring too (see second part of the fix).
 @Robert, could you create a kernel packages with both patches from the Red Hat bugzilla page applied?  Thanks."

---

### Post by qmater001 on 2011-07-10
> **cucisan said:**
> as i switched my harddrive now im in the process of reinstalling.

out of curiosity i installed kernel 3.0 latest rc from mainline kernel ppa...

as soon as i install bumblebee it crashes on boot :) seems to be acpi_call - using default natty kernel works without problems with bumblebee installed.

*edit*

i will now stay on natty default kernel with blacklisting ath9k and only using my umts stick and see for how long it takes to freeze...

so no sandybridge fixes (irq hangs here we go) and no wlan fixes.

so how is it? 
did u try 

   run vblank_mode=0 glxgears and let it run for 30 seconds or so
   kill it then check dmesg

also, did you managed to install bumblebee?
good luck!

---

### Post by AureiAnimus on 2011-07-10
> **cucisan said:**
> funny you mention that. connectify is a windows program as far as i could find out. this features is also available through network manager (under ipv4 settings -> share to other computers; just in case you don't know)

what kind of instability issues are you talking about? which OS (as connectify turns out to be a win program).

Connectify is indeed a windows program. My desktop runs windows and since back when we got fast internet the wireless wouldn't work, we have a cable run up to the desktop computer and the router is non-wireless, so i tried sharing the internet through the desktop with Connectify. The instability is just slow internet, 2 bars of connectivity when my laptop is on top of the desktop. (The desktop doesn't experience instability.) However, I have decent to good connectivity when trying the neighbours network. So i'm guessing the issue is in Connectify or my desktops wireless card.

---

### Post by cucisan on 2011-07-11
> **qmater001 said:**
> so how is it? 
did u try 

   run vblank_mode=0 glxgears and let it run for 30 seconds or so
   kill it then check dmesg

also, did you managed to install bumblebee?
good luck!

i know about the hangcheck errors, but using -10 kernel fixes that completely for me :)

bumblebee installed via ppa, but not working with oneiric kernel 3.0rc ... acpi_call seems to cause kernel oops.

with blacklisting ath9k and only using umts stick no freeze for over 20hrs :) but i will wait longer to see if its really the cause..

---

### Post by cucisan on 2011-07-11
qmater001: also see [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/761065]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/761065")

the second patch only seems to be for va acceleration...

---

### Post by qmater001 on 2011-07-11
interesting, that you dont get any more hangs, cause other people, me included still get them with the patched kernel. less, but they`re still there... some ppl recomended the second patch... unfortunatelly i don`t know how to use the patch (still a a noob into linux :)

---

### Post by cucisan on 2011-07-11
> **qmater001 said:**
> interesting, that you dont get any more hangs, cause other people, me includem still get them with the patched kernel. less, but they`re still there... some ppl recomended the second patch... unfortunatelly i don`t know how to use the patch (still a a noob into linux :)


hm thats indeed strange... :)

im running the natty default kernel (with ath9k blacklisted) since yesterday... and no freeze... but (as expected) i915-hangcheck/irq errors.

i guess for me thats not the freezing issue... just the GUI stutters sometimes..

---

### Post by _byron_ on 2011-07-12
hello all

thank you for this topic... particulary cucisan
It solved all my problems on my asus K53SJ !!

touchpad mutltitouch !!!
i won 30% battery usage by disabling my GT520M graphic card !!
reduce the full powered fan !!

but...
concerning the fan i noticed that it seems to turn all the time at reduced speed.
I tried lm_sensors but the only probe it found is :

acpitz-virtual-0
Adapter: Virtual device
temp1:        +45.0°C  (crit = +88.0°C)

i tried fancontrol and pwmconfig without result

could i need some custom kernel configuration or bios update ?
do you have similar problem

can the nvidia graphic card fan be modulated ? even without proprietary driver ?

---

### Post by qmater001 on 2011-07-13
@cucisan so how are things working with 3.0.0 ? wich rc did you use? i installed it today, but i got an error (it failed in regards to the nvidia driver), and also when i boot in  3.0.0-5.6 i get a could not write bytes - broken pipe.. any suggestions?

---

### Post by cucisan on 2011-07-13
the fan is not related to nvidia, there is only one fan for the whole system in this laptop.. so the only chance is to control it via ACPI.

@qmater: im not using kernel 3.x as i said, it did crash on bootup.

---

### Post by qmater001 on 2011-07-14
i managed to compile kernel 3.0 rc7 , installed it.. and unfortunatelly i could reproduce again "the lagging/freezing" bug... 
so, i may be hardware related...
**so, as a poll.. how many of you have this issue?? i will appriciate every answer.**

---

### Post by inversus on 2011-07-19
Btw, do you recommend me to buy this laptop?
Do you think that ubuntu runs ok on it?

---

### Post by _byron_ on 2011-07-20
I have some absolute freeze when i use banshee.
loop chunk of music, keyboard down, graphics frozen, power button disabled...

3 or 4 times a day i have to long press the power button to reboot !!! my laptop is "on" 12 hours/day

I only noticed that when i learn music via banshee... i should try with another media player such as VLC.

uname -a
Linux robin-K53SJ 2.6.38-10-generic-pae #46-Ubuntu SMP Tue Jun 28 16:54:49 UTC 2011 i686 i686 i386 GNU/Linux

lspci | grep Network
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by _byron_ on 2011-07-22
I can confirm !!
I have critical hang of the whole laptop when using banshee and no problem while playing VLC

---

### Post by cucisan on 2011-07-23
what are you doing when the freezing occurs? listening to local mp3s or anything else? like webradio etc?

---

### Post by qmater001 on 2011-07-23
update: if you still have the jittery jumpy touchpad install this
[http://pkgs.org/download/debian-wheezy/debian-main-amd64/xserver-xorg-input-synaptics_1.4.1-1_amd64.deb.html](http://pkgs.org/download/debian-wheezy/debian-main-amd64/xserver-xorg-input-synaptics_1.4.1-1_amd64.deb.html)

as in regards to the hanging... i belive it`s just sandy bridge... so.. maybe somebody will try the new stable kernel 3.0 that was just released today. (see if you can get bumblebee working :D)

---

### Post by qmater001 on 2011-07-24
I may have found at least part of the issue i was having (lagging and freezing that is )
skype seems to be the culprit, and it seems a lot of people are having this issue..
[https://jira.skype.com/browse/SCL-731](https://jira.skype.com/browse/SCL-731)

do you?

---

### Post by Ench on 2011-07-24
_byron_ try Clementine, it is quite good music player imho.

qmater001: my freezes are very rare after update to 2.6.38-10 and latest bumblebee. I don't have skype to boot automatically on startup tho

---

### Post by cucisan on 2011-07-24
i don't use skype.. so no relation for me

---

### Post by _byron_ on 2011-07-25
I play local files on data partition (ext4)..

No probs all the day long with VLC

---

### Post by _byron_ on 2011-07-25
> **Ench said:**
> _byron_ try Clementine, it is quite good music player imho.


I will make some test, thank you

---

### Post by _byron_ on 2011-07-26
> **_byron_ said:**
> I will make some test, thank you

Same problem !
How can i find interesting log file when i reboot my laptop ?

---

### Post by fabio.parisini on 2011-07-26
Thanks for the nice post... I have a problem tough. I have a K53SV, I can install bumblebee as you suggest, but when I reboot and try the gdm login the xserver resets and does not allow me to get in; any clue on what I should do?

Thanks :D

---

### Post by cucisan on 2011-07-27
i use rhythmbox (was the ubuntu default before banshee) for everything from webstreams and local files - no freezes or anything.. can play for hours.

---

### Post by inversus on 2011-07-27
> **cucisan said:**
> i use rhythmbox (was the ubuntu default before banshee) for everything from webstreams and local files - no freezes or anything.. can play for hours.

Please help me out!
I'm thinking about buying this laptop (k53sv); I will use Linux!

Is it a good option? Do you still have big problems? Does your laptop only freezes playing music? Does it happens frequently?

Tnks!

---

### Post by qmater001 on 2011-07-27
did you guys tryed to update banshee from the nattye proposed repository? i have now 2.0 (2.0.1).. also some of the freezing i had the impression may be related to libre office, i had a few while i was copy pasting from calc

---

### Post by Mr.BS on 2011-07-30
GREAT THREAD!\\:D/

Finally scrolling on touchpad working, i will try disabling the nvidia later to increase battery time or is this to be expected in 11.11?
If the nvidia card is disabled, will this drop the internal temperature of the laptop (with the same (low) fan speed)?
And how about the (not working) FN functions? Will this get better in 11.11?

I have no freezing problems but i don't use Skype but i do use WLAN most of the times. Very rarely i have the 2-4 seconds delayed respons mainly when typing and letters don't appear right away......not a big deal.

Another thing i noticed is the WLAN LED, it doesn't light up after reboot/startup while WLAN is activated. If i use Fn and F2 to switch off and on the LED is working with WLAN activated.

---

### Post by Mdelem on 2011-08-03
Hi guys,

Just bought an Asus X53SV-SX200V (K53SV model), I'm experiencing the freezes too.

I'm a Fedora 15 refugee where freezes happen too. I switched to ubuntu because this forum seemed active and helped me work out the touchpad, hotkeys and optimus stuff. Thanks everybody :)


On ubuntu, I've updated to the 3.0.0-7-generic kernel following these instructions : [http://marcin.juszkiewicz.com.pl/2011/06/20/linux-3-0-under-ubuntu-natty-11-04/](http://marcin.juszkiewicz.com.pl/2011/06/20/linux-3-0-under-ubuntu-natty-11-04/)

I've also formatted to align my hard drive partitions with the physical sectors of the disk.

After that, I still get the freezes.
They seem to be related to high hard disk and CPU load. I can reproduce by using the GWT compiler which uses up to 8 threads and a few gigabytes of ram (around 512m per thread).

I've made experiments by changing the number of threads used by the compilation process.
[LIST]
[*]1 thread => OK
[*]2 threads => small/medium lags
[*]4 threads => heavy lag, cannot move the mouse during minutes
[*]8 threads => so much hard drive activity (swap?) that I never managed to reach the end of the compilation. Mouse does not work nor Ctrl+Alt+Del. Had to hard reboot.
[/LIST]

Compilation using 8 threads is successful on an older computer with a **non** Sandy Bridge Intel i5 architecture.

Anybody experiencing freezes under heavy multicore load ?

---

### Post by silentbang on 2011-08-04
> **qmater001 said:**
> I may have found at least part of the issue i was having (lagging and freezing that is )
skype seems to be the culprit, and it seems a lot of people are having this issue..
[https://jira.skype.com/browse/SCL-731](https://jira.skype.com/browse/SCL-731)

do you?

yea.it sometimes gets lag when I login Skype while playing music in Banshee

---

### Post by slavinzing56 on 2011-08-05
nice.... looking forward to it.

---

### Post by _byron_ on 2011-08-05
Hi folks !!

I find a workaround for the card reader !
follow the link :
[http://ubuntuforums.org/showpost.php?p=11065709&postcount=7](http://ubuntuforums.org/showpost.php?p=11065709&postcount=7)

---

### Post by Mr.BS on 2011-08-06
Thanks _byron_!

Another problem solved.;)

Nobody problems with the switching of the brightness of the screen?
Most of the times i use the lowest brightness but when using the power button or start Frozen Bubble the brightness level switches to the default value.
Would be nice if brightness was always the same.

---

### Post by slavinzing56 on 2011-08-08
thx for the reply cucisan, but. i dont get any constant lags. On 10.10, i  used to boot, and once i was logged in, i just clicked on my "usual  apps" (firefox, skype, pidgin, chrome, and libre office), well if i do  the same on 11.04, thinks are getting stuck/laggy, to the point where  there`s nothing but lag lag lag and the apps will not load (or crash),  for minutes, and then i have to restart. if i just open the appes one by  one, giving them some time to load until i start the other, then  everything works smooth.
i have another hdd so i`ll try to use that one to see if it makes any difference. 
and in regars to grub? any ideea how can i set 2.6.38.10 as default to be loaded instead of 2.6.39 ?

---

### Post by cucisan on 2011-08-11
the asus K53SV and also my A53SV has the "intel sandybridge throttling" problem, you find infos about that on google...(many new laptops have that)

there is a routine in the BIOS from Asus, which throttles the cpu down to ~650mhz on heavy load, this has been covered in some of the reviews i have read about the asus.

but normally this only applies when the GT540 and CPU are under load...
which makes playing heavy duty games impossible (like BFBC2)

for windows there is "throttlestop", which helps much but does not disable it completely. for linux there are those "msr-tools" which bring a kernel module that disables throttling ... you can find the howto easily on google on how to use it (asus g53 forum and also some blog posts)

> **Mdelem said:**
> Hi guys,

Just bought an Asus X53SV-SX200V (K53SV model), I'm experiencing the freezes too.

I'm a Fedora 15 refugee where freezes happen too. I switched to ubuntu because this forum seemed active and helped me work out the touchpad, hotkeys and optimus stuff. Thanks everybody :)


On ubuntu, I've updated to the 3.0.0-7-generic kernel following these instructions : [http://marcin.juszkiewicz.com.pl/2011/06/20/linux-3-0-under-ubuntu-natty-11-04/](http://marcin.juszkiewicz.com.pl/2011/06/20/linux-3-0-under-ubuntu-natty-11-04/)

I've also formatted to align my hard drive partitions with the physical sectors of the disk.

After that, I still get the freezes.
They seem to be related to high hard disk and CPU load. I can reproduce by using the GWT compiler which uses up to 8 threads and a few gigabytes of ram (around 512m per thread).

I've made experiments by changing the number of threads used by the compilation process.
[LIST]
[*]1 thread => OK
[*]2 threads => small/medium lags
[*]4 threads => heavy lag, cannot move the mouse during minutes
[*]8 threads => so much hard drive activity (swap?) that I never managed to reach the end of the compilation. Mouse does not work nor Ctrl+Alt+Del. Had to hard reboot.
[/LIST]

Compilation using 8 threads is successful on an older computer with a **non** Sandy Bridge Intel i5 architecture.

Anybody experiencing freezes under heavy multicore load ?

---

### Post by cucisan on 2011-08-11
> **_byron_ said:**
> Hi folks !!

I find a workaround for the card reader !
follow the link :
[http://ubuntuforums.org/showpost.php?p=11065709&postcount=7](http://ubuntuforums.org/showpost.php?p=11065709&postcount=7)

thanks! i updated the first post

---

### Post by joebarker182 on 2011-08-13
hello guys i have asus k43, and the azurewave bluetooth combo card NB037 is always disabled, how to enabled it ?

---

### Post by Philip Piper on 2011-08-15
s

---

### Post by _byron_ on 2011-08-18
bluetooth working on K53SJ

1. download the driver:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714862/+attachment/1913129/+files/ar3011-dkms_1.1ryu2.3_all.deb](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714862/+attachment/1913129/+files/ar3011-dkms_1.1ryu2.3_all.deb)

2. install the driver:
sudo dpkg -i ar3011-dkms_1.1ryu2.3_all.deb

3. Check the installation:
run "dkms status" to see if there are the following info:
ar3011, 1.1ryu2.3, 2.6.38-11-generic-pae, i686: installed (or similar)
After a reboot, the bluetooth icon should appear and indicate that bluetooth is working.

source : [http://ubuntuforums.org/showthread.php?t=1791400](http://ubuntuforums.org/showthread.php?t=1791400)

---

### Post by Franzcesco on 2011-08-20
Hi, I have an Asus x53s, I'm able to use ubuntu (64 bit) thanks to this post and your constant updates. I still have some problems (some of them already repoted above):


[LIST=1]
[*]Sometimes **ubuntu freeze on boot just before login** screen. It happens often with the latest kernel version 2.6.38.11. (I've read something about, could be related to the bumblebee nvidia.xorg.conf??);
[*]installing **the realtek driver for the card reader really messed up the 2.6.38.11 version of the kernel,** so that it won't boot anymore (any advice to return to the old configuration??); EDIT: I removed the driver and reinstalled the kernel, seems to work well now....
[*]**Occasional freeze of the system** (it happened a few times, I think related to ryhthmbox cannot say how :confused:);
[*]**skype consumes all ram, and hangs system till crash on first run** (known problem on the net, no solution for the moment, it really drives me crazy);
[/LIST]

Ready to provide more info if you think it's useful. For the moment, thanks for this post, that really helped me!

---

### Post by bloodred6366 on 2011-08-21
installing the realtek card driver shown here
[http://ubuntuforums.org/showpost.php?p=11065709&postcount=7](http://ubuntuforums.org/showpost.php?p=11065709&postcount=7)

would not compile for me on Natty_i386. I had to manually edit the Makefile and replace "$PWD" with "$(shell pwd)".

then it compiled, and after reboot it is working great. havent had any kernel issues.

thx a lot!

---

### Post by theskin on 2011-08-21
> **Franzcesco said:**
> Hi, I have an Asus x53s, I'm able to use ubuntu (64 bit) thanks to this post and your constant updates. I still have some problems (some of them already repoted above):


[LIST=1]
[*]Sometimes **ubuntu freeze on boot just before login** screen. It happens often with the latest kernel version 2.6.38.11. (I've read something about, could be related to the bumblebee nvidia.xorg.conf??);
[*]installing **the realtek driver for the card reader really messed up the 2.6.38.11 version of the kernel,** so that it won't boot anymore (any advice to return to the old configuration??); EDIT: I removed the driver and reinstalled the kernel, seems to work well now....
[*]**Occasional freeze of the system** (it happened a few times, I think related to ryhthmbox cannot say how :confused:);
[*]**skype consumes all ram, and hangs system till crash on first run** (known problem on the net, no solution for the moment, it really drives me crazy);
[/LIST]

Ready to provide more info if you think it's useful. For the moment, thanks for this post, that really helped me!

I also have an X53 , installed 11.04 32 bit , updated to kernel 3 .. [https://techtimely.wordpress.com/2011/08/19/install-linux-kernel-3-0-on-ubuntu-11-04/](https://techtimely.wordpress.com/2011/08/19/install-linux-kernel-3-0-on-ubuntu-11-04/)

everything is working perfectly , wi-fi , function keys , even the HDMI detects all resolutions on the TV . power usage is on par with windows and the cpu temp is fine too

---

### Post by qmater001 on 2011-08-23
installing previous version of skype solves the problem, for skype. also.. system freezes due to libreoffice (tools > options, uncheck hardware acceleration and anti-alising)
in case you cant find some older version of skype, i have v 2.1 something . deb, so i can provide it.
good luck

---

### Post by razorpl on 2011-08-28
Hello.
Im running asus x53sv-sx200v and after installation of nvidia drivers compiz seems to stop working. 
I've tried many tricks, editing xorg.conf, reinstalling drivers, using older drivers and always i've getting information that my driver is installed but not in use.
What can i do to install nvidia drivers?
After many tries i think that i broke sth, cause after instalation of bumblebee my fan starts to spin at full speed, and i've got black screen.

I've reinstalled my ubuntu and i'm afraid of installing bumblebee one more time.

id like to get some games working on ubuntu for example starcraft II.

What should i do?
Please help!

Peter

---

### Post by Koppie on 2011-08-28
I also struggled with this.  My solution: just deactivate the Nvidia drivers altogether.  Clean install of 11.04, Classic Mode (just because I still like Gnome 2), deactivated Nvidia, and 3d graphics work perfectly, Compiz and everything.  I have an Asus A73S with Optimus, which means I have two video cards: Nvidia and the built-in Intel.  Ubuntu has no problem with the built-in Intel card.  Sure, I'm not really getting hardware acceleration, and battery life is terrible because the Nvidia card is still sucking power, but it all Just Works.

I did experiment with Bumblebee, and it's useful if you really need 3D acceleration in Ubuntu with an Optimus setup, but kills DRI support for the Intel card, which means no Compiz (which is much more important to me).

For gaming, just dual boot into Windows.  I don't play games often enough to worry about it more than that.

--Koppie

---

### Post by razorpl on 2011-08-29
> **Koppie said:**
> I also struggled with this.  My solution: just deactivate the Nvidia drivers altogether.  Clean install of 11.04, Classic Mode (just because I still like Gnome 2), deactivated Nvidia, and 3d graphics work perfectly, Compiz and everything.  I have an Asus A73S with Optimus, which means I have two video cards: Nvidia and the built-in Intel.  Ubuntu has no problem with the built-in Intel card.  Sure, I'm not really getting hardware acceleration, and battery life is terrible because the Nvidia card is still sucking power, but it all Just Works.

I did experiment with Bumblebee, and it's useful if you really need 3D acceleration in Ubuntu with an Optimus setup, but kills DRI support for the Intel card, which means no Compiz (which is much more important to me).

For gaming, just dual boot into Windows.  I don't play games often enough to worry about it more than that.

--Koppie

Koppie, thanks for your answer.
I actually have dual boot, as you said: for gaming in windows. But  im looking forward for better solution to get 3d games like starcraft 2 working on my Asus model.
With clean install of ubuntu compiz working fine with natty and classic gnome. 
but 3d mode in games doesn't work: i mean all graphic is black and i just can see few simple polygons. But no textures.
How was your experiment with bumblebee?
What have u done to get 3d working without fan speed problems?
Does nvidia mode activated means 3d support in games but no compiz?
I'really dont care if my laptop suck power cause im constantly connected to AC, but i hope that someone got solution for hardware acceleration in games and compiz working in same time.

Razor.

---

### Post by Koppie on 2011-08-29
Bumblebee is great.  But you have to realize what it does.  It basically disables 3D rendering for your system, but gives you a "pipe" that you can run 3D apps through, and the pipe uses the Nvidia card.  So that means no Compiz, as long as you're okay with that.  I didn't test Starcraft II, but I tested glxgears and scorched3d and they both ran GREAT.  Starcraft II is a windows app which means you'll need to run it inside wine, which will have to run inside bumblebee.  Not sure if anyone has tried that yet.

Bumblebee also has utilities to turn the entire video card on and off, not just the fan.

But no, if you have an Optimus card, there doesn't seem to be any way to get 3d games and Compiz running at the same time.  I gave up once I got Compiz working because this is primarily a work computer and I don't have time to spend trying to make games work outside of windows.  So I'm not running bumblebee any more.  (In fact, I just re-installed Ubuntu so I wouldn't have to deal with uninstalling bumblebee.)  The good news: it looks like there is some work on an Optimus driver for Linux, so give it 6 months or a year and we may have 100% compatibility in Linux again.

You might also want to try the linux 3.0 kernel; I had some success with that, except it made all my text upside down and backwards!

---

### Post by FirstByté on 2011-08-29
I bought my Asus U41S all because my old system needed a change. I felt truly sad that I didn't research about Asus/nvidia enough before getting entangled with Optimus :( [All the while at the shop my mind reminded me that Nvidia was no good for Linux]

> **Koppie said:**
> Bumblebee is great.  But you have to realize what it does.  It basically disables 3D rendering for your system, but gives you a "pipe" that you can run 3D apps through, and the pipe uses the Nvidia card.  So that means no Compiz, as long as you're okay with that.  

...

Bumblebee also has utilities to turn the entire video card on and off, not just the fan.

Thanks for the info on this. Many times I wonder what bumblebee or ironhide really does (because I have tried many [fixes]("http://ubuntuforums.org/showthread.php?t=1835188")).

> **Koppie said:**
> 
But no, if you have an Optimus card, there doesn't seem to be any way to get 3d games and Compiz running at the same time.  I gave up once I got Compiz working because this is primarily a work computer and I don't have time to spend trying to make games work outside of windows.  

So I'm not running bumblebee any more.  
...

I love compiz so much that I use Ubuntu Classic...

[SIZE="3"]**What session manager do you use; Unity or Classic gnome?**[/SIZE]

Currently I 'hybrid' Classic (bottom gnome-panels) *on* Unity session.
Reasons: 
-I navigate with lower taskbar
-I hate typing commands to start apps (Unity way ](*,) )
-I hate to click on Notification areas to get basic info (that moveover would have given--very medieval)
- COMPIZ has all the WHISTLES!!

PLEASE HOW CAN I GET COMPIZ TO WORK with **Ubuntu Classic**?
Note: It currently works with Unity and I have Bumblebee install

Else I might be forced to sell this to a windoz only freak; I don't have time for games. I need mobility and durability :(

---

### Post by razorpl on 2011-08-30
> **Koppie said:**
> Bumblebee is great.  But you have to realize what it does.  It basically disables 3D rendering for your system, but gives you a "pipe" that you can run 3D apps through, and the pipe uses the Nvidia card.  So that means no Compiz, as long as you're okay with that.  I didn't test Starcraft II, but I tested glxgears and scorched3d and they both ran GREAT.  Starcraft II is a windows app which means you'll need to run it inside wine, which will have to run inside bumblebee.  Not sure if anyone has tried that yet.

Bumblebee also has utilities to turn the entire video card on and off, not just the fan.

But no, if you have an Optimus card, there doesn't seem to be any way to get 3d games and Compiz running at the same time.  I gave up once I got Compiz working because this is primarily a work computer and I don't have time to spend trying to make games work outside of windows.  So I'm not running bumblebee any more.  (In fact, I just re-installed Ubuntu so I wouldn't have to deal with uninstalling bumblebee.)  The good news: it looks like there is some work on an Optimus driver for Linux, so give it 6 months or a year and we may have 100% compatibility in Linux again.

You might also want to try the linux 3.0 kernel; I had some success with that, except it made all my text upside down and backwards!

So theoretically with bumblebee installed i have possibility to manually disable 3d acceleration which results 3d in compiz working? it sounds pretty astonishing :P

---

### Post by cucisan on 2011-08-30
bumblebee/ironhide doesn't mean it will disable compiz, thats utterly wrong.

the only reason compiz will stop working is after setting up bumblebee/ironhide and then updating the nvidia driver will overwrite some GL libs the intel drivers needs for compiz. like i already said in this thread! (there is a also a bugreport for this and currently no way around it despite reinstalling bumblebee)

i used compiz and played many steam games all at the same time.
because the nvidia driver is run on a second X server, which has nothing todo with the Xserver the intel card is running.

for everyone who just don't need the nvidia card, you can add the ironhide ppa and just install the acpi-call package..

then load it and disable your card (in /etc/rc.local). which will give you good batterylife with mediocre gfx performance with the intel card...

i don't own this laptop anymore so i'm not able to give anymore support, but i can tell you, with ubuntu oneiric at least the sandybridge laptops will work much better/smoother.. but there are other issues there (mostly bad batterylife which have workarounds) ;)

---

### Post by Franzcesco on 2011-08-30
> **theskin said:**
> I also have an X53 , installed 11.04 32 bit , updated to kernel 3 .. [https://techtimely.wordpress.com/2011/08/19/install-linux-kernel-3-0-on-ubuntu-11-04/](https://techtimely.wordpress.com/2011/08/19/install-linux-kernel-3-0-on-ubuntu-11-04/)

everything is working perfectly , wi-fi , function keys , even the HDMI detects all resolutions on the TV . power usage is on par with windows and the cpu temp is fine too

well, probably part of the solution is installing 32bit version when oneiric is released. Thanks!

---

### Post by Franzcesco on 2011-08-30
> **qmater001 said:**
> installing previous version of skype solves the problem, for skype. also.. system freezes due to libreoffice (tools > options, uncheck hardware acceleration and anti-alising)
in case you cant find some older version of skype, **i have v 2.1 something . deb, so i can provide it**.
good luck

That would much appreciated... :) 
I can't find older debs

---

### Post by DumbEar on 2011-08-30
hey,
sorry for bothering, but i was trying to fix issues with touchpad, and   keyboard with your post here (i got ntb asus n53s hope it dont mind) [http://ubuntuforums.org/showthread.php?t=1791081](http://ubuntuforums.org/showthread.php?t=1791081) 
and i got few errors like the first 1: when i try to "repair"touchpad" i run all commands from here [https://bugs.launchpad.net/ubuntu/+s...04/comments/64]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/681904/comments/64")    but when i try to run yours after    sudo rmmod psmouse && sudo modprobe psmouse

it says it cant locate module psmouse 

the 2. error is when i try to "repair" keyboard.
i can run the first set of commands, but when i want to 
run sudo aptitude....it says such command does not exist

i will be grateful if you could help me..

---

### Post by Mr.BS on 2011-09-02
@ DumbEar

Did you get any error messages after the Elantech patch? Maybe you have different type of touchpad...?
And for the 2. problem......try sudo **apt-get** install... this worked for me.;)

---

### Post by javidemon95 on 2011-09-18
hi. i have an asus a53s with i7 2630QM. will run ubuntu well on it?
sorry for my bad english

---

### Post by Mr.BS on 2011-09-18
Yes, i have a K53SJ with same processor for 3 months now and Ubuntu works just fine.
Some adjustments need to be made but that's all in the first posts of this thread...:popcorn:

---

### Post by javidemon95 on 2011-09-19
Thanks you. I will try it. I will tell you how it was.

---

### Post by DumbEar on 2011-09-20
well then i have problem with command 
sudo dpkg -i [newlycreated-package].deb     ...it says such folder does not exist

---

### Post by javidemon95 on 2011-09-21
all work perfect for me less the nvidia. any idea?

---

### Post by Mr.BS on 2011-09-23
@ DumbEar

Did you cd into the right directory?
Was there a file build by the dpkg-buildpackage command? What was it's name?
Have you also tried sudo dpkg -i acpi4asus-dkms_2.6.39-1_all.deb?

@ javidemon

Any error messages?
Afaik, packages like Bumblebee and Ironhide are still a bit experimental.
Im my case Bumblebee is working for about 90%. Can't switch it 100% off which would be nice for less power consumption.
Haven't tried Ironhide though.....anyone here maybe?

---

### Post by gillza on 2011-10-05
> **cucisan said:**
> ```

git clone git://git.iksaif.net/acpi4asus-dkms.git
cd acpi4asus-dkms
make
sudo make install
sudo modprobe asus-nb-wmi

```

all keys are working :) strike

with natty default kernel...

*edit*:

as soon as a kernel update is coming, the files installed will be overwritten.
but being the dkms branch is quite easy to make it "stick"

```

sudo aptitude install debhelper
cd acpi4asus-dkms
dpkg-buildpackage
sudo dpkg -i [newlycreated-package].deb

```


This worked for volume up/down on G53SX-A1.
In addition Bluetooth drivers also worked as they laptops use the same chip. I assume much from this thread works for all G73 and G53 models.

Thank you!

---

### Post by Koppie on 2011-10-10
#9 worked for me too!  Thank you!

---

### Post by iammuneeb on 2011-10-11
Thanks for this wonderful guide.

I just bought Asus K53SV - V2G

I followed the steps given in first post and I got following things working.

1. Bumblebee  
2. Special Function Keys (Vol Up etc)
3. Touchpad


Sometimes I see my mouse pointer stops for a sec, then works again, so I guess I'm having some problem with freezing.

Didn't notice any change in WiFi connectivity.

I don't know how to check for FAN speeds so can't tell more about it.

Yet to check card reader, I'll inform when I get one.

Things I want to give a try:

Getting touchpad working for multi-touch gestures such as Zoom In/Out two fingers, rotate image, etc

So how should I go about this?

---

### Post by Koppie on 2011-10-11
> **iammuneeb said:**
> Getting touchpad working for multi-touch gestures such as Zoom In/Out two fingers, rotate image, etc

So how should I go about this?

If you followed the instructions from the first post, then you already have the touchpad driver.  Go to System >> Preferences >> Mouse Preferences and you should see a tab for Touchpad.  There you can enable two-finger scrolling, disable while typing, etc.  

There's another, fancier utility out there that gives you extra options for the touchpad, like "rotate" scrolling (a la original iPod), but I forget what it's called.  These days I find simpler is better.  (Except for my Compiz spinny cube, of course!)

---

### Post by iammuneeb on 2011-10-14
> **Koppie said:**
> 

There's another, fancier utility out there that gives you extra options for the touchpad, like "rotate" scrolling (a la original iPod), but I forget what it's called.  These days I find simpler is better.  (Except for my Compiz spinny cube, of course!)

The touchpad is working fine. But yes I need Rotate, Zoom In, Zoom Out option. I would like to know the name of  the app which you are talking about.


Also does anybody know how to get Full Gnome 3 working on 11.10 on this k53sv? I have installed Bumblebee, and I'm getting Fallback mode only.

---

### Post by bulva on 2011-10-15
> **cucisan said:**
> ```

git clone git://git.iksaif.net/acpi4asus-dkms.git
cd acpi4asus-dkms
make
sudo make install
sudo modprobe asus-nb-wmi

```all keys are working :) strike

with natty default kernel...

*edit*:

as soon as a kernel update is coming, the files installed will be overwritten.
but being the dkms branch is quite easy to make it "stick"

```

sudo aptitude install debhelper
cd acpi4asus-dkms
dpkg-buildpackage
sudo dpkg -i [newlycreated-package].deb

```

I'm running G53s, currently with old 2.6.32-5 kernel (3.x kernel panicks when loading). I have no problems with wifi or touchpad, the cpu frequency scaling works nicely (spins down all the way to 0.8 GHz when idle). Fn for turning wifi on/off works fine (the most useless key ever, sight)

What does not work:

[LIST]
[*] fn-keys for screen brightness or volume
[*] I can't control the screen brighness with an panel applet, it doesn't go dim when on battery either. The only option is through nvidia-settings.
[*] Keyboard backlight (no functionality at all, less alone brigness controll)
[*] Sensors-detect doesn't detect any sensors and as a result I don't see CPU temp in Conky
[/LIST]
 
I tried compiling acpi4asus, it fails with:

```
undefined reference to linux/input/sparse-keymap.h:
```And I indeed don't have such a header in the system. Could someone who succesfully compiled this module please run:

```
sudo updatedb && locate sparse-keymap.h 
```And tell me the results?

---

### Post by iammuneeb on 2011-10-15
> **bulva said:**
> I'm running G53s, currently with old 2.6.32-5 kernel (3.x kernel panicks when loading). I have no problems with wifi or touchpad, the cpu frequency scaling works nicely (spins down all the way to 0.8 GHz when idle). Fn for turning wifi on/off works fine (the most useless key ever, sight)

What does not work:

[LIST]
[*] fn-keys for screen brightness or volume
[*] I can't control the screen brighness with an panel applet, it doesn't go dim when on battery either. The only option is through nvidia-settings.
[*] Keyboard backlight (no functionality at all, less alone brigness controll)
[*] Sensors-detect doesn't detect any sensors and as a result I don't see CPU temp in Conky
[/LIST]
 
I tried compiling acpi4asus, it fails with:

```
undefined reference to linux/input/sparse-keymap.h:
```And I indeed don't have such a header in the system. Could someone who succesfully compiled this module please run:

```
sudo updatedb && locate sparse-keymap.h 
```And tell me the results?

```
$ sudo updatedb && locate sparse-keymap.h
/usr/src/linux-headers-3.0.0-12/include/linux/input/sparse-keymap.h

```

How did you get nvidia-settings  working? I keep getting following dialog box. 

```
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
```

I didn't do the nvidia-xconfig as it gets me blank screen (I tried that on 11.04, yet to try on 11.10)

---

### Post by bulva on 2011-10-15
Here's what I did:

[LIST]
[*]Got rid of previously installed Nvidia drivers:
[/LIST]
```
sudo apt-get --purge remove nvidia-*
```
[LIST]
[*]Installed proprietary driver:
[/LIST]
sudo apt-get install nvidia-glx nvidia-settings nvidia-xconfig


[LIST]
[*]Additional libraries you might need:
[/LIST]
```
sudo apt-get install mesa-common-dev libgl1-mesa-dev libglu1-mesa-dev libxi-dev libxmu-dev libglut-dev freeglut3-dev
```
[LIST]
[*]Blacklisted free nouveau drivers (you don't need it but sometimes it comes back when updating kernel):
[/LIST]
```
sudo gedit /etc/modprobe.d/blacklist.conf
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

```
[LIST]
[*]And did what he asks for, then rebooted:
[/LIST]
```
sudo nvidia-xconfig
```This should create a xprg.conf for you. Now I'm not sure if You have the proprietary driver in Ubuntu repos (I'm running Debian), if not download the driver from here:

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

And run the binary as root.

Now everything that I have in /usr/src/linux-headers-2.6.32-5-amd64/include/linux is autoconf.h,  bounds.h,  compile.h,  utsrelease.h and  version.h. Seems like this kernel is too old. I just tried compiling my own 2.6.39 but it also doesn't load... Was anyone succesfull with compiling custom kernel for asus G53/G73 ?

---------------------------------------------------------------------------------------------------------------------------------------------------

I've found a way to get the screen brightness keys working by editing /etc/X11/xorg.conf and adding:

```
Option "RegistryDwords" "EnableBrightnessControl=1"
```

in Section "Monitor"

---

### Post by iammuneeb on 2011-10-16
Bumblebee is working fine on my k53sv laptop. But how can I run full Gnome 3 (I get fallback otherwise) or Unity 3D.

If I remove nvidia proprietary drivers, I'm getting full Gnome 3 and Unity 3D, but using bumblebee I'm unable to get that.

---

### Post by bulva on 2011-10-19
I have noticed two new issues:

[LIST]
[*]System shuts down instead of hibernating
[*]One of the usb 2.0 ports stops detecting the usb mouse after some time (usb 3.0 port works fine)
[/LIST]

The shutdown was due to UUID mixed up - after fixing that it goes into hibernation but fails to recover due to some problems with usb3 driver (?), saying "device usb3 failed to quesque"s and than hangs. I will keep on looking into this.

-------------------------------------------------------------
I got the hibernation working using following steps:


[LIST]
[*] sudo gedit /etc/X11/xorg.conf and adding the following
[/LIST]

[LIST]
[*] under the "Device" section: Option "NvAGP" "3"
[*]Then I used this script: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)
[/LIST]
It is still displaying some weird (hard drive?) error but Evyrything seems to work after resuming from hibernate

---

### Post by iammuneeb on 2011-11-02
I'm facing one new issue after upgrading to 11.10 with kernel 3.0.0-12 (iirc, not on laptop right now).

The number of cpus suddenly drop to 1 at runtime, sometimes 3 and sometimes come to normal 8. This causes the cpu temperature to rise suddenly. 

Is anyone facing this problem? Any solutions to it?

PS: Before I was using 11.04 with old kernel 2.6.38-11 [/ 12]

---

### Post by designerferro on 2011-11-02
I've been waiting for a thread as good as Cucisian's with 11.10 upgrade to Asus to come up, but nothing came up yet.

---

### Post by Koppie on 2011-11-02
I want to add my experiences with 11.10 and the new 3.0 kernel.  In a word:

FANTASTIC.

Built-in support for function keys, trackpad, sleep, etc.  No more endless wait to wake up from sleep mode; it's as fast as you'd expect from an 8-core processor!

Still have the same problem with Optimus; that's NVidia's problem.  I hear they're working on Linux support for Optimus but it will be a while before we have a driver.  In the mean time I got 3D to work by disabling Nvidia altogether and using the onboard Intel graphics chipset.  (Remember, Bumblebee/Ironhide won't work with Unity 3D / Compiz.)

But I have it working the way I want and am super happy with the hardware support in 11.10.

---

### Post by qmater001 on 2011-11-03
> **Koppie said:**
> 

Still have the same problem with Optimus; that's NVidia's problem.  I hear they're working on Linux support for Optimus but it will be a while before we have a driver.  In the mean time I got 3D to work by disabling Nvidia altogether and using the onboard Intel graphics chipset.  (Remember, Bumblebee/Ironhide won't work with Unity 3D / Compiz.)

But I have it working the way I want and am super happy with the hardware support in 11.10.


how did you get the nvidia card disabled? and how many hours do you get on battery with the nvidia card disabled?

thanks

---

### Post by designerferro on 2011-11-03
Koppie, Im very interested two. Do you think we should start a new thread just for the 11.10 and keep this one clean?

---

### Post by designerferro on 2011-11-05
I've created a new [thread for the Asus k53sv Ubuntu 11.10]("http://ubuntuforums.org/showthread.php?t=1875982"). Logging my experience there. Hope it helps anyone.

---

