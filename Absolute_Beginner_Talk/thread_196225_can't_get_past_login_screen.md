---
title: "can't get past login screen"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-06-13
ever since the initial installation, i can't get past the login screen.

i enter my username and password, press enter...the screen transitions to the beginning of what should be ubuntu's beautiful desktop but the screen remains blank and the mouse pointer is sluggish. it hangs there forever.


i am running an amd64 3400 with 512mb ram, and integrated video.

thanks for any help!!!

---

### Post by u.b.u.n.t.u on 2006-06-13
How many times have you been able to successful log in post the initial install?

---

### Post by shanepardue on 2006-06-13
zero times.

and i've checked the video config and even substituted video cards so i know it's not that. for some reason i think it has something to do with using a 64-bit with an i386 breezy cd. i've heard people say that it should work fine, but it seems something is up there or with my ram.

i'm at loss of ideas to be honest.

---

### Post by Ahriman on 2006-06-14
Are you able to log in if you use the Live CD (either the i386 one or the 64-bit one)?

---

### Post by u.b.u.n.t.u on 2006-06-14
Have you checked the integrity of the CD you are using? When you put it in the CD and reboot to CD you will see an option to check the CD for any errors.

Ahriman's question is also important to know the answer to.

---

### Post by shanepardue on 2006-06-14
the live cd doesnt work either..gets to where it would be loading the desktop and stalls..sluggish mouse and all.

both cd's are straight from ship-it and have been used on many computers. i even tried another shipit cd and the same issue occurred. i tried reinstalling a couple times also.

i unplugged all the hardware and booted with only video, keyboard, and hda. still nothing.

---

### Post by drtvasudevan on 2006-06-14
[QUOTE=shanepardue]ever since the initial installation, i can't get past the login screen.

i enter my username and password, press enter...the screen transitions to the beginning of what should be ubuntu's beautiful desktop but the screen remains blank and the mouse pointer is sluggish. it hangs there forever.


i am running an amd64 3400 with 512mb ram, and integrated video.

thanks for any help!!![/QUOTE]

happened to me too!
it said the final config will be done at first log in and that did not come through.
i restarted and same problem.
exited to lower level with ctrl alt F2
root log in appeared.
entered passwd
gave new password.
confirmed.
rebooted.
voila!
went past log in screen. after a few questions - i think locale config- was through.

tv

---

### Post by u.b.u.n.t.u on 2006-06-14
Therefore it has to be the hardware, I would think. Either the CPU, RAM, video card, CD rom or mainboard or an unknown device.

I think we can exclude the cpu, ram and CD rom.

That leaves the video card/mainboard and unknown device as the prime agents.

Are you able to post what mainboard it is, and what video card?

Do you have any other hardware installed.

I would also test a different Linux live CD. That would reveal a lot.

It may be a stupid question, but you didn't state - are you using the 64bit ubuntu version?

Edit:

You only mentioned the "a 64-bit with an i386 breezy cd"

---

### Post by pjeeanah on 2006-06-14
I had the same problem with breezy. The problem was with the video card driver settings. I had an NVIDIA 6600 LE card.

When you get to the login screen, I would suggest that you try to press CTRL+ALT+F1.

You get the login prompt, you can then login with your username and password.

If you have an NVIDIA VGA chip, I would suggest you edit the /etc/X11/Xorg.conf file. 
Replace any mention of "nvidia" by "vesa". 

Then press CTRL+ALT+BACKSPACE and try to login at the GUI.

Hope this helps.

---

### Post by u.b.u.n.t.u on 2006-06-14
I would think the default is "nv" or not? Mine was "nv" and then when I installed the 3d drivers it became "nvidia".

The "vesa" does sound like it may work. Just make sure to backup your xorg,conf file first.

---

### Post by pjeeanah on 2006-06-14
I think you're right, ''nv" should be replaced by ''vesa".

---

### Post by shanepardue on 2006-06-14
i am using the 32-bit breezy version as my dapper shipit cd's are on the way..

i have already checked to make sure the driver is set to vesa and used two different video cards to make sure it wasn't that.

my mainboard is an ASUS A8V-MX.
i'm also running AMD64 3400 just as a reminder.

any ideas?

---

### Post by shanepardue on 2006-06-14
i hope that the dapper cd's i receive in the mail will fix the problem..if not, i'm stuck and it doesn't seem anyone else is able to get to the bottom of this either

---

