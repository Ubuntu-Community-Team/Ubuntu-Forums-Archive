---
title: "pon vs wvdial and internet access"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by gonnoc on 2007-11-05
Hi,
I'm new to linux and ubuntu (but not that new to OS's and computer setup). Anyway and I'm trialing linux and the install (7.04) went fine (dual boot) but there is some trouble with an external dial-up modem setup.

I read the documentation which said I should run scan modem, get & install a driver then just follow instructions which I pretty much did (finding a modem driver was a nightmare I don't even think I succeeded but I found something I thought might be close). After all this nothing worked the Administration>Network setup was done, and I  edited the wvdial.conf file but still no connection or sign of even being on the right track.

Then I came across a site that said do it using    sudo pppconfig, then pon <provider name> to connect.
[http://ubuntuguide.org/wiki/Dapper#How_to_configure_network_connections](http://ubuntuguide.org/wiki/Dapper#How_to_configure_network_connections)
This method worked and I now have internet access.

I guess my question is what is wvdial for - and the Adminstration>Network GUI. Both of which have been reset to blank or minimal nonsense values by me so it appears the GUI setup seems completely independent of the pppconfig setup (etc/ppp/peers/<providername>, etc/chatscrpts/) and nonfunctional? I even disabled the modem driver I downloaded and installed and it still connects so I assume contrary to the documentation the modem driver wasn't necessary.

So how do the wvdial vs pppconfig connections differ? 
Its also a bit frustrating the GUI network utilities and bar icons don't reflect the actual connection status and what the actual setup is - is there anyway to tie them into the pppconfig setup and display what has actually been setup?

I didn't see anything about the pppconfig alternative in the documentation covering internet connections that came with ubuntu  -  it would have been really useful to have there.

Also while I'm here I have a windows app (SAS)  I use quite a lot is there any utility that will let me run that from Linux or will I have to boot into windows to do this?

Thanks in advance for any help or elucidation with these points
Gary

---

### Post by Bartender on 2007-11-06
See if this helps any with some of your questions
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

---

