---
title: "no sound"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by natehatewindows on 2007-10-22
I have no sound. When i look into the device manager it has my intel HDA card listed, it says 82801G (ICH7 family) HDA controller....i think thats my card. I have no idea on where to start with this because i tried using dapper before i switched to gusty...hoping for your help. :) 

thanks in advance for everything, you guys are always a huge help!

have nice day!!

oh and FYI its in a toshiba satellite p-105

---

### Post by runemaste644 on 2007-10-22
well, look in volume control and see if anything is muted. If anything is muted (especially PCM) unmute it and see if you get any sound.

---

### Post by natehatewindows on 2007-10-23
> **runemaste644 said:**
> well, look in volume control and see if anything is muted. If anything is muted (especially PCM) unmute it and see if you get any sound.

ok i looked in volume control and nothing was muted. It has the option of two sound devices:
1. HDA Intel (alsa mixer)
2. conexant CX20549 (venice) (OSS mixer).....

i have searched the forums and have not found to much about this card in gusty.....so help would be amazing!!

thanks for everything!!

good day!

---

### Post by coreyelledge on 2007-10-23
I just had the same problem.  I simple restarted and the problem was fixed.  I know this isn't really the answer to why it happened, but it worked for now.  Whenever I opened a .mp3 with Rhythmbox Music Player it displayed an error about gstreamer.  Hope this helps!

---

### Post by natehatewindows on 2007-10-23
> **coreyelledge said:**
> I just had the same problem.  I simple restarted and the problem was fixed.  I know this isn't really the answer to why it happened, but it worked for now.  Whenever I opened a .mp3 with Rhythmbox Music Player it displayed an error about gstreamer.  Hope this helps!

yeah i have never had sound, a reboot wont help..... :)

no system sounds, no music....nothing at all.

---

### Post by Skweek on 2007-10-23
Try this;

sudo apt-get install linux-backports-modules-generic

Reboot.

---

### Post by natehatewindows on 2007-10-23
did it and it says:

[sudo] password for home:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-generic
home@home-laptop:~$ 

I just got my modem working but it seems i can use and update, apt-get or install any plugins.....its like ubuntu does not see i have a connection. im using gnome-ppp and the whole time im nline its says "dialing 547000......"

---

### Post by Skweek on 2007-10-23
I'm afraid I can't help you with your connection problem.  

Anyone else?

---

### Post by hyper7 on 2007-10-23
what's odd is that this actually worked for me for about .5 seconds before my system completely froze and I had to hard break.

anyway, upon reboot, i'm right back where i was.

thanks for the suggestion.  i'll make due for the time being while these network/sound issues get solved.

---

### Post by danjwray on 2007-10-23
> **Skweek said:**
> Try this;

sudo apt-get install linux-backports-modules-generic

Reboot.

oh my god i think i love you Skweek! I've had no sound on my Toshiba Satellite u300-113 in both gutsy and feisty for the last month and a half! that's done it! I tried everything else! thank you!

---

### Post by natehatewindows on 2007-10-28
> **Skweek said:**
> Try this;

sudo apt-get install linux-backports-modules-generic

Reboot.

ok i got my connection figured out and tied this.....no luck. but when i do it my conexant modem wil not work either so i uninstalled the backports, when the backports are installed and i try to use kppp it just says "modem busy". Im not really sure where to start now so any help would be great.
below is the command "cat /proc/asound/cards" so you can see the info....thanks for all the help in advance! :) hope you are all having a good weekend!

home@home-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd0340000 irq 22

---

### Post by art.by.bec.com on 2007-10-29
Hi All,
I have just worked out how to boot ubuntu on to my computer and am exploring what it is about ... and am getting more boggled by the second. However I am dedicated to get my lame grey matter around it. I refuse to keep paying for crap microsoft.
I am not getting it at all though!

I have a Toshiba Satellite U300, it has an integrated webcam and a sound card??? but i cant get them to work on ubuntu and have no idea what to do. Please if any one know the next step (in baby talk) i'd appreciate it

Much anticipation
bec

---

### Post by gene6482 on 2007-10-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				there is a bug in gutsy which prevents the sound from working.  Hopefully it's fixed soon.

---

### Post by natehatewindows on 2007-10-30
ok cool....now i have a quesiton...

Its says if i boot with acpi off it might work....what does acpi do and how can i try to boot without it?

thanks! :)

---

### Post by art.by.bec.com on 2007-11-01
HI
I may be wasting everyone's time posting this as i am an absolute beginner with linux, but i think i have found a strange occurrence...
I have had NO sound on my Toshiba lap with feisty and then went to Gutsy... I downloaded a kids program GCompris V8.3.2
I went to look at it and heard my first sounds!!
Still doesn't work for anything else but it might be a clue to how to get things to work... or i might be absolutely stupid and not understand why this is happening

---

### Post by Pumalite on 2007-11-01
Here are a few links and tips that might help (not sure):
[http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound)
[http://ubuntuforums.org/showthread.p...ght=sound+will](http://ubuntuforums.org/showthread.p...ght=sound+will)
[http://ubuntuforums.org/showpost.php?p=3588321&postcount=5](http://ubuntuforums.org/showpost.php?p=3588321&postcount=5)
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide)

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://www.alsa-project.org/main/index.php/MainPage](http://www.alsa-project.org/main/index.php/MainPage)
If it doesn't work go to [http://www.alsa-project.org/main/index.php/MainPage](http://www.alsa-project.org/main/index.php/MainPage), download the
alsa-driver, lib and utils and follow the Howto at the same address and look for your driver at the Sound card matrix. Then, if needed, apply the patch and add something at the end of /etc/modprobe.d/alsa-base (sudo gedit) at described in the previous link. I do not own the same laptop but I also have got a Intel Sound Card and worked a bit to have a functioning audio.
I hope it will help you

After fiddling with the sound settings trying various suggestions in the Comprehensive Sound Problem Solutions Guide thread, I totally buggered up my sound. Oh well, a fresh install of Feisty never hurt anyone and I had my /home directory on a separate partition.

After the new install, I still had the 6 symptoms described above.

Thinking that it might be some sort of .config file remnant, I created a new user and everythng worked properly. A-HA! Comparing the user home directories, I noticed the presence of a .asoundrc file and another similarly named file. After doing some research here about what the file is for (and it's safe removal), I deleted it, logged out and returned to a system with full working sound.

My suggestion is this:

1. Create a new user account
2. Login using new user account
3. Check to see if sound works properly
4. If it does, then the issue is likely some sort of config file. Look for the .asoundrc file in your original home directory and move it to a backup folder (just in case)
5. Log back in as your original user and test.
6. If it fails to cure the problem, try the Comprehensive Guide above.

---

### Post by ferdostar on 2007-11-01
Look if you had GStreamer installed

---

### Post by natehatewindows on 2007-11-03
ok i tried  the user thing and it id not work so im right where i was before. When i boot alsa=off sound work perfect but since the is a laptop i need acpi for battery stuff and all. Also i tired booting aspi_osi=! Linux but still have not sound. When i boot acpi=off another interesting thing happens, i know many of use with toshibas are getting a strange error message when we boot saying something like "cannot allocated resources region 7...8...9 blah blah blah" and on each line it says something about PCI. Well anyways when i boot acpi=off this message is not present. 
I do have GStreamer0.10 installed on this machine. If any of you are have a similar problem and using Nvidia graphics cards pay attention to your temps, this issue is also effecting your fans!

see this to know more about problems with toshibas and gusty: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)

thanks for all the tips!

---

### Post by natehatewindows on 2007-11-03
> **art.by.bec.com said:**
> HI
I may be wasting everyone's time posting this as i am an absolute beginner with linux, but i think i have found a strange occurrence...
I have had NO sound on my Toshiba lap with feisty and then went to Gutsy... I downloaded a kids program GCompris V8.3.2
I went to look at it and heard my first sounds!!
Still doesn't work for anything else but it might be a clue to how to get things to work... or i might be absolutely stupid and not understand why this is happening

dude that sounds pretty crazy to me but im going to install it just to see if it works. What model of toshiba do you have....bios version? maye lspci info?

thanks! :)

---

### Post by natehatewindows on 2007-11-07
ok so i think there is a fix now to this bug, i posted the link a few posts above this one. But i cant figure out how to do it and its been a few days and no one has psted a how to.....if anyone know what they are talking about and could take me through it i would be very thankful. I would lke to keep 2.6.22.14 so i can keep my modem working (linuxant driver).

Thanks!

---

### Post by seatowngrrl on 2007-11-12
> **danjwray said:**
> oh my god i think i love you Skweek! I've had no sound on my Toshiba Satellite u300-113 in both gutsy and feisty for the last month and a half! that's done it! I tried everything else! thank you!

I would like to second danjwary's love of Sweek!  I don't know how I missed this thread, but I have been searching and searching around the interweb for a way to get sound on my machine.  I am so happy, now I can fully use this wonderful new computer of mine.  No more computing in the quiet!  

Thank you again!!!!!

---

### Post by art.by.bec.com on 2007-12-01
YEAAAAAAAAAAAAAAHHHHHHHHHHH!
I have sound now too! Thank you!
However... the internal cam, memory card slot and mic doesnt work!!!
Not sure if i am bright enough for linnux!!!
bec
:lolflag:

---

### Post by HappyEisentrout on 2007-12-01
My sound card is now recognized but it only comes out as static, any ideas?

---

