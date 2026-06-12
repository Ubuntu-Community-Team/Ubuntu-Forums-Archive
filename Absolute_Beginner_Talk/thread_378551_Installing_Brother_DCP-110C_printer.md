---
title: "Installing Brother DCP-110C printer"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by Mr. Svinlesha on 2007-03-07
Hey.

I'm having problems installing my Brother DCP-110C printer.  Following the advice on [this]("http://ubuntuforums.org/showthread.php?t=105703") page, I downloaded what I believe is the correct LRP driver (dcp110clpr-1.0.2-1.i386.deb) and CUPS Wrapper (cupswrapperdcp110c_1.0.0-1_i386.deb).  I then used the commands suggested on the web page, modified for my specific printer, and extracted/installed the packages.  I was careful to turn the printer off and then on again at the correct steps in the process, and as far as I can see I was very careful to follow the instructions exactly as written.  

For the first time the correct printer showed up in the Printers window (I had previously followed the instructions on the Ubuntu help page without success, but had been careful to remove that printer before I started this installation).  HOWEVER:

When I highlight the printer icon and select properties, some info is missing.  Under the Paper tab, I'm unable to select paper size, paper type, source or layout.  Under the Advanced tab I get nothing but a blank little screen.

Anyone out there have any advice for me?

---

### Post by Mr. Svinlesha on 2007-03-07
bump.

---

### Post by Mr. Svinlesha on 2007-03-07
Alas, alack, and woe is me.

Can no one help the widow's son?

---

### Post by Mr. Svinlesha on 2007-03-07
bump again.

---

### Post by Mr. Svinlesha on 2007-03-08
Bumpity bumpity bump bump.

---

### Post by Mr. Svinlesha on 2007-03-08
Still waiting for advice or help on this issue.

---

### Post by 3ntity on 2007-03-14
**[Read second part of post for relatively simple Feisty instructions]**

Hail!
I JUST got my printer working as follows, i'm not sure if uninstalling/reinstalling the printer actually helped, but you can give this a shot:

```
followed instructions on [with correct DEB's (see further in this post)]; steps 6 and 7 didn't work for me, read on if that's your case as well:
[http://www.ubuntuforums.org/showthread.php?t=123539]("http://www.ubuntuforums.org/showthread.php?t=123539")

The debs i used were: 
[http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/dcp110clpr-1.0.2-1.i386.deb]("http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/dcp110clpr-1.0.2-1.i386.deb")
and:
[http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperdcp110c_1.0.0-1_i386.deb]("http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperdcp110c_1.0.0-1_i386.deb")

After following the instructions in the aforementioned post:
open a terminal, type su, enter, and the root password
type: chmod a+rw /dev/usblp0 [i.e. printer, check it's in /dev]
uninstalled printer from system-> administration -> printing
added new printer in same place, adding /dev/usblp0 as device location. 
Tried a test page, which worked, and printed a few other documents, which worked as well. I had trouble with the cups stuff...
```

I hope this helps and works for you. I'm a big Ubuntu n00b myself, so i fear i won't be able to help if anything goes wrong. Search around on the forums (for 110C or DCP-110C, for instance) if you need more help, otherwise hope someone else notices your post :)

Ps. this worked on Ubuntu Dapper (6.06)

**EDIT:** Formatted my hard drive and followed the above method, which worked again. Just so you know :)

=========================================================================================

**UPDATE for Feisty:**
I couldn't get my printer working with feisty, so i did the following:

**Note:** all commands were executed as superuser in the folder were the .deb files had been downloaded to! Also, ensure you have csh installed (sudo aptitude install csh), thanks **gudy1024**]
[LIST][*]Downloaded LPR driver from: [http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/dcp110clpr-1.0.2-1.i386.deb]("http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/dcp110clpr-1.0.2-1.i386.deb")[*]installed with command:[*]```
 dpkg -i --force-all dcp110clpr-1.0.2-1.i386.deb
```[*]Downloaded CUPS driver from: [http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperdcp110c_1.0.0-1_i386.deb]("http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperdcp110c_1.0.0-1_i386.deb")[*]Installed with command:[*]```
dpkg -i --force-all cupswrapperdcp110c_1.0.0-1_i386.deb
```[*]The last line of output from the terminal i got read:[*]```
lpadmin: Unable to copy PPD file! 
```[*]I looked this up on the brother website, and followed instructions 1-4 on: [this link]("http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#60")[/LIST]
That wasn't too bad now, was it? :D Now, go print away!

---

### Post by gudy1024 on 2007-04-01
Thank you for your information :)
let me add a tiny note... before you start installing with dpkg.... please run this first in terminal

sudo aptitude install csh

because I got an error:

Setting up cupswrapperdcp110c (1.0.0-1) ...

 ****** ERROR: csh is required. ******

and you wonder:  what's that again "csh" ?? :))

---

### Post by 3ntity on 2007-04-22
> **gudy1024 said:**
> Thank you for your information :)
...
Did it otherwise work?

---

### Post by Mr. Svinlesha on 2007-08-06
Well, I'm back at the point that I'm getting ready to once again reinstall my printer with Feisty Fawn.  I have one simple question before following the how-to above:  should I turn off and disconnect the printer before I start the installation process?  Or should I leave it hooked up? Or does it not matter either way?

---

### Post by Mr. Svinlesha on 2007-08-06
Bump.

---

### Post by Mr. Svinlesha on 2007-08-06
Well, I've done step 1 (install csh) and turned off my printer.  When I try the next command (*dpkg -i --force-all dcp110clpr-1.0.2-1.i386.deb*) I get the following message:
> dpkg: operation requires read/write access to dpkg status area
 If I put "sudo" in front of the command, FF replies:> dpkg: error processing dcp110clpr-1.0.2-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 dcp110clpr-1.0.2-1.i386.deb

Help?  Anyone?

---

### Post by Mr. Svinlesha on 2007-08-06
Well, after some fooling about I finally figured out how to extract the files (I was missing the path name) and followed the rest of the instructions.

When I was done, I had *two* Brother DCP-110c printer icons in my printer window.  Under the "Properties" window of one of them, I couldn't access the "Paper" tab: which was precisely the problem I had previously.  But the other one looked good, so I kept it and marked it as my default printer.

But even though I'm a step closer, I'm still not printing.  Under the "Connections" tab, when I select "Printer type: Local or Detected Printer", the window beneath informs me "No printers detected."

Also, I'm having a terrible problem with the Printers window (System>Adm>Printing).  Whenever I highlight the DCP-110, right-click and select properites, it hangs something awful.

Suggestions, anyone?

---

### Post by Mr. Svinlesha on 2007-08-06
Well, after fooling around a bit more I finally solved the problem, but nothing more or less than *restarting my system*.  I think the problem was that I had told the printer to print something before going fully through the process of selecting a local printer, which then blocked it from accepting more jobs from me until I closed down and restarted, clearing my ports.  I think.

Anyway, congratulate me: I am now officially an Ubuntu Computer Geek.

---

