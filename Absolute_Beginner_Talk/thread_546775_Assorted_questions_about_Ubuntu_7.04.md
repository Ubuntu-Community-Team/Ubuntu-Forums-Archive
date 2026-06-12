---
title: "Assorted questions about Ubuntu 7.04"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Danddyesu on 2007-09-09
Hello Forum Members:

I am new to Linux, and have just downloaded Ubuntu 7.04.  I was hoping that you might offer some recommendations and/or insights regarding a few questions I have.  In considering the following questions, if you feel that I should have downloaded a different distro, please let me know.  Let me thank you in advance for your assistance, D.

I am currently using what I believe is referred to as a dual boot, because I am not ready to completely leave Windows XP at this point.  The computer I installed Ubuntu 7.04 on is our second computer, and is still connected (through Windows XP) to the Internet via a wireless home network.  Our other computer has the direct DSL connection, and runs only XP.

My problem is that I can’t get internet access through Ubuntu 7.04.  When I go into network setting in Ubuntu 7.04, there is no option for wireless connection, only wired connection or modem. 

1.	Should I have downloaded a different distro?  Perhaps, part of the problem is that I have a locked home network, using NetGear Wireless.  Is it possible that Ubuntu 7.04 does not have option for wireless connection because my network is locked and can’t be seen?
2.	In a related question, will I be able to access the internet with the dual boot set up while I am in either Ubuntu 7.04 or XP.  That is, will I be forced to choose one or the other operating system to go online?  
3.	Are all my programs (e.g., WordPerfect Office X3, Quicken, Palm Pilot, etc.) available or “usable” through Ubuntu 7.04, even though they are installed and “running” under XP? 
4.	I just bought ZoneAlarm to update my antivirus and firewall.  Do I have to install it in both XP and Ubuntu 7.04, or just in XP?
5.	We are trying out Linux because of the “bloat” in XP which slowed a once very quick and powerful computer, and because we can no longer open PDF files with Adobe.  Will these be problems under Ubuntu 7.04?
6.	And, finally, can I start Ubuntu 7.04 without having to log in and enter my password each time?

Thank you, D.

---

### Post by Graphite on 2007-09-09
I'm not an expert by any means, but:

2) My network cards (one wireless and one wired) both work flawlessly under both Ubuntu 6.06 and Windows XP; I can access the net from whichever OS I happen to have booted up. As long as Ubuntu has a driver for your network card, there shouldn't be any need to choose.

3)You won't normally be able to run Windows programs under Ubuntu without a minor bit of fiddling. You'll need to use a program WINE ([www.winehq.com](www.winehq.com)) or something similar to run them. How is your windows partition formatted? If it's in FAT32, you should be able to see the files from your Ubuntu install. If it's in NTFS you'll find it more difficult, although probably not impossible.

4) As I understand it, the risk of your Ubuntu install becoming infected with a virus is negligable. This is due to a combination of good security design and effectively no viruses currently existing "in the wild". Also, the built-in firewall is reputed to be very good. If you want Zonealarm's functions to protect your Ubuntu install then you'll need to install it under Ubuntu; however, I think it's pretty much redundant. If you want to play with the settings of Ubuntu's biult-in firewall, install and run its GUI, called "Firestarter".

I hope some of that helps! If someone contradicts me they're probably right; I'm still learning all this stuff!

---

### Post by overdrank on 2007-09-09
> **Danddyesu said:**
> Hello Forum Members:

I am new to Linux, and have just downloaded Ubuntu 7.04.  I was hoping that you might offer some recommendations and/or insights regarding a few questions I have.  In considering the following questions, if you feel that I should have downloaded a different distro, please let me know.  Let me thank you in advance for your assistance, D.

I am currently using what I believe is referred to as a dual boot, because I am not ready to completely leave Windows XP at this point.  The computer I installed Ubuntu 7.04 on is our second computer, and is still connected (through Windows XP) to the Internet via a wireless home network.  Our other computer has the direct DSL connection, and runs only XP.

My problem is that I can’t get internet access through Ubuntu 7.04.  When I go into network setting in Ubuntu 7.04, there is no option for wireless connection, only wired connection or modem. 

1.	Should I have downloaded a different distro?  Perhaps, part of the problem is that I have a locked home network, using NetGear Wireless.  Is it possible that Ubuntu 7.04 does not have option for wireless connection because my network is locked and can’t be seen?
2.	In a related question, will I be able to access the internet with the dual boot set up while I am in either Ubuntu 7.04 or XP.  That is, will I be forced to choose one or the other operating system to go online?  
3.	Are all my programs (e.g., WordPerfect Office X3, Quicken, Palm Pilot, etc.) available or “usable” through Ubuntu 7.04, even though they are installed and “running” under XP? 
4.	I just bought ZoneAlarm to update my antivirus and firewall.  Do I have to install it in both XP and Ubuntu 7.04, or just in XP?
5.	We are trying out Linux because of the “bloat” in XP which slowed a once very quick and powerful computer, and because we can no longer open PDF files with Adobe.  Will these be problems under Ubuntu 7.04?
6.	And, finally, can I start Ubuntu 7.04 without having to log in and enter my password each time?

Thank you, D.

Hi and welcome 
1. If you can post the out put of the command
```
lscpi
```
In the terminal located under applications, accessories, terminal This will tell us your wireless
card and we can maybe help from there. 
2. Hopefully not, we maybe able to help with the wireless
3. Hi your programs on xp are just that on xp. Ubuntu can read and write to ntfs file systems with a little tweaking. You may have to search to find a comparable program that you use in xp.
4. No need for anti-virus in linux  
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)
5. I have not heard of any issues pertaining to that issue.
6. Yes you can auto login which is under system, administration, login window. Then under the security tab check enable auto login and then from the drop down window select the user name. and then close. Good luck!

---

### Post by Danddyesu on 2007-09-09
Graphite, you rock. Thank you.

---

### Post by mikewhatever on 2007-09-09
> 1. Should I have downloaded a different distro? Perhaps, part of the problem is that I have a locked home network, using NetGear Wireless. Is it possible that Ubuntu 7.04 does not have option for wireless connection because my network is locked and can&#8217;t be seen?

Ubuntu is a good linux distribution, but if it does not work on your hardware or you do not like it for some reason, do consider downloading another distro. Meanwhile, provide information about the wireless card. 

> 2. In a related question, will I be able to access the internet with the dual boot set up while I am in either Ubuntu 7.04 or XP. That is, will I be forced to choose one or the other operating system to go online?

Yes, you'll get a choice of which of the OSs to boot, but it is not related to whether or not you want to go on line.

> 3. Are all my programs (e.g., WordPerfect Office X3, Quicken, Palm Pilot, etc.) available or &#8220;usable&#8221; through Ubuntu 7.04, even though they are installed and &#8220;running&#8221; under XP?

No. The two OSs are completely isolated residing on separate partition. Moreover, windows programs do not work natively on linux.

> 4. I just bought ZoneAlarm to update my antivirus and firewall. Do I have to install it in both XP and Ubuntu 7.04, or just in XP?

No. There is no need for ZA on Ubuntu, plus the version you must have bought is for XP.

> 5. We are trying out Linux because of the &#8220;bloat&#8221; in XP which slowed a once very quick and powerful computer, and because we can no longer open PDF files with Adobe. Will these be problems under Ubuntu 7.04?

Every OS requires a certain amount of maintenance, otherwise it will slow down and things might stop working. It might also happen on Ubuntu.

> 6. And, finally, can I start Ubuntu 7.04 without having to log in and enter my password each time?

Yes, but to use Ubuntu, you'll still need to know your password.

---

### Post by Danddyesu on 2007-09-09
Thanks, Mikewhatever!

---

### Post by Tautoa on 2007-09-09
Looks like your questions were answered already, but it can't hurt to add another opinion, especially since I was asking the same sort of questions a couple of months ago :)

If you have two or more operating systems on one computer, then yes, that is what we mean by dual boot :) I had an XP/Ubuntu dual boot setup myself when I started out... I got rid of XP entirely about three days ago... it's a good feeling :)

I don't think I can help with the wireless issue, having never had a problem with my own. But, I also have a wireless network, with a Netgear router, and mine is also locked, hidden, password protected and just about every other security measure in place, so there's no reason why yours shouldn't work too :)
Luckily, you won't be forced to choose between XP and Ubuntu for your internet access, you can use either, its just a matter of getting the wireless working.

Some programs that you might have used on Windows, also have Linux equivalents. I think its fair to say that Word Perfect won't ever have one... but there are other programs that do the same job and have a similar interface to help you switch. Try OpenOffice. If there is a program that you just have to have, WINE is a good option, just make sure you read the help stuff first.

Of course, you shouldn't underestimate the determine of virus-creators to cause problems, but thankfully, they have more or less ignored Linux in favour of some of the more vulnerable operating systems (I know, I shouldn't laugh...)

I did try a program for PDFfiles, I forget the name, but it was pretty good... I'm sure a quick search of the forums will help you out there :)

I'm not sure about Ubuntu, but certainly in Kubuntu, you can set it so that it automatically logs in when you turn the computer on... although some security experts will frown upon this :) But don't worry about Kubuntu just yet, there's plenty of time to mess with window managers when you have the wireless working and an (Open)Office suite up and running.

On that note, welcome to Ubuntu, to UbuntuForums, to quick operating systems, and that warm feeling that you get from open source software :)
I should go now, before I scare the new people away...

---

### Post by Danddyesu on 2007-09-10
Dear Tautoa:

Thank you for the kind words.  Best wishes.

---

### Post by louieb on 2007-09-10
> **Danddyesu said:**
> 
1.    Should I have downloaded a different distro?  Perhaps, part of the problem is that I have a locked home network, using NetGear Wireless.  Is it possible that Ubuntu 7.04 does not have option for wireless connection because my network is locked and can’t be seen?


 
Still should have picked up that you have a wireless card. If its not listed under System>administration>network.  please follow overdrank's sugestion and post a list of your hardware only he fat fingered it :-s should be** lspci. **

Once you get Ubuntu to find you wireless card. Then we can help you get it set up form there.

---

