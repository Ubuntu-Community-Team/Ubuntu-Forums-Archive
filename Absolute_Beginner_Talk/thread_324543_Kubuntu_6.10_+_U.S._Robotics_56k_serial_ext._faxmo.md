---
title: "Kubuntu 6.10 + U.S. Robotics 56k serial ext. faxmodem = no internet"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by Jack the R on 2006-12-23
I've been at this for better than an hour, reading through old threads, but no luck yet.

Kubuntu 6.10

U.S. Robotoics 56k serial external faxmodem, rs232, v.90 56k standard with x2 technology.  Yeah, it's old but I'm using it right now with windows.  No problems with the modem.

I've commented out the "auth" line in etc/ppp/option and put an empty resov.conf in /etc, as suggested in this thread:

[http://ubuntuforums.org/showthread.php?t=323138&highlight=external+modem](http://ubuntuforums.org/showthread.php?t=323138&highlight=external+modem)

I've tried following Bartender's instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=320949&highlight=external+modem](http://ubuntuforums.org/showthread.php?t=320949&highlight=external+modem)

> Then go into System>Administration>Networking and see if Ubuntu shows a new modem device. It should.

But I'm on Kubuntu and can't figure out what the KDE equivalent is.

I've run the lspci command and nothing suggestive of a U.S. Robotics modem comes up, though my winmodem is detected.

I have no idea how to check com ports to see which my modem might be hiding on.

I'm new to Kubuntu so please spell out all steps I must take in excruciating n00b detail ](*,) 

Thanks.

---

### Post by _duncan_ on 2006-12-24
Suggest you read this thread thoroughly. The key is setting the correct init string for the modem:

[http://www.ubuntuforums.org/showthread.php?t=271111]("http://www.ubuntuforums.org/showthread.php?t=271111") 

The 2nd link on my signature (Dial-Up Modem Wiki) might be helpful also to set up the dialer program.

Good luck!

---

### Post by ieee488 on 2006-12-24
The quickest way for you to find out which port Kubuntu thinks your modem is at is to use wvdialconf. Follow the directions in the DialUp HowTo.

Once you know which ttyS#, then you can switch to using kppp to dial out.

---

