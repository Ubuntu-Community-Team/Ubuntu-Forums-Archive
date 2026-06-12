---
title: "can't connect to teh intarweb..."
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by SCACelt on 2007-10-05
Ok, so I've got my Ubuntu 7.04 working, and I'm seeing that it's pretty sweet.  Here's my only problem.  I'm trying to get on  my parent's protected network, so I go into the configuration to enter the WEP key, only to find that the box for the WEP key isn't long enough to take the entire thing.  The network (we're on DSL) is detected just fine, just can't connect to it.  Any help is greatly appreciated for this Linux noob.

kthxbai

---

### Post by mojoman on 2007-10-05
> **SCACelt said:**
> Ok, so I've got my Ubuntu 7.04 working, and I'm seeing that it's pretty sweet.  Here's my only problem.  I'm trying to get on  my parent's protected network, so I go into the configuration to enter the WEP key, only to find that the box for the WEP key isn't long enough to take the entire thing.  The network (we're on DSL) is detected just fine, just can't connect to it.  Any help is greatly appreciated for this Linux noob.

kthxbai

I don't know what you're connecting through but normally you can enter a key as hex or ASCII. One is just a passphrase and the other is a long string of letters and numbers. Sounds like you're entering the latter when you're  asked for the former. Ask mom and dad what their passphrase is.

---

### Post by shifty_powers on 2007-10-05
try having a look at [ndiswrapper](ndiswrapper.sourceforge.net/). (also available via synaptic). Means you can use windows drivers with linux, and in my experience will make life easier with this....

---

### Post by SCACelt on 2007-10-05
Yeah, I'm entering the long string of letters and numbers.  I don't recall them having a passphrase but I'll check it out.  Thanks.  I'll update if I have more questions (wait, that's not an "if" lol)

---

### Post by El Cabrón on 2007-10-05
Maybe it needs to be changed from 64 to 128
I haven't see the wireless network manager but I'm assuming you must configure it for the key length.

---

### Post by SCACelt on 2007-10-06
Ok, so I downloaded ndiswrapper, and have absolutely no idea what to do with it.  I don't know how to work the command window in 7.04 and my folks don't recall ever setting a passphrase so I don't know what to do.  Is there a way to set it up so I can just enter the 64-character string to connect my wireless?   is there a complete n00b howto that walks through every step and what things do?  Thanks for being helpful :D

---

### Post by Incense on 2007-10-06
If you can see the network form your computer, then you don't need NDISWrapper. That is just for getting your wireless to work. I would make sure you are connecting to the right network (I see three on my system right now) and make sure it really is WEP and not WPA encryption, and that you have the information down properly. WEP 64k or WEP 128k. Try to connect directly to the router with an ethernet cable and see if it works. You may just have to reset the the router and set up the securty all over again if you can't get the settings to be properly reconized. If your folks don't remember setting a passcode, then maybe you are connecting to the wrong network. Good luck.

---

### Post by SCACelt on 2007-10-06
Well I don't know what I did, but I managed to change an option on my wireless and now it's working...I changed it to 64/128 bit KEY and it connected no sweat :)

---

### Post by n3tfury on 2007-10-06
> **shifty_powers said:**
> try having a look at [ndiswrapper](ndiswrapper.sourceforge.net/). (also available via synaptic). Means you can use windows drivers with linux, and in my experience will make life easier with this....

um, this doesn't look like a driver issue to me.

---

### Post by n3tfury on 2007-10-06
> **SCACelt said:**
> Well I don't know what I did, but I managed to change an option on my wireless and now it's working...I changed it to 64/128 bit KEY and it connected no sweat :)

oh, you mean what was already suggested:

> **El Cabrón said:**
> Maybe it needs to be changed from 64 to 128
I haven't see the wireless network manager but I'm assuming you must configure it for the key length.

---

