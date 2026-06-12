---
title: "Printing"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by theoldgit on 2007-04-01
I have Ubuntu 6.06 lts. I have been printing for weeks on a HP photosmart 6260 and on a network printer HP Photosmart c6810. All has been good. Now out of the blue i cant print a thing. The only clue is in the status line it says Stopped:job-stopped.

So, how do I start it again?

TIA

---

### Post by land0 on 2007-04-01
Sounds like a CUPS(Common Unix Printing System) or hplip issue . I would try restarting cups and hplip. Go to the top left menu System-->Administrator-->Services enter your password when prompted. When the app opens scroll down to the print services make sure they are both checked. If they are both checked un-check them by clicking the check box to the left of the service. Then restart them by checking both check boxes. If one of the check boxes is unchecked then check it. Test your print capability after that. If that did not resolve the issue I would try [http://www.cups.org/newsgroups.php?gcups.general+T](http://www.cups.org/newsgroups.php?gcups.general+T) as you will get the most comprehensive solutions there.

---

### Post by dstew on 2007-04-01
I have Xubuntu, so my print manager is the CUPS local web site opened by putting **[http://localhost:631/admin](http://localhost:631/admin)** into the URL text input in my web browser.

Anyway, when my printing stopped mysteriously, I went to the manager, printers tab, and found a button that said Start. I pushed it and the printer worked again. Somehow it had been stopped in the print job software, and all I had to to was start it again.

---

### Post by theoldgit on 2007-04-02
I tried restarting but nothing, I looked for the start button but it was already started.
I have since found this message on the Admin page, it is for the hp6260
/usr/lib/cups/filter/foomatic-rip failed
Does that help at all?

---

### Post by theoldgit on 2007-04-04
Well I now tried the CUPS forum too but nothing after 2 days. So I am now to the point of desperation. An operating system which won't allow printing becomes pretty useless really so does anyone have any ideas where to go next.

Thanks

---

### Post by lumiawaily on 2007-05-22
i have the EXACT same problem with multiple printers (hp deskjet 3420, canon ip2000, canon mp150).   I'm using ubuntu feisty 7.04.  

Someone should look into this.  I'm very desperate for printing capability.  I have to switch into windows to all the time because of this...

---

### Post by BLTicklemonster on 2007-11-12
Wheee. 

I got an HP Deskjet 720C specifically because it's supported.

Kind of supported as in "networking is supported" in linux, I suppose, because I've been over this 7 times, and nothing is printing.

What in the world are the developers messing with compriz for when you can't use a printer or network worth a flip?

So now, if I want to print something, I have to boot to windows. Great. Same thing with networking. If I want to use the network, I have to boot to windows.

---

### Post by FuturePilot on 2007-11-12
> **BLTicklemonster said:**
> Wheee. 

I got an HP Deskjet 720C specifically because it's supported.

Kind of supported as in "networking is supported" in linux, I suppose, because I've been over this 7 times, and nothing is printing.

What in the world are the developers messing with compriz for when you can't use a printer or network worth a flip?

So now, if I want to print something, I have to boot to windows. Great. Same thing with networking. If I want to use the network, I have to boot to windows.

I've found that there seems to be a huge problem with the new printing system and HP printers. 2 of my 3 HP printers did not work without messing around with it, whereas in previous versions I had no problem setting them up. The problem seems to be that the new printing system tries to assign them through the HPLIP driver. And if your printer is anything like my 2 they_do_not_work with HPLIP. The connection needs to be assigned with a USB #. But the new printing system does not give you this option like gnome-cups-manager did. So in my case I had to install gnome-cups-manager, remove the problematic printers. then reinstall them through gnome-cups-manger making sure to specify the connection with USB #X at the end. Worth a shot.

---

### Post by jerrynewt on 2007-11-12
I am running Gutsy 7.10 so don't know if it works the same as 6.06, but physically go to your printer(s) and see if they can print out a network configuration or printer config page. If they can, get the URL (usually at the bottom of the config page). Open up your printer tab and hit new printer. Go through the config setup and find where you can enter the URL of the printer. When the config finishes see if it works and set as default printer. I am running a C5140 All in one HP and have had to do this a couple of times, but it works like a charm. Good luck !! And don't give up -- Linux is the best OS I have ever used and the support forums are the best around.

---

### Post by BLTicklemonster on 2007-11-13
? 

Okay, it's not usb, it's ltp1.

And uri address? I can't even remember my own address. I just remember how to get here after work every day. If there weren't beer in the fridge, I'd probably not be able to do that.

Oh, and I've installed hplip because someone who tests hp printers came along and said to. How do I uninstall that now?

---

### Post by jerrynewt on 2007-11-13
Go to your printer and have it print out a test page. On that page will be the URL. When you install a new printer (System>Administration>Printing) there will be a box come up during the configuration of the new printer labeled URL. Enter the URL you got from the printer test page. After configuration have the new printer do a test page and see if it works.

---

### Post by BLTicklemonster on 2007-11-13
It won't print a test page. That's the whole problem. I even went to 

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_720C](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_720C)

and got the ppd for this specific printer, and use that to install, and I get nothing.

Is there some wierd linuxness whereas I have to install the lpt1 drivers first or something?

In the printer configuration panel, I see this:

parallel:/dev/lp0

and at the bottom, it says connected to the localhost.

if that helps any.

---

### Post by jerrynewt on 2007-11-13
You have to physically go to the front panel of the printer. There should be a way for you to have the printer give you a test page.

---

### Post by BLTicklemonster on 2007-11-13
Physically on the printer... nope, just a paper feed, and an on off button.

Catch you tomorrow. Thanks.

---

### Post by 11hjpphty76lkjj on 2007-11-13
can you run hp-check and post the output?

A

---

### Post by Tomàs M. on 2007-11-21
Solved deleting /etc/pnm2ppa.conf
HTH

---

