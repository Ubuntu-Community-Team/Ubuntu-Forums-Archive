---
title: "Canon MP150 - No Linux Drivers?"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by hoges on 2007-01-07
Hi All,

I've been using ubuntu for a couple of days now, and was thinking of setting it up as a print server for my canon pixma mp150, but at this stage, all I can find is posts about non existent printer drivers. Is this true? I've heard of turboprint - is the free version able to be set up as a shared network printer? I have no interest in the scanning option, solely the printing part.

Also, this would be shared to both linux and windows comps.

Any help would be appreciated.

Cheers
hoges

---

### Post by hoges on 2007-01-07
Nobody?

I just tried turboprint, which works well but the free version prints with a big logo on top of it. Any ideas at all with be appreciated.

Cheers
hoges

---

### Post by hoges on 2007-01-08
bump

C'mon people, it's either this or windows ME!!!

---

### Post by yabbadabbadont on 2007-01-08
Pay for Turboprint before you resort to WinME.  (it will be the less painful option...  :lol:)

---

### Post by RudolfMDLT on 2007-01-08
This is just a shot in the dark but you could try using a card reader? Remove the Flash Card from the Cannon and read it in linux using a flash card reader?

---

### Post by yabbadabbadont on 2007-01-08
> **RudolfMDLT said:**
> This is just a shot in the dark but you could try using a card reader? Remove the Flash Card from the Cannon and read it in linux using a flash card reader?

I think you have confused this thread with one about a camera not working...  :D

This is about getting a Canon printer to work in linux.  (which isn't easy since only Canon Japan shows any interest in providing drivers or information :()

---

### Post by hoges on 2007-01-08
RudolfMDLT: Thanks for the suggestion, but it's a multifunction printer, and it doesn't have a card reader in it. Thanks for the response though.

yabbadabbadon't: I would but i don't want to pay for anything :twisted: It's an old computer with me already loaded, and using it as a printer server is more for convenience than anything else.

Windows ME works, but it is slow and painful, and more susceptible to attacks, since it will only have a freebe virus protection program on it - the router is connected to the internet.

I could try the canon japan site, although i don't speak japanese, so even on the slight chance there's a driver, i'll have to guess at what i'm doing :-k 

I did notice that the linux scanner project (can't remember the name), has reverse engineered the scanner part of the machine. Only thing is i've never used it - i only use it for the occasional photocopy, which is done through the machine itself anyway.

So it looks like i'm stuck with "ME" then?:(


EDIT: This is a long shot, but would the drivers work under wine?

---

### Post by jedd on 2007-01-08
turboprint its OK
No limitations with low print resolution on plain paper! - no logo
its work fine on my mp160 ;)

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

---

### Post by pelo8280 on 2007-04-07
Download this: [ftp://rpmfind.net/linux/fedora/extras/development/i386/gutenprint-5.0.0.99.1-2.fc7.i386.rpm]("ftp://rpmfind.net/linux/fedora/extras/development/i386/gutenprint-5.0.0.99.1-2.fc7.i386.rpm")  to your desktop.  Install "Alien" through the Synaptics Package Manager (it may already be installed).  Open a terminal window and type:
     sudo alien --scripts [*path to rpm file*]
This will create a deb package in your home folder (or the folder that you cd'd to).  Run and install that.  Then, attach your printer, turn it on, Go to System, Administration, Printing, add, etc. and install the printer with the "MULTIPASS MP150" driver.

Your Canon Pixma MP160 should work.

---

### Post by aquinashub on 2007-10-22
I downloaded the .rpm file to my desktop and installed "Alien." When I typed "sudo alien -scripts [*the path to rpm file*]" I received the message: "*You can not use --generate or --single with --install.*"

Am I making a simple syntax error? Or is there something else at work here?

---

### Post by fatalerr on 2007-10-22
you need two dashes before 'scripts'

---

