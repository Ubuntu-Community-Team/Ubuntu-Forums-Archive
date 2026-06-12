---
title: "AVG Anti Virus Woes"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Ahunt on 2007-04-30
I downloaded AVG Anti-Virus last night and installed it as per the instructions at [http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064) . 

It all went perfectly - unpacked and set up fine.

I tried a scan and that went fine. 

Next I tried an update and it downloaded two of five update files perfectly and then the update failed. I tried re selecting update and it indicated that an update was in progress, but there was nothing downloading. I closed AVG and then reopened it - same thing. Tried a reboot - same thing. It is just locked for updates. The internet connection was fine through all this.

As per the AVG for Linux User Guide I tried some apropriete command line interfaces, including "update" and "repair" as per the manual. They all worked fine, but any attempt to ask it to update, result in "Process 'avgupdate' is already running." The repair function didn't fix it either. 

Nothing seems to fix it.

Can someone suggest a fix for this problem or alternatively tell me how I can re-install AVG without causing havoc? (I still have the deb package saved).

Thank you in advance for any help!

Adam

---

### Post by starcraft.man on 2007-04-30
Quick question, are you behind a NAT Router? That would be any router you bought in the last five years I think. If so, I don't really think an AV program is that important on Linux.

The truth is that if your behind a NAT router its practically impossible to get a virus less you install it yourself. The best way to prevent infection is via behaviour, view all email in plain text, don't open attachments, don't fileshare from illicit sites/files, run no script and adblock plus in your firefox. Not to mention in all honesty, most viruses are coded to detect a Windows PC (thats what most hackers run, so its what they know) thus it would be harmless since it wouldn't see anything it was programmed to.

That said, I have used AVG before on my windows PC and while I'm not completely sure I think that this might be one of the times their servers go down. Happened to me all the time where their servers returned busy or just didn't ping at all, wait a couple of hours or a whole day and should be back. If not might be a wee bit more serious >.>.

---

### Post by wormser on 2007-04-30
With the windows AVG updater you can download the new virus definitions and 'posibly the updates' from their site or download.com.  Save them on your computer then look for the place in AVG to update and select the location you saved them to.  The Linux version probably works this way also.

Good luck.

---

### Post by Ahunt on 2007-04-30
Well thanks for the thoughts.

I didn't really want to debate the need for anti-virus. I think that if you forward e-mail then there is always the chance to infect someone else's Windows PC with a virus forwarded to you  even  if you can't run the virus yourself. We are on dial-up straight onto the net - no server protection there.

I have tried to locate the virus definition file, but it is set up very differently on Linux than on Windows. Can't find it there at all.

Perhaps I will just re-install the deb installer file and see what happens? Any thoughts?

Adam

---

### Post by redsox37 on 2007-05-04
Just update from the terminal window. Open a terminal and type:

sudo avgupdate -o

It'll will go to grisoft and get all the new definitions for you and install them automatically.
Reply With Quote

---

