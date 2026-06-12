---
title: "Epson printer stops working."
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by whitefort on 2007-02-18
Hi,

I have an Epson Photostylus RX425 printer/scanner.  A week or so ago, I set it up with my Ubuntu system, and it was working perfectly.  I haven't used it again until today (when I urgently needed it), and I CANNOT get it to work.

The printer itself is fine and still works (I tried it with my old windows machine again).  Ubuntu seems to find it OK, and everything seems right except that when I try to print (either my work or the test page) the job just sits in the printer queue forever.

I just don't know where even to start looking for what's wrong - I've tried deleting that printer icon, then followed the setup examples in my textbooks again to create a new one, and everything looks fine - except that it won't print.

I would be REALLY grateful if anyone could help me get this working again (if only to avoid the scorn of my windows-loving friends who will take this as another example of 'Linux is only for PC experts' - I've been getting a lot of that lately...)

I'll answer any questions, provide any listings etc that you need.

Please help!

---

### Post by solar george on 2007-02-18
Check all of the connections (I know it sounds obvious but having some one say "Dose that bit have to be plugged in?" when you are trying to work out what is wrong with the driver, well I'm sure you can guess the correct response)

Disconnect the power from the printer, reboot the computer, delete any print jobs, reboot the computer and reconnect. This worked on my HP but it may not work for you.

Goodl Luck.

---

### Post by whitefort on 2007-02-18
Okay, here's what I did...

Turned everything off. Disconnected & reconnected everything.
Turned on computer.  Logged in.  Deleted existing printer in the printer settings.

Turned on Printer.  gnome-cups immediately kicked in and identified it, leading me through the new printer wizard thingie.

Everything looked OK.  Clicked on the icon for the newly recognised/installed printer.  Clicked 'Print Test Page.'

Little printer appeared in the notification bar - in short, everything doing what it does when the printer prints - except that it doesn't.

I DID notice that as soon as I tried to print the test page, a few lights went out on the printer.  I don't recall that happening when it was working.

I'd be really grateful if anyone could help me sort this out.  Without a working printer I'm going to have to go back to windows, at least for serious work.

Thanks.

---

### Post by solar george on 2007-02-18
> Without a working printer I'm going to have to go back to windows, at least for serious work.
Keep the linux install (dual boot) and keep trying with the printer.

Does the new printer thing list more that one available driver?

---

### Post by whitefort on 2007-02-19
Hi - still no luck getting the Epson RX425 working again, so this is another plea for help.

Everything in the Ubuntu (GUI) settings seems to be telling me that the printer should work.  And its built in scanner is working perfectly, so Ubuntu can definitely connect to the hardware.

I was wondering if trying to print the test page generates a log file anywhere, and whether that might offer any clues as to the problem.

I really can't think of anything I've done that could have stopped the printer from working.  Last week I set it up, tested it, and it was perfect.  Then when I came back to actually USE it, nothing.

I DID set up the firestarter firewall during the week - presumably that wouldn't break the connection to a local printer?  Also, the problem persists, even with the firewall turned off.

I'm at my wits end here, and just don't know what else to try.  All help gratefully appreciated!

Thanks!

---

### Post by audiofreq on 2007-10-30
Hey I'm in the same boat.

Same printer...i'm using gutsy.

Printer was working when i first installed. So was the scanner. Then tried to print but there was no paper so i got an error on the printer but no error on the screen. Put paper in. Deleted the job...tried printing again and nothing happens. 

I've uninstalled the printer and now when i try reinstall it i don't think it's detected.

It's plugged in via usb and also works fine in xp.

---

### Post by yarjoooz on 2008-07-18
I have the same problem though another printer - Epson DX7450. Scanner works - printer stopped working. And printer spooler tells me that printer seems to be disconnected. But when I try to pull the usb plug out and plug into another usb socket - printer is discovered but I still can't print anything. 
Any help please.

---

### Post by yarjoooz on 2008-07-18
Hi

Exactly the same problem - scanner works, printer is discovered but when I try to print test page - printer is disconnected.
Please advise.

Regards

---

### Post by LucidLoon on 2008-07-19
Hi.
I've had a similar problem with an Epson C-80. I'd send a job to print and the print head would just move back and forth and not print anything. After a lot of reading in the forums and googles, I went into the synaptic package manager and uninstalled anything that was foomatic. Then I installed the gnome-cups manager and my printer started working fine. The print quality needs to be tweaked but it was a big step in the right direction.

Hope it helps.

---

