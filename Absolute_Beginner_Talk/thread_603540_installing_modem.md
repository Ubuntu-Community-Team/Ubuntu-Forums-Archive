---
title: "installing modem"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by nichos on 2007-11-05
In winXP I fax via an "AOL Dial-On-Demand" feature whos properties are all blacked out & cannot get any info to put in the Ubuntu attempt to install my modem.

Internal modem:- ESS ES56T -P1 Data Fax Modem  on COMM 4

Where does one get all that info needed in Ubuntu?

nick

---

### Post by qamelian on 2007-11-05
Which version of Ubuntu are you using?

---

### Post by nichos on 2007-11-05
The  magazine CD  said Ubuntu 7, but am not conversant with the names, seem to be millions..

Must fix it to send faxes, i use it lot

What is destrus etc ?       nick

PS since I upgaded directly from the net to Gutsy

---

### Post by qamelian on 2007-11-05
> **nichos said:**
> The  magazine CD  said Ubuntu 7, but am not conversant with the names, seem to be millions..

Must fix it to send faxes, i use it lot

What is destrus etc ?       nick

PS since I upgaded directly from the net to Gutsy

"Distro" is short for distribution. It means the core Linux operating system plus any supported applications and so forth.

If you have upgraded to Gutsy, go to System > Administration > Restricted Drivers Manager and see if your modem is listed. If it is, put a check mark in the box to enable it. If any other files / packages are needed, the Restricted Drivers Manager will attempt to download and install them for you.

---

### Post by nichos on 2007-11-06
Alas, nothing else is listed but the Nvidia grfx card, which is ticked in use.

Some gen I saw said to get "Scan modem" utiil, but like all else I downloaded it I tried to install but it turns out a DEAD text file & don't know how to run/install drivers & programs.

If I find some & extract them the result is another text file, not like windows where they are executables.

Some I did not catch in time, to direct to the desktop, and they disappeard in oblivion. Even search can't see them.

I am at my wits end going around in circles. Perhaps am not suited for these shenanegans.

What some idiot pushed out as linux equal to windows seems a lot of rubbish.

Some blasted Unibond??? modem came up & it says 764mbs @ 23 days to download on   BBand. In windows that takes 5-6mnts.                  thanx                   nick

---

### Post by louieb on 2007-11-06
> **nichos said:**
> What some idiot pushed out as linux equal to windows seems a lot of rubbish.

Right on! [Linux is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm")

As far as your modem goes I did some [Google Linux Searching]("http://www.google.com/linux") around. 

All I found was widows drivers,  and some winmodem to linmodem stuff.
[http://linux.derkeiler.com/Newsgroups/comp.os.linux.networking/2006-11/msg00100.html](http://linux.derkeiler.com/Newsgroups/comp.os.linux.networking/2006-11/msg00100.html)

> If I find some & extract them the result is another text file, not like windows where they are executables.What you probably have is a shell script - sort of like a windows batch file. Saw some of those around for detection of modems. 

> am at my wits end going around in circles. Perhaps am not suited for these shenanegans.Your modem may not be suited for Linux. If you have to use it your probably stuck with XP.  Found a few references  to it in other Linux forums, but did not see where anyone actually got it working.

And if you get it working theres the problem of getting AOL's fax on demand. Have you checked with AOL to see if they have a Linux version?


Good Luck.

---

### Post by nichos on 2007-11-06
1. Ok then, modem is out. BUT how about this "efax & ktefax or something I downloaded, I found it by shear luck, but  how to get to use it I failed to find.

For instance this "efax-gtk-3.src.tgz"  (it says: "whis is GZP archive) I have a choice to save to disk or open with archive Manager,
either I tried I ended up of not finding how to use it afterwards. What is the WHOLE proceedure to get something & gaet to use it?

2. Some numbhead, worst than me, said Aol never head of Linux.

3. How then do I find where the things I extracted go, and if found how to get them to work?   I am completely lost.

Read a lot of info sites & files but there is always something I luck in knowledge and cannot complete the operation involved.

Thanx                    nick

---

### Post by Bartender on 2007-11-07
> **nichos said:**
>  Some numbhead, worst than me, said Aol never head of Linux.

You're awful quick to bite the hand that feeds.  Your numbhead friend was probly trying to say that AOL doesn't cooperate very well with a Linux PC.
PCWorld ran an article a coupla years ago, listing the Top 10 stupidest inventions ever conceived regarding computers.  AOL was #1.  Who's the numbhead now?

Drop AOL and find yourself an ISP that works well with Linux.

---

### Post by nichos on 2007-11-07
Do you or anybody else knoe of one that works with Linux?, Must be cheap cause as an OAP can't afford but the lowest end of BBand & I pay AOL £9pm BBand & £5pm for Talk giving free Local/Nat day & night 365days a year, plus the inevitable BT £11pm.

Actually he was the AOL techy on the fone who never heard of Linux, but I forgave him as he was talking from Asia somewhere where Linux hasn't reached perhaps yet.

Can you help also on:- I download a program/utility I extract & install it & then it disappears in oblivion. 

Then say if I found it, how can I run it. XP was easy doing it with clicks.        nick

---

### Post by Bartender on 2007-11-10
Take a read thru my ongoing "Dial-up" thread.  It's a work in progress.
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

In post #9 I attempt to explain what I think are the 3 hurdles to dial-up in Linux.  Try to identify where you stand.  I'm guessing that you're probably going to have trouble with Hurdle #1 (a winmodem inside) and #3 (crappy ISP).

You're in the UK somewhere?  I can't point to any specific ISP's.  Wrong country.  If you google around for "isp linux" or "cheap isp" and add your general location you should be able to pull up some local ISP's.  Some will say absolutely nothing about Linux.  Others might include some basic instructions for configuring KPPP in their Support section, and those would be promising ones to look into.  Any ISP that does not require any downloads in order to connect are likely candidates.

"Accelerator" software doesn't work in Linux so watch out for that.

I've been looking into ISP's here in Washington State.  I'll e-mail their support team and ask if linux works.  Don't ask for support because they're unlikely to offer it.  The response might give you some idea of what to expect from them.

---

### Post by nichos on 2007-11-10
Thank you for going into so much trouble.

I will be trying here in UK & get an old external modem too.

Looked at your  link, BUT too complecated for me.

Many thanks anyway,                   nick

---

### Post by Bartender on 2007-11-11
> **nichos said:**
> Looked at your  link, BUT too complecated for me.

nick, I tried to make my "Dial-up' thread as coherent as possible.  I know what it feels like to look at "instructions" that quickly get too complicated.

Maybe print the thing out and go thru it piece by piece.

If you go shopping for an external, make sure you understand the differences.  A serial modem, such as the US Robotics serials, are hardware modems.  I think of them as a little computer that only does one thing.  USB externals are usually not hardware modems.  They're basically winmodems in a box.

And watch out for really old 24Kbps and 36Kbps externals.  

I don't think this link will work after the bid closes, but this would be perfect.
[http://cgi.ebay.com/US-Robotics-56K-v-92-External-Fax-Modem-USR5686E_W0QQitemZ130171760895QQihZ003QQcategoryZ14920QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/US-Robotics-56K-v-92-External-Fax-Modem-USR5686E_W0QQitemZ130171760895QQihZ003QQcategoryZ14920QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

And if your PC doesn't have a serial port, there are ways around that too.  I pointed out one of them in my thread.

---

### Post by nichos on 2007-11-13
You  jolted my memory. I may still have my old USRobs either 32 or 45 up in the loftI will search it out.

Thanks                nick

---

