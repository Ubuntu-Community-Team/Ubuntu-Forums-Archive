---
title: "Bad Archive Mirror - 8.04 Daily Build PPC"
date: 2008-04-28
forum: Apple Hardware Users
---

### Post by toyota_f1 on 2008-04-28
At 82% of the install on the live cd during the "Configuring APT" stage I get a "Bad Archive Mirror" error.  I have changed nothing from the defaults, just trying a straight install... so far no luck getting it to work.  Was hoping this one would be easier to get going than the Gutsy version that I gave up on. :)

This is on a G3 400Mhz, 13 gig HD (original), ATI Rage 128 video, 768 mb RAM.

---

### Post by stream303 on 2008-04-28
Check this out - in fact it was your message that alerted me to the fact that the installer is probably going to hang now that we've been moved - something I didn't think about since I had already installed an RC, and just edited my sources.list file.  Great heads-up!

[http://ubuntuforums.org/showthread.php?t=772930](http://ubuntuforums.org/showthread.php?t=772930)

---

### Post by toyota_f1 on 2008-04-28
So are we just talking about replacing all the archives.ubuntu.com/ubuntu
with
ports.ubuntu.com/ubuntu-ports

in the /etc/apt/sources.list file?

Can I just do it from nano from a terminal in the live cd?

---

### Post by stream303 on 2008-04-28
> **toyota_f1 said:**
> Can I just do it from nano from a terminal in the live cd?

Sure, just sudo nano -w /etc/apt/sources.list, and then do an apt-get update

I guess the way I was doing it was to avoid a possible hang situation.  Kind of taking the scenic route ... :)

---

### Post by toyota_f1 on 2008-04-29
Still No Joy when I tried this... as soon as I hit 82% in the install during the installing apt portion I get the Bad Archive Mirror again.  Meh.

---

### Post by toyota_f1 on 2008-04-29
okay, so I replaced my /etc/apt/sources.list  with the one I found noted at [http://ubuntuforums.org/showthread.php?t=772930](http://ubuntuforums.org/showthread.php?t=772930)

then did a sudo apt-get update and ran the update manager just for fun.

After sitting patiently through the start of the install for the umpteenth time it FINALLY made it past my 82% stall.  Quite happy for now.  :)

---

### Post by stream303 on 2008-04-29
Hmm..  during installation, is the system trying to make the firewire port the ethernet connection?  If so, you don't want that and should choose the real ethernet port if that's the case.

Also try the "alternate" non-live installer image - I know it works if I do the "expert" choice during install...

Does the live cd connect to the internet without trying to install?

---

