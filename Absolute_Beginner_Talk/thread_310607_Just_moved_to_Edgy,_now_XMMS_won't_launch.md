---
title: "Just moved to Edgy, now XMMS won't launch"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2006-12-01
Coincidence? We think not. Here's what I got in the terminal:
```
Message: device: default
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 2518 error_code 8 request_code 72 minor_code 0
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 2519 error_code 8 request_code 72 minor_code 0
```
Should I just uninstall and reinstall? TIA.

---

### Post by ricardisimo on 2006-12-01
> Should I just uninstall and reinstall? TIA.

So much for that idea. No change:
```
Message: device: default
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 2518 error_code 8 request_code 72 minor_code 0
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 2519 error_code 8 request_code 72 minor_code 0
```

---

### Post by echo $USER on 2006-12-01
try purging all the config files as well as uninstallation...

> sudo apt-get remove --purge xmms
> sudo apt-get install xmms

---

### Post by ricardisimo on 2006-12-01
I'm not sure what this has to do with anything, but the one big glitch during the Edgy install was Firestarter, which is causing me problems with Synaptic and and Add/Remove. Here's what I got during the uninstall/install of XMMS:
```
Removing xmms ...
Purging configuration files for xmms ...
Setting up firestarter (1.0.3-1.2ubuntu3) ...
 * Starting the Firestarter firewall...                                  [fail] 
invoke-rc.d: initscript firestarter, action "start" failed.
dpkg: error processing firestarter (--configure):
 subprocess post-installation script returned error exit status 200
Errors were encountered while processing:
 firestarter
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Meanwhile, if I try starting Firestarter, this is what I get:
A```
 proper configuration for Firestarter was not found. If you are running Firestarter from the directory you built it in, run 'make install-data-local' to install a configuration, or simply 'make install' to install the whole program.

Firestarter will now close.
```

---

### Post by echo $USER on 2006-12-01
Why not uninstall firestarter?  You only need it if you are running services accessible to a WAN.  XMMS is more inportant to me than firestarter.  Just purge/remove firestarter and reinstall XMMS... see if that is the resolution.

---

### Post by quarkhirad on 2006-12-01
ur xmms is not launching because you probably have got xmms for 6.06 installed. 
U have to uninstall the application and then reinstall xmms for 6.10

As far as ur problem with synaptic. To my knowledge firestarter is an important part for any package manager .

---

### Post by ricardisimo on 2006-12-01
> **quarkhirad said:**
> ur xmms is not launching because you probably have got xmms for 6.06 installed. 
U have to uninstall the application and then reinstall xmms for 6.10

As far as ur problem with synaptic. To my knowledge firestarter is an important part for any package manager .

I'm fairly certain that there is no special 6.10 version of XMMS. As for removing Firestarter entirely, that sounds a tad extreme. I'd prefer to hear more input from others on this first.

---

### Post by ricardisimo on 2006-12-02
Can someone suggest perhaps another forum to ask this question? The XMMS forum appears to be defunct.

---

### Post by ricardisimo on 2006-12-15
In Launchpad, [this very issue]("https://bugs.launchpad.net/distros/ubuntu/+source/xmms/+bug/58192") came up but I'm having difficulty deciphering the solution. What exactly am I supposed to do with the line ```
export XLIB_SKIP_ARGB_VISUALS=1
```?

---

### Post by ricardisimo on 2006-12-16
[SIZE="7"]Hello?[/SIZE] [SIZE="4"][COLOR="Gray"]Hello?[/COLOR][/SIZE] [SIZE="1"][COLOR="Silver"]Hello?[/COLOR][/SIZE]
[SIZE="7"]Anyone there?[/SIZE] [SIZE="4"][COLOR="Gray"]Anyone there?[/COLOR][/SIZE] [SIZE="1"][COLOR="Silver"]Anyone there?[/COLOR][/SIZE]

---

### Post by OffHand on 2006-12-16
Xmms is obsolete. Why not try a different player like Audacious? It's the best winamp clone around in my opinion.

---

### Post by 8bit on 2006-12-17
> **OffHand said:**
> Xmms is obsolete. Why not try a different player like Audacious? It's the best winamp clone around in my opinion.

Thanks a million OH. I downloaded Audacious and it kicks XMMS' ***!

---

### Post by ricardisimo on 2006-12-21
The story's not quite so rosy on my end. I've installed Audacious, and not only do I no longer have System Sounds (logout.wav, startup.wav, etc.) but Audacious has completely locked up my compootor a few times already. Bootup is different now as well... slower... although that could possibly be coincidence. Any ideas as to what's going on? Thanks.

---

### Post by ricardisimo on 2006-12-21
Never mind... I just had to change the output plugin from ALSA to PulseAudio. I've got something like ten output plugins. Can someone explain what they all are and how I would ever use them? Thanks.

---

### Post by Kingstrum on 2007-01-04
I had the same issue with XMMS (yes, I know there's a boatload of new players, but they all have the annoying habit of wanting to index my 20GB+ collection ***their*** way) and after much surfing your quick tip solved it.

```
export XLIB_SKIP_ARGB_VISUALS=1
```

Added it to my *.bashrc* and now it's all good. Which plugins do you have that you're unsure of?

Kingstrum

---

