---
title: "No Sound"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by dkov on 2007-11-05
I installed Ubuntu 7.10 on my Gateway 4028GZ laptop with a clean hard drive. I don't get any sound. There is no obvious indication that anything is wrong but I get no sound from any application, through the internal speakers or the headphone jack. Any ideas?

---

### Post by Liberi on 2007-11-05
Welcome to Linux, I guess. I have similar problems, on a similar system (Gateway MT 3707). I still have no sound, but you may have better luck then I. Try this thread: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and see what happens.

---

### Post by chrisTGc on 2007-11-05
Hi,go onto System>Preferences>Sound and have a look at Default Mixer Tracks - Device and what does it say there ? ,

Chris.

---

### Post by HuddleHoop on 2007-11-05
I have the same problem but where do I find the "shell"

---

### Post by dkov on 2007-11-05
I'm not exactly sure what you're looking for so I'll try to be descriptive:

Under Device, I can choose from Intel 82801-DB-ICH4 (Alsa Mixer) or Analog Devices AD1981B (OSS Mixer).

I've made various selections under each, not knowing exactly what they do.

---

### Post by HuddleHoop on 2007-11-05
> **dkov said:**
> I'm not exactly sure what you're looking for so I'll try to be descriptive:

Under Device, I can choose from Intel 82801-DB-ICH4 (Alsa Mixer) or Analog Devices AD1981B (OSS Mixer).

I've made various selections under each, not knowing exactly what they do.

I think I tried all of them but no sound, I was following the other posts instructions but could not find where to pype in the shell command.

---

### Post by dkov on 2007-11-05
I think that's the terminal: Applications->Accessories->Terminal.

---

### Post by HuddleHoop on 2007-11-05
Thanks that was it but i got this message 

aplay: invalid option --1

with this 

aplay  -1

---

### Post by dkov on 2007-11-05
> **Liberi said:**
> Welcome to Linux, I guess. I have similar problems, on a similar system (Gateway MT 3707). I still have no sound, but you may have better luck then I. Try this thread: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and see what happens.

I tried that thread and I think I need the Intel ICH4 driver, which appears not to be available:
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel")

Bummer.

I'm trying to avoid any type of dual boot/VM arrangement if at all possible but not sure if I have any other options?

---

### Post by dkov on 2007-11-05
> **HuddleHoop said:**
> Thanks that was it but i got this message 

aplay: invalid option --1

with this 

aplay  -1

It should be a lower case L, not a one.

---

### Post by mali2297 on 2007-11-05
> **HuddleHoop said:**
> Thanks that was it but i got this message 

aplay: invalid option --1

with this 

aplay  -1

It should be a small case "L" not "one". Copy/paste:
```

aplay -l

```

---

### Post by Liberi on 2007-11-05
> **dkov said:**
> I tried that thread and I think I need the Intel ICH4 driver, which appears not to be available:
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel")

Bummer.

I'm trying to avoid any type of dual boot/VM arrangement if at all possible but not sure if I have any other options?

Not sure...I have an ATi that *should* work with Ubuntu and Alsa (SB450), but I'm yet to get it to. Makes things nice and interesting.

---

### Post by chrisTGc on 2007-11-05
> **HuddleHoop said:**
> I think I tried all of them but no sound, I was following the other posts instructions but could not find where to pype in the shell command.

In System>Preferences>Sound leave all fields as Auto-Detect except Device where i always choose ALSA which for me is C-Media PCI Alsa.Hit every test button except record,any sounds ? .

If no go onto Applications>Accessories>Terminal and type in alsamixer .Check for all fields should show green.

---

### Post by HuddleHoop on 2007-11-05
thanks I'm trying that now but the test takes so long](*,)](*,)

---

### Post by dkov on 2007-11-05
Is there someplace I can register a request to support my chipset?

Does anyone have any experience with a cheap USB sound card and Linux? I don't need anything fancy.

---

### Post by HuddleHoop on 2007-11-05
I also tried  "alsamixer" and the bars have 

4 white blocks

4 green blocks

and most have 

1 red block

but 1 has 2 

hope that makes sense to you.

---

### Post by HuddleHoop on 2007-11-05
the autodetect just goes on and on and on and on........

---

### Post by mali2297 on 2007-11-05
> **HuddleHoop said:**
> I also tried  "alsamixer" and the bars have 

4 white blocks

4 green blocks

and most have 

1 red block

but 1 has 2 

hope that makes sense to you.

Check that they're not muted, it should be 00 and not MM at the bottom. To toggle mute/unmute, press "m".

---

### Post by Pumalite on 2007-11-05
What about:

sudo lshw -C sound

---

### Post by HuddleHoop on 2007-11-05
here is what  "sudo lshw -C sound" returned


 *-multimedia:0          
       description: Multimedia controller
       product: SAA7133/SAA7135 Video Broadcast Decoder
       vendor: Philips Semiconductors
       physical id: 4
       bus info: pci@0000:02:04.0
       version: d1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=saa7134 latency=32 maxlatency=32 mingnt=84 module=saa7134
  *-multimedia:1
       description: Multimedia audio controller
       product: SB Audigy LS
       vendor: Creative Labs
       physical id: 5
       bus info: pci@0000:02:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=CA0106 latency=32 maxlatency=20 mingnt=2 module=snd_ca0106
106

---

### Post by Pumalite on 2007-11-05
What do you get when you type this in the Terminal:

alsamixer

---

### Post by HuddleHoop on 2007-11-05
> **HuddleHoop said:**
> I also tried  "alsamixer" and the bars have 

4 white blocks

4 green blocks

and most have 

1 red block

but 1 has 2 

hope that makes sense to you.

Hi I tried that one erlier

---

### Post by Pumalite on 2007-11-05
If you still have no sound, try this:

sudo apt-get install linux-backports-modules-generic

And reboot. Let's see.

---

### Post by chrisTGc on 2007-11-05
> **dkov said:**
> I'm not exactly sure what you're looking for so I'll try to be descriptive:

Under Device, I can choose from Intel 82801-DB-ICH4 (Alsa Mixer) or Analog Devices AD1981B (OSS Mixer).

I've made various selections under each, not knowing exactly what they do.

leave them all as auto detect except device field and on that go with whatever includes alsa.

Try google for;  launchpad bug #113644  ,there is a lot of info there and the fellah got his intel ich4/i810/i820 sound chip working ok.

best wishes chris.

---

### Post by HuddleHoop on 2007-11-05
> **Pumalite said:**
> If you still have no sound, try this:

sudo apt-get install linux-backports-modules-generic

And reboot. Let's see.

Ok I got this and I'm about to reboot

tom@tom-desktop:~$ sudo apt-get install linux-backports-modules-generic
[sudo] password for tom:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-backports-modules-2.6.22-14-generic
The following NEW packages will be installed
  linux-backports-modules-2.6.22-14-generic linux-backports-modules-generic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1386kB of archives.
After unpacking 5661kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main linux-backports-modules-2.6.22-14-generic 2.6.22-14.10 [1360kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main linux-backports-modules-generic 2.6.22.14.21 [25.4kB]
Fetched 1386kB in 3s (396kB/s)                                      
Selecting previously deselected package linux-backports-modules-2.6.22-14-generic.
(Reading database ... 89042 files and directories currently installed.)
Unpacking linux-backports-modules-2.6.22-14-generic (from .../linux-backports-modules-2.6.22-14-generic_2.6.22-14.10_i386.deb) ...
Selecting previously deselected package linux-backports-modules-generic.
Unpacking linux-backports-modules-generic (from .../linux-backports-modules-generic_2.6.22.14.21_i386.deb) ...
Setting up linux-backports-modules-2.6.22-14-generic (2.6.22-14.10) ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic

Setting up linux-backports-modules-generic (2.6.22.14.21) ...
tom@tom-desktop:~$

---

### Post by HuddleHoop on 2007-11-05
Hi again,

I've reboot but still no sound.:mad:

---

### Post by Pumalite on 2007-11-05
Here is a collection of links and tips for you to peruse. See if you find your answer here:

[http://ubuntuforums.org/showthread.php?t=569280](http://ubuntuforums.org/showthread.php?t=569280)
[http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound)
[http://ubuntuforums.org/showthread.p...ght=sound+will](http://ubuntuforums.org/showthread.p...ght=sound+will)
[http://ubuntuforums.org/showpost.php?p=3588321&postcount=5](http://ubuntuforums.org/showpost.php?p=3588321&postcount=5)
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide)

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://www.alsa-project.org/main/index.php/MainPage](http://www.alsa-project.org/main/index.php/MainPage)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)
From another user:

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

### Post by Dan Sabean on 2007-11-05
Thank you!
I have been SO frustrated with this issue since I dual-booted my Toshiba laptop (same sound card as mentioned in this thread SB450).  I upgraded to Gutsy on my IBM r50e with no trouble whatsoever, but when I did the fresh install of Gutsy on my good machine, I had a few issues.  The sound problem was the last on my list, and I have been fighting it for a week!

This is what finally worked for me:
sudo apt-get install linux-backports-modules-generic

Thanks again for helping me finish this!

:guitar:

---

### Post by HuddleHoop on 2007-11-05
Hi Guys,
thanks for all the help but alas I'm back with my Vista and listening to my favorite tunes, :guitar I will try ubuntu again some day but for now bye \\:D/\\:D/\\:D/

---

### Post by HuddleHoop on 2007-11-05
> **Dan Sabean said:**
> Thank you!
I have been SO frustrated with this issue since I dual-booted my Toshiba laptop (same sound card as mentioned in this thread SB450).  I upgraded to Gutsy on my IBM r50e with no trouble whatsoever, but when I did the fresh install of Gutsy on my good machine, I had a few issues.  The sound problem was the last on my list, and I have been fighting it for a week!

This is what finally worked for me:
sudo apt-get install linux-backports-modules-generic

Thanks again for helping me finish this!

:guitar:

I'm glad I could help :):):)

---

### Post by Pumalite on 2007-11-05
> **Dan Sabean said:**
> Thank you!
I have been SO frustrated with this issue since I dual-booted my Toshiba laptop (same sound card as mentioned in this thread SB450).  I upgraded to Gutsy on my IBM r50e with no trouble whatsoever, but when I did the fresh install of Gutsy on my good machine, I had a few issues.  The sound problem was the last on my list, and I have been fighting it for a week!

This is what finally worked for me:
sudo apt-get install linux-backports-modules-generic

Thanks again for helping me finish this!

:guitar:

You are welcome. Happy to hear I helped somebody!. Good luck.

---

