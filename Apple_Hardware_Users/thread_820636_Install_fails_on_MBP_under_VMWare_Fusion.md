---
title: "Install fails on MBP under VMWare Fusion"
date: 2008-06-06
forum: Apple Hardware Users
---

### Post by DanGillis on 2008-06-06
I have a brand-new MacBook Pro 4,1 (Penryn) running OS X 10.5.3. I installed VMWare Fusion 1.1.3 and am now attempting to build a Ubuntu system. I have tried both 7.10-desktop-i386 and 8.04-desktop-i386. In both cases I get the same symptoms.

At installation time the keyboard does not work. The mouse works fine. I get sounds when clicking the keyboard which lead me to believe it's inhibited or locked. What I have done so far:

Searched the syslog
Changed the keyboard type in system preferences/keyboard/layout to MBP

When I initially got this error in Heron I searched on the VMWare site, and noticed that they only document 7.10 and lower, thus I downloaded Gibbon and tried again.

I apologize in advance if this is not the right forum for this question, I am a new user to this site.

---

### Post by DanGillis on 2008-06-06
Some screen grabs to show exactly where I'm at in the installation. I get to page 6 of 7, where you need to set up your username and pwd, and set the hostname for the computer - can't type anything so it's time to quit.

[http://www.flickr.com/photos/27417747@N04/2556676846](http://www.flickr.com/photos/27417747@N04/2556676846)

[http://www.flickr.com/photos/27417747@N04/2555854013](http://www.flickr.com/photos/27417747@N04/2555854013)

---

### Post by DanGillis on 2008-06-06
RESOLVED. I found the solution on the VMWare site, under the following link. Turns out my problem was with a software packaged called "Lotus Mobility Client", which evidently uses SecureInput

Shut down this software, and Ubuntu installs.

See Frequently Asked Questions about Fusion - [http://communities.vmware.com/docs/DOC-2890](http://communities.vmware.com/docs/DOC-2890)

Of course this opens up a whole slew of new problems :).

---

