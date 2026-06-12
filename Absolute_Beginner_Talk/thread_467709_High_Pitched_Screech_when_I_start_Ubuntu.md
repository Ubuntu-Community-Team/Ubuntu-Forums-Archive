---
title: "High Pitched Screech when I start Ubuntu"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by RJG on 2007-06-08
I just got my new Lenovo laptop and installed Ubuntu on it. I had trouble with not getting any sound so I searched around and found a package from another forum that solved the sound issue. The problem is, I have one more sound than I would like.
Whenever I power on the laptop I get a high pitched squealing noise at the Ubuntu loading screen. It's driving me, and my dog, nuts. I'm glad it hasn't happened in public yet.
The package I used to solve my sound problem was an Alsa patch.
Does anybody know what is causing the noise, has anyone had the problem occur to them and, most importantly, how do I make my dog not chew my new laptop to stop the squealing?

P.S. I'm an absolute beginner as I only got the laptop yesterday and this is the first time I've ever used any Linux distro. If this thread is wrong the wrong spot, sorry.

---

### Post by diatribe on 2007-06-08
try booting without the splash in loud mode and see what is initialising when the sounds happens, also does it come from the speakers or is it a hardware problem or what?

E: the way you'll need to do this is from a terminal type:

sudo gedit /boot/grub/menu.lst

scroll down to where it has your kernels listed, and remove the instances of quiet and splash for the kernel you will be booting, and save the file.  then reboot and it should be just text running down the screen

---

### Post by RJG on 2007-06-08
The problem only started once I used the Alsa package to restore sound. It only happens during startup and not when I shutdown.

I can stop the problem by plugging in the headphones, though sometimes it continues when on the desktop and I have to unplug and replug the headphones to stop it.

Having followed the instructions in the first reply, I removed "quiet" and "splash" from the menu.lst.

The sound begins while it says it is setting up the "network interface".

Does this help at all?

---

### Post by freebird54 on 2007-06-08
Not quite what one would expect - but I'll let the person who asked for that info respond to that point...

Have you tried setting the alsamixer settings down to, say, 70% ?  Not sure which one it would be - but some sound anomalies come from that.  It sounds (sorry) like some kind of feedback loop, but I'm not familiar with your hardware so I can't help further than that  :)

Good luck - we don't want to give the dog indegestion either!

---

### Post by ramjet_1953 on 2007-06-08
If you have an on-board, or attached microphone, this could be the problem.

Right click on the speaker icon in the top bar, and select [COLOR="Blue"]Open Volume Control[/COLOR].

Either use the slider to reduce the microphone level, or just click on the icon below the slider to mute it.

Regards,
Roger :cool:

---

### Post by RJG on 2007-06-08
I've adjusted microphone vilume levels in Alsamixer, turned down Mic Boost for both Mic and Front Mic and lowered the volume of the Mic itself. I might have to talk a bit louder but it didn't start the high pitched noise.

Thanks team.

Now, how do I get my loading screen back to normal? :P

---

### Post by diatribe on 2007-06-08
just replace the instances of splash and quiet ;)

---

### Post by RJG on 2007-06-08
Well, if I knew where I deleted them from, I would. I can't seem to find the options to change the startup screen and images. I found the option to change the login window though...

---

### Post by freebird54 on 2007-06-08
When you edited your /boot/grub/menu.lst file, you had an entry like:

```
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hde4 ro **quiet splash**
```

just change it back to add in **quiet splash** to the end.

(don't change anything else to match mine!!!)  :)

---

### Post by RJG on 2007-06-08
I removed quiet and splash everywhere they appeared in the menu.lst, so there's more than those to take care of. Is there anyway to restore defaults?

---

### Post by freebird54 on 2007-06-08
Not that is as simple as just putting them back.  They ONLY go on lines that look the example I gave you - that start with kernel, and do not reference (recovery mode) in the title.  ON my system, there is only 1 line like that - how many did you have ? :)

---

### Post by RJG on 2007-06-08
I'm afraid I must have deleted quiet and splash from more than just the kernal section then.

Talk about being in over my head.

---

### Post by freebird54 on 2007-06-08
OK - I'll post all the lines I can find in mine that have either in it... hang on!

---

### Post by freebird54 on 2007-06-08
```
**splash**image (hd0,3)/boot/grub/images/splash(3).xpm.gz
```

you won't have that particular picture - but you might have killed the splash out of splashimage..
```

# defoptions=quiet splash
```

another place...and seems to be the last.  If you had more, you had more kernel lines (which will happen when you have kernel updates).

A silly question - any chance you made a backup before you modded the file?  :)

Does it still not seem to work?

---

