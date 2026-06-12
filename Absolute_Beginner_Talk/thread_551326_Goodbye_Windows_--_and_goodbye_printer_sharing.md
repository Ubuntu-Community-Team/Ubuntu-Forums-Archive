---
title: "Goodbye Windows -- and goodbye printer sharing?"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by ladasky on 2007-09-15
Hi folks,

I'm new to Ubuntu, but not a complete Unix novice.  I've never been root on my own Unix box (though I've read about sudo, and it seems as if no one actually is root on Ubuntu, at least not for very long?).

I have ditched Windows at last.  I've been wanting to do it for at least three years now.  While the computer that runs Ubuntu is a great standalone box, and talks to my router and the wider Internet, I've broken every other feature on my home network.  I need to get those features back.

My home setup consisted of two Windows 2000 systems, with one PowerBook G4 laptop thrown into the mix.  I have two questions which may belong in different forums.  You don't need to answer my questions here if you don't want -- just tell me which forums I should visit with each question, if that's more appropriate.  I'll cut and paste.

The most important network connection that I need to re-establish is the following one:

PowerBook G4 (Mac OS X) --> Ubuntu PC --> HP OfficeJet G55 printer

I had this working before, when the PC ran Windows.  Of course I just set it up once, almost two years ago, and then forgot what I did.  The Mac is still trying to talk to a Windows box through the old protocol, so of course it finds nothing.

On the Ubuntu side, the printer was automatically detected.  But I'm a little confused by what the CUPS database returns when it auto-detects.  It looks like it detects TWO printers -- "HP OfficeJet G55" and "HP OfficeJet_G55".  Notice the subtle difference in spelling?  Only the second selection enables local printing.  I'm not sure what the first selection is for.  They are not marked in any way that clearly indicates that they have a separate purpose, but there is a difference.

I got the HPLIP Toolbox installed, and attempted to configure the print settings through CUPS.  Up pops a web page.  Is this what a modern printer daemon looks like?  Still much to learn, have I.

Anyway, I click on the Administration Tab.  Basic Server Settings are on the right, and I select the checkbox marked "Share published printers connected to this system."  Up pops a dialog box which prompts me for a user name and password.  The only user/password combo I've defined at this point is my own, so I enter it.  Is this a sudo request?  If so, why does it look different than the sudo password box that appears in the middle of the screen when I'm installing software? 

Worse, when I enter the only user name and password that I've defined, why does the darn dialog box simply pop up again, as if I have done nothing?  The only way I can get this to stop is to click "Cancel" which then gives me a "401-Unauthorized" message.  Yet, when I return to the Administration page, it appears that the checkbox was successfully changed?  And while I'm no expert at reading logs, when I click on View Access Log I see what appears to be an error-free attempt to modify cupsd.conf -- here are some representative lines:

localhost - - [14/Sep/2007:18:58:36 -0700] "GET /admin/log/access_log HTTP/1.1" 200 21098 - -
localhost - - [14/Sep/2007:18:58:45 -0700] "POST / HTTP/1.1" 200 368 Get-Jobs successful-ok
localhost - - [14/Sep/2007:18:58:45 -0700] "POST / HTTP/1.1" 200 368 Get-Jobs successful-ok
localhost - - [14/Sep/2007:18:58:56 -0700] "POST /admin HTTP/1.1" 200 62 - -
localhost - - [14/Sep/2007:18:58:56 -0700] "PUT /admin/conf/cupsd.conf HTTP/1.1" 401 0 - -
localhost - - [14/Sep/2007:18:58:56 -0700] "POST /admin HTTP/1.1" 401 62 - -
localhost - - [14/Sep/2007:18:58:56 -0700] "POST /admin HTTP/1.1" 200 62 - -
localhost - - [14/Sep/2007:18:59:05 -0700] "POST /admin HTTP/1.1" 200 62 - -
localhost - - [14/Sep/2007:18:59:06 -0700] "PUT /admin/conf/cupsd.conf HTTP/1.1" 401 0 - -
localhost - - [14/Sep/2007:18:59:05 -0700] "POST /admin HTTP/1.1" 401 62 - -
localhost - - [14/Sep/2007:18:59:05 -0700] "POST /admin HTTP/1.1" 200 62 - -
localhost - - [14/Sep/2007:18:59:15 -0700] "POST / HTTP/1.1" 200 368 Get-Jobs successful-ok
localhost - - [14/Sep/2007:18:59:15 -0700] "POST / HTTP/1.1" 200 368 Get-Jobs successful-ok
localhost - - [14/Sep/2007:18:59:16 -0700] "GET /admin HTTP/1.1" 200 0 - -
localhost - - [14/Sep/2007:18:59:16 -0700] "POST / HTTP/1.1" 200 2070 CUPS-Get-Devices -
localhost - - [14/Sep/2007:18:59:16 -0700] "GET /admin HTTP/1.1" 200 6476 - -
localhost - - [14/Sep/2007:18:59:17 -0700] "GET /cups.css HTTP/1.1" 304 0 - - 

So, I'm confused.  Have I shared the printer, or haven't I?  When I try to locate the printer from the PowerBook, I'm not finding it.

Now, one more thing, which is possibly unrelated to printers, but I'm not sure.  This may only be a file sharing issue.  My PowerBook was configured for file sharing with the Windows machines.  From the Ubuntu machine, I can see the PowerBook but I can no longer log in.  Under System > Administration > Networking, I can see the PowerBook's icon.  If I click on this, the button at the upper left of the Network File Browser window reads, &#8220;Windows Network &#8211; PowerBook.&#8221;  But I don't get the login prompt I used to get.  I can reach the same dead-end by clicking the following chain of links from the Network File Browser: Windows Network > workgroup > PowerBook.

If the printing and file sharing problems are related, I'm guessing it's because I configured the PowerBook to do all of its communicating using Windows protocols.

Any advice is appreciated.  &#8220;Buy a book&#8221; would be appropriate advice too, if the book actually discusses my problems.  Thanks!

---

### Post by mikeyphi on 2007-09-15
You might have done this already:-
If the printer is directly connected to your Ubuntu computer - open System/Administration/Printing select the Global settings tab - ensure Share printers is ticked.
For File sharing - have you installed you installed Samba/NFS?
Can't help with Network settings for Mac - but when I set up windows/ubuntu I just used the Wins server options on ubuntu. 
Isn't OS X unix based? if so there should be a simple way for communication!

---

### Post by ladasky on 2007-09-16
Thanks for your note, Mikeyphi.  Unfortunately my problems aren't solved yet.

I hadn't tried the Global Settings tab under System/Administration/Printing.  But you use Ubuntu 7.04 and I selected 6.06 (more on why I did this at the end of this post).  The only item under the Global Settings menu in 6.06 reads "Detect LAN Printers."  This doesn't seem to serve the purpose of printer sharing -- rather, it looks like it's meant to search for remote printers?

When I click Detect LAN Printers, I get a sudo password request, and then I get a warning: "Enabling LAN printers detection will open port 631 on your system. This exposes you to the risk of exploiting any security vulnerabilities of the printing system. Remote attackers could potentially gain access to your system with the privileges of the 'cupsys' user."

I proceeded anyway.  Meanwhile, I found this page:

[https://help.ubuntu.com/community/NetworkPrintingFromMacOSX](https://help.ubuntu.com/community/NetworkPrintingFromMacOSX)

That page says to do a port scan on your own machine in order to confirm that your printer port is open.  I tried this.  The port scan window remains blank.  I also tried a port scan on the Mac and I can see a few open ports there.

As for file sharing between the Mac and my Ubuntu desktop machine -- yes, I thought it would be more automatic and simple, because OS X is Linux under the hood.  I didn't think I would have to install anything extra to make that connection work.  I may be wrong.  It looks like I need to tweak CUPS on the Mac side for printing.  Meanwhile, port 631 on my Ubuntu machine appears to be closed still.

So now, is there any reason that I shouldn't be running 7.04?  I chose 6.06 because I wanted to install Scibuntu:

[http://scibuntu.sourceforge.net/index.html](http://scibuntu.sourceforge.net/index.html)

Their web pages said to use 6.06.  HOWEVER, if I understand Ubuntu correctly, Scibuntu is just a fancy Package Manager-type script?  Is there any reason to expect that an application like GROMACS will NOT run on top of 7.04?  GROMACS is the only application I really need, I can wait for the rest.  And I can install and compile GROMACS manually if I must, skipping Scibuntu.

I'd like to follow the directions that you and that OS X printer sharing page have provided, but 6.06 appears to be missing a few pieces of the puzzle.  Maybe I should just upgrade and try again?  Advice is, once again, appreciated!

---

### Post by Sayers on 2007-09-16
Comming from debian where I had to do this all terminal based... Anywho set it yes as share printers and what that is going to do is share all your printers via localhost:631 . So ifconfig lets say ifconfig gives you an example

inet addr: 1.1.1

Go in firefox to 1.1.1:631 then login and find the printer then it will be in the brower like 1.1.1/printers/Printer92X just add ipp://1.1.1/printers/Printer92X to the machine your doing this on and it should work. 

Sorry if this was hard to understand.

---

### Post by perce on 2007-09-16
You have to change the line  
Listen 127.0.0.1:631
to
Listen 631
in your file /etc/cups/cupsd.conf
in order to share printers on your LAN. At least this is what selecting share printers on Feisty does. After this change you should restart cups with sudo /etc/init.d/cupsys stop followed by /etc/init.d/cupsys start (or just a reboot à la Windows). Unfortunately I can't tell you if here are other changes you have to do. 

Once the Linux machine shares the printers, OS X should see them, because it uses cups too. Or at most you must tell it to browse the LAN to look for printers. Good luck.

---

### Post by ridgeland on 2007-10-14
Thanks Mikeyphi and Sayers.
I was searching for how to share printers here at home between two PCs both using Ubuntu.
I think just turning on both "Global" options on both PCs was all it took.
On the second PC I turned on Global -> [x] Share Printers.  Then from the first PC I went to 192.168.123.112:631 and saw the CUPS printers for the second PC.  I clicked on the printer I wanted then copied the address.  Here it was 192.168.123.112:631/printers/i560 so on the first PC I created a new printer with that address.  That got a test page to print.  I think if I had been patient though just the Global settings would have done it, as the second PC popped up the first PC's printer as soon as all the Global settings were checked ON.
Thanks again.

---

### Post by measekite on 2007-10-16
> **ridgeland said:**
> Thanks Mikeyphi and Sayers.
I was searching for how to share printers here at home between two PCs both using Ubuntu.
I think just turning on both "Global" options on both PCs was all it took.
On the second PC I turned on Global -> [x] Share Printers.  Then from the first PC I went to 192.168.123.112:631 and saw the CUPS printers for the second PC.  I clicked on the printer I wanted then copied the address.  Here it was 192.168.123.112:631/printers/i560 so on the first PC I created a new printer with that address.  That got a test page to print.  I think if I had been patient though just the Global settings would have done it, as the second PC popped up the first PC's printer as soon as all the Global settings were checked ON.
Thanks again.

I would like to know if that worked properly.  If so I see a potential problem.  If you host printer gets its IP address from a DHCP server you may have a different IP address the next time it is renewed.  If that happens then hard coding the printer IP address [COLOR=Plum]192.168.123.112:631/printers/i560[/COLOR] will cause the printer to be disabled.

---

### Post by ridgeland on 2007-10-16
In the past we had the issue of floating IP addresses from our router (US Robotics) but I used the router's setup program and fixed the local address (by MAC?).  Now 192.168.123.112 is always the same PC.  We've used fixed addresses so long I just take it for granted.  Fixed addresses made NFS very easy.

---

### Post by strabes on 2007-10-17
I use the ip method and have never had a problem. I get the ip of the host machine using ifconfig, then add the printer to the computer from which I'm trying to print using this sort of http address:```
http://ip.of.host.comp:631/printers/nameofprinter
```

---

