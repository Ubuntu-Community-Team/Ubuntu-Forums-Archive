---
title: "blank screen on tray-loading iMacs"
date: 2006-07-17
forum: Apple PPC Users
---

### Post by Wizardling on 2006-07-17
With the LiveCD for 6.06 after the loading screen I get blankness. Nothing. Nada. Though I can hear stuff being loaded. This is with my Lime Rev c tray-loading iMac as well as other old CRT iMacs of mine. The Rev c has 512 MB RAM and is upgraded to a 600MHz G3. The rest of my CRT iMacs have their original processors.

The fix from this thread [http://ubuntuforums.org/showthread.php?t=75604&highlight=imac+blank+screen]("http://ubuntuforums.org/showthread.php?t=75604&highlight=imac+blank+screen") which I used under 5.10 no longer works for 6.06 - assuming it's the same trouble.

---

### Post by RHTopics on 2006-07-17
After you changed the /etc/xorg.conf file, what method did you use to restart the X Server?

You might try the following keystrokes:

"**control**", "**alt**", "**F7**" to return to the blank X session screen
"**control**", "**alt**", ("**delete**" or "**backspace**") to restart X session

Note: use the **delete **key if you have the original iMac keyboard otherwise use the **backspace** key.

---

### Post by mehmehmeh on 2006-07-17
i just used that fix with 6.06 ubuntu and xubuntu on my slot loading imac dv 400. I found ubuntu to be almost unusable with the live cd on my imac, but i only have 192 MB of ram. xubuntu is going alright so far.


forgot to mention I had missed these commands before
> sudo killall gdm

Then make your edits to xorg.conf. Now start gdm:

sudo /etc/init.d/gdm start

but since you used that method before you probably already knew.

---

### Post by Wizardling on 2006-07-17
> **RHTopics said:**
> After you changed the /etc/xorg.conf file, what method did you use to restart the X Server?


I never got that far. The /etc/xorg.conf file is blank. Nothing there. Therefore I assumed it didn't exist.

---

### Post by RHTopics on 2006-07-17
Wizardling,

Sorry, I typed too fast on the previous post.

It should be /etc/**X11**/xorg.conf,

Try that, it should be there.

---

### Post by Wizardling on 2006-08-11
> **RHTopics said:**
> Wizardling,

Sorry, I typed too fast on the previous post.

It should be /etc/**X11**/xorg.conf,

Try that, it should be there.

Pardon me, I was copying you only in my reply. I DID use:

sudo vi /etc/x11/xorg.conf

The file opened is blank. It does not exist. I tried pico as well - same result. New file. No current file exists.

Has anyone found out how to get Ubuntu 6.06 working on early CRT iMacs? The method for 5.10 does not work, as I said earlier.

---

### Post by Wizardling on 2006-08-11
ok, for some reason, pico is now open to open /etc/X11/xorg.conf on ANOTHER CRT iMac. But upon saving the changees:

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 60-60
VertRefresh 43-117
EndSection

I then type sudo /etc/init.d/gdm restart

and get the following:

Starting GNOME Display Manager... [fail]

:-( So 6.06 is totally FUBAR on CRT iMacs?

---

### Post by jazzman on 2006-08-11
Try this [http://www.ubuntuforums.org/showthread.php?t=225049](http://www.ubuntuforums.org/showthread.php?t=225049)

I have my imac 233 running Xubuntu. I then loaded ubuntu-desktop through Synaptic. Although it is a little slow it runs fine.

Good Luck- Jazzman

---

### Post by linear on 2006-08-12
> **Wizardling said:**
> I then type sudo /etc/init.d/gdm restart

and get the following:

Starting GNOME Display Manager... [fail]

:-( So 6.06 is totally FUBAR on CRT iMacs?

With the Dapper Live CD, you need to type

**sudo killall -HUP gdm**

to restart Gnome.

---

### Post by 3rdalbum on 2006-08-14
And make sure you open /etc/X11/xorg.conf, not /etc/x11/xorg.conf (it's case-sensitive)

---

