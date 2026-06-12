---
title: "Installing Printer - Canon BJC-6000 ?"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by 2CV67 on 2006-12-19
As a holiday from trying to get Edgy to work my USB WiFi (Agh!!! - I have ethernet cables trailing all over the house for now) I thought I would set up my printer next....

First bad news is it's a Canon BJC-6000 & I know Canon & Linux don't mix, but then in my short sharp experience, most things & Linux don't mix. :(

I duly went to System > Administration > Printing > Add a printer, but no printer was detected.
I selected the option "Parallel port Canon" & got to "Step 2 of 3: Printer Driver"
I selected BJC-6000 & started to feel optimistic (I should know better by now...).
I clicked on the "Driver" options & found "Gutenprint" & "bjc6000al.upp"
After Googling, I decided on Gutenprint & clicked "Install Driver"

This took me to another screen called "Select a PPD file"
I don't see any PPD files there to select.
After more Googling, I have to admit I don't know what to do here.

Any tips for a next move?

---

### Post by BarfBag on 2006-12-19
Have you gone directly to Canon's website and seeing if they have a Linux driver?

I have an Epson and it was a breeze to set up.  Hope things work out for you.  :(

---

### Post by 2CV67 on 2006-12-19
There is no Linux driver for the BJC-6000 on the Canon Download Library site, as far as I can see.

Thanks for the question though.

---

### Post by jbutler12 on 2006-12-19
Forgive me for going off-topic, but do you have a Belkin Wireless G USB for your wireless?  I just spent two very frustrating days trying to set it up, but i got it to work finally (it works better than in windows) and i could help you with it if you want.  If its not the Belkin, just ignore this post, but the Belkin is really popular so i figured id ask.

(sorry if this is off-topic i figured i might be able to help though)

---

### Post by 2CV67 on 2006-12-19
No - it's an Inventel/Atmel WU221L & the story to date is at:
[http://www.ubuntuforums.org/showthread.php?p=1886979#post1886979](http://www.ubuntuforums.org/showthread.php?p=1886979#post1886979)

but I appreciate your offer of help!

I am still open to help on that thread too, if anybody has an idea...

Back on installing printers - what is the "Select PPD files" screen all about?

---

### Post by 2CV67 on 2006-12-23
Fresh from the triumph of getting Ubuntu to talk by USB WiFi, I now have time to look again at the printer.

I tried again installing a new printer, selected BJC-6000 OK & when I came to the driver, I selected Gutenprint & was about to click the "install driver" button next to it (logical - no??) when I decided to check Synaptic PM & found I already have the latest version.
So I skipped to Next & voila! - printer installed!

BUT - it does not work yet.

I tried printing a page & I tried printing a test page, but no cigar.

The screen says it is sending to the printer, but there is no reaction, or maybe an occasional knock.
The printer does not even feed the paper in.

I tried powering down & rebooting a couple of times & also selecting the alternative driver (bjc***.upp) but still no action.

Any ideas or suggestions please guys?

Thanks!

---

### Post by linux4me on 2006-12-23
I feel your Canon-induced pain. I had similar problems with a Canon IP4200 and finally decided my time was worth more than keeping the Canon. Since a local retailer had some of the HP printers on sale for 1/2 price, I got one on the Linux-recommended list which was very easy to set up and has performed well.

My suggestion, if you can afford to do so this time of year, is to go buy a printer known to work with Linux.

You can find out which ones do here: [http://openprinting.org/show_printer.cgi?recnum=Canon-BJC-6000]("http://openprinting.org/show_printer.cgi?recnum=Canon-BJC-6000")

That link also has information on how to get your printer working if you decide to go that route, though as you will find on that site, that particular printer doesn't seem to be completely compatible with Linux...yet.

Good luck whatever you decide.

---

### Post by 2CV67 on 2006-12-24
Buy a different printer so I can use Ubuntu?...

...& a new camera?
...& scanner?
...& WiFi set-up?
...& what else???

Just so I can boast I don't pay Microsoft for their OS, which at least WORKS!

OK, I am trying to calm down & smile....:( ...no...:-| ...better...:) ...there!

Now, which thread is this?

Ah yes, printer...

Thanks for the link to the LinuxPrinting site.
I had been there & frankly I could not follow it, even after 3 tries.
Right at the top it says "Recommended driver: gutenprint" & I have gutenprint.
Is that not enough?
Do I also need to do the tutorials on  CUPS, LPD, LPRng, PPR, PDQ, no spooler, foomatic  etc etc etc?

It really seems ungrateful to complain about Ubuntu which was free & surely has some good features (Synaptic Package Manager is the only one which springs to mind) but it did say on the tin "(it should "Just Work", TM)".
That was why I decided to try it.

So far, NOTHING has "just worked"...NOTHING!

OK, I am trying to calm down & smile again....

So, back at the printer, is there any hope it may work a bit with gutenprint, or do I have to try to understand all the gray print on CUPS through foomatic, or is it really just hopeless?

Honestly, I AM trying hard to make Ubuntu work & have been at it for nearly a month, so far.

I really appreciate any help & I promise not to snap (again) at any hand that may feed me! 

Thanks (hopefully) :)

---

### Post by 2CV67 on 2006-12-24
Hello forum & Merry Xmas!

I spent another hour or so reading the LinuxPrinting & Openprinting pages about my printer:
[http://openprinting.org/show_printer.cgi?recnum=Canon-BJC-6000](http://openprinting.org/show_printer.cgi?recnum=Canon-BJC-6000)
[http://www.freestandards.org/en/OpenPrinting/Database/CUPSDocumentation](http://www.freestandards.org/en/OpenPrinting/Database/CUPSDocumentation)

but I am still unable to figure out what they are saying - I suppose it is clear to experts, but not to noobies. (This is the absolute beginner forum, is it not?)

The LinuxPrinting page says: *"Recommended driver: gutenprint "*
I have that as standard, according to Syn-Apt.

Further down it says:[I]
"The following driver(s) are known to drive this printer:
    * Recommended: gutenprint "

" The Gutenprint package already ships with all needed PPD files for CUPS and data files for Foomatic. Therefore we do not provide PPD files for download here.

If you got Gutenprint with your operating system distribution, use the printer setup program coming with your distribution. Otherwise it is recommended to use the CUPS driver if you use CUPS as your printing system or the IJS driver if you use another spooler.

IMPORTANT: Always use the Foomatic data and/or PPD files of the Gutenprint version which you are actually using! Remove and re-create your print queues after every update of Gutenprint. If you are using the Gutenprint package of your Linux distribution, it is possible that the Foomatic data and/or the PPD files can be in separate packages. Make sure you install them and that they are of the version corresponding to your Gutenprint package."[/I]

They lost me early on there, but does it not kinda say that everything should be already in the Ubuntu Edgy distro?

Or am I looking for some *"Foomatic data and/or the PPD files ... in separate packages"* ?
If so - what & where??

Thanks to any kind expert (relatively) who can straighten me out somewhat on this! :)

---

### Post by 2CV67 on 2006-12-26
Hey! - I went to the Turboprint site:
[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

Clicked on "Download & try the free edition now"
Told them what printer & where I heard of them, just to be polite.
Clicked on download.
Right-clicked on the .deb package for Ubuntu.
Double-clicked on the downloaded package like they said.
Clicked on "Install" & it installed!
Selected my printer model from "Setup"
Printed a test page first try!
Printed a page from OOotext first try! (OK - I hesitated when it said "default printer" - but it worked).

MAN - IT JUST WORKED! 

...that would make a good trade-mark...   but not for Ubuntu yet... ;) 

This is the best experience I have had since I installed Linux.  :D :D :D 

OK - I know I need to pay if I want to use the best resolution, but compared to where I am with the Linuxprinting fiasco...

---

