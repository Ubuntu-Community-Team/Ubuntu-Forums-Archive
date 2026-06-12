---
title: "Having trouble with ndiswrapper"
date: 2005-07-23
forum: Absolute Beginner Talk
---

### Post by Rhadryn on 2005-07-23
I haven't been able to get on the internet on my laptop, which has ubuntu.  I have followed the instructions for ndiswrapper up until I am supposed to install the .inf file.  I tried bcmw15.inf and one other one, and neither of them worked apparently.  I don't know how to figure out the correct .inf file.  My wireless card is Xircom 32-bit.

---

### Post by poofyhairguy on 2005-07-23
[QUOTE=Rhadryn]I haven't been able to get on the internet on my laptop, which has ubuntu.  I have followed the instructions for ndiswrapper up until I am supposed to install the .inf file.  I tried bcmw15.inf and one other one, and neither of them worked apparently.  I don't know how to figure out the correct .inf file.  My wireless card is Xircom 32-bit.[/QUOTE]

This place has the correct files:

[http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php)

---

### Post by byen on 2005-07-23
[QUOTE=Rhadryn]I haven't been able to get on the internet on my laptop, which has ubuntu.  I have followed the instructions for ndiswrapper up until I am supposed to install the .inf file.  I tried bcmw15.inf and one other one, and neither of them worked apparently.  I don't know how to figure out the correct .inf file.  My wireless card is Xircom 32-bit.[/QUOTE]
 Did yu try this thread? worked like a charm.
[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683) (just remember to go through the first 6 pages.
And if yu did...bcmw15.inf is the one to use as far as i remember... how did yu get the drivers..from the manuf cd? or the internet..(if so check the version etc). Sorry i couldnt give you a perfect solution..the best bet would be to post your request on the thread mentioned... that dude (jonny) is good...seems 2 know his stuff!

---

### Post by Rhadryn on 2005-07-23
I have no idea how I am supposed to use that first website, with the list of drivers.

The link on the forum looks good, but I cannot find bcmw15 on the computer.  The laptop came with all of the drivers already installed, I never had a manufactor's CD.  I'll check out that topic though, and post if I can't find anything to work.

---

### Post by byen on 2005-07-23
> The laptop came with all of the drivers already installed, I never had a manufactor's CD
Ok. So your laptop came with the drivers installed but you did not get the drivers? they usually give the wireless driver with the cd-set tht you get..anyways... if  you did not find the files in c:\drivers or whatever your default drivers may be.. google the web for your model number and see if you can find any...... google...google....google...

Note: I know how insanely frustating this might be cuz i spent literally days trying to fix this in fedora until i found the thead given above and ubuntu! just hold your guns...be patient.

---

### Post by Rhadryn on 2005-07-23
Thanks!  I found the driver, but it is for windows 98.  This is probably an incredibly stupid question, but what can I do about that?

---

### Post by byen on 2005-07-23
[QUOTE=Rhadryn]Thanks!  I found the driver, but it is for windows 98.  This is probably an incredibly stupid question, but what can I do about that?[/QUOTE]
 well... are the files rqd for ndiswrapper in there? if so try em out and use the thread that i mentioned be4 as a guide... simply follow it. what bad can happen...it cant get worse...
and be4 you start please remember to clear all the junk that must have piled up from previous ndiswrapper installation attempts... (procedure also in the thread!)

PS_ all you have to do is search for the 2 files from the driver folder (mentioned in the thread)  and copy them to a place which you can easily access.

---

### Post by byen on 2005-07-23
ok these are the files you need :
1. bcmwl5.inf or bcmwl5a.inf 
2. bcmwl5.sys

see if you can locate these drivers...if you are running windows. select the file-properties and see if it is a .inf file or a .sys file...sometimes windows does not show the extension. goodluck.
PS- as i said please be patient.

---

