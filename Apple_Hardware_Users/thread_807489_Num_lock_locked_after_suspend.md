---
title: "Num lock locked after suspend"
date: 2008-05-25
forum: Apple Hardware Users
---

### Post by Garrulousbrevity on 2008-05-25
Hey,

I'm using a second gen macbook, and I'm having an odd problem after suspend. 

When waking up, everything seems to be working fine, except that the numlock LED is on, which impressive because that's been broken since I updated to hardy, and only the numpad numbers work, nothing else.  Including the numlock key, meaning I can't turn numlock off.  I don't know if this goes away once the password screen is dealt with because... well... my password has letters in it too.  

The only thing I can think of that would be new is that there was an update a day or two ago that required a restart, and the installation of zsnes and gsnes, both of which have been removed to test to see if they were to blame.  

Any help would be appreciated.

---

### Post by cyberdork33 on 2008-05-25
have you tried pressing F6 twice to switch off the numlock?

---

### Post by Garrulousbrevity on 2008-05-26
Well, I have tried hitting F6.  I tried seeing if hitting it twice made a difference over hitting it once, or 25 or 50 times or so on... but now I can't recreate the problem. 

I'll post again if it starts up again.

---

### Post by Garrulousbrevity on 2008-05-26
I just hit the problem again.  Hitting F6 once actualy makes it so that the numpad keys actually cycle through what's selected, essentually acting as the arrow keys, while hitting F6 a second time would make it type numbers again.

---

### Post by cyberdork33 on 2008-05-26
> **Garrulousbrevity said:**
> I just hit the problem again.  Hitting F6 once actualy makes it so that the numpad keys actually cycle through what's selected, essentually acting as the arrow keys, while hitting F6 a second time would make it type numbers again.
are you using an external keyboard or something? This bug report might be useful:
[https://bugs.edge.launchpad.net/mactel-support/+bug/201887](https://bugs.edge.launchpad.net/mactel-support/+bug/201887)

---

### Post by Garrulousbrevity on 2008-05-26
No, I'm using the normal macbook keyboard, so that bug didn't quite apply.  

I did try to see if I had numlockx installed, a fix for some people in that bug report, but I didn't have it on this computer. Another fix in that report was to use another keyboard to turn numlock off, however I only have a PS2 keyboard, and macbooks only have USB and Firewire inputs.   

When I say that the numpad turns on, I mean that the keys on the right side of the keyboard start acting as the numpad.

---

### Post by stueng on 2008-05-27
Yeah this is a known issue... hitting F6 does nothing for me though, I have to hold down the function key and press F6 twice to get numlock off

---

### Post by cyberdork33 on 2008-05-27
> **stueng said:**
> Yeah this is a known issue... hitting F6 does nothing for me though, I have to hold down the function key and press F6 twice to get numlock offThat is the same as hitting F6 twice. By default the F-keys perform the "special" function. Using the Fn key in combination accesses the associated F-key. (This is how it works in OS X, and for some reason this was brought over to Linux when support for these keyboards was added.

Bug here:
[https://bugs.edge.launchpad.net/mactel-support/+bug/201711](https://bugs.edge.launchpad.net/mactel-support/+bug/201711)

---

### Post by Arne Caspari on 2008-06-16
Try to run 'sudo apt-get remove mouseemu'. It fixed the issue for me.

---

### Post by ecksiota on 2008-10-03
Looks like this thread is dead, but removing the mouseemu package seemed to work around the problem for me. I am using Macbook1,1 with Hardy 2.6.24-19-generic.

---

