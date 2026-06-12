---
title: "can someone login to this and tell me if it's workin?"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by 070107 on 2007-07-01
**Thanks to all that tested the ftp server.  I've shut it down for now and will write a simple how-to for noobs once I test it a little more.**



I'm desperate to see if I have everything configured correctly to allow me to run an ftp server on my machine.  Yes, I'm a noob at this.

If you can see the three pdfs in there, then make a post and I'll call this a success.  If someone can verify this for me real quick, I'd be grateful.

fyi, these forums have solved a lot of problems for me on Ubuntu.  I will place a noob how-to guide on getting an ftp server up and running once I iron out the bugs.

Thanks!

---

### Post by tgm4883 on 2007-07-01
Nope, did you forward the port?

---

### Post by 070107 on 2007-07-01
Dang.  Yeah, I made my router forward that port this computer.  I'm confident I did that part correctly, as I figured out how to do that sort of thing when getting my torrent program going.

I also use Firestarter so I told Firestarter that the port 1337 was ok as well.

What did I miss?  I'm pretty sure the IP is correct since that's what [http://whatsmyip.org/](http://whatsmyip.org/) is telling me. Hmm

---

### Post by tgm4883 on 2007-07-01
Just realized I can't even ping you

---

### Post by 070107 on 2007-07-01
The log is showing this (I xxxx'd out the IPs trying to connect in case someone doesn't want their IP posted here):

[INFO ]Open connection - xxx
[INFO ]Close connection : xxx - null
[INFO ]Open connection - xxx
[INFO ]Close connection : xxx - null
[INFO ]Open connection - xxx
[WARN ]Login failure - anonymous
[INFO ]Close connection : xxx - anonymous
[INFO ]Open connection - xxx
[WARN ]Login failure - anonymous
[INFO ]Close connection : xxx - anonymous

Does that help figure out what's going on with it?

---

### Post by 070107 on 2007-07-01
I can see a few different IPs logging in ... but no "looks fine to me" post yet ... so is it workin?  Thanks for all those who are trying to assist.

---

### Post by RRS on 2007-07-01
Tried pinging first, 80% (4 of 5) suscessfull

URL gets me loggon pop-up but 401 error on attempts to loggin

Maybe double check loggin and password?

Never tried to set up anything like this myself, so afraid I can't be of more help, sorry

---

### Post by PilotJLR on 2007-07-01
The server was up a second ago... I could login too. The server either froze when I gave the "ls" command, or maybe you're working on it now and restarted it...

Either way, the ftp server was responding a second ago

---

