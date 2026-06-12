---
title: "How to share a printer between Ubuntu and Windows, the really easy (and stupid) way"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by mwshook on 2006-09-24
After probably a dozen hours of trying to share an HP PSC printer/scanner between my Ubuntu and WindowsXP computers. I finally gave up. I read all the howtos, and wikis, I tried configuring SAMBA a million different ways. I tried hooking up the printer to the Ubuntu computer and the windows one.

Eventually, I came up with this solution: 

[IMG]http://sewelldirect.com/images/SW-2201.jpg[/IMG]

The [USB switch]("http://sewelldirect.com/USBManualShareSwitch2To1.asp") connects 2 computers and one USB device. It has a big button in the middle. Pushing the button has the same effect as unplugging the device from one computer and plugging it into the other one. As an added bonus, I can share the scanner too.

Considering how cheap this thing was, and how well it works, I would reccommend it to anyone who is tired of futzing around with SAMBA. (This is assuming your two computers and printer are all in the same room)

---

### Post by nix4me on 2006-09-24
Samba is not needed to share printers.  CUPS is the printer daemon and sharing is taken care of by IPP.  Hunt around on the forums and wiki and you will find information on how to share a printer using cups/ipp.

nix4me

---

### Post by nix4me on 2006-09-24
Here is a link on how to do it:

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by bodhi.zazen on 2006-09-24
I should not tell you this, but you can just move the USB cable directly without your blue box. :)

I agree with cups.

---

### Post by louieb on 2006-09-24
I have an HP7660 printer attached to a windows xp box. I also have a couple of ubuntu desktop pc's on my home network. On xp the printer is a shared device. In ubuntu all I did was open system>adminstration>printing, chose network printer, it listed the printer, asked me for a xp user and password, entered that, and it works.

---

### Post by mjpatey on 2006-09-25
Thank you for that link!  (The one that explains how to do it, not the one that sells you a blue widget).

I copied and pasted the new cupsd.conf contents into my current cupsd.conf (after backing it up), followed the rest of the guide, and voila!  I'm able to print to my Ubuntu computer's printer from my Windows computers now.

The guide was a little vague at points, so here's some clarification for anyone who feels a little uncertain about it:

1.  They really do mean you copy and paste the contents of their file over top of your file's contents.  Back up your original, as this one will be replacing it completely.

2.  After restarting CUPS, my regular printer's icon in the "Printers" folder disappeared, so I thought I'd done something wrong.  I tested it by printing to it from Firefox, and it printed just fine.  But it was still missing from the Printers list, which was a little unsettling.  After closing and re-opening Printers, it appeared again.  So don't worry if that happens.

3.  In setting up the Windows computers on your network to access your Ubuntu machine's printer, the line given in the guide is:

[http://PRINTSERVERNAME:631/printers/PRINTERNAME](http://PRINTSERVERNAME:631/printers/PRINTERNAME)

"PRINTSERVERNAME" is the actual network name of your Ubuntu machine (what comes after the "@" at a terminal prompt).  "PRINTERNAME" is the name of your printer as it appears in the Printers folder in Ubuntu (in my case, it was Stylus-Color-900).

Hope this helps!

---

### Post by razorsmile on 2006-09-26
well I'm not having quite such luck with the CUPS configuration...

I also replaced the cups.conf file with the one in the link...but still nothing from the windows machine.  I can now access the cups server if, on the windows machine, i go to 192.168.1.3:631 , the ubuntu machine where the printer is served from - if I then go to the printers and try to print a test page it seem to get stuck.

if i try running lpstat on the ubuntu print server I get the following
```

matt@matt-desktop:~$ lpstat -r -d -p
scheduler is running
no system default destination
printer Stylus-D68 now printing Stylus-D68-24.  enabled since Tue 26 Sep 2006 11:26:37 BST
        Unable to lookup host 'e' - Unknown host

```

and looking at the windows machine where the cups admin page is up, I also get the 'unable to lookup host 'e' - Unknown host'.

it seems the printer has the address ipp://e

which doesn't seem right to me ;-)  but where's it got this from and how do I change it?  and is that likely to be the problem?

---

### Post by mwshook on 2006-09-30
I assure you I read all those howtos and wiki pages, with no avail. I could get my printer installed and recognized, and send jobs to the Windows printer queue, but the best I could get it to do was make some noise, flash its lights, and hang.

](*,) 

I think the problem is specific to the HP PSC-1200 series.

Oh, and using the blue box is less annoying than switching the cables.

---

### Post by cschlosser on 2006-10-08
I am haveing a similar problem with an HP PSC 1315 all in one. I added a new printer from the network and when i try to print it sends it to the printer and the printer makes some noise and does nothing else. If I try to cancel the job on the xp computer it doesn't cancel and I have to reboot the XP computer. I am not sure if the driver is not any good for the 1310 series printers or if it is the XP computer causeing this problem but some help would be appresiated.  ](*,)

---

### Post by JohnPhys on 2007-03-18
cschlosser:

I having similar issues, but with trying to print TO the 1315 on a Ubuntu machine FROM a WinXP machine.  I've followed many a howto, and can print to the 1315 just fine from Ubuntu.  I'm wondering if it's a driver issue with WinXP, since (sometimes) I can get the job to show up in the printer queue, but then it gets dropped and nothing happens.

---

### Post by murlosad on 2007-03-26
I'm having the same problem with my Lexmark X1185 printer.  I did find a website that mentioned using a RAW queue if you have the correct drivers installed on the Windows machine. But, I haven't been able to figure that out yet.

Here's the link: [http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html]("http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html")

-edit-

used adobe's postscript drivers on my XP box and it works great.

---

### Post by bustherh on 2007-10-08
I am trying to print from a xandros box to kubuntu with a hp photosmart. xandros seems to connect but then it askes me for a username and password and I cannot figure out how to set this on kubuntu.

---

