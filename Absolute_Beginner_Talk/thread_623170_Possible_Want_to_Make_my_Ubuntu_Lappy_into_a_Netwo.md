---
title: "Possible Want to Make my Ubuntu Lappy into a Network Server type thing..."
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by ajskhan on 2007-11-25
I have Xubuntu loaded on a 256mb, 700mhz IBM thinkpad laptop.

I basically want to:
1. Connect it to my internet/network (EASY!)
2. Attach my printer [(Canon - MF3240)]("http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=nni&q=Canon+Printer+MF3240+Laser+Printer&btnG=Search")
3. Want to use the PRINTING PART and attach the PRINTER to my network, basically so I can print from any PC to that printer. 

Currently it is attached to PC1, and when PC1 is off, if PC2/PC3 want to print, I must turn PC1 on, print, then turn it back off. I was hoping if I can just attach the printer to Xubuntu, I can just make it a network  printer (sorta like a print server?) and then PC1, 2, and 3 can all print without any turning on and off. I can also just set the power consumption settings to very low or whatever.

Questions:
a. Will it automatically have the driver(S)?
b. Are there any flaws in my plan?
c. will the lowest power settings work with this?


4. Want to still be able to use the SCANNER part. I don't mind doing something like scanning from the laptop, but automatically saving to a network PC of my choice? Any ideas?

5. I also wouldn't mind running something like ORB (PC only) to stream my music and a radio station or two live. Is there any alternative that would work on Xubuntu? But is as easy to use?




THANKS A TON!

---

### Post by ajskhan on 2007-11-27
bump?

---

### Post by siciliancasanova on 2007-11-27
Are you saying you want it to print while being connected to comp 1 with it turned off?

Not sure how that will work.  If it's a new printer I would recommend returning it and getting one with wireless or one that doesn't require USB just one that can sit on the network anywhere in your house.

Not sure if that's what you're looking for but that's what I would do.  Then you don't have to turn anything on or off, the printer will always be ready to print from whatever computer you are on.

EDIT:  I forget that people's houses might not be hardwired in every room and wireless might not be sufficient if all your machines don't use wireless.

---

### Post by Whiffle on 2007-11-28
Yeah you can do that, in fact thats pretty much   the same setup I have.  I have a 450 mHz compaq presario laptop sitting on my shelf, its my print server, torrent downloader/seeder, temp logger(if i ever get around to it), apache server, ftp server...etc.  Works nicely, and only pulls 15 watts.  And it does it all over wireless since I'm too cheap to buy a proper network card for it.  As of right now its been running a month, which is when the last power outage was.  Only problem is the *one* usb port (yes, one usb port...silly compaq), is getting loose so i have to wiggle the printer cable to make it work.  grr.

You can use CUPS for printing over the network.  Google around a bit, theres a couple of good howtos on how to make it work in ubuntu.

I havn't tried it, but it looks like you can share the scanner over the network using saned   [http://linux.die.net/man/8/saned](http://linux.die.net/man/8/saned)

Oh, and yes you can probably stream music from it too.  Theres quite a few different options for streaming in linux, none of which I've played with.  I just hook my desktop up to my stereo :P

---

### Post by siciliancasanova on 2007-11-28
I stand corrected :)

---

