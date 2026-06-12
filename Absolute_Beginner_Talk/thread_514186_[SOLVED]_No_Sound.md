---
title: "[SOLVED] No Sound"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by definedglory on 2007-07-31
When I started up Ubuntu it didn't make the start up noise that it usually does but I didn't really think anything of it. Well when I went to Amarok to play some music no sound came out. I checked my volume and it was all the way up in the volume controls. 

Also when I closed Amarok it said something about KNotify and something that crashed on the previous start-up what should I do. 

I don't know if this is an issue but I am running a dual-boot system with Windows and Ubuntu through Wubi.

---

### Post by atomkarinca on 2007-07-31
when you type alsamixer in the terminal can you see the equalizer? if yes, is the master volume all the way up?

---

### Post by definedglory on 2007-07-31
Yes. Master is at 100.

---

### Post by shagster_ on 2007-07-31
post your output of 
```
lspci
```
i ran into this same issue because i had onboard audio and also a SB live card, the onboard audio was being defaulted on....

have you referenced this?
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by definedglory on 2007-07-31
Yes I refrenced that post, but I'm running into problems when I get to:

 > (3) Check to see if the ALSA driver for your sound card exists. Go to [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) and search for your sound card (chipset) manufacturer in the dropdown box. You'll be given a matrix of the sound cards made by the manufacturer. Try to match the chipset you found in step 2 with the driver(green hyperlink text).

    * Success - You will have found the driver for your soundcard's chipset.

    *
      Failure - You will have not found the driver for your soundcard chipset. (at the moment I cannot help you, but stay tuned!)

(4) Now go back to the shell and type
Code:

sudo modprobe snd-

Now, press the TAB key BEFORE pressing the ENTER key to see a list of modules. Try to find the module that matches the driver you found in step 3.


For example, my driver is a via82xx so I would type, sudo modprobe snd-via82xx.

    *
      Success
          o
            A success here means that your soundcard was installed, but it was not being loaded. Now you have loaded it for the current session.
          o
            To load it for all sessions (you will probably want to do this) you will have to edit /etc/modules (I think this is the file, I'll check once I get to my Dapper PC).
          o
            Type this into the shell
            Code:

             sudo nano /etc/modules

          o
            Add only the name of the module to be loaded at the end of the file. In my case, the via82xx module gave me sound so I added "snd-via82xx" to the end of the file.(iii) Make sure that you have all channels unmuted in alsamixer
          o
            See the alsamixer section
          o
            Play media using your favorite media player. Set your audio engine to alsa. In some cases, you have to configure your audio engine within another (media engine) like in Kaffiene in Kubuntu. If you hear sound, hurray!
          o
            One final step. Go onto Saving Sound Settings

EDIT: I went through the above steps and nothing ended up happening.

---

### Post by shagster_ on 2007-07-31
i really wish i had my terminal in front of me because i have a couple bookmarks of what helped me resolve my issue....but i think it was along these lines..
1) figure out if my sound card was recognized by the kernel (it was listed in 'lspci')
2) find the module that represented my sound card (SB live was snd-emu01k1)
3) then checked a file like /etc/modules to make sure it was loaded when i powered up
4) then there was a command that would list the order sound cards were loaded, and in that command you can tell it which to load first - i had to choose my SB live card over the onboard audio

---

### Post by definedglory on 2007-07-31
Ok it is not loaded here it was it look like
> 
  GNU nano 2.0.2             File: /etc/modules                       Modified  

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
fuse


Now what?

EDIT: By the way, I don't know if it means anything but the sound does work when I use Windows.

---

### Post by definedglory on 2007-07-31
Ok the sound is fixed I had to use the commands:


sudo dpkg-reconfigure alsa-base 

sudo dpkg-reconfigure linux-sound-base

Thanks for all the help.

---

### Post by TKR101010 on 2007-08-02
> **definedglory said:**
> sudo dpkg-reconfigure alsa-base 

sudo dpkg-reconfigure linux-sound-base

Thank you so much. That worked for me too :)

---

