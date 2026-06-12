---
title: "Sound-Audacity Problem"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by MNGS on 2006-04-15
Okay, 5.10 installed and looks great.

But...Audacity won't work. Message I get when I open it is:

[CENTER]Error intitializing Audio
There was an error initializing the audio i/o layer.
You will not be able to play or record audio.
Error: Host error.[/CENTER]

Then, Audacity opens, but, obviously, won't work.

I do hear sounds when the OS boots, etc.

A major use of this will be recording a podcast ([http://MrNiceGuyShow.com/](http://MrNiceGuyShow.com/) feel free to listen. Shameless plug, I know, sorry) so, hopefully you can help...

...and I'd be very grateful.

Thanks,
-M!

---

### Post by ronb on 2006-04-17
I'm having the exact same problem.  I have already loaded audacity on my PC at work and personal G3 PowerBook.  It works great on both.

Using the Synaptic Package Manager, I downloaded and installed audacity on Ubuntu and then no luck.

Thanks for any advice.

---

### Post by hentaidan on 2006-04-17
[QUOTE=ronb]Thanks for any advice.[/QUOTE]

Google is your friend :) 

Most likely cause is ESD, to disable:
System > Prefs > Sound, and uncheck "Enable software sound mixing (ESD)"


Take a look @ [http://audacityteam.org/wiki/index.php?title=LinuxIssues]("http://audacityteam.org/wiki/index.php?title=LinuxIssues")

or if you want to stay within the forums: [http://ubuntuforums.org/showthread.php?t=154375]("http://ubuntuforums.org/showthread.php?t=154375")

---

### Post by ronb on 2006-04-17
[QUOTE=hentaidan]

Most likely cause is ESD, to disable:
System > Prefs > Sound, and uncheck "Enable software sound mixing (ESD)"

[/QUOTE]

At **System > Prefs > Sound** I found "Enable sound server startup"

I unchecked that and Audacity starts without a hitch.  Thanks.

My microphone doesn't work, but I think that's another issue.

Thanks again.

---

### Post by hentaidan on 2006-04-17
[QUOTE=ronb]At **System > Prefs > Sound** I found "Enable sound server startup"[/QUOTE]

Umm.. yeah thats the one... my bad! :rolleyes:

---

### Post by mostwanted on 2006-04-17
[QUOTE=ronb]At **System > Prefs > Sound** I found "Enable sound server startup"

I unchecked that and Audacity starts without a hitch.  Thanks.

My microphone doesn't work, but I think that's another issue.

Thanks again.[/QUOTE]

That's a bad fix. The problem is because Audacity uses OSS whereas Ubuntu uses ALSA for sound. To enable sounds for OSS apps in Ubuntu install the also-oss package. No need to turn off other sounds.

---

### Post by ronb on 2006-04-17
[QUOTE=mostwanted]To enable sounds for OSS apps in Ubuntu install the also-oss package. [/QUOTE]


I installed the package **alsa-oss** (ALSA wrapper for OSS applications v. 1.0.9-1), and I'm back to the original problem.  Do I need to configure the package?

Thanks.

---

### Post by mostwanted on 2006-04-17
[QUOTE=ronb]I installed the package **alsa-oss** (ALSA wrapper for OSS applications v. 1.0.9-1), and I'm back to the original problem.  Do I need to configure the package?

Thanks.[/QUOTE]

Dunno. It worked for me =/

Make sure the sound server is enabled.

---

### Post by Quicky on 2006-04-18
Hi mostwanted, did you manage to get Audacity working without any errors? I've been having exactly the same problem - I also installed the alsa-oss package but to no avail - I still get the initialising audio error.

Thanks

---

### Post by fdoving on 2006-04-18
Your problem is that ESD is locking the sound device. Audacity can't access it. Stopping ESD before using Audacity is a solution. Else you can configure ESD to release the device like 5 seconds after it played the last sound. That way you can start audacity without problems.

Edit /etc/esound/esd.conf

Mine looks like this:
```

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 1
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

```

The '-as 1' part makes esd release the audio device after 1 second.
I don't use esd very much so i want it to release the device fast to give my other apps access to the device.


- Frode

---

### Post by Quicky on 2006-04-18
Cheers for that.

---

### Post by Sgurd on 2006-10-08
> **fdoving said:**
> Your problem is that ESD is locking the sound device. Audacity can't access it. Stopping ESD before using Audacity is a solution. Else you can configure ESD to release the device like 5 seconds after it played the last sound. That way you can start audacity without problems.

Edit /etc/esound/esd.conf

Mine looks like this:
```

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 1
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

```

The '-as 1' part makes esd release the audio device after 1 second.
I don't use esd very much so i want it to release the device fast to give my other apps access to the device.


- Frode

I went to edit my esd.conf and it already looked exactly like that.  Audacity still won't work unless I uncheck ESD and then reboot.

Any ideas?  Thanks - JD

---

