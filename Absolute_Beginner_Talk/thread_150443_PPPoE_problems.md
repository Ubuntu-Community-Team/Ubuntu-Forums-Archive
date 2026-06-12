---
title: "PPPoE problems"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by kiff on 2006-03-26
Just installed Breezy this afternoon. It seems to work reasonably well, but I had a lot of problems connecting to the net using my ADSL modem. I followed the suggestions on the ADSL PPPoE page on the Ubuntu Wiki, but I couldn't run pppoeconf because it couldn't find a PPPoE access concentrator, whatever that is.

Eventually I followed the advise of gendibal in another post and disabled IPv6 in about:config for Firefox.

Now I can browse the web (hence my ability to write this post), but I still can't run pppoeconf. That wouldn't be a problem if I could check email or run synaptic, but I can't. When I try to update through the terminal I get the following message:

```
sudo apt-get update
Err http://security.ubuntu.com breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://archive.ubuntu.com breezy Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://archive.ubuntu.com breezy-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://archive.ubuntu.com breezy-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg  Could  not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gp g  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/Release. gpg  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release. gpg  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
```

Can anyone tell me what might be going on? ](*,)

---

### Post by RRS on 2006-03-26
What make/model modem do you have and who's  your IP?

Unlikely I can provide much help as a newbie myself but someone who can may need the xtra info.

When I installed breezy it performed a DHCP configuration during the install proccess (I had the modem and cables connected) and I had full I-net access with no further manual setup needed.

I've always been under the impression that PPPoE was handled by the modem or router so I can't understand why you should have to do any setup in breezy.

Also don't see why you can't access email if you're able to get online to browse. The problem with synaptic may be unrelated.

Wish I could offer some real help but I'm sure someone smarter then me will have some answers.

---

### Post by kiff on 2006-03-26
Thanks for trying.

I'm using a NetComm NB5 modem router, and my ISP is iPrimus (Australia).
Like you, I'm a little mystified as to why I can't use email or any other Internet related software (GAIM etc) apart from Firefox, nor Synaptic. 

Hopefully someone else will have an answer. :-)

---

### Post by kiff on 2006-03-26
I also tried the following action helpfully suggested by Gendibal:

> the other thing you might need to know is that if you can't get Synaptic to work, you may need to edit your /etc/dhcp3/dhclient.conf file.
Uncomment the line that starts "prepend domain-name-servers" and replace the default 127.0.0.1 with the dns servers of your ISP.......

I guessed that "uncomment" means to remove the # at the beginning of the line. Unfortunately that still doesn't seem to have helped. Anyone have any ideas?

---

