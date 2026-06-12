---
title: "monitor meant to turn off?"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2008-01-04
hi there,
i was wondering - is monitor (on ubuntu 7.10 gutsy gibbon) meant to turn off at startup/shutdown/restart/etc ? is it meant to turn off so that it is more user-friendly? im guessing (since i was too) new users (to linux i mean) may be freaked out when seeing all those lines of unknowing stuff....

---

### Post by spydon on 2008-01-04
No, your bootsplash is probably set at the wrong resolotion...
try edit /etc/usplash.conf to the resulotion you have for example it can look like this:

# Usplash configuration file
xres=1024
yres=768

I have noticed that this happens quite often on laptops with gutsy that the splash screen disappears because of a faulty usplash.conf...

---

### Post by the_nomad on 2008-01-04
the fact is, if leaved, monitor turns on again showing the login screen... that's why i've asked :)

---

### Post by spydon on 2008-01-04
Ah then it's not the problem that I thought it was...
Well i'm off for bed now good night :).

---

### Post by Mrs Twaddle on 2008-01-07
> **the_nomad said:**
> the fact is, if leaved, monitor turns on again showing the login screen... that's why i've asked :)

I'm getting this too, it is seriously beginning to annoy me:confused:

---

### Post by Mrs Twaddle on 2008-01-21
anyone got any ideas?

---

### Post by spydon on 2008-01-21
Are you using old monitors?
Because one of my really old monitors does like this but I don't use it anymore...

---

### Post by thelatinist on 2008-01-21
> **the_nomad said:**
> hi there,
i was wondering - is monitor (on ubuntu 7.10 gutsy gibbon) meant to turn off at startup/shutdown/restart/etc ? is it meant to turn off so that it is more user-friendly? im guessing (since i was too) new users (to linux i mean) may be freaked out when seeing all those lines of unknowing stuff....

To clarify, when you turn on your system you still see the Power-on Self-test and grub, but then your screen goes black for 30-40 seconds before your login screen comes up?  If so, this *is* the usplash problem, and you should be seeing something that looks like the screenshot below.

If you are not getting this, you should try the suggestion Spydon made.

---

### Post by Mrs Twaddle on 2008-01-21
I get the power on self test, grub and the Ubuntu screen with the loading bar. And just before the log in screen it swtiches off and then back on.

No idea how old my monitor is. It is a CRT though.

---

### Post by thelatinist on 2008-01-21
> **Mrs Twaddle said:**
> I get the power on self test, grub and the Ubuntu screen with the loading bar. And just before the log in screen it swtiches off and then back on.

No idea how old my monitor is. It is a CRT though.

How long is it off? If only for a second or so, it may just be a slow switching from usplash to GDM login screen, in which case your monitor loses video signal for a bit and the lights will turn amber or it will go into powersave mode.  If that is the case, then you aren't missing anything.

---

### Post by Mrs Twaddle on 2008-01-21
it is just a second. Not worried about missing anything, it is just annoying

---

### Post by thelatinist on 2008-01-21
I read somewhere that a seamless boot progresssion (like that of a Macintosh) is on the long-term to-do list for Ubuntu.  But for now we will just have to make do with a little clicking.

---

