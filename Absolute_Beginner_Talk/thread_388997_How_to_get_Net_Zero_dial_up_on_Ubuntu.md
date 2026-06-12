---
title: "How to get Net Zero dial up on Ubuntu?"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by dajayhawk on 2007-03-20
I just installed ubuntu.  I used to have windows but something went terribly wrong.  I used net zero.  How can i use net zero dial up on ubuntu.  keep in mind that i have no internet on my system with ubuntu on it.  thanx

---

### Post by jem7v on 2007-03-20
The main issue you're going to run into is that Linux tends to have very poor dial-up support because most modems are Winmodems.  You can read a little more about it here:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

Essentially, a winmodem is a stripped down modem that doesn't have the hardware to do its job and asks Windows to do a lot of the work for it.  Because there's so no standard for how winmodems work (and because their developers tend not to open-source their drivers) they're hard to write drivers for in Linux and have pretty poor support.

But if you have a Real hardware modem you shouldn't have a problem, because they're supported quite well.

---

### Post by Bartender on 2007-03-20
People have had varying luck with Netzero/Juno.  I can connect to Juno but get kicked off after 20 minutes without warning regardless of whether I'm actively surfing or downloading.  So that's pretty much useless.  I've talked to or heard from a few other Linux/Juno users and some have reported that they don't get kicked off like I do.  Sure wish I knew what the deal was there.

Evolution can be used to check Juno/Netzero email.  I'm stuck at halfway getting Thunderbird to work with Juno.  Can receive but can't send, and Juno techies have been useless.
PM me if you want the Evolution directions.

jem7v probly identified your immediate problem.  This has been discussed to death on Ubuntu forums, so there's lots of info to be found.  Winmodems don't work in Linux without software tweaking, and many just won't work period.  In some cases the tweaks aren't that difficult, but tell that to someone who just installed Linux!

I bought a couple of old Sportster external modems on ebay.  Flashed them to the latest firmware by hooking them up to a Windows PC and going to the USRobotics website.  An external modem is probly your best bet.  Well, broadband is the real answer but you know what I mean...

EDIT:  The only reason I haven't dumped Juno is we're getting it really cheap.  If you're paying $10/month for it drop Juno and find an ISP that doesn't use any proprietary software to connect you.  Two cheap ISP providers that shold work just fine with Linux (I've talked with both of them) are Copper.net or Nationwide Access.  Copper limits you to 200 hours/month (that's roughly 6 hours/day)

---

### Post by dajayhawk on 2007-03-21
so is there any way i can get my net zero to work w/o having to buy new hardware.  my computer is a compaq presario and it is quite new.  

if so is there an easy step by step guide u can give me  

thanx

---

### Post by t4thfavor on 2007-03-21
There is a sticky on this forum with winmodem instructions. If your laptop is newer, you may not have a serial port, at which point an external modem will not help you much (they are all serial) search for slmodem, and slmodemd and you should find whay you need to get started. Of course you will have to have internet to do that. Linux as a whole can be a bit overwhelming at first, but once you get to know your distro, it will get alot easier. If you can not get it to work, you could do what I do and use another pc as the dialup router. I have an old Compaq that sits in the corner and faithfully serves out my 28.8 internet connection over WIFI without a hitch. 

It runs IPCOP, and has an old USRobotics hardware modem, probably the easiest linux box I have ever set up.

---

