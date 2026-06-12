---
title: "Serious Whine"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Habumongoose on 2007-03-13
OK, so after a great write up in PC World I bought 6.10 Edgy Eft. I even read up on the internet about the OS . But not enough. No or very little internet connection support, and no mention of the need for a serial port. I found this out after I bought a nice new lap top W/O a serial port.. it is going to be  ( come hell or high water ) my new science machine...no Bill Grap or Mac dodo allowed. I found info that the 3COM 3CXM756 pc card modem would work...sure, I have finally got the machine I.E. Ubuntu to recognize it's existence in the device manager, but it refuses to load the software I downloaded to disk from the USR site. So I am stuck with a nice new machine and a great program but I cannot get on the internet to download the programs I need to proceed ( I tried burning to disk on the Bill Gates machine but no dice and no install ) . I really could use some cheese with my whine. I just received " The Official Ubuntu Book"... no help here. The only mention of inter net hookup is KPPP..this is a KUBUNTU program, I do not have it in Ubuntu 6.10 ( unless it is a secret yet to be revealed ) It is other wise an informative book, but god help you if you are not an engineer. 30 I am out of gas at this point.

---

### Post by Shatrat on 2007-03-13
I haven't used dial-up or a serial port since 2000, but here is a resource which should help you out.
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

If your hardware is working then you should just need to check out one of the configuration methods at the bottom.  I don't know much about it but hopefully it get's you moving further along.

Also, think about using the enter key more when you post, blocks of text are hard on the eyes.

---

### Post by ricardisimo on 2007-03-13
I'm curious as to what you mean by "I bought 6.10 Edgy Eft", since Ubuntu is designed to be free. Also, all dial-up modem questions I'd have to refer you to [http://www.linmodems.org/](http://www.linmodems.org/). They are very helpful. If you have an issue with the "ScanModem" tool, post back or do a forum search. It's a driver issue, and ScanModem is the tool to help you.

---

### Post by kvonb on 2007-03-13
Use the Ubuntu DVD version, it contains all of the software in the main and universe repositories, ie everything that is available in the "Add/Remove" menu item, and Synaptic (Menu->System->Admin->Synaptic).

I'm not sure if you can get Canonical to send you a free copy or not, you might have to pester someone who can either download/burn it for you, or ask someone on these forums VERY nicely and they might send you a copy.

For dial-up there is gppp, or if you right click on one of the panels you can add the "Modem monitor" applet.

---

### Post by godd4242 on 2007-03-13
I hate to put it so brutally but I doubt that any OS, much less a technical knowledge specific one (cause yes even Ubuntu is more demanding than XP) was prepared for a damned dial up connection.
You're gonna have a helluva time with apt-get update just so you know.

---

### Post by Habumongoose on 2007-03-13
Thanks to all who replied.

DSL & Cable do not work here, I cannot afford satellite, so dialup is it ( for now moving to New Mexico soon )
.
Got 6.10 from Amazon...not every thing is 'free', the DVD version from Canonical.

I downloaded Scanmodem to disk...Ubuntu does not like it..unless I am doing something wrong to get it to run ( very likely at this stage of my ignorance ). So, to review I can get all I need off the internet, but I cannot get on the internet... nice circle.

---

### Post by MrKlean on 2007-03-13
I hate to tell you this, but Ubuntu is free... in any form.  You go to the download sites and get it.  If you want, they will mail you a free cd... no cost for shipping either !!!  Thot you might want to know !

---

### Post by kvonb on 2007-03-14
Canonical (the people who make Ubuntu), will mail you a FREE copy of Ubuntu, however it will take upto 8 weeks to get there!

Also I don't think they will send the DVD version, so I would AGAIN suggest asking someone in your country to send you a copy of the DVD.

It is FREE to download (if you have a good Internet connection!), and a writeable DVD costs pennies.

Post a thread in the Forum asking if someone would be nice enough to do that for you, I'm sure you will get a response.

Maybe look in the "LOCO" section of the main page, I'm guessing that you are in the US, there are tons of user groups there.

I could send you one, but again it would take at least 4 weeks to get there from Australia!

---

### Post by t4thfavor on 2007-03-14
if you have a soft modem there is a prog called slmodem or something like that, it usually works. Or you could do as I do and set up an IPCOP as the dialup server and share it over wireless not too efficient, but it will get you online. All this is assuming that your wireless card works.

---

### Post by kvonb on 2007-03-14
Try this:

On the main menu, select: System->Administration->Networking

Does it have an entry called  "Modem connection"?

If it does, click on it and then select "properties" on the rhs.

 Click "enable connection" and enter your dial-in details, then select the 2nd tab along the top and see if there is a device listed under "modem".

Let me know how you went.

Regards, Kev :)

---

### Post by ricardisimo on 2007-03-14
I had LOTS of problems with ScanModem myself... you can probably still find a few of my threads. Just make sure of a few things:
[LIST=1]
[*]Hand it to Ubuntu exactly as you downloaded it (don''t extract beforehand, for example)
[*]Don't forget to navigate your terminal to the appropriate directory
[/LIST]
I learned the last lesson while trying to get ScanModem working... total noob at the time, not knowing what it was that wasn't working right - my brain or the app. Good luck.

---

### Post by Habumongoose on 2007-03-16
ricardisimo,
   Thanks, got scanModem to run ( the good news ), no drivers available..it is a conexant modem ( bad news ). Still trying the pc card modem, but have to give it a few days...work you know.

---

