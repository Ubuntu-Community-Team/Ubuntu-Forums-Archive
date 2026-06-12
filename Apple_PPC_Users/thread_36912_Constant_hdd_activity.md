---
title: "Constant hdd activity ?"
date: 2005-05-25
forum: Apple PPC Users
---

### Post by karl_kashofer on 2005-05-25
Hi !

Running Ubuntu 5.04 on a Powerbook Pismo with a 4 Gig Toshiba harddrive.

Problem is: The harddisk is constantly active. It seems very similar to the problem in this post: [http://www.ubuntuforums.org/showthread.php?t=5617](http://www.ubuntuforums.org/showthread.php?t=5617)

Every three or so seconds I get a scratching sound from the hdd. 
I have had disks die on me before, so I know the sound a bad hdd makes, this one is different though. I have also replaced the disk with another 4Gb disk, and it does the same thing.
I tried to put the hd to sleep with "hdparm -y /dev/hda" which works nicely, the drive spins down and silence commences. However, after 3 seconds the disk powers up again and makes this awful noise again.
The noise does not happen if I wait at the Yaboot screen, so its definitely something in Ubuntu.
I have killed all userland processes including all the logging to no avail. 
I tried the suggestion about acoustic management from the aforementioned thread, but apparently the drive does not support this as it just throws up an error.

This noise is not only annoying, it also prevents the hd from ever spinning down. 

Anyone having a similar experience ? 
Ideas ?

Thanks,
Karl

---

### Post by Kamping_Kaiser on 2005-05-25
I have only seen things like that when a system has its swap partition thrashing. Do you have enough swap? And does running top or a simmilar command give any hint as to whats using the hdd/swap/other?

---

### Post by karl_kashofer on 2005-05-25
Hi !

I dont think its swap, the sound is different than acutal hd access, i.e. if I load an application.

Anyway here is my top:
top - 13:08:15 up 10:59,  3 users,  load average: 0.67, 1.17, 1.00
Tasks: 106 total,   2 running, 103 sleeping,   0 stopped,   1 zombie
Cpu(s):  7.8% us,  1.6% sy,  0.0% ni, 87.0% id,  2.9% wa,  0.7% hi,  0.0% si
Mem:    256128k total,   231464k used,    24664k free,     3608k buffers
Swap:   211348k total,      572k used,   210776k free,    70896k cached

I disabled swap with swapoff, no change.

Its very weird.
Any other pointers ?
Thanks,
Karl

---

### Post by karl_kashofer on 2005-05-25
Hi again !

I have made a short recording of the sound, maybe this rings a bell with someone:
[http://www.kashofer.dyndns.org/weird_sound.ogg](http://www.kashofer.dyndns.org/weird_sound.ogg)  (500kb)

The computer was idle at that time, just sitting there recording to RAM.

Its the loud sound in the foreground, the background noise is another computer.

Hope this helps,
Thanks,
Karl

---

### Post by skoal on 2005-05-25
I killed the "dbus-1" service along time ago and never looked back.  If you use Gnome, you'll lose some functionality but your hard drive will be quiet.  You'll get some dbus error at startup of Gnome.  I use XFCE anyways.

My drive was accessed every 2-3 seconds before, and now it's quieter than a mouse on tippie-toes.  There were several other services I've killed since migrating to Ubuntu, all in an effort to keep my drive from spinning all the time. In case you're interested, here's my (custom) runlevel 5:

skoal@morpheus:///etc $ ls rc5.d/
K11anacron   S12alsa    S20apmd        S20rsync         S99stop-bootlogd
S05vbesave   S13gdm     S20inetd       S89atd
S10sysklogd  S19cupsys  S20makedev     S99acpi-support
S11klogd     S20acpid   S20nvidia-glx  S99rmnologin

---

### Post by karl_kashofer on 2005-05-25
Hi !

I tried killing nearly all processes but that did not help.
Even if I boot into the failsafe terminal I still get the noise.

Its not there booting from live-cd or at the yaboot prompt, so its definitely something in ubuntu.

I will maybe repost my question in one of the general support forums, just to get a bigger audience.

Cheers,
karl

---

### Post by Rxke on 2005-05-25
Have the same thing on a Clamshell iBook...

it is weird, because if I run it on batteries, no... rather let it startup under battery power, the disk goes to sleep after awhile (depending on what i'm doing of course...)
so this 'scrape/click' sound isn't really "neccesary"? (sorry for primitive Engrish, I'm tired)

could it have to be something to do with the fact that on batt. startup it does not do fscking?

---

### Post by Rxke on 2005-05-25
Hmmm instead of hdparm -y /dev/hda I tried hdparm -Y /dev/hda (sleep instead of standby mode...)

And the disk spun down, and is still down... after minutes!
BTW, I'm using it currently as a glorified router for the B&W I'm typing this on. (Clamshell's screen is broken, B&W hasn't got wireless...)
Ans still, despite network activity etc, the drive doesn't spin up. grrrreat!

Of course, putting yr disk to sleep isn't a solution...

(EDIT) Turns out this makes your system errrr... VERY unresponsive, heh.
Not recommended.... Be warned.

---

### Post by karl_kashofer on 2005-05-25
Ha !

I did hdparm -Y as well, which spun down the disk, but then I could not wake the disk up again ! It would not start spinning any more.

I had to hard-reset :)

Could you get it running again ?

Cheers,
Karl

---

### Post by Rxke on 2005-05-25
Heh. You answered when I was editing my post.

Guess what... I belatedly discovered the same thing, yay!

strange... totally unresponsive, tried hdparm -y after that, and now everything kinda hangs... xcept it's still routing fine, I can switch desktops, but that's about it.
(can type in cli, but don't get a prompt, and too newbie to get out of it, I think...)

---

### Post by karl_kashofer on 2005-05-25
Ah I see, similar experience...

So what happend to your Clamshell ? Did you find out what the problem was ?

I dont know what to do, this sound is so annoying, but as it does not seem to be a problem with the hd I am reluctant to buy a new one.

Cheers,
Karl

---

### Post by Rxke on 2005-05-25
'cool' 
now everything looks to be jammed... no mouse, a weird screen, with a scrollbar , just sitting there...
still routing though :D

and since this clamshell has a *Very* loud HD, (people actually think it's a ventilator, and a rather loud one, at that...) I don't mind for the moment, heh. Enjoying the silence.

*what's that smell? Something's on fire? ;)  )

---

### Post by Rxke on 2005-05-25
I guess I'll have to do a reboot eventually... totally unresponsive now...

---

### Post by karl_kashofer on 2005-06-03
Got this one solved, read here: 

[http://www.ubuntuforums.org/showthread.php?t=36976](http://www.ubuntuforums.org/showthread.php?t=36976)

Cheers,
Karl

---

