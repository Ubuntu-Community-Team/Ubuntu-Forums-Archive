---
title: "what is lpd and where is it?"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by iansane on 2008-01-19
hi I'm trying to install a brother mfc6800 printer. I have attempted to install the lpr and cupswrapper pakages. Brother says for my model I need to have lpd installed first. I thought lpd was part of the lpr package but it's not because the lpr only partially installs because theres no /etc/init.d/lpd

Now Nothing I do will remove my partially installed lpr package and it has my synaptic locked down. All I can do with apt-get is try to reinstall the package. Other than that, apt-get is locked down to. It wants me to reinstall the package in order to remove it but If I could install it completely  I wouldn't be trying to remove it. Can someone tell me where to get this lpd is it part of another package?

Thanks

---

### Post by iansane on 2008-01-19
Although this was posted only an hour ago, I have been trying for days to get some help with this and all I can get is directed to one of the posts about other printers. I know it's not the fault of anyone here in the ubuntu community. This is the only thing I have had such trouble getting help with. Brother really needs to work on their driver compatability with ubuntu.

Well I think I solved my own problem.

First I had to find and edit the mfc6800 postrm and post inst scripts. I had to comment out the command to restart /etc/init.d/lpd since it did not exist. When I tried to reinstall it just rewrote them and then gave me the same problem again. When I edit them and remove mfc6800lpr it worked.

Great! my synaptic and aptget are back working again! Next I took a guess and installed lpr from add/remove programs. Sure enough the ilusive lpd that brother and the mfc6800lpr.deb could not find is there now.

All of the error messages I had being related to lpd not being there, I tried reinstalling. I have never been so relieved to see a package install with no errors. To be on the safe side I reinstalled the cupswrapper.deb package. Only one message, not an error. After cups restarted it said "lpadmin not found" but this was not part of the install. It's something else I will try to figure out. 

One of you who is good at writing how to's and has nothing better to do might want to include this info for the mfc6800. It took me days to figure out what package to install because there isn't one called lpd and that is what was missing. I could read about what lpd/lpr is but that was no help in noing what to install and which one to install first. I hope this info will help someone else although I'm starting to wonder if I'm the only person alive with this particular model

---

### Post by mario.p.s on 2008-01-19
> **iansane said:**
> 

First I had to find and edit the mfc6800 postrm and post inst scripts. I had to comment out the command to restart /etc/init.d/lpd since it did not exist.
When I tried to reinstall it just rewrote them and then gave me the same problem again. When I edit them and remove mfc6800lpr it worked.l

I did the part of commenting out the command to restart /etc/init.dlpd --> this solved the problem of not being able to update anything.

Now what do you mean by the fact that if I reinstall the Brother drivers I'll have the same problem and the fix is to EDIT the /var/lib/dpkg/info/mfc8840dlpr.postrm file and then REMOVE the lpr ?

Thanks a lot.  I've been searching for a solution for this issue for days+++ as well.

---

### Post by iansane on 2008-01-19
OK sorry I wasn't very clear on that. I was really happy after being very frusterated for hours

I was just saying that after the failed install the script files are still in /var/lib/dpkg/info . So you can't do a reinstall because something somewhere rewrites the scripts recreating the error again.

You have to comment out the lines in the script and before doing anything else do "sudo dpkg -r mfcxxxlpr . Also it's the name that you see in the error message, not the name of the original deb package, just in case you don't know. I was so confused, I can't believe I finally got it  Mine was mfc6800lpr.

Anyway, that removes it and frees up synaptic. 

Now before attempting the install again, use synaptic to install lpr (not the lpr deb package but the one in synaptic). It puts the lpd in /etc/init.d/  It will remove cups but after your done with this you can reinstall cups.  First you might need to open the printers console and delete the mfcprinter if there is one there. Now reinstall the downloaded lpr.deb package and then reinstall the cupswrapper package. Your brother printer should show up in the printers console now. It took mine a few seconds but then a notice popped up from the system tray with a configure button. Now is when I had to reinstall the cups file that was removed by installing lpr. It was nessesary for my other printer which uses a cups mp150 driver.

I don't remember which one but I did a search for cups and made sure all of them were installed except for cups-bsd. That one will remove lpr. Here's a list of the cups files I have installed now

bluez-cups (for bluetooth, don't know why)
cupsddk
cupsddk-drivers
cups-pdf
cupswrappermfc6800
cupsys
cupsys-client
cupsys-common
cupsys-driver-gimpprint
cupsys-driver-gutenprin

I'm just listing them because I can't remember which one got removed when installing lpr. Of course there are several libcups and libcupsys files but I didnt' touch them so they aparently were not affected. I really don't know anything about it as you can probably tell but that is how I was able to make my old brother printer and my newer cannon mp150 both print from the same computer. I left out the part about reinstalling the cups file earlier cause I was not aware until I tried to print from the mp150 today that it had removed cups mp150 and cups pdf printer.

Sorry so confusing, I really don't have a clue but it works

---

### Post by iansane on 2008-01-22
OK after some study and learning about symbolic links, I removed everything and started over. I was able to do it right in only a few easy steps. I posted a complete step by step how to, starting fresh, called "How to install Brother MFC6800 on Ubuntu Gutsy"  It is here.  [http://ubuntuforums.org/showthread.php?t=674727](http://ubuntuforums.org/showthread.php?t=674727)

---

