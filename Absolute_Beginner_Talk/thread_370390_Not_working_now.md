---
title: "Not working now"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Pistolla on 2007-02-25
Never had this happen to me and i want to stay with Linux/Ubuintu/kubntu
  I have been with (K)UbuntU FOR a while now, I have both. Yesterday i  noticed that the keyboard does not work.  It worked up until yesterday (24 February) around 3pm. No readon, no notice, nothing. I dual-boot and under winXP it works (the keyboard) fine. I want to know what has happened that made it not work.
  I will say that when i restart the comp that the keyboard works for me to decide which OS i want to run but when Ubuntu/Kubuntu runs i cannot get the keyboard to work. Help, please!?

---

### Post by highneko on 2007-02-25
Maybe it's a loose connection? Sounds simple, but I can't think of anything else. Maybe try reconnecting it?

---

### Post by jkeyes0 on 2007-02-25
since the keyboard works, when you get to the grub screen, can you select the "recovery mode" kernel option?

If you can get in that way, and the keyboard works, you should be able to edit your xorg.conf file with
```
sudo nano /etc/X11/xorg.conf
```

and look for the section that says "InputDevice" and describes your keyboard. Make sure it looks something like this:

```

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

```

Some of the options might change depending on your keyboard type, but the "kbd" driver should probably be the same.

---

### Post by Pistolla on 2007-02-26
Sorry for the long delay
  
  Connections are fine as it woirks on windows and when i am at the initial (i guess) splash screen where i decide to either run Ubuntu or Windows.

---

### Post by Pistolla on 2007-02-26
Me again

jkeyes, i did the first as recommended and when that screen came up, there was nothing for me to look for.

Now a brain-dead stupid question, was i suppose to search for it?  I searched for input device (with the space in-beween) and got back a cannot be found or something or other. i will try that and see if that what was needed to be done.  If that fails i don't know what to do. i don't want to go back to Windows full-time.  It is for this type of problem i keep it so i can a way to get here.

By the way, thanks for both replies :guitar: .  Since it sometimes is the obvious thing that is wrong but this has me plussed

---

### Post by irish_flu on 2007-02-26
There's no space in InputDevice, but you might just have better luck scrolling through the xorg file.  It's not that long.  Could you see text in the file?

---

### Post by Pistolla on 2007-02-26
Thanks for the reply Irish_flu:guitar: 

No text in the file. When i typed sudo nano part, it just came to a blank black screen with certain options at the bottom (which i think is normal) but nothing else.  So i searched from the optiom ^W for where is" (sorry for the redundancy but i am letting it be known where i was at).  Alas and alak, i get nothing but that blank screen.

Since my mouse works, should i just go into the file in regular mode to see if it is there?  Or could it be done in Recovery mode. i am not used to text mode under root user.  Just what i am slowly, very slowly learning here.

Again thanks :guitar:

---

### Post by v8YKxgHe on 2007-02-26
Linux is a case sensitive operating system "/etc/x11/xorg.conf" is not the same as "/etc/X11/xorg.conf" You need to do the latter one:

"sudo nano /etc/X11/xorg.conf"

---

### Post by Pistolla on 2007-02-26
:guitar: Thanks AlexC for clear up i kow it's usually operator error (me)

Here is the conundrum.  As i mentioned at the very outset i run both Kubuntu and Ubuntu. I was under Kubuntu and i couldn't "look" in my root folder as i can under Ubuntu. the catch is when i knee-jerkedly logged out of session under Kubuntu (it automatically logs in under whatever default) and went to the splash screen and i could type my username and password and guess what, i am under Ubuntu again:guitar: :) 8) :razz: 

i don't want to use Windows any more than i have to; which is rare by the way.  For purposes not yet tackled under linux and i don't know if i have the wherewithall or knowledge to contribute

The initial problem is still there however. At least under Kubuntu.  So as of now, i am stoked and will wait a few and try it under Kubuntu at least that initial part Alex. The question, then, is if i get that far and it is there or (pardon the redundancy), if it is not there, what's next?

---

