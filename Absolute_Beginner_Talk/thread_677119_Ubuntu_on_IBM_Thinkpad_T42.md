---
title: "Ubuntu on IBM Thinkpad T42"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Fr4nk on 2008-01-24
Dear Ubuntu Forum Experts,

My question is can my system run Ubuntu and continue to perform my usual tasks with the proposed software?

If I could appeal to the Linux Gods on this wonderful forum for some of their knowledge and expertise that would be great.

Also any known issues with the above, important thoughts or ANY other comments are welcome.

Many thanks for your time, it is much appreciated.

Frank.

Current System:
- IBM Thinkpad T43 Laptop
- 1.86 GHz
- 1.0 GB RAm
- Intel 802.11 B/G Wireless
- 60GB Harddrive
- 14.1" TFT 1024*768 Display
- Windows XP SP2
- Avast Pro 4.7.1098
- Zonealarm Pro 7.0.462.000
- Microsoft Office XP
- Firefox 2.0.0.11

Usual Tasks:
- Surfing the web with Firefox
- Writing documents with Microsft Word
- Designing spreadsheets with Microsoft Excel
- Download photos from holidays from my Canon A410 digital camera

Proposed Software:
- Ubuntu 7.10
- Avast Pro 4.7.1098
- Zonealarm Pro 7.0.462.000
- Open office 2.3.1
- Firefox 2.0.0.11
- Software for my Canon A410 ?!?!?!

---

### Post by wolfen69 on 2008-01-24
you should not have any problems running ubuntu. however, you will not need a firewall or anti-virus.(linux has a built in firewall and there are basically no virii written for linux. nice, huh?) this isnt windows.

---

### Post by pw2buz on 2008-01-24
I'd recommend starting with Ubuntu 7.04 (Feisty Fawn).  I've seen lots of complaints about 7.10.  Run the livecd first (i.e. do not install from the CD, just run Ubuntu from the CD).  See if your wireless and ethernet are recognized.  Wireless can be difficult to get working, at least for newcomers such as me.  My Ubuntu computer (dual boots Ubuntu 7.04 and Windows XP) is a Thinkpad T41---the livecd detected its ethernet and wireless easily (wireless is a miniPCI with an Atheros chipset.

Search the Absolute Beginner Talk forum for my posts (username pw2buz) to see what fixed wireless for me.

Pw2buz

---

### Post by louieb on 2008-01-24
T30 running Ubuntu 7.10. here
Two great resources for Linux on a think pad
[ThinkWiki - Linux on ThinkPad]("http://thinkwiki.org/wiki/ThinkWiki")
[ThinkPad Forum ]("http://forum.thinkpads.com/")

---

### Post by aaronjab on 2008-02-01
IBM T43- Running Gutsy Gibbon (7.10)

My wireless network adapter worked instantly-

I installed Windoz 2k3 as a VM... Vmware Server works great BTW.

My only issue is the display- Can't seem to tweak the resolution properly. It only likes 1024*768.. If I switch it to 1280*1024, I lose part of the screen- meaning when I move my mouse down towards the bottom right hand side of the screen, the whole display moves... Very strange... I've played with other drivers but the all screw X up... Oh well.

I'm currently trying to get the integrated fingerprint reader to work...

-Cheers

---

### Post by Pilkjaer on 2008-02-21
> **aaronjab said:**
> IBM T43- Running Gutsy Gibbon (7.10)

My wireless network adapter worked instantly-

I installed Windoz 2k3 as a VM... Vmware Server works great BTW.

My only issue is the display- Can't seem to tweak the resolution properly. It only likes 1024*768.. If I switch it to 1280*1024, I lose part of the screen- meaning when I move my mouse down towards the bottom right hand side of the screen, the whole display moves... Very strange... I've played with other drivers but the all screw X up... Oh well.

I'm currently trying to get the integrated fingerprint reader to work...

-Cheers

try to install driver for your graphic card. ATI driver can be found here: [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)
there you download like 50MB *.run file. you need to run it from Terminal as root. you can run it later by browsing to the directory and typing ```
sudo ./ati_driver_name.run
```
also before that you need to make the .run file executeable. Right-click, select properties and check "executeable".

I'm running T42 and have almost no problems at all with Gutsy Gibbon (7.10). The only thing unsolved at the moment - scrolling with UltraNavi. Middle key not functioning properly. Also, keyboard layout mismatches.

---

### Post by Pilkjaer on 2008-02-21
> **louieb said:**
> T30 running Ubuntu 7.10. here
Two great resources for Linux on a think pad
[ThinkWiki - Linux on ThinkPad]("http://thinkwiki.org/wiki/ThinkWiki")
[ThinkPad Forum ]("http://forum.thinkpads.com/")

Thanks a lot! Great links for ThinkPad-users.Especially [http://thinkwiki.org/wiki/Drivers](http://thinkwiki.org/wiki/Drivers) :) a real time-saver.

---

### Post by Dewnutt on 2008-03-15
Thanks for the links to the thinkpad sites. They will be very helpful. 

here is what I have put Ubuntu 7.10 on. 


Current System:
- IBM Thinkpad T30 Laptop
- 1.80 GHz
- 2.0 GB RAm
- Linksys Wireless
- 40GB Harddrive
- Windows XP SP2
- Symantec Corp 10.X AV
- Zonealarm Pro 6.5
- Microsoft Office 2007
- Firefox 2.0.0.9

Now that that is out of the way, and I am a complete n00b here. I have to go figure out how to use this OS, and figure out what is and isn't working. Would one of you all be willing to direct me to the place where I can see what of my hardware is going to need a bit of attention? From what little I have read on this OS, I am pretty sure that I will grow to like it. Though, MS has put out such a fine product, that I am able to survive on trying to keep their OS's alive and functional. Thanks in advance for any ideas or help that you are able to provide.

---

### Post by urwatuis on 2008-03-16
I have a T23 PIII 1.2Ghz 768MB ram and a 40 GB hd and Ubuntu 7.10 running fine. I had display roblems when I tried to install until I chose F4 VGA and set the resolution to 1024x768. Then the install went smooth and it runs like a champ. I had to install packages to get Rhythmbox to play mp3's but no biggie I guess. I would like to know if there are any anti spyware programs or cookie blockers for linux. I like Spybot for Windows. Is there anything like that for Ubuntu?

---

