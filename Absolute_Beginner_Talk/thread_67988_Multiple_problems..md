---
title: "Multiple problems."
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by Alkor on 2005-09-21
I just installed Ubuntu Linux 5.1 and have encountered multiple problems.

1.  Unable to connect to Internet.  I go to “network connections” and setup Ethernet connection: DNS server, Gateway IP, Subnet Mask, IP etc.  Then I activate it and still can’t connect to Internet.  It does not give me any feedback, I can’t see if it is connected or not.  Is there any way to test connection?  Am I doing something wrong?
2.  Can’t access my other two harddrives (NTFS).  I go to “drives” (or something like that) and there is a button, “enable”.  I click on that button and it says “inaccessible”.  Same thing happens with other hard drive and partition.
3.  My sound card is detected but I can’t play music for some reason.  I get this repeating “drum sound” like it froze.

Thanks in advance.

---

### Post by aysiu on 2005-09-21
[QUOTE=Alkor]
2.  Can’t access my other two harddrives (NTFS).  I go to “drives” (or something like that) and there is a button, “enable”.  I click on that button and it says “inaccessible”.  Same thing happens with other hard drive and partition.[/QUOTE] Follow these instructions: [http://www.frankandjacq.com/ubuntuguide/5.04/index.html#windows](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#windows)

---

### Post by Alkor on 2005-09-21
[QUOTE=aysiu]Follow these instructions: [http://www.frankandjacq.com/ubuntuguide/5.04/index.html#windows](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#windows)[/QUOTE]
Thanks for reply.  I type that in command line then it asks me to enter my password but my keyboard does not respond to anything except for "enter".

---

### Post by matthew on 2005-09-21
[QUOTE=Alkor]Thanks for reply.  I type that in command line then it asks me to enter my password but my keyboard does not respond to anything except for "enter".[/QUOTE]
When you type a password in the terminal nothing will appear on the screen. This is so that if someone were standing behind you they could not see your password. It doesn't even print ****'s so that no one can see the password's length. I know it can be a bit confusing the first time you see that, but you really can type your password even though nothing is appearing on the screen. Type it slowly and carefully and hit <enter> and it should work.

---

### Post by Alkor on 2005-09-21
Ok this is what I do to configure Ethernet.
In "Networking" I click on "ethernet" and then "properties".
Then I choose "Static IP" and enter Gateway IP: 192.168.123.254, IP: 192.168.123.254, Mask: 255.255.255.0.
After that I click "Ok" and go to DNS section and add two IP adresses.
Activate the Ethernet(eth0).
After all of that I still can't access any of the websites.

I also tried choosing DHCP instead of Static IP and it does not work either.
So what am I doing wrong?

---

### Post by Alkor on 2005-09-23
Up

---

