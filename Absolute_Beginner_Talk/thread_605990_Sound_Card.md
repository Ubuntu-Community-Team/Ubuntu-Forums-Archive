---
title: "Sound Card"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by ikerbera on 2007-11-07
I had some problems with my laptop's sound card which I tried to solve with all the information avalaible in Internet but nothing worked. So I give up and I want to ask if [[COLOR="RoyalBlue"]this[/COLOR]](http://www.icemat.com/products/icematsiberia/icemat_siberia_usb_soundcard_)  external sound card will work with ubuntu.
Thank you.

---

### Post by ukripper on 2007-11-07
Can you give some details of your current soundcard.

---

### Post by Pumalite on 2007-11-07
Post:

sudo lshw -C sound

---

### Post by Daveth on 2007-11-07
I concur- you would seem to be in a better position getting your existing souncard working- that Icemat has practically no linux presence on the web that I could find. It might work, but then again might not. I don't want you to waste you money.

---

### Post by ikerbera on 2007-11-08
> **Pumalite said:**
> Post:

sudo lshw -C sound

Well, now I'm at work so I can't post commands. As soon as I get home I will post everything you ask me.
As a preview I can tell that the sound card is an *Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)*. I've searched for solutions but nothing worked and a friend of mine have the same sound card but (rev 02) and ubuntu automatically detects it without a problem.
Thank you for your help.

---

### Post by ukripper on 2007-11-08
There is a bug been reported on launchpad relating to this soundcard.
 
check here - [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/130559](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/130559)

---

### Post by ukripper on 2007-11-08
looks like someone resolved this issue on launchpad using realtek drivers -


 "[I]Dario F wrote on 2007-10-09: (permalink)

Guys, same card, I solved everything by installing realtek's audio drivers ( [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false) ), using latest alsa release instead of the one shipped with realtek's package. hope this helps.
[/I]"

---

### Post by ikerbera on 2007-11-08
Well, I tried installing the realtek drivers and nothing. I tried again the backport stuff (for third time) and nothing.

> **Pumalite said:**
> Post:

sudo lshw -C sound

```
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```

that's what the command sows

---

### Post by Pumalite on 2007-11-08
Your card is recognized and the kernel loads the module. Try this link:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

(make sure you have all the Gstreamers installed)
(what shows up if you type: 'alsamixer' in your terminal?)

---

### Post by ikerbera on 2007-11-08
Instaling alsa again worked like charm. I tried this again without result, but now I downloaded the 1.0.15 version and it's working perfectly.
Thank you very much.

---

### Post by atlascomplete on 2007-11-08
I'll tag this thread so I can try it on my HP laptop when I get home.

---

### Post by Pumalite on 2007-11-08
> **ikerbera said:**
> Instaling alsa again worked like charm. I tried this again without result, but now I downloaded the 1.0.15 version and it's working perfectly.
Thank you very much.

You are welcome. Good luck.

---

### Post by ukripper on 2007-11-09
Great!

---

### Post by arkone on 2007-11-10
Hi all.I'm italian boy. I've a solution for audio on a f3sa laptop. After 2 week and so many procedures with insuccess(including wiki's ubuntu and all that i've found over the google). 
First install the latest version of Alsa 1.0.15 final. 
After, you create a file in /etc/modutils called, for example, 'alsa' with this sequence of aliases and options:

alias char-major-116 snd
alias snd-card-0 snd-hda-intel
# module options should go here
options snd-hda-intel model=lenovo
     
# OSS/Free 
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0
       
# card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
 
The most important is the line:
options snd-hda-intel model=lenovo

For a secure success, add the line above in the file /etc/modprobe.d/alsa-base too
 If it doesn't exixt, create! 

After you must restart. Before you start to dancing, run 'alsamixer' and unmute all channel and set the volume.

I hope that this 'tweak' is good for you. Ehm.. sorry for my english.
Bye.

---

### Post by Markus72 on 2007-11-27
Hello Arkone,

don't mind about your English! You just saved my life :)

Feel honoured that according to my searches you are the first and only guy who provides a straight-forward method to get this stuff running on an ASUS F3Sa!!

Thanks a lot
Markus

PS: I added your solution to the Ubuntu Wiki: [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by potatu on 2007-11-28
I have an ASUS F3Jp, thinking of giving this a go. However, noob that I am, when installing alsa 1.0.15, do I have to remove the old version first? This is not mentioned in the guide you linked to in the Wiki, markus.

---

### Post by Markus72 on 2007-11-28
Hi potatu,

good question. Lazy as I am I just installed the new one without uninstalling the other.
For me, it works fine. But the packet manager tells me that 1.0.14 is still installed, whereas the command line version always tells 1.0.15.

I don't know exactly about all dependencies of alsa but I could imagine that uninstalling the alsa 1.0.14 could cause more uninstallations than wanted...

As soon as noone else objects, I would say: just install it an leave the old one where it is. :)

Markus

---

### Post by potatu on 2007-11-28
Allrigt, gave it a go, seemed to install nicely, but as I rebooted the last time, I can't seem to make it work. As I try to open the volume control I get this message:

No volume control GStreamer plugins and/or devices found.

Tried running alsamixer as well, that gave me this message:

alsamixer: function snd_ctl_open failed for default: No such device

As I said, noob-alert. How can I make it find my card?

EDIT: Turns out my user priviliges also disappeared. Read in a few threads that this could probably account for the error messages -  my user did not have access to the sound card. Had to boot in recovery-mode and add my username to adm & admin, now the priviliges are back (along with my administration menu) but I get the same error with the volume control. It seems it actually doesn't find my card. I've added all priviliges.

Any ideas?

---

### Post by amis on 2007-12-10
> **potatu said:**
> Allrigt, gave it a go, seemed to install nicely, but as I rebooted the last time, I can't seem to make it work. As I try to open the volume control I get this message:

No volume control GStreamer plugins and/or devices found.

Tried running alsamixer as well, that gave me this message:

alsamixer: function snd_ctl_open failed for default: No such device

As I said, noob-alert. How can I make it find my card?

EDIT: Turns out my user priviliges also disappeared. Read in a few threads that this could probably account for the error messages -  my user did not have access to the sound card. Had to boot in recovery-mode and add my username to adm & admin, now the priviliges are back (along with my administration menu) but I get the same error with the volume control. It seems it actually doesn't find my card. I've added all priviliges.

Any ideas?

I'm experiencing the same problem. Anyone has ideas? I'm also a noob on Linux... :\

Thanks, 
André

---

### Post by jimwmiller on 2007-12-18
Help!  I also having this same problem.  Upgraded because I could not ever get my mic to work and now no sound works.  Also, does anyone know when gutsy will migrate to alsa 1.0.15?

Thanks!
-Jim

---

### Post by oppilif86 on 2008-02-16
I have an Asus F3SA and have been having the same problem: I managed to fix it by copying:
[LIST]
[*]snd-hda-intel.ko from /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/ into /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/
[*]modules/* in alsa's compile directory into /lib/modules/.../kernel/sound
[/LIST]
then running 'depmod -a' and rebooting.

I found this solution here: [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by eraserpt on 2008-04-26
> **arkone said:**
> Hi all.I'm italian boy. I've a solution for audio on a f3sa laptop. After 2 week and so many procedures with insuccess(including wiki's ubuntu and all that i've found over the google). 
First install the latest version of Alsa 1.0.15 final. 
After, you create a file in /etc/modutils called, for example, 'alsa' with this sequence of aliases and options:

alias char-major-116 snd
alias snd-card-0 snd-hda-intel
# module options should go here
options snd-hda-intel model=lenovo
     
# OSS/Free 
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0
       
# card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
 
The most important is the line:
options snd-hda-intel model=lenovo

For a secure success, add the line above in the file /etc/modprobe.d/alsa-base too
 If it doesn't exixt, create! 

After you must restart. Before you start to dancing, run 'alsamixer' and unmute all channel and set the volume.

I hope that this 'tweak' is good for you. Ehm.. sorry for my english.
Bye.

Just saved my life :D, this solution also works for asus f3sv :popcorn:

---

