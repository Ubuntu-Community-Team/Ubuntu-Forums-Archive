---
title: "firefox not responding"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by asg33 on 2007-03-07
hey, new to ubuntu and linux just got started on edgy eft last week. everything seem to be going good, and i've solved a lot of problems searching the forums, very helpful. i ran into a new problem today though. when i start up firefox, i can browser for about 5 min, and then i get the not responding fade to gray, where i can't do anything in firefox, then it comes back for about 30 seconds then back to not responding, this happens infinitely until i open the system manager and kill the firefox process. i really don't know what the problem is and i've searched the forums for something along those lines, and can't really find an answer. not sure where to start with this. any help would be greatly appreciated. 

ubuntu edgy eft (6.10)
p4 2.4 ghz, 1gb ram
cable modem, w/linksys wtrg54 router.
ati radeon 9200se

---

### Post by schwascore on 2007-03-07
We need more info in order to help. Open up a terminal session and run firefox.  Check the terminal output for any errors and post them.

---

### Post by asg33 on 2007-03-07
> **schwascore said:**
> We need more info in order to help. Open up a terminal session and run firefox.  Check the terminal output for any errors and post them.

will do, as soon as i get home. thanks for the response.

---

### Post by asg33 on 2007-03-07
ok been using firefox for a good 4 hours, everything seemed ok then it went into the "not responding" thing again. here's what my terminal said:

"DCOPClient::attachInternal. Attach failed Could not open network socket"

that just kept repeating. after i killed firefox, it still kept repeating. i rebooted and am using it now, but i'm positive it will happen again. any ideas? thanks in advance.

---

### Post by schwascore on 2007-03-07
Ok, we're in uncharted territory for me, but a quick google search for your error helped a little.  Seems as though the problem isn't necessarily with Firefox, but with the connection between Firefox and your network.  This is beyond my scope of knowledge, but at least we have narrowed down the problem.  Perhaps you could start to investigate your network connection.  If you have a wireless connection, that might be the smoking gun because of the poor driver support for many chipsets.  Good luck, sorry I can't do any more!

---

### Post by asg33 on 2007-03-07
> **schwascore said:**
> Ok, we're in uncharted territory for me, but a quick google search for your error helped a little.  Seems as though the problem isn't necessarily with Firefox, but with the connection between Firefox and your network.  This is beyond my scope of knowledge, but at least we have narrowed down the problem.  Perhaps you could start to investigate your network connection.  If you have a wireless connection, that might be the smoking gun because of the poor driver support for many chipsets.  Good luck, sorry I can't do any more!

i appreciate it, i did google it and couldn't fine anything either. i do have a wireless router, but my desktop (where i have ubuntu on) is hardwired to the router. i use the wireless for a laptop that's running xp. anyone else???

---

### Post by loki99 on 2007-12-02
Same problem over here. Firefox doesnt start properly and states the same error.


"DCOPClient::attachInternal. Attach failed Could not open network socket"

I'd be thankful for any solution!

---

### Post by loki99 on 2007-12-02
I found a temporarily fix for this in another thread. You have to run dcopserver in concole which fixes the issue until you log out. I simply autostart it for now, but there should be a proper fix for this, right?

---

### Post by frank002 on 2007-12-02
Is your problem only with Firefox? Have you tried Opera or Epiphany?

---

### Post by loki99 on 2007-12-03
> **frank002 said:**
> Is your problem only with Firefox? Have you tried Opera or Epiphany?

As far as I know it was only firefox. At least seamonkey did work out of the box.

---

