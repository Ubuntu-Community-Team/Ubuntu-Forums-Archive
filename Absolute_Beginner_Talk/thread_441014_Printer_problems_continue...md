---
title: "Printer problems continue.."
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-05-10
<start lament>
...printing really should be easier <sigh!>- it's one of those things everyone needs to do. Yet the documentation makes it sound so difficult, and maybe that's because it actually isn't easy
</lament>

However: I have followed all of the instructions on CUPS to install my printer, which is  a brother HL1230 b/w laser situated on my home network at 192.168.0.2 and managed by a $20 generic print server that has managed to print for over  a year  happily under windows 98 and XP

Trying to get the printer to work under ubuntu, I was asked for a pdd during the installation, and I found one with a  foomatic (?) which was recommended as the one to use by wherever I found it. 
cups told me the printer was installed, at the right IP address etc, but when I try to print a test page I get a permanent message saying "printer busy will retry in 10 seconds" Needless to say nothing will print. 

Looking through the docs here to try and understand I find mention of a CUPS wrapper specifically for my printer. Do I need it? What si it? How should I use it? 

Or is there an easier solution? This business of printing really is easier under windows

---

### Post by dolphin_oracle on 2007-05-10
try brother's site.  They supply drivers for debian for this printer.  You will need the LPR driver and the cupswrapper driver.  

[http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

just make sure to get the debian versions.

i used this guide to install my mfc9700.  just replace your printer type whenever it specifies the printer the thread was about.

[http://ubuntuforums.org/showthread.php?t=105703&highlight=brother+printer](http://ubuntuforums.org/showthread.php?t=105703&highlight=brother+printer)

good luck!

---

### Post by klytu on 2007-05-10
> **ginestre said:**
> <start lament>
...printing really should be easier <sigh!>- it's one of those things everyone needs to do. Yet the documentation makes it sound so difficult, and maybe that's because it actually isn't easy
</lament>

However: I have followed all of the instructions on CUPS to install my printer, which is  a brother HL1230 b/w laser situated on my home network at 192.168.0.2 and managed by a $20 generic print server that has managed to print for over  a year  happily under windows 98 and XP

Trying to get the printer to work under ubuntu, I was asked for a pdd during the installation, and I found one with a  foomatic (?) which was recommended as the one to use by wherever I found it. 
cups told me the printer was installed, at the right IP address etc, but when I try to print a test page I get a permanent message saying "printer busy will retry in 10 seconds" Needless to say nothing will print. 

Looking through the docs here to try and understand I find mention of a CUPS wrapper specifically for my printer. Do I need it? What si it? How should I use it? 

Or is there an easier solution? This business of printing really is easier under windows

I don't use your printer model so unfortunately I can't give specific advice. But some general comments might help. 

First of all read the information here: [http://openprinting.org/show_printer.cgi?recnum=Brother-HL-1230](http://openprinting.org/show_printer.cgi?recnum=Brother-HL-1230)
and the linked pages there. This is good for background and might lead you to a specific answer. For example, are you using the recommended driver (HL1250)? Make sure you have the correct ppd file as listed in that link as well. 

For general troubleshooting -Try ```
tail -f /var/log/messages
``` while you are attempting to print a test page. The output may give a clue as to where the job is getting stuck. If all else fails, you can also try to physically connect the printer to your Ubuntu box, set it up, and see if you can get it to print. If you can, then you can assume the problem lies in communicating properly with the print server.

---

### Post by ginestre on 2007-05-12
If I query the status of my printer I get the message

Ready: /usr/lib/cups/backend/lpd failed

This is presumably why everything stays in the print queue and doesn't print even though  the printer is ticked as 'ready'. What to do? Grateful for pointers

This is a Brother HL 1230 installed as indicated as a 1250 with foomatic via CUPS on lpd://192.168.0.2 via a generic print server magic box

---

### Post by ginestre on 2007-05-12
I'm bumping this thread in the hope of a reply from someone more knowledgeable than me; thanks in advance!

---

### Post by ginestre on 2007-05-13
I am becoming increasingly frustrated by this: everything else in ubuntu works so much better not only than expected, but even than hoped: but printing is the pits. It's a pity, because it's one of those basic operations that really ought to be simple... yet all of the explanations about printing everywhere seem to require an intelligence far superior to mine, and a degree of knowledge that somehow seems greater than should be needed to get the damn laser printer to knock out a few pages. 

However: I have spent -literally - days reading all sorts of stuff here and elsewhere in an attempt to understand. Despite this, I have failed, miserably. I even found that when I post a question to the forum, if I mention 'printing' in the title, it gets ignored, whereas any other topic instantly attracts kind helpful useful relevant advice which solves the problem. So I have resorted to the dirty trick of not putting 'printing' in the title of this post. I've even put something which deliberately attracts attention. I know this is bad form. But I'm desperate.  Will it work? Probably not, but who can say. However,  PLEASE can someone PLEASE answer a few idiot questions from this patently idiotic idiot? I have to print the wife's thesis in record time, and am feeling, well, woefully inadequate.

a) Is CUPS necessary to printing in ubuntu, or is it just a  helper? If it is just a helper, is there another helper who maybe helps more, and hinders less?  
b) if a printer has been installed in CUPS, and if CUPS says it is there, available,and ready, is that true? Or is it an illusion?
c) Following on from (b), if CUPS says everything is brilliant, hunky dory and working why doesn't Open Office list the printer? And why doesn't CUP manage to print a test page? 
d) When I open CUPS, why does say that it has found an Epson and a Canon printer, which I don't have, both on LPT1- which is not connected to anything?
e) do I need a foomatic? as well as a ghostcript? And should I put my ppd file in before or after the other stuff? Some say one thing, some another- but I can't print either way.
f) does ubuntu like printing to an IP address? And should I use http: or lpd: ? Or maybe even something else?
g) Is it possible to get so exasperated by anything else? (This is the only question I can answer on my own. The answer is no.)

Excuse the outpouring. I've been trying to sort it out for a week. And thanks for your patience. It's probably more than mine.

---

### Post by OffHand on 2007-05-13
The topic title you picked is inappropriate imo.

[How To Ask Questions The Smart Way]("http://www.catb.org/~esr/faqs/smart-questions.html")

---

### Post by Campingman on 2007-05-13
The title worked for me, it got my attention!  Got no idea how to help with the printer though, sorry.
Did you say which printer you are trying to get working?  Cannot see it.  Might help!

---

### Post by ginestre on 2007-05-13
I know the title was a dirty trick. but as I said above, I'm desperate. And Campingman, thanks for the encouragement. You see more clearly than I do.

It's a Brother HL 1230 which works best, according to Linuxprinting.org, with a HL1250 PPD file, which I have failed to get to work. It's located at [http://192.168.0.2](http://192.168.0.2). It printed quite happily from there in a previous o/s incarnation.

---

### Post by ramjet_1953 on 2007-05-13
Did you go here?

[http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-1230](http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-1230)

And then download the PPD file?

Regards,
Roger :cool:

---

### Post by diskotek on 2007-05-13
saerch for your printer driver, and just apply instructions. it just took 5 minut for me to install a canon pixma driver.

---

### Post by ginestre on 2007-05-13
> **ramjet_1953 said:**
> Did you go here?

[http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-1230](http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-1230)

And then download the PPD file?

Regards,
Roger :cool:

Thanks, yes I've been there several times and it just won't work for me. The printer installs fine, shows up on lists (but not in Open Office) yet when I print,the CUPS thingie just says "printer busy: will try again in 10 seconds" and this situation can last for days....

---

### Post by laidback on 2007-05-13
I have great sympathy with your frustration and plight. All appears so hopeless and beyond solution, however, may I suggest that you stick with it despite the current frustrations, it will get resolved in the end and the outcome will be worth the aggrevation. It's not the end of the world, just yet.
I have no direct understanding of your problem but from what you have said I would work along these lines:-

Check connection, if USB then try another USB card if at all possible.
Check printer cable, replace it
Check printer, can it print the test page etc
Check printer on another system, alternate Linux or XP for example
Look for a vanilla style driver that would allow basic printing
Print from the command line using lp, lpr etc
Check that another printer works on your system
.
.
it does work so continue to dig, the solution will appear.

Good Luck

Laidback

---

### Post by mar225 on 2007-05-13
Posting This crap might get you some assistance.

Quote   "I have failed miserably. Perhaps I should kill myself."

When is the funeral?

---

### Post by ginestre on 2007-05-13
Still failing to print under CUPS, on the web I find the following comment:

quote from linuxprinting.org

On Ubuntu Linux the administrative tasks of the CUPS web interface are disabled by default. They say that this is for security reasons. To re-enable them, add the user "cupsys" to the "shadow" group in /etc/group

end quote

Is this true? Is this why I haven't been able to move from print queue to paper for over a week? And  if it is true, just how  does one 'add the user "cupsys" to the "shadow" group in /etc/group'?

Grateful for help.

..............
still trying to print to a Brother hl 1230 across  a home network: but likely to give up soon

---

### Post by lionel47 on 2007-05-13
Hmmm...I have a Brother DCP-7020 and printing to is was as easy as going through the printing wizard.  Of course I had to use the HL1250 driver but everything seems fine.  Anyway, are you trying to print to a network printer or is it attached to your ubuntu box?

---

### Post by ginestre on 2007-05-13
it's on the network, unfortunately

---

### Post by OffHand on 2007-05-13
Stop making new threads about the same problem. Cross posting does not help. Concentrate your efforts (and ours).

---

### Post by ginestre on 2007-05-13
This is what I have at the moment

HL-1230 "Printer busy; will retry in 10 seconds..."
	Description: shelf second attempt
Location:
Make and Model: Brother HL-1230 Foomatic/hl1250 (recommended)
Printer State: processing, accepting jobs, published.
Device URI: [http://192.168.0.2](http://192.168.0.2)

here is the last aprt of the error log, if anyone can make head ortail of it...

D [13/May/2007:17:09:50 +0200] CUPS-Get-Printers
D [13/May/2007:17:09:50 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [13/May/2007:17:09:50 +0200] cupsdReadClient: 8 POST / HTTP/1.1
D [13/May/2007:17:09:50 +0200] cupsdAuthorize: No authentication data provided.
D [13/May/2007:17:09:50 +0200] Get-Printer-Attributes ipp://localhost/printers/HL-1230
D [13/May/2007:17:09:50 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [13/May/2007:17:09:50 +0200] cupsdReadClient: 8 POST / HTTP/1.1
D [13/May/2007:17:09:50 +0200] cupsdAuthorize: No authentication data provided.
D [13/May/2007:17:09:50 +0200] Get-Printer-Attributes ipp://localhost/printers/LaserOnShelf
D [13/May/2007:17:09:50 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [13/May/2007:17:09:56 +0200] cupsdNetIFUpdate: "lo" = localhost...
D [13/May/2007:17:09:56 +0200] cupsdNetIFUpdate: "eth0:avahi" = 169.254.6.28...
D [13/May/2007:17:09:56 +0200] cupsdNetIFUpdate: "eth1" = 192.168.0.4...
D [13/May/2007:17:09:56 +0200] cupsdNetIFUpdate: "lo" = localhost...
D [13/May/2007:17:09:56 +0200] cupsdNetIFUpdate: "eth1" = fe80::2e0:4cff:fea5:895b%eth1...
D [13/May/2007:17:09:56 +0200] cupsdReadClient: 8 POST / HTTP/1.1
D [13/May/2007:17:09:56 +0200] cupsdAuthorize: No authentication data provided.
D [13/May/2007:17:09:56 +0200] CUPS-Get-Printers
D [13/May/2007:17:09:56 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [13/May/2007:17:09:56 +0200] cupsdReadClient: 8 POST / HTTP/1.1
D [13/May/2007:17:09:56 +0200] cupsdAuthorize: No authentication data provided.
D [13/May/2007:17:09:56 +0200] Get-Printer-Attributes ipp://localhost/printers/HL-1230
D [13/May/2007:17:09:56 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [13/May/2007:17:09:56 +0200] cupsdReadClient: 8 POST / HTTP/1.1
D [13/May/2007:17:09:56 +0200] cupsdAuthorize: No authentication data provided.
D [13/May/2007:17:09:56 +0200] Get-Printer-Attributes ipp://localhost/printers/LaserOnShelf
D [13/May/2007:17:09:56 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)

---

### Post by OffHand on 2007-05-13
Any reason why you need cups?

---

### Post by ginestre on 2007-05-13
> **OffHand said:**
> Any reason why you need cups?

I don't know: is there another way? This one doesn't seem to work for me.  It sort of happened as I tried to read through the copious documentation about printing. Any solution is fine - I need to print over a wire-based ethernet network to a Brother HL 1230 printer located at 198.162.0.2

---

### Post by Benbow on 2007-05-13
I hesitate to say this but I suffered similar problems with my printer, not a Brother, and eventually solved it by downloading a trial version of Turboprint, checked that it worked and then PAID to use it permanently.
Not everyones solution but here -
[http://www.turboprint.com/](http://www.turboprint.com/)
make sure it works with your printer first!

---

### Post by Benbow on 2007-05-13
I posted a misspelling in the last post. Herewith, see above.

---

### Post by tagra123 on 2007-05-13
I had a terrible time too. Cuos is a mess in ubuntu and hasn't work right for a while.

The way I got it to work isn't pretty, but it's not hard either. If you can get it to print on a local machine then you can get it to print over the network using my method.

[http://ubuntuforums.org/showpost.php?p=2591426&postcount=8](http://ubuntuforums.org/showpost.php?p=2591426&postcount=8)

---

### Post by ginestre on 2007-05-14
Whilst doing an entirely different thing (installing sleuthkit so I could check an md5) I noticed that the log contained references to my printer! Is it possible that the clue to everything is hidden herein? But I don't know what it means (sob!)


Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libdate-manip-perl 5.44-3 [169kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe sleuthkit 2.06-3 [2208kB]
Fetched 2377kB in 10s (224kB/s)                                                
Selecting previously deselected package libdate-manip-perl.
(Reading database ... 96279 files and directories currently installed.)
Unpacking libdate-manip-perl (from .../libdate-manip-perl_5.44-3_all.deb) ...
Selecting previously deselected package sleuthkit.
Unpacking sleuthkit (from .../sleuthkit_2.06-3_i386.deb) ...
Setting up hl1230lpr (1.1.2-1) ...
mkdir: cannot create directory `/var/spool/lpd/HL1230': No such file or directory
chown: cannot access `/var/spool/lpd/HL1230': No such file or directory
chgrp: cannot access `/var/spool/lpd/HL1230': No such file or directory
chmod: cannot access `/var/spool/lpd/HL1230': No such file or directory
/var/lib/dpkg/info/hl1230lpr.postinst: 4: /etc/init.d/lpd: not found
dpkg: error processing hl1230lpr (--configure):
 subprocess post-installation script returned error exit status 127
Setting up libdate-manip-perl (5.44-3) ...
Setting up sleuthkit (2.06-3) ...

Errors were encountered while processing:
 hl1230lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dolphin_oracle on 2007-05-19
have you tried the native drivers from Brother's website.  There are some special instructions in the fact.  I don't know if they work on feisy, as I'm running edgy.

[http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

I'm printing to a mfc9700 connected to another computer over the network.  I believe while doing the initial setup, I needed to use a dummy device url, then change it later.  It was in the faq.

Also, I believe to use the native drivers, you need a symbolic link or two.  Its also in the fact, but the howto by Bob Songs on the mfc210c worked for me.

[http://ubuntuforums.org/showthread.php?t=105703&highlight=mfc-210c](http://ubuntuforums.org/showthread.php?t=105703&highlight=mfc-210c)


I never could get mine to work right with the foomatic ppd drivers.  Even when I got it to print, it the alignment wasn't right.

good luck!

---

