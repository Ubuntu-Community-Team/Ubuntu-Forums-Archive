---
title: "Need an Epson PM-A820 Driver please."
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by T4K3Z0U on 2007-09-28
I just got my printer bck from the repair shop after it fizzed in just 2 months after purchase, so this is the first time I have tried to use it on feisty.
Thing is the closest driver available is a PM820C but that doesn't work for me. All the printer does is spit out all the paper thats in the paper try and then keep giving me error messages that there is no paper. Its not a printer fault coz it still works in winblows, which is a pain to switch OS just to do a quick print job.

If you know where and how I can download a driver for my printer to use in Ubuntu please let me know ASAP.


Cheers

---

### Post by Daveth on 2007-09-28
any of this lot ? - sorry have to get off to work- could not find anything in the Gutenprint driver list.

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

---

### Post by T4K3Z0U on 2007-09-28
Doesn't look like it

---

### Post by T4K3Z0U on 2007-10-03
Bump!

---

### Post by Terl on 2007-10-03
Go to [Linuxprinting.org]("http://www.openprinting.org/printer_list.cgi?make=Epson").  I have looked up the epson line (that is the link).  Follow directions they give.  This is an excellent source for your Linux printing needs.  They list a PM820C

---

### Post by T4K3Z0U on 2007-10-03
> **Terl said:**
> Go to [Linuxprinting.org]("http://www.openprinting.org/printer_list.cgi?make=Epson").  I have looked up the epson line (that is the link).  Follow directions they give.  This is an excellent source for your Linux printing needs.  They list a PM820C

So if it isn't there it doesn't exist for Ubuntu/linux basically?

The PM820C is the one I mentioned in my OP. It just spits the paper out over and over again until the tray empties, if you reload it like I did, it just repeats, but no printing.

---

### Post by Terl on 2007-10-03
Did you click the printer number in the link I gave you?  It has directions for how to set it up.  If you do not see your exact model, you can search a bit on the internet.  Lots of times a similar model's driver may work.  In the link I gave you, just click the printer model you want to check out.  Note the headings though, they tell you if the printer is just a paper weight.

---

### Post by T4K3Z0U on 2007-10-03
> **Terl said:**
> Did you click the printer number in the link I gave you?  It has directions for how to set it up.  If you do not see your exact model, you can search a bit on the internet.  Lots of times a similar model's driver may work.  In the link I gave you, just click the printer model you want to check out.  Note the headings though, they tell you if the printer is just a paper weight.

Perhaps I didn't explain myself clearly or I am completely missing something :confused: That printer number you gave me, has a default driver on Ubuntu which I tried and it didn't work, as I said in my OP and my previous post.

---

### Post by Terl on 2007-10-03
Sorry for the miscommunication.  I am at work and misread one of your posts.

I found this link as well:  [Gutenprint]("http://www.linuxprinting.org/show_driver.cgi?driver=gutenprint").  It does not list your model but there are similar models to try.  I have not had much luck in googling that model either.

---

### Post by T4K3Z0U on 2007-10-03
> **Terl said:**
> Sorry for the miscommunication.  I am at work and misread one of your posts.

I found this link as well:  [Gutenprint]("http://www.linuxprinting.org/show_driver.cgi?driver=gutenprint").  It does not list your model but there are similar models to try.  I have not had much luck in googling that model either.

No thats cool man, I thought perhaps I am missing something obvious.

I don't know what is similar to my printer as its from Japan, so....

I found this info on the net but the codes don't appear to be for Ubuntu or I'm entering them wrong.

[http://blogs.sun.com/sayama/entry/printing_with_brandz_and_linux]("http://blogs.sun.com/sayama/entry/printing_with_brandz_and_linux")

---

### Post by Terl on 2007-10-03
That site is more geared towards Solaris it appears...

The best path I have found is to try Gutenprint ([Gutenprint-was GIMP print]("http://gimp-print.sourceforge.net/")).  They list your printer as being supported.

---

### Post by T4K3Z0U on 2007-10-03
Thanks. I just downloaded it and went to open the file but nothing happens. Is that automatically installed or do I need to manually do that some how?

I appreciate your help. I'm still a beginner

---

### Post by Terl on 2007-10-03
Did you download from the site?  If so, found this on the site:  > All Other Users
Users of other operating systems, such as Linux, Solaris, FreeBSD, OpenBSD, HP-UX, etc. should download the main package, named "gutenprint-5.0.0.tar.bz2". This is a "source tarball"; it contains the source code for the package and must be compiled to produce binary executables. The command to unpack this file is


tar xjvf gutenprint-5.0.0.tar.bz2

On some systems, you may have to issue the following command:


bunzip2 -c gutenprint-5.0.0.tar.bz2 | tar xvf -

This will create a subdirectory named gutenprint-5.0.0. You should read the files named README and NEWS in that subdirectory for further instructions. 



NOTE:  Before you do the above, try opening synaptic and search for Gutenprint.  It may be in the repository and you will have an easier install with less keystrokes :)

---

### Post by T4K3Z0U on 2007-10-03
> **Terl said:**
> Did you download from the site?  If so, found this on the site:  

NOTE:  Before you do the above, try opening synaptic and search for Gutenprint.  It may be in the repository and you will have an easier install with less keystrokes :)

Yes thats in the repository as is gimp print. Does that mean I can just start printing or is there more to do?

---

### Post by T4K3Z0U on 2007-10-03
> **T4K3Z0U said:**
> Yes thats in the repository as is gimp print. Does that mean I can just start printing or is there more to do?

No I made a mistake. Gimp print is not there coz the small box to the left is not green like the gutenprint one.

---

### Post by LowSky on 2007-10-03
I CHECK THIS WEBSITE AND IT DOES LIST YOUR PRINTER

[http://www.linuxprinting.org/show_driver.cgi?driver=gutenprint]("http://www.linuxprinting.org/show_driver.cgi?driver=gutenprint")

---

### Post by T4K3Z0U on 2007-10-03
> **LowSky said:**
> I CHECK THIS WEBSITE AND IT DOES LIST YOUR PRINTER

[http://www.linuxprinting.org/show_driver.cgi?driver=gutenprint]("http://www.linuxprinting.org/show_driver.cgi?driver=gutenprint")

It's listed but it isn't high lighted as a link, just that it exists. Or so I was to understand.

---

### Post by Terl on 2007-10-03
> **T4K3Z0U said:**
> No I made a mistake. Gimp print is not there coz the small box to the left is not green like the gutenprint one.  

Sounds Like Gutenprint is installed.  This is the link to the [manual in pdf]("http://gutenprint.sourceforge.net/gutenprint-users-manual.pdf") which should help you the rest of the way in getting it configured.

---

### Post by YannBuntu on 2008-05-29
Hello,

I also have a PM-A820:
- I made it run perfectly (print+scan) on Gutsy (don't remember how :) )
- Now on Hardy, the printer runs out-of-the-box but I can't find the way to make the scanner run :(

EDIT: on Gutsy (where both printer+scanner work), I have :
- printer driver: Epson PM A820-CUPS +Gutenprint v5.01simplified
- Xsane v 0.991
On Hardy (where printer is ok, but scanner is not recognized), I have:
- printer driver: Epson PM A820-CUPS +Gutenprint v5.02simplified
- Xsane v 0.995

---

