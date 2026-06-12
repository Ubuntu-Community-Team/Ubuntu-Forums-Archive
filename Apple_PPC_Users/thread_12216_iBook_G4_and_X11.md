---
title: "iBook G4 and X11"
date: 2005-01-22
forum: Apple PPC Users
---

### Post by jamincollins on 2005-01-22
I've tried installing Ubuntu a few times now and the install seems to succeed without error.  However when X attempts to start I'm left with solid cycling colors (red, blue, green, etc).  If I restart the iBook and manually enter single user mode the text display is fine.  Anyone have any ideas how I can get X properly configured?

This is on a 14" 1.33 Ghz G4 iBook.

---

### Post by jamincollins on 2005-01-30
No ideas or suggestions?  Is no one running Ubuntu on a G4 iBook???

---

### Post by TekMate on 2005-01-30
This one may work [http://geekounet.org/powerbook/files/XF86Config-4-g4](http://geekounet.org/powerbook/files/XF86Config-4-g4)

---

### Post by pvz on 2005-01-31
Here's the XF86Config-4 for my iBook G4 12" running Ubuntu Hoary:
[http://www.petrvz.net/~pvz/XF86Config-4-ibookg4_ubuntu](http://www.petrvz.net/~pvz/XF86Config-4-ibookg4_ubuntu)

---

### Post by jamincollins on 2005-01-31
Just tried both configs... end result.. no change.

I can hear the X session starting (startup sounds and such) but I only get solid colors on the display that cycle through various colors (red, green, blue, white, grey, black, etc).

---

### Post by TekMate on 2005-02-01
Can you post your file?

---

### Post by jamincollins on 2005-02-01
[QUOTE=TekMate]Can you post your file?[/QUOTE]

Which file?  The XF86Config-4 or the XFree86.0.log?  I'll gladly provide any information needed to get this working.  However for the configs, I tried them as provided by the other two posters so they are readily available if that's what your after.  I did save the XFree86.0.log files for the startups under each config too if those would be helpful.

---

### Post by Viro on 2005-02-01
What about both? We'll have a look at the config, and the errors that config caused.

---

### Post by jamincollins on 2005-02-01
[QUOTE=Viro]What about both? We'll have a look at the config, and the errors that config caused.[/QUOTE]

The files should be available here:

[http://asgardsrealm.net/~jcollins/ibook-x11/](http://asgardsrealm.net/~jcollins/ibook-x11/)

---

### Post by jamincollins on 2005-03-27
Well, looks like this was somewhat self inflicted.  Recently tried Yellow Dog Linux and found that I was able to start X with an 8 and 16 bit depth after the install finished.  This prompted to be retry the Ubuntu installation and it appears to be working.  The only thing I can think of that I did differently between the previous installation and this one was passing a video option during the initial install ("video=ofonly", iirc).  Seems this option is not necessary on the iBook and potenially harmful to getting X working.

Now the only thing left to get working is the Airport Extreme.  Which from the look of some of the other posts I've found will be difficult to say the least (if not entirely impossible currently).

---

