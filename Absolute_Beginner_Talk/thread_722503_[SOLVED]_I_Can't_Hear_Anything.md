---
title: "[SOLVED] I Can't Hear Anything"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by perito on 2008-03-12
I have an ubuntu 7.10 live cd and a kubuntu 7.04 live cd, when I put them in my Toshiba Satellite laptop I cant hear anything
i have windows vista already on it and the sound card there is realtek high definition audio

how can I make the sound work on ubuntu? 
i think ubuntu sees the sound card since aplay -l and lspci - give results....
please help

---

### Post by Tom--d on 2008-03-12
mm.. it should work (I had vista with my Toshiba laptop (gone now :))and it said I had realtek high.....audio) as sound worked out of the box for me.

Have you tried Restricted drivers?

---

### Post by perito on 2008-03-12
no... how do i do that?

---

### Post by mali2297 on 2008-03-12
Check that the sound isn't muted. Right-click on the speaker icon, by default at the right of the top desktop panel, and select Open Volume Control.

..**or**, open a terminal and type
```

alsamixer

```

---

### Post by perito on 2008-03-12
i just checked the restricted drivers ...
its not there
this is so weird... I've checked everything, its not muted and ubuntu sees my sound card... i think its a driver issue
how can I find the correct driver for my sound card?

---

### Post by Tom--d on 2008-03-12
Open up a termainal and type:

```
alsamixer
``` 
as mali2297 said and post here the out come. (copy the text shown, just text)

---

### Post by jdgiotta on 2008-03-12
Greetings
I have the same problem[HTML]
&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.14 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA ATI SB                                                             &#9474;
&#9474; Chip: Realtek ALC861                                                         &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master                                                                 &#9474;
&#9474;                                                                              &#9474;
&#9474;                       &#9484;&#9472;&#9472;&#9488;          &#9484;&#9472;&#9472;&#9488;                                     &#9474;
&#9474;                       &#9474;  &#9474;          &#9474;  &#9474;                                     &#9474;
&#9474;                       &#9474;  &#9474;          &#9474;  &#9474;                                     &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;                                     &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;                                     &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;                                     &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;                                     &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;                                     &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;                                     &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;                                     &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;                                     &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;                                     &#9474;
&#9474;         &#9484;&#9472;&#9472;&#9488;          &#9492;&#9472;&#9472;&#9496;          &#9500;&#9472;&#9472;&#9508;          &#9484;&#9472;&#9472;&#9488;          &#9484;&#9472;&#9472;&#9488;         &#9474;
&#9474;         &#9474;OO&#9474;                        &#9474;MM&#9474;          &#9474;OO&#9474;          &#9474;OO&#9474;         &#9474;
&#9474;         &#9492;&#9472;&#9472;&#9496;                        &#9492;&#9472;&#9472;&#9496;          &#9492;&#9472;&#9472;&#9496;          &#9492;&#9472;&#9472;&#9496;         &#9474;
&#9474;                      73<>73         0<>0                                     &#9474;
&#9474;      < Master >       PCM           Mic         Caller I      Off-hook       &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[/HTML]
Unfortunately, I can't get the Master Volume to level up.

---

### Post by Chemist on 2008-03-12
if you press m you should be able to unmute channels within the alsamixer

---

### Post by perito on 2008-03-13
heres the result
```

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.14 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488; 
&#9474; Card: HDA Intel                                                              &#9474; 
&#9474; Chip: Realtek ID 268                                                         &#9474; 
&#9474; View: [Playback] Capture  All                                                &#9474; 
&#9474; Item: Master [dB gain=0.00, 0.00]                                            &#9474; 
&#9474;                                                                              &#9474; 
&#9474;           &#9484;&#9472;&#9472;&#9488;             &#9484;&#9472;&#9472;&#9488;                                              &#9474; 
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474; 
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474; 
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474; 
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474; 
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474; 
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474; 
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474; 
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474; 
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474; 
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474; 
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474; 
&#9474;           &#9492;&#9472;&#9472;&#9496;             &#9492;&#9472;&#9472;&#9496;             &#9484;&#9472;&#9472;&#9488;             &#9484;&#9472;&#9472;&#9488;            &#9474; 
&#9474;                                             &#9474;MM&#9474;             &#9474;MM&#9474;            &#9474; 
&#9474;                                             &#9492;&#9472;&#9472;&#9496;             &#9492;&#9472;&#9472;&#9496;            &#9474; 
&#9474;         100<>100         100<>100                                            &#9474; 
&#9474;        < Master >          PCM            Caller I         Off-hook          &#9474; 
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;


```
Caller I and Off-hook are MM, when i click m, they turn to 00 but when i press Esc they return back to MM...
are they the problem? what should I do now?

---

### Post by perito on 2008-03-13
are caller I and Off-hook the problem or is it something else?

---

### Post by konungursvia on 2008-03-13
Are you using the Azalia soundcard? If so, search for my user name and the words "install backport" so you can install a quick backport of the ALSA that works with Azalia.

---

### Post by perito on 2008-03-13
as far as i know its 
realtek high definition audio
is there a command to check for my sound card...

---

### Post by konungursvia on 2008-03-13
Yes, the command is this:

```
lspci -v
```

I would try installing the backports, this solution works with a lot of soundcards, and only takes a minute. Type this in a terminal, let it download and install, then reboot:

sudo apt-get install linux-backports-modules-generic

---

### Post by perito on 2008-03-15
I cant get the back ports, Im getting
```

The following packages have unmet dependencies:
  linux-backports-modules-generic: Depends: linux-backports-modules-2.6.20-16-generic but it is not installable
E: Broken packages

```

What should I do?
I tried [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
but when I compile I get tons of errors telling me 
```

cp: cannot stat `snd-hpet.o': No such file or directory
cp: cannot stat `snd-page-alloc.o': No such file or directory
cp: cannot stat `snd-pcm.o': No such file or directory
cp: cannot stat `snd-timer.o': No such file or directory
cp: cannot stat `snd.o': No such file or directory

```

and so on...

Please, please help me... I really to make the sound thing work...

---

### Post by perito on 2008-03-15
where can i find a driver for my sound card?

---

### Post by perito on 2008-03-15
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
Im trying method A, which is 
sudo module-assistant update
but Im getting 
sudo: module-assistant: command not found

what does that mean? what should I do?

---

### Post by perito on 2008-03-15
Im getting Build of the package alsa-source failed!
and this
```

 &#9474; make[6]: *** [/usr/src/modules/alsa-driver/acore/hwdep.o] Error 1          &#9618; 
 &#9474; make[5]: *** [/usr/src/modules/alsa-driver/acore] Error 2                  &#9618; 
 &#9474; make[4]: *** [_module_/usr/src/modules/alsa-driver] Error 2                &#9618; 
 &#9474; make[3]: *** [modules] Error 2                                             &#9618; 
 &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'      &#9618; 
 &#9474; make[2]: *** [compile] Error 2                                             &#9618; 
 &#9474; make[2]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9618; 
 &#9474; make[1]: *** [build-stamp] Error 2                                         &#9618; 
 &#9474; make[1]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9646; 
 &#9474; make: *** [kdist_image] Error 2

```

what should i do?

---

### Post by mali2297 on 2008-03-15
> **perito said:**
> I cant get the back ports, Im getting
```

The following packages have unmet dependencies:
  linux-backports-modules-generic: Depends: linux-backports-modules-2.6.20-16-generic but it is not installable
E: Broken packages

```

What should I do?


* Open the package manager **Synaptic** and go to the menu **Settings -> Repositories**. 
* From there, enable the repositories *main, universe, multiverse, restricted and gutsy-backports*. 
* Click on the **Reload** button to make Synaptic aware of the new software repositories.
* **Search** for linux-backports-modules-generic and install it.

As I understand your first post, you run the Live CD. Whatever solution that we might find, it won't be permanent. It would be easier if Ubuntu were installed on the hard drive.

---

### Post by perito on 2008-03-15
The following packages have unmet dependencies:
  linux-backports-modules-generic: Depends: linux-backports-modules-2.6.20-16-generic but it is not installable
E: Broken packages


I installed Ubuntu 7.04 but I still have problems with this sound card

---

### Post by perito on 2008-03-15
and this also
```

Cannot find /lib/modules/2.6.22-14-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```
how to install  linux-ubuntu-modules-2.6.22-14-generic

---

### Post by perito on 2008-03-15
now i cant even remove the pakage
im getting this
```
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Cannot find /lib/modules/2.6.22-14-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by mali2297 on 2008-03-15
So, you've got 7.04 installed now? Post the output of
```

uname -a
lspci | grep [Aa]udio
aplay -l
cat /proc/asound/modules

```

It's bedtime for me. If this problem still is not resolved tomorrow, I will help you.

---

### Post by perito on 2008-03-16
```

ubuntu@ubuntu-laptop:~$ uname -a
Linux ubuntu-laptop 2.6.20-16-generic #2 SMP Tue Feb 12 05:41:34 UTC 2008 i686 GNU/Linux
ubuntu@ubuntu-laptop:~$ lspci | grep [Aa]udio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
ubuntu@ubuntu-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ubuntu@ubuntu-laptop:~$ cat /proc/asound/modules
 0 snd_hda_intel
ubuntu@ubuntu-laptop:~$ 

```

---

### Post by perito on 2008-03-16
problem solved ... thx all
for ppl with same problem, check this
[http://ubuntuforums.org/showthread.php?t=725427](http://ubuntuforums.org/showthread.php?t=725427)

---

### Post by mali2297 on 2008-03-16
> **perito said:**
> problem solved ... thx all
for ppl with same problem, check this
[http://ubuntuforums.org/showthread.php?t=725427](http://ubuntuforums.org/showthread.php?t=725427)

Congratulations. :)
Mark the threads as solved.

---

