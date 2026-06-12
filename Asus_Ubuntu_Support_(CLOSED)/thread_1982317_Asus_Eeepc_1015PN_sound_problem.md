---
title: "Asus Eeepc 1015PN_sound problem"
date: 2012-05-18
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Thatoo on 2012-05-18
Hello,  

I'm here because mtron ask me to expose my problem to the comunity.
First, I want to thank him for what he wrote here, [http://sites.google.com/site/mtrons/howtos/eeepc-1015pn](http://sites.google.com/site/mtrons/howtos/eeepc-1015pn) , it's really helpful. I have an Asus Eeepc 1015PN.

Everything was working very well on ubuntu 11.10. Now I updated to precise, pretty much everything work but I have a little problem with the sound. It works when I use any software but the system say that "the peripherique intel hda 269BV doesn't work". So I can't use the general ubuntu volume (the system volume) and obvioulsy, the sound keyboard shortcuts don't work neither. 
I can show you how appear the sound system :
[[IMG]http://data.imagup.com/12/1152011717.png[/IMG]]("http://www.imagup.com/data/1152011717.html")

I tried to change things in here, /etc/modprobe.d/alsa-base.conf , but I don't manage to change anything so I let "options snd-hda-intel model=asus" at the end.

I tried a live usb and in fact, everything is working fine. I don't know what I misconfigured when I updated from 11.10 to 12.04...

mtron ask me to attach these result to my message : 

yogo@Yogo-ordi:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
yogo@Yogo-ordi:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf7cf8000 irq 45
yogo@Yogo-ordi:~$ lspci -v -k -s 00:1b.0
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 841c
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f7cf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

And I ran the alsa-info.sh script [1] (the bash script is attached) but I don't know how provide the log output it created. I have that on my screen : 

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See '/home/yogo/Téléchargements/alsa-info.sh --help' for command line options.

Home directory /home/yogo not ours.
Automatically upload ALSA information to [www.alsa-project.org?]("http://www.alsa-project.org?") [y/N] : 

if I say y, I feel it's uploading something to the alsa website but if I san N, nothing happen and in both case, I don't know where is the log file.

img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

### Post by mtron on 2012-05-19
hello! 

> Home directory /home/yogo not ours. Did you run the script as root? 

The debug output should be in the folder /tmp. Have a look there. 

Did you add any manaual alsa parameters to $HOME/.asoundrc?, also post the /etc/default/alsa file. 

can you share your pulseaudio config please?

/etc/default/pulseaudio
/etc/pulse/client.conf
/etc/pulse/default.pa
/etc/pulse/system.pa

When we get those files (and the output of the sysinfo script) we can hopefully help ypu to fix this upgrade problem.

Cheers!

---

### Post by Thatoo on 2012-05-19
I manage to run the script with sudo. The command was sh...
here it is : 
yogo@Yogo-ordi:~/Téléchargements$ sudo sh alsa-info.sh
alsa-info.sh: 373: alsa-info.sh: [[: not found
ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

alsa-info.sh: 395: alsa-info.sh: [[: not found
alsa-info.sh: 407: alsa-info.sh: [[: not found
alsa-info.sh: 448: alsa-info.sh: [[: not found
alsa-info.sh: 501: alsa-info.sh: [[: not found
alsa-info.sh: 508: alsa-info.sh: [[: not found
alsa-info.sh: 515: alsa-info.sh: [[: not found
alsa-info.sh: 522: alsa-info.sh: [[: not found
alsa-info.sh: 529: alsa-info.sh: [[: not found
pcilib: sysfs_read_vpd: read failed: Connection timed out
alsa-info.sh: 618: alsa-info.sh: [[: not found
alsa-info.sh: 628: alsa-info.sh: [[: not found
alsa-info.sh: 759: alsa-info.sh: [[: not found
Automatically upload ALSA information to [www.alsa-project.org?]("http://www.alsa-project.org?") [y/N] : alsa-info.sh: 769: read: Illegal option -e
alsa-info.sh: 786: alsa-info.sh: [[: not found

alsa-info.sh: 796: alsa-info.sh: [[: not found

Your ALSA information is in /tmp/alsa-info.txt.jVrRJoAmpa


I attach the log that I found in /tmp, it's name is alsa-info.txt.jVrRJoAmpa in the Thatoo Files.tar.gz file.

No, I didn't add anything there $HOME/.asoundrc .

I attach the /etc/default/alsa file in the Thatoo Files.tar.gz file.

And I share also my pulseaudio config in the Thatoo Files.tar.gz file attached.img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

### Post by Thatoo on 2012-05-24
In fact, I don't have this file  $HOME/.asoundrc . 
I'm sure I've never modified it so I didn't check last time.
To be sure, I've just verified this morning and I have the surprise that I don't even have this file... is it normal?
not  /home/.asoundrc
not  /home/yogo/.asoundrc  (yogo is my user name on this computer.)
img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

### Post by mtron on 2012-05-24
hm, so let's see if the config problem is user generated.

Create a new user account and see if sound works there. If so, it's most likely a pulse misconfiguration so remove the ~/.pulse folder in your home directory and re-login.

If the new user has also no sound the problem is somewhere deeper in the alsa configuration (although the alsa-info output you posted looked ok to me..)

Can you post the 'dmesg" output after a fresh boot and provide the /var/log/syslog please?

---

### Post by Thatoo on 2012-05-24
You're right, it's a problem with my user account because I try a new one and the invited session and both work.

However, I try to put .pulse folder and even .pulse-cookie file in the bin, I didn't empty it but still they are in the bin and I restart session and then computer and nothing change for me.
Do I restore it or do I totally delete it?

Here are the file you asked me.

Thank you for your help, I feel we are in progress and I'm happy.

 
img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

### Post by Thatoo on 2012-06-05
So, should I erase definitely put .pulse folder and even .pulse-cookie file? They are in the bin but I keep the bin full until you tell me what I have to do.
I don't have new one in my home folder when I restart the computer and the problem is not solved.

Cheers,
img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

### Post by mtron on 2012-06-06
Hello! 

Your syslog shows many pulseaudio errors like this:
```
[pulseaudio] main.c: Failed to acquire autospawn lock
```

try 'pulseaudio -k' to kill it, then restart it so that it runs in the foreground with 'pulseaudio' (from the terminal) and post the startup messages.

Google suggests that this might be a permissions error, so if you get
> E: core-util.c: Home directory /home/username not ours. have a look [here]("http://ubuntuforums.org/showthread.php?p=6208727") for possible fixes.

---

### Post by Thatoo on 2012-06-07
yogo@Yogo-ordi:~$ pulseaudio -k
E: [pulseaudio] core-util.c: Home directory /home/yogo not ours.
E: [pulseaudio] main.c: Impossible de tuer le démon : Permission non accordée
yogo@Yogo-ordi:~$

so I'm going to try for the permission error and I will tell you what I manage to do.
Can I empty my bin and definitely delete the two files? 
img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

### Post by Thatoo on 2012-06-07
so after a 'sudo chown yogo /home/yogo' I have

yogo@Yogo-ordi:~$ pulseaudio -k
yogo@Yogo-ordi:~$ pulseaudio
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: Échec de pa_pid_file_create().
yogo@Yogo-ordi:~$ 

I will restart the computer and tell you if it's working.
img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

### Post by Thatoo on 2012-06-07
Thank you so much for your help.
It's working very well now!

:P:P:P:P:P:Pimg, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

