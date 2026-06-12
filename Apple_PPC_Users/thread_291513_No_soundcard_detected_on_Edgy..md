---
title: "No soundcard detected on Edgy."
date: 2006-11-02
forum: Apple PPC Users
---

### Post by guX on 2006-11-02
Hey, I just installed Edgy on my iBook. I've no sound. The volume applet in gnome-panel is muted. When I try to double-click on it, I get this: [quote=gnome-panel]The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.[/quote]

When I try to open alsamixer, I get this: [quote=alsamixer]alsamixer: function snd_ctl_open failed for default: No such device[/quote]

Anyone have any ideas?

---

### Post by pay on 2006-11-02
```
lspci | grep -i audio
```tells you what card you have. Then you have to add the card ```
sudo nano /etc/modules.d/alsa
```an example would be ```
alias char-major-116 snd
alias char-major-14 soundcore

alias snd-card-0 snd-emu10k1
alias sound-slot-0 snd-card-0

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias /dev/dsp snd-pcm-oss

options snd cards_limit=1

```change snd-emu10k1 to your card```
modules-update -f
/etc/init.d/alsasound start
```unmute the channels
```
/etc/init.d/alsasound save
```then save

I'm a gentoo user so the steps in Ubuntu may be different

---

### Post by gerghk on 2006-11-02
try this from the commandline
   modprobe snd-powermac
then type
   lsmod | grep snd-powermac

to check that the module loaded properly
if all went well the sound should now be working

now to make this work every time you boot up, add snd-powermac to your /etc/modules file

hope that works out for u :)

---

### Post by Ameet on 2006-11-09
I have the same problem as GuX on my system, with same errors EXCEPT ...

* I have a Gateway 600YGR laptop (pentium 4)
* running Dapper (6.06)

I tried following Pay's advice, with this result ...
```
~$ lspci | grep -i audio
0000:02:03.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)

```
and
```
~$ find /etc/modules.d/alsa
find: /etc/modules.d: No such file or directory
~$ find /etc/modules.d
find: /etc/modules.d: No such file or directory

```

So am I supposed to create a directory modules.d?  And a file "alsa" within it?  or are these supposed to already be there?  Is the problem here that I have Dapper rather than Edgy, and need a different solution?

Thanks for any suggestions.  My unix is basic so please be specific about things to try :eek:

---

### Post by Zarephath on 2006-11-10
Information posted about modprobe had an error. The corrected syntax is:  modprobe snd_powermac..then just edit /etc/modules and add that command so I will load on boot.

---

### Post by Ameet on 2006-11-10
Keeping in mind that i don't have a Mac, I am assuming I need something **other** than "snd-powermac".  Here's what I **do have**:
```
~$ lsmod | grep snd
snd_maestro3           25380  0
snd_ac97_codec         93216  1 snd_maestro3
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd_page_alloc         10632  1 snd_pcm
snd                    55268  6 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd

```

My /etc/modules file has this:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
sbp2
sr_mod
fglrx

```

Can anyone tell me what I am missing?  Again, this is a Gateway laptop with a Pentium 4 chip, and I'm running Dapper, all upgrades marked and installed using Synaptic Manager.

Thanks,
Ameet.

---

### Post by Zarephath on 2006-11-10
Well first off you should have posted in the PC forum and not PPC since that is mainly Apple and or derivatives thereof. However looking at your output you already have the ac97 drivers loaded...I would try installing alsamixer, or alsamixer gui and make sure the main sound isn't muted. I have seen this happen to me and others in the past...

---

### Post by Ameet on 2006-11-12
Hi, Zarephath,

Thanks for the suggestion.  I just installed alsamixergui (which wasn't installed).  On running, I get this message:
"alsamixer: function snd_ctl_open failed for default: No such device"

The sound isn't muted.  So I'm still not sure of what the problem is.

I posted here because guX had *exactly* the same error message as I have been having - i figured the problem was probably not platform specific.  You are right it should be better posted on the PC not PPC side but if its not platform specific I figured someone may be having insights here as well.

---

### Post by Ameet on 2006-11-12
I figured out my problem! :-)

I didn't have proper user authorization.  So I went to System > Administration > Users and Groups, picked my account, and enabled audio access.  Then I logged out and back in, and *presto!*.

GuX, I wonder if that will work for you as well?

Thanks, everyone, 
Ameet.

---

### Post by john8520 on 2006-11-12
What if you type lspci | -i audio or lspci | grep snd and nothing comes up? I'm unable to get sound working in my powerbook...

I have looked in the "Users and Groups" control panel, and I am authorized to use audio devices.

---

### Post by gnomeza on 2006-11-12
> **john8520 said:**
> What if you type lspci | -i audio or lspci | grep snd and nothing comes up? I'm unable to get sound working in my powerbook...

And if you run  "lsmod | grep snd" ?

I suspect, like me, you have a Powerbook5,2 (grep motherboard /proc/cpuinfo) and Edgy is loading snd-aoa instead of snd-powermac.

snd-aoa in not supported on Powerbook5,2.
See [http://johannes.sipsolutions.net/Projects/snd-aoa/](http://johannes.sipsolutions.net/Projects/snd-aoa/)

Fixed this by doing:
```
sudo su 
echo "alias snd-card-0 snd-powermac" >> /etc/modprobe.d/snd-powermac
echo -e "blacklist snd-aoa-i2sbus\nblacklist snd-aoa-soundbus" >> /etc/modprobe.d/blacklist-snd-aoa

```

---

### Post by john8520 on 2006-11-12
running "lsmod | grep snd" also returned nothing.

running "grep motherboard /proc/cpuinfo" returned "Motherboard: APPL, Powerbook1998 MacRISC"

---

### Post by gnomeza on 2006-11-13
Hmm. Guess that's a Powerbook G3 Wallstreet.
Should be supported by snd-powermac. Well, maaaybe...

---

### Post by john8520 on 2006-11-13
I have no idea... :P

Is snd-powermac preinstalled, or so I need to apt-get it?

---

### Post by gnomeza on 2006-11-13
The rest of the output of /proc/cpuinfo should mention the codename of your powerbook. Linux HOWTOs will almost always mention the codename (Wallstreet, Pismo, Lombard etc).
Some useful specs here: [http://www.lowendmac.com/pb2/index.shtml](http://www.lowendmac.com/pb2/index.shtml)

snd-powermac is a kernel driver. It would be installed automatically with the kernel.
Try "/sbin/modinfo snd-powermac" to see if it's installed.
If your sound hardware is supported by it then running "sudo modprobe snd-powermac" should make a pcm device appear in /dev/snd.

---

### Post by AlphaMack on 2006-11-13
I had this happen to me when I used the *alternate* CD on my PowerBook G4 but not when I installed Edgy with the live CD.  Odd.

---

### Post by john8520 on 2006-11-13
I think its not working because of my kernel, for these reason:

I run "/sbin/modinfo snd-powermac" and get back:

```

modinfo: could not open /lib/modules/2.6.17.11/models.dep

```

And when I run "sudo modprobe snd-powermac" I get back:

```

FATAL! Could not load: /lib/modules/2.6.17.11/models.dep: No such file or directory.

```

So, I guess I may need a new kernel? I'm not using Yaboot BTW, this is an old world mac.

---

### Post by john8520 on 2006-11-13
Alright, I tried "upgrading" to the 2.6.18.rc6 kernel, and I get the same errors.

Should I be using the vmlinux file that came on the CD?

EDIT - Nope, booting off the included "vmlinux" file doesn't work, it can't fine the root file system.

---

### Post by john8520 on 2006-11-13
Ok, I've done sudo vi /etc/modules, and and-powermac **is** there... Anything else I may be able to try?

---

### Post by stmiller on 2006-11-14
The driver snd-powermac is now obsolete. It has been replaced with snd-aoa.

It is for powermac machines, specifically. Not sure if it is for G3 powerbooks. Let me check a few things and get back to you.

---

### Post by john8520 on 2006-11-14
Alright, a friend of mine showed now how to properly load the kernel modules, so now when I run "lsmod | grep snd" I get back:

```

snd_powermac                      48796  1
snd_pcm_oss                       46912  0
snd_mixer_oss                     19360  1 snd_pcm_oss
snd_pcm                           92452  2 snd_powermac,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
nd_timer
soundcode                          8676  1 snd
snd_page_alloc                     8680  1 snd_pcm

```

I dunno what any of that means, but is there some kind of speaker test program I can run?

---

### Post by stmiller on 2006-11-15
Type this in a terminal:

```
$ speaker-test -t sine
```

---

### Post by john8520 on 2006-11-15
Yep it works fine!

But whenever I tried to play an MP3 off a website, or play it through Gxine, it didn't work.

---

### Post by theJagger on 2006-11-18
> **gnomeza said:**
> The rest of the output of /proc/cpuinfo should mention the codename of your powerbook. Linux HOWTOs will almost always mention the codename (Wallstreet, Pismo, Lombard etc).
Some useful specs here: [http://www.lowendmac.com/pb2/index.shtml](http://www.lowendmac.com/pb2/index.shtml)

snd-powermac is a kernel driver. It would be installed automatically with the kernel.
[B]Try "/sbin/modinfo snd-powermac" to see if it's installed.
If your sound hardware is supported by it then running "sudo modprobe snd-powermac" should make a pcm device appear in /dev/snd.[/B]

DONE! I have an iBook: PowerBook4,1 MacRISC2 MacRISC Power Macintosh
(got that info from: #grep motherboard /proc/cpuinfo)

basically the sound device did not show up till I did the "sudo modprobe snd-powermac" now every thing is SWEEET!:KS

---

### Post by babgolis on 2007-03-23
OK, total NOOB here. I have a rev 5.2 powerbook. I am able to manually load snd-powermac, but I'm not clear on how to unload snd-aoa & automatically load snd-powermac. I tried some of the earlier suggestions, but no luck. Can anyone give me a hand? Thanks

---

