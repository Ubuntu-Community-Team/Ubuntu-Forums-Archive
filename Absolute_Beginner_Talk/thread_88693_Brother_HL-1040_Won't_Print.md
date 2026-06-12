---
title: "Brother HL-1040 Won't Print"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by linewb on 2005-11-10
I can't get this printer to work.  I've tried setting it up through System Admin but am having no luck.  It looks like everything is ready to go and then nothing happens.  Does the listing of recommended drivers mean they are already installed in the system?  I've tried to download the recommended driver from linuxprinting.org but I'm not sure I've done it properly.

I know this isn't the printer as it was running fine on this hard drive with Windows just last week.

I was fed up w/ Windows because of it's price and Microsoft's unhelpful nature so I recently installed Ubuntu.

I'm a complete beginner here and afraid any advice you all have would have to be pretty thorough.  Imagine I'm your dumb uncle who has no idea what you're talking about, but needs the help anyway.  I literally don't know what root means.  I see all kinds of commands listed everywhere but have no idea where I would go to type them in.  I'm no idiot, though, and I'm willing to learn.  Thanks in advance to anyone who can help.

---

### Post by Kapre on 2005-11-10
[QUOTE=linewb]I can't get this printer to work.  I've tried setting it up through System Admin but am having no luck.  It looks like everything is ready to go and then nothing happens.  Does the listing of recommended drivers mean they are already installed in the system?  I've tried to download the recommended driver from linuxprinting.org but I'm not sure I've done it properly.

I know this isn't the printer as it was running fine on this hard drive with Windows just last week.

I was fed up w/ Windows because of it's price and Microsoft's unhelpful nature so I recently installed Ubuntu.

I'm a complete beginner here and afraid any advice you all have would have to be pretty thorough.  Imagine I'm your dumb uncle who has no idea what you're talking about, but needs the help anyway.  I literally don't know what root means.  I see all kinds of commands listed everywhere but have no idea where I would go to type them in.  I'm no idiot, though, and I'm willing to learn.  Thanks in advance to anyone who can help.[/QUOTE]

Are you using the latest Ubuntu release (5.10)? Cause I'm trying it out on my system by looking if the driver is present (and it is). Can you go to the Printer Setting window again and see if your printer is present on the list?

K

---

### Post by linewb on 2005-11-10
Thanks for responding.

I'm running on 5.04 (just ordered a copy of breezy).

Yes, the make and model of the printer is on the list.  That's what's so frustrating about it.

Any advice is much appreciated.

---

### Post by Kapre on 2005-11-10
[QUOTE=linewb]Thanks for responding.

I'm running on 5.04 (just ordered a copy of breezy).

Yes, the make and model of the printer is on the list.  That's what's so frustrating about it.

Any advice is much appreciated.[/QUOTE]

OK. I'm doing this on the 5.10 version...When you add the printer was it detected? On Breezy, I have the ff options, printer type (local or network - you choose one), Use a detected printer (where the bottom portion shows the detect printed, below that is use the printer by specifying port (you have the option of choosing which port - maybe you just need to specify which port to use) when you select the options needed, you press the forward button and you'll go to step2 on selecting the printer driver and that's it.

Check if you have the same options on your release.

K

---

### Post by linewb on 2005-11-10
Yes, I have the same options.  Here's what I've been doing:

1) I choose Local Printer.  Funny thing is, the option "Choose Another Printer By Specifying a Port" is also automatically chosen, so that when I click forward both options are marked.  Should I choose a different port?  How would I know which port to use?  There's only one printer connection on my hard drive (athlon amd 1600+).


2 )Choose option for Brother HL-1040.  The recommended driver (hl7xo) appears as an option next to "Install Driver".  When I click to install the driver it indicates the driver is already installed.

3) Click Apply.  Then the box closes up.

Then I go to print a test page, and nothing happens.  Try to print from AbiWord and nothing happens.  The printing icon appears and the system believes it is printing.

It's a drag.  I've checked the dum-ass stuff like the connection.  Any further suggestions?  I really appreciate the help.

---

### Post by Kapre on 2005-11-10
[QUOTE=linewb]Yes, I have the same options.  Here's what I've been doing:

1) I choose Local Printer.  Funny thing is, the option "Choose Another Printer By Specifying a Port" is also automatically chosen, so that when I click forward both options are marked.  Should I choose a different port?  How would I know which port to use?  There's only one printer connection on my hard drive (athlon amd 1600+).[/quote]

Can you try choosing another port (parallel port - even though it is already) and then go with the install choices.


> 2 )Choose option for Brother HL-1040.  The recommended driver (hl7xo) appears as an option next to "Install Driver".  When I click to install the driver it indicates the driver is already installed.

3) Click Apply.  Then the box closes up.

Then I go to print a test page, and nothing happens.  Try to print from AbiWord and nothing happens.  The printing icon appears and the system believes it is printing.

It's a drag.  I've checked the dum-ass stuff like the connection.  Any further suggestions?  I really appreciate the help.

I know that this may sound as a dumb idea but can you reboot and try it again?

K

---

### Post by linewb on 2005-11-10
Whoo-hoo!

I had tried rebooting before, but this time I rebooted with the printer turned on and that did the trick.  The system detected printer and I was able to install it and print.  I don't know why it didn't want to install manually, but what the hell.

Only thing is, now I'm low on toner.  Any suggestions for that?  :p 

Seriously, thanks for the help.  It means a lot to me.   

So glad I haven't gone crawling back to Microsoft.

---

### Post by Cufishing on 2005-11-10
I have a Brother USB HL2040, and have had excellent results from both the default "Ubuntu" reccomended driver, and the Brother download.

1. Ensure the printer is plugged into the port and is powered on.
2. Are you using USB by chance?
3. Have you visited the 'Brother' web site?
[http://solutions.brother.com/linux/en_us/](http://solutions.brother.com/linux/en_us/)
They provide both CUPS and LPR drivers, along with easy to follow istallation directions.

Here is a good read about print spooling:
[http://www.linux.com/howtos/Printing-HOWTO/spoolers.shtml](http://www.linux.com/howtos/Printing-HOWTO/spoolers.shtml)

Also, if the OS is detecting the printer, is it giving you a "o" bubble to click to acknowledge?

---

### Post by Kapre on 2005-11-10
[QUOTE=linewb]Whoo-hoo!

I had tried rebooting before, but this time I rebooted with the printer turned on and that did the trick.  The system detected printer and I was able to install it and print.  I don't know why it didn't want to install manually, but what the hell.

Only thing is, now I'm low on toner.  Any suggestions for that?  :p 

Seriously, thanks for the help.  It means a lot to me.   

So glad I haven't gone crawling back to Microsoft.[/QUOTE]

I'm glad it did the trick.

K

---

