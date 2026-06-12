---
title: "Basic problem setting up net access"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by Pedal_Pusher on 2007-02-22
I'm an absolute beginner and I have problems accessing the internet reliably.

My setup is 2 PCs the first is running XP Home and Ubuntu 6.10 (since yesterday).  The second is running XP Pro and they are both connected via ethernet to a D-Link DSL-504T ADSL Router which is plugged into my ISP.

Both machines access the internet and run Firefox etc fine under XP.

When I try to run Firefox under Ubuntu it almost always hangs when trying to load the home page.  Very occasionally it loads the home page but then hangs after I have linked through to the next page.

Update Manager shows 'Downloading file 1 of 9' then waits for a long time before giving me 9 failure messages followed by 'The repository might be no longer available or could not be contacted because of network problems'.

The dual boot machine seems to be 192.168.1.2  It will ping 192.168.1.1 (the router) and 192.168.1.3 (the XP Pro machine) quite happily.

Any suggestions as to what I have overlooked and should change will be most welcome.

---

### Post by Ben Sprinkle on 2007-02-22
> **Pedal_Pusher said:**
> I'm an absolute beginner and I have problems accessing the internet reliably.

My setup is 2 PCs the first is running XP Home and Ubuntu 6.10 (since yesterday).  The second is running XP Pro and they are both connected via ethernet to a D-Link DSL-504T ADSL Router which is plugged into my ISP.

Both machines access the internet and run Firefox etc fine under XP.

When I try to run Firefox under Ubuntu it almost always hangs when trying to load the home page.  Very occasionally it loads the home page but then hangs after I have linked through to the next page.

Update Manager shows 'Downloading file 1 of 9' then waits for a long time before giving me 9 failure messages followed by 'The repository might be no longer available or could not be contacted because of network problems'.

The dual boot machine seems to be 192.168.1.2  It will ping 192.168.1.1 (the router) and 192.168.1.3 (the XP Pro machine) quite happily.

Any suggestions as to what I have overlooked and should change will be most welcome.
1. Renew your dhcp in your router. (Usually to get there type your gateway in firefox or something)
2. Double click the network icon > configure > disable > enable
It will renable your internet with a fresh ip. This may solve the problem.

---

### Post by gudy1024 on 2007-02-22
[http://ubuntuforums.org/showthread.php?t=367566](http://ubuntuforums.org/showthread.php?t=367566)

success :))))))))

---

### Post by Pedal_Pusher on 2007-02-22
Hi Ben and Gudy,

Thanks for the quick replies - but unfortunately neither seems to have solved my problem.

---

### Post by Ben Sprinkle on 2007-02-22
Reset your router and modem if you have one. Try that and see if it helps.

---

### Post by Pedal_Pusher on 2007-02-22
I powered everything off, unplugged the router and started up from scratch.
Starting Firefox under Ubuntu just hung 'connecting to news.bbc.co.uk'.

I then started Firefox on th XP Pro machine, went back to the the dual boot and tried again.  It worked for about 2 minutes and then gave me the 'connection has timed out' message.

The solution must be close - but what ?

---

### Post by Pedal_Pusher on 2007-02-22
Following a suggestion from igknighted in another thread I tried :-

ping -c 5 [www.gentoo.org](www.gentoo.org)

It worked OK (zero packets lost).

---

### Post by gudy1024 on 2007-02-22
have you truly edit the configxxxx-386 in your /boot dir? because its exact the same problem I had

adsl router.... IPv6 :(

keep in mind after a system upgrade the config file  can be newer, I begon with *23-386... then after upgrade it was *28-386 

pls check
gudy

---

### Post by Pedal_Pusher on 2007-02-22
Gudy,

I used gedit to change the boot/config-2.6.17-10-generic file under the File System.

In the /boot directory there were only 6 files and one subdirectory (grub).  This was the only config file so I thought it had to be the one.

Edit .....

I found some info in a thread from mikeman ( #367498 )  which had been supplied by ubunutgoz :-

try disabling ipv6

a - in FIREFOX browser type about:config
b - in the Filter bar (just below address bar) type ipv6
c - in the next window down (preferences), you'll see a single line network.disable.Ipv6
, double click until it is bold and the value is true.

I did this and now firefox seems to work OK but Update Manager still fails.

I am beginning to think that I have an issue with the router (D-Link DSL-504T) as it seems to be a common link in other similar threads and is now a discontinued model.

---

