---
title: "[SOLVED] Printing on an HPOffice via XP"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by DutyDuty on 2007-11-11
I've got ](*,) I've spent forEVER trying to hook Ubuntu up to the printer in the other room. I've got a USB printer in the other room, and it's connected to an XP desktop. On my Vista partition, I can print easily, but Ubuntu is not so confidant, and leaves every job in the queue, one "printing" and the rest waiting. None ever print, and I've checked, right drivers, right names, and Windows firewall shows nothing being blocked.

---

### Post by DutyDuty on 2007-11-11
bump

---

### Post by DutyDuty on 2007-11-11
last bump of the night.

---

### Post by anewguy on 2007-11-12
I think you might get more responses if you started a new thread with a new title.  The current title makes it look like you want help printing on a HPOffice from XP - no mention of Linux.  You might want to try something like "Problem printing from Linux to HPOffice on a networked PC".  I'd leave the XP thing out of the title and instead put it only in the text of your message.  You might get a few hits that way. 

I wish I could help you but I don't have a 2nd PC, so obviously I have nothing networked at the time.

Good Luck!:)

---

### Post by FuturePilot on 2007-11-12
Can you post the output of 
```
cat /var/log/cups/error_log
```

---

### Post by DutyDuty on 2007-11-12
It returned nothing. Opening said file with Text Editor showed it to be empty.

---

### Post by Sef on 2007-11-12
1) What HPOffice model do you have?

2) How are you hooking it up?  directly, samba, other?

---

### Post by DutyDuty on 2007-11-12
It's HPOffice J5700. I hooked it up via the Printing option in System >> Administration. It is off a USB in the other room from the XP machine. This Ubuntu Laptop is hooked up to that XP by a network with five computers. All four other computers can print, as far as I know. Ubuntu could print while I had 7.04, too.

---

### Post by bhold on 2007-11-12
[https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)

See the last item in the above link, disabling bi-directional support on the XP printer. Worked for me, good luck.

---

### Post by DutyDuty on 2007-11-12
Followed those instructions twice, nothing doing.

---

### Post by vsweeney on 2007-11-12
I have the same problem.

Just installed Ubuntu 7.10 on my laptop.  I connect to the remote printer on a Windows XP machine.  

When I print I briefly see the document get spooled on the Windows machine but nothing prints out.

---

### Post by DutyDuty on 2007-11-12
That's a similar problem, but sure/bump
(This is just about the last thing keeping me from switching from Vista completely.)

---

### Post by bhold on 2007-11-12
Here is the output of the lpoptions command from my system, suggest you compare to your system and see if that might provide ideas for anything else to try. (I am on Ubuntu 7.10, remote printing to printer on an XP system works fine.)

bhold:~> lpoptions
media=A4 finishings=3 copies=1 job-hold-until=no-hold job-priority=50 number-up=1 auth-info-required=none job-sheets=none,none printer-info='HP officejet 4215 on XP system' printer-is-accepting-jobs=1 printer-is-shared=1 printer-location printer-make-and-model='HP OfficeJet 4200 Foomatic/hpijs (recommended)' printer-state=3 printer-state-change-time=1188428313 printer-state-reasons=none printer-type=36876

---

### Post by DutyDuty on 2007-11-12
Minor/Huge setback: I cannot see the XP box anymore on the Network. It's on, connected. The printer  and the computer are not visible anymore.

---

### Post by bhold on 2007-11-13
Sorry I can't offer up something more specific, maybe some one with more Linux / XP networking background will chime in. But at this point I would do the following if it were my systems:

1. On your XP system, verify that workgroup is still defined. Verify that shares are still defined. If so, can other systems access the shares? Or is is just your Ubuntu system that is having the problem?
2. Reboot XP and Ubuntu system. I know this is not a satisfying and rigorous solution, but often works wonders particularly when Microsoft products are involved in the problem mix.
3. What happens after the reboot? Do things come up still failing? Or do they work for a while then crap out later?? If they come up working for a while, check files under /var/log/ for error messages and see if that provides any useful info. I'm not sure which files to check, but you might find something under /var/log/cups/. You can  ls -l -R /var/log immediately after the Ubuntu reboot then do this periodically and look for file size changes, that might give a clue on where to look for relevant errors.

Just a few ideas, good luck.

---

### Post by DutyDuty on 2007-11-14
Sorry, I've already done each of those, nothing doing.

---

### Post by DutyDuty on 2007-11-14
bump

---

### Post by stchman on 2007-11-14
> **DutyDuty said:**
> I've got ](*,) I've spent forEVER trying to hook Ubuntu up to the printer in the other room. I've got a USB printer in the other room, and it's connected to an XP desktop. On my Vista partition, I can print easily, but Ubuntu is not so confidant, and leaves every job in the queue, one "printing" and the rest waiting. None ever print, and I've checked, right drivers, right names, and Windows firewall shows nothing being blocked.

You could try getting a print server with a USB input.  This way you would not have to leave the XP machine on all the time.

You could also get the HP Officejet Pro K5400tn.  It has a built in ethernet card.  Linux printing reports that it works with Linux perfectly.

I personally have a Color Laserjet 2605dn and it works excellent with Linux.  I have 5 computers in my house and all of them can use the printer.

---

### Post by DutyDuty on 2007-11-14
OK, new solution. I've got a smaller Epson Stylus Photo R220 hooked directly to my laptop. It works. I'll be back when that solution runs out.

---

