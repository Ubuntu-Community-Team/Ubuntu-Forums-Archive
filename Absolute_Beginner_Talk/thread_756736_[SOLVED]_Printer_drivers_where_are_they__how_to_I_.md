---
title: "[SOLVED] Printer drivers: where are they?  how to I apply them to my device?"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by yeats on 2008-04-16
I had asked this question at the end of [this thread]("http://ubuntuforums.org/showthread.php?t=556980") three days ago and have not gotten a response, so I'm starting a new thread to address this separate question.  I have a Canon Pixma MP210 All in One Printer/Scanner.  Following advice on the other thread, I found the appropriate drivers (printer and scanner) on the [Canon Australia]("http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp210_support.aspx") site, downloaded them, and installed them using the gdebi package installer.  The Synaptic Package Manager shows them as installed as well.  When I attempt to apply the drivers to my printer using System > Administration > Printing, it only gives me the option to either 1) select from a list of models (mine is not included) or 2) navigate to a PPD file on my computer.  When I use Gnome CUPS Manager, it's the same thing.

I have scoured these forums and the web for instructions about how one might accomplish this, and several of my peers here have apparently done it, but I can't seem to figure this out.  Could someone who has made this succeed (or knows how) please explain how to do this?

I'll also mention that I'm hoping to learn a skill here - this isn't just so my printer will work.  Understanding how to use software I've downloaded from the net (rather than from the repositories) is something I really want to understand on a basic level.  Thank you.

---

### Post by Mark_in_Hollywood on 2008-04-16
Start here:

Re: Canon pixma mp210
Posted by: LeKing56 (IP Logged)
Date: October 25, 2007 01:49AM

I put the driver of the MP150 and it works !
[http://forums.linux-foundation.org/read.php?25,3055,3055,quote=1](http://forums.linux-foundation.org/read.php?25,3055,3055,quote=1)

and/or


How to get a Canon all-in-one printer working with Ubuntu
[http://www.ubuntugeek.com/how-to-get-a-canon-all-in-one-printer-working-with-ubuntu.html](http://www.ubuntugeek.com/how-to-get-a-canon-all-in-one-printer-working-with-ubuntu.html)

please mark this thread solved if it works.

---

### Post by yeats on 2008-04-16
Thank you so much.  I'll give this a shot this evening and let you know how it goes.

:-)

---

### Post by yeats on 2008-04-16
My printer now works, but the scanner is still not recognized.  Do you have any advice?

---

### Post by HermanAB on 2008-04-16
If you wish to read up, the underlying printer install engine is called 'foomatic' and the scan system is called 'sane'.  Some Googling and you'll be a boffin in no time.

---

### Post by Mark_in_Hollywood on 2008-04-17
> **chrissharp123 said:**
> My printer now works, but the scanner is still not recognized.  Do you have any advice?

Please know that I haven't used your product. I went to the SANE devices page:

[http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)

for Canon products. I don't see yours listed, BUT, like using the MP150 drivers, it's more than possible that one of those SANE drivers makes your scanner work. Please: google your model number and the keyword: linux, you may have to dig 5 or 10 pages deep, but somebody may have found a solution.

I'm sorry to not have more for you. I bought an Epson CX5000 and had the same problem as you, I ended up following about half of somebodies post, when the scanner started working. If you want to see how I did that, search this forum for my user name and CX5000.

If you get something going, but it's not perfect, get back to me, I'm glad to try to help.

---

### Post by timcredible on 2008-04-17
nothing specifically against canon, but if you buy an hp printer/scanner, you have a much better chance of it working correctly.  hp has very good linux drivers for their products, and it's very easy to set it up (in ubuntu 7.10 i did absolutely nothing but plug my psc4180 in and reboot, and i had the printer and scanner working correctly).  i've had 3 hp printer/scanners, and they all worked perfectly with ubuntu, mepis, and pclos.  there's a website that lists which hp printers work well with linux.  not that i'm really advocating buying a new printer, but in the future, when you want a new one, you may want to keep this in mind.

---

### Post by Mark_in_Hollywood on 2008-04-17
Well, I had a little extra time for this after all:

Canon's webpage with the drivers for printer and scanner:

[http://canon.com.au/products/all_in_one_printers/all_in_one_printers/mp160_support.aspx](http://canon.com.au/products/all_in_one_printers/all_in_one_printers/mp160_support.aspx)

and the explanation of what you need to do to get it all working.

[http://www.ubuntugeek.com/how-to-get-a-canon-all-in-one-printer-working-with-ubuntu.html](http://www.ubuntugeek.com/how-to-get-a-canon-all-in-one-printer-working-with-ubuntu.html)

If you have not already install ALIEN, then get Synaptic to install it. The Canon drivers are in .rpm (Red Hat) format. ALIEN will easily and robustly make them work in Ubuntu (DEBIAN).

Reading further in UBUNTUGEEK's how-to:

[B]Now we need to get the scanner completely installed. To do this, we need to install the scanner back-end.

Download the sane scanner back-end from here. Save it to your home directory.

Turn on your Canon all-in-one printer, do a complete restart (not a simple log-out), and log back in. To test your scanner, place something in your scanner and open XSane by clicking Applications -> Graphics -> XSane Image Scanner. To scan, click on the Scan button. Don’t forget to set the scan resolution to your liking.[/B]

I checked that and it's for the MP150.

Maybe it will "just work"

Let us know.

P.S. to the fellow posting about HP versus Canon, etc. I believe that at one time, there was better support for the Linux Community from one manufacturer or the other. That has changed in the last two to three years. Suggesting that the original poster needs to consider other equipment in the future is "reverse engineering" his work now.

---

### Post by yeats on 2008-04-17
Mark in Hollywood,

Thanks so much for your help.  A user named "themunkee" helped me in the other thread (see [here]("http://ubuntuforums.org/showthread.php?p=4737448#post4737448")) to get the scanner working with the GIMP.  I've learned a lot from all of your suggestions!

Thanks!
Chris

---

