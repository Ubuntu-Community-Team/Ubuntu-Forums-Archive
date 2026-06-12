---
title: "Serial Modem- Not the usual problem"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by LaidbackBill on 2007-08-12
After three months or so of working with no problems, the modem would connect but then drop the connection.  After becoming disgruntled for a couple of days and leaving it alone, which didn't fix the problem by the way, I went into sys>admin>networking.  After playing with the settings I found that I had lost the DNS settings and re-entered them.The applet didn't hold the setting after turning off machine and I would have to re-enter on each cold boot.  Well I tried to enter the DNS #s differently to see if they would stick, only to get a bug report and no connection.  How do I come out of this dilemma?  
The modem dials now but will not connect to firefox or evolution.  Because of this I can't send the bug report on the crash and I can't get into "networking" to change the borked settings.  What to do? Suggestions?

Bill

---

### Post by mgarces on 2007-08-16
From what I can figure out, you are able to dial out; modem connects; no internet; Right?
Start by pinging some domain, like [www.google.com](www.google.com) and a IP addres (google -> 216.239.59.147) whats the error for each case?

Please post your */etc/resolv.conf*
Perhaps I did not get your problem, but it looks like a DNS problem... :-?

---

### Post by _duncan_ on 2007-08-17
The System>Administration>Network application used to work well until Dapper 6.06. Some bugs were introduced starting with Edgy 6.10 and carried over to Feisty 7.04. The problems were as you described:  a lot of settings are not kept by the application.

Fortunately there are alternative dialer programs available: wvdial, pppconfig (with pon & poff), gnome-ppp and KPPP.

The first 2 (wvdial and pppconfig) are terminal-based and comes with the default ubuntu install, so they are particularly useful for standalone computers without internet connection.

The last 2 (gnome-ppp and KPPP) are GUI-based, but you have to download the necessary packages to install.

Click on the 2nd link of my signature (Dial-Up Modem Wiki) for details on how to get these dialer programs to work.


PS. Some serial modems require hardware-specific initialization strings for authentication to work, although most should work with the default init strings provided by the dialer program.

---

### Post by LaidbackBill on 2007-08-21
Thanks for the responses.  I haven"t checked back in a week or so.  The modem works fine now, but somehow when I was trying to get the dns numbers reentered in the administration network application I somehow crashed the program and now when I try to get there all I get is a "bug report" with the notification that the program has crashed.  I really don't want to reinstall the os if I don't have to.  I was hoping there might be a way to install the network applet from the install cd  thus saving the hassle of reinstalling the video drivers, printer drivers, etc.  A couple of months ago it would have been easier but it's been a while and I think it would take a considerable amount of time as I didn't log all the procedures and would have to start over.

Thanks Bill

---

