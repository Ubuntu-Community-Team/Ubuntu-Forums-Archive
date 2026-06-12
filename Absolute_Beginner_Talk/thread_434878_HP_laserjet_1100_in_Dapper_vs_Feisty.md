---
title: "HP laserjet 1100 in Dapper vs Feisty"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by RH9R on 2007-05-06
Threads on HP 1100 users show lots of issues in multiple version. This post is to show quirks that may help those struggling w/ getting printing to work w/ this printer
 
First install: Dapper on a Microstar mainboard: live CD detected/configured perfectly - no issues.
 
  Microstar died and I got an Asus P5B-VM mainboard. Install went fine. No printing. A week in configuration/driver hell. 'Never printed anything but garbage. One user, MetalMusicAddict (may his name be praised for generations!) suggested Feisty. I was hesitant to switch, with all the threads of quirks/bugs. I read that all the .iso downloads were 'live' CDs, and thought I had nothing to lose, and tried it. It printed. The joy returned.  
 
 Here's the strange part. When I pulled the trigger and installed Feisty. The printer wizard test page STILL PRINTED GARBAGE, but printing a Word formated doc from Open Office printed just fine!? I don't know what's up with that strangeness, but wanted to let other HP1100 owners know that the wizard test page may not be the last word in whether or not the config works. 
 
Best of luck to 1100 owners.

---

### Post by scrooge_74 on 2007-05-06
I have a HP 1100 and I have never had any problem with it using Debian Sarge, Dapper, Edgy, Feisty.

In fact it is tied to a laptop using Edgy and mine uses Feisty to print over the network.

It works beautifull

---

### Post by RH9R on 2007-05-14
'Looks like my 'thrill of victory' was premature. HP 1100 still not working. 'Stumped. Anyone that can help, pls hollar. Many Thx.

 Scrooge74 - I know what you mean. On my last box (microstar main board), it was effortless & ran like a hose.

---

### Post by scrooge_74 on 2007-05-15
Try changing the settings for the parallel port on the bios, maybe that will help. I once had to make some changes, I think I could not print for some reason while I was playing around with an internal modem

---

### Post by tgalati4 on 2007-05-15
Sounds like your printer's processor is failing.  Do a google search on your model and summarize the horror stories that others have had.  HP printers are generally will supported under Linux, so one should consider hardware problems that crop up in multiple Linux installations.

If you are handy, put a small heat sink on the dsp, using heat paste.  Or, toss it and get another printer that will give you less frustration.  I can't recommend HP because of numerous quality problems.  Although they work well under Linux, they just don't last.  (Except my ancient Laserjet 4.)

---

### Post by RH9R on 2007-05-15
The thought of replacing the printer has crossed my mind more than once. I love the way my feisty install works. I went laser because of the high quality printing & I don't need to print photos or color. Is there a printer of choice for low cost of print (typically laser). I don't want to re-purchase the printer every year or every other year due ink costs.

---

### Post by RH9R on 2007-05-15
What's making me nervous is that the boards say the 1100 should work 'perfectly'
[http://tldp.org/HOWTO/Printing-HOWTO/printers.html](http://tldp.org/HOWTO/Printing-HOWTO/printers.html)
If one that's 'perfect' won't work, why would a new one?

---

### Post by tgalati4 on 2007-05-16
I think the term "perfectly" refers to the printer driver as being provided or assisted by the manufacterer.  Some printers  will mimic PLC or postscript and the drivers are modified versions of existing drivers, so they may only rate partial because not all of the printer features can be accessed.

The topic of hardware reliability is another issue.  I can only recommend searching google and making your decision based on user reviews.

An older business-class printer may have better reliability than a new consumer-grade printer.  Older business printers also have parts available as the consumer-grade printers are considered disposable.

Case in point, I have several HP Photosmart printers that folks have given to me because the print cartridge cradle has broken.  Printer works fine otherwise but the cartridges don't stay snug in the carriage and the print quality is poor as a result.  You can't buy the carriage parts.  I was able to make a good working printer from two broken ones.  These were expensive printers when new and they tend to fail shortly after the warranty period (usually a year).  

I've also experience three Officejets with scanner, belt, or power-on failures.  Again, these were lightly-used printers failing after 13 to 18 months.  I can't recommend HP because of this, but they do have good support under Linux.  So find a good, used HP business printer and you will be set.  Check your local printer repair center, or a computer show.  Craigslist.org is another option.  Many times businesses sell off equipment when they move or shut down.

---

### Post by scrooge_74 on 2007-05-16
Have you tried installing HPLIP?

---

### Post by RH9R on 2007-05-16
scrooge_74, HPLIP (I think 1.7.3) is installed, to no effect. _Sincere thx_ for asking, 'cause I and many are capable of overlooking the obvious. 
 
tgalati4: you thoughts are, I think, quite valid & wise. 'Consisten w/ my experience in other environments. I think will next boot w/ a W2k drive & verify there's no issue w/ printer or cable. If it prints well, perhaps I can take the box to a brick & mortar store & see if more recent stuff prints alright. I'd love to get a used business grade printer, but the opportunity to try them first, is limited. 
 
Again, thank you both. I appreciate your help.

---

### Post by merlinus on 2007-05-16
> **tgalati4 said:**
>  Although they work well under Linux, they just don't last.  (Except my ancient Laserjet 4.)

I also have an LJ4, and printing is v-e-r-y  s-l-o-w under Ubuntu as compared to Win2000.  It is set up as direct (LPT1) on one computer, and networked on the other.

Any way to speed things up a bit?

Many thanks!

-merlin

---

### Post by tgalati4 on 2007-05-17
I have my LJ4 set up on Damn Small Linux shared through CUPS.  It is slow, but I'm not sure if it is the parallel port interface or just the queue priority.  Printing has always been a background operation in Linux/Unix so it's never been been as fast as Windows or Novell print services.  

The downside is if the spooler gets borked in Windows, it tends to take Windows with it.  In Linux it will print out two weeks later when the one borked job gets deleted.

Novell had the fastest print protocol, but that was a bygone era.

It's true you don't have the ability to test used printers, but you can get them so cheap (even free) that I normally don't worry about it.  If a printer is truely borked, then you can salvage the memory (special EDO, parity type), the print drums, fusers, lasers etc.  Normally you can keep the older Laserjets going for 1 -2 million copies.

Perhaps others can chime in on how to improve print speed for LPT Laserjet printers.  There are settings in BIOS for LPT performance, settings in CUPS for spooler performance, and settings on the printer (and memory) that can speed up performance.

---

### Post by RH9R on 2007-05-25
I took home a new HP 1020 on sale, and plunged back into printer hell. 3 hrs later, I'm no further. 
 
Does anyone use an Asus p5b-vm mainboard?  What printer do you use? Did you have to code War and Peace to get it to work?

---

### Post by mmikee66 on 2007-05-25
the hp1000 series all have firmware issues with ubuntu :(

you will need to manually add the firmware file to your system.

check out the how to at [http://linuxdesktopsoftware.com/2007/04/how_to_install_a_hp1000_series.html]("http://linuxdesktopsoftware.com/2007/04/how_to_install_a_hp1000_series.html")

---

### Post by RH9R on 2007-05-26
MMikee. Thank you. I appreciate your help. I'm a bit discouraged, and was ready to get a refund on the printer. I'll give this a go before throwing in the towel. 
 
Again, Thank You.

---

### Post by RH9R on 2007-05-26
mmikee66, I'll be dipped in smelly stuff & rolled in suger. It worked exactly as the link instructed. I was nervous when it said to 'make the firmware usable' (presumably unzipping it. I had no idea where it had downloaded to. At each such point, just following the command line inputs did exactly what it needed. This is the first time I've had normal print output since I bought the new asus motherboard. I was afraid of irreconcilable conflicts w/ the board. 
 
Thank You, Mikee. This one has driven me just NUTS for the last 6 wks. If I didn't like ubuntu so much, I'd have bailed long ago. Its the best interface I've seen since the old lunch-pail style Mac SE30 days. You've made a poor newbie very very happy. Thank You!!!

---

### Post by Speedoo on 2007-06-05
I'm having the same problem with my HP Laserjet 1100.  The printer window shows it installed and "ready", but when I send it a job it just sits there.  I don't think the problem is with the printer, because I'm using a dual boot system and the same printer works fine in Win XP.   I read somewhere that this

[http://linuxdesktopsoftware.com/2007/04/how_to_install_a_hp1000_series.html](http://linuxdesktopsoftware.com/2007/04/how_to_install_a_hp1000_series.html)

might help, but when I went to "getweb 1100", there's apparently no such thing.
Sure would be nice to get this working again (it worked in Edgy, stopped with Feisty) cuz it's a chore to have to leave my laptop and come reboot my desktop to Windows every time I want to print something.

---

