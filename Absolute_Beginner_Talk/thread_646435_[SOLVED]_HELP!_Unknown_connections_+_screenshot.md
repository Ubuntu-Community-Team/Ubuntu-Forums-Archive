---
title: "[SOLVED] HELP! Unknown connections + screenshot"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by kernel tom on 2007-12-21
Hey all, 

I need help, big time.  Whenever I use a torrent (my client is ktorrent) I end up with connections that just seem to hang, after the download is complete.  This is after I stop seeding too!.  The service/program both register as Unkown in Firestarter which I've been using to manage my iptables.  No matter what I do I can't get rid of these connections, and I'm convinced I should be able to.

Is there a setting i'm missing in ktorrent? Like a clean up connections after download is complete?

Does anyone else have this problem? 

Any ideas whatsoever?

oh and by the way... when I run "netstat" none of these connections show... at all

I attached a screen shot, I am pretty sure these connections are from torrents, but I want them to be gone when I close ktorrent, and I'm done downloading/seeding

i also attached the output of "netstat"

thanks a lot guys, this has been a huge problem for me,
tom

---

### Post by tehet on 2007-12-21
You can use sudo tcpdump to see if there's actually any traffic. If not, perhaps Firestarter doesn't properly update the list of connections.

---

### Post by Vadi on 2007-12-21
Hm, another way to check what ports do you have open is to go to system, administration, network tools, port scan, type **localhost** and scan. That'll show which ones are open.

---

### Post by kernel tom on 2007-12-21
yeah there is absolutely no traffic to/from these connections....

I'm guessing that these are just outgoing connections that haven't timed out yet?  And eventually they will timeout?

-kt

---

### Post by maddog39 on 2007-12-21
Yea I get random connections like that all the time. I've run wireshark on my connection many times and usually they mean nothing. I personally wouldnt worry about it if I were you.

---

### Post by seventhc on 2007-12-21
If you right click on those from firestarter it will let you look up the host name.

---

### Post by kernel tom on 2007-12-21
> **maddog39 said:**
> Yea I get random connections like that all the time. I've run wireshark on my connection many times and usually they mean nothing. I personally wouldnt worry about it if I were you.

Yeah I don't think I'm going to worry about them... I would like to know how to kill these outbound connections if I feel the need to however.

---

