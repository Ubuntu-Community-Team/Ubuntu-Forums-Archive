---
title: ":( Stuck at loading &quot;wheel&quot; on boot"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by ConsummateK on 2007-05-27
So, yesterday I installed Feisty and everything seem to be fine. 

Basically all I have done was the normal system updates, then the restricted driver for Nvidia to enable desktop effects. 

After that I installed flash as well as Beagle. Everything is good so far I have rebooted plenty of times without any problems. 

Then today I installed WINE. It would probably also be good for me to note that this is all being done on AMD64 Feisty and all said applications (flash and WINE) are the 64 bit varients. 

The last thing I remember doing before this problem started was going into the Log on window configuration and changing the color and now when I boot I get the Ubunto loading bar (which finishes) but then I never make it to the loading window, it just sits there with the little wheel. 

Anyway some insight into how I might fix this would be great, I'd really rather not reinstall from scratch. Sorry for not being able to give more qualifying evidence of what might of caused this but i'm at a complete loss myself! :-k

---

### Post by maniacmusician on 2007-05-27
> **ConsummateK said:**
> So, yesterday I installed Feisty and everything seem to be fine. 

Basically all I have done was the normal system updates, then the restricted driver for Nvidia to enable desktop effects. 

After that I installed flash as well as Beagle. Everything is good so far I have rebooted plenty of times without any problems. 

Then today I installed WINE. It would probably also be good for me to note that this is all being done on AMD64 Feisty and all said applications (flash and WINE) are the 64 bit varients. 

The last thing I remember doing before this problem started was going into the Log on window configuration and changing the color and now when I boot I get the Ubunto loading bar (which finishes) but then I never make it to the loading window, it just sits there with the little wheel. 

Anyway some insight into how I might fix this would be great, I'd really rather not reinstall from scratch. Sorry for not being able to give more qualifying evidence of what might of caused this but i'm at a complete loss myself! :-k
hi,

Does it freeze up before login or after login? I'm assuming before.

it's likely that one of your bootup processes is failing. So, you need to see what's going on behind the pretty logo and wheel. To do this, boot up in recovery mode. When your computer is starting  up, and it says "Loading Grub, please wait.... Press Esc to enter the menu", press Esc. 

Choose the entry with "recovery mode" in parenthese next to it. It's usualyl the second one. Watch the computer boot up and note down what it gets stuck on.

---

### Post by ConsummateK on 2007-05-27
Well, I tried booting to the recovery mode and it left me at what seems like a terminal prompt...but i'm nowhere near experienced enough with terminal commands to go from there.

It's freezing after the OS loading screen but before the login screen. 

However when I hold my power key to force restart I can see a series of processes with [ok] after them and the last one says something about booting...(I know real helpful...unfortunately I can't go check now)

---

### Post by ConsummateK on 2007-05-27
After a series of boots I was able to find some possibly helpful information. 

After holding the power button to force reboot the machine (after freezing between the OS load screen and the log in screen) the last process it shows in the list is:

loading local boot scripts (/etc/rc.local)

Then after attempting to boot in recovery mode the last thing that shows before leaving me at a terminal prompt is:

* Setting up console font and keymap [ok] 

I did change the application font...but then I changed it back. I don't think it could cause this?

Anyway...hope this helps.

---

### Post by ConsummateK on 2007-05-27
*cough*

Sorry to bump...if I don't get any help here my options include reinstalling and reinstalling : (

---

### Post by ConsummateK on 2007-05-27
Last bump

Halp!

---

### Post by pointbreak on 2007-05-29
Hi,
Sorry not a magic fix but read your thread cos I have very similar problem. Was searching the forums and got hits on your thread and another one with a title like "tried to make login pretty and broke gnome". At the bottom of that post is a fix that looks the most promising for me. Maybe it will work for you. I'm at work so wont be trying it for hours otherwise I could have provided something more definite. Good luck.

---

### Post by pointbreak on 2007-05-30
Dang. No joy with that idea; rebuild.

---

