---
title: "Evolution Adressbook [export to cellphone]"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Jabz.biz on 2008-03-03
Hi Guys,...

I just have the first couple of hours with ubuntu behind me. As a retired Windows user I keep asking myself why I was waiting for 4 years to test this...

Anyway, this is my first post...and I`m sure it`s somehow a bizarre question I have. 

I just set up my emailaccounts in Evolution and imported my adressbook from thunderbird. Everything worked fine. When I checked out my contacts too see how a businesscard looks like in evolution, I saw plenty new options wich are not available in thunderbird.

Birthdays, 4 different email adresses,...wow! I mean, I love it...but I fear the moment when I try to go back to thunderbird or some other programm (e.g. cellphone). Won`t the datasets be broken? Does anyone have any experience with that? I mean, I add new data that cannot be displayed in thunderbird or my cellphone, at least CSV-Lists must be broken. 

Unfortunatelly I cannot try myself right now...but this one won`t let me sleep so please let me know if you have any idea if exporting/ importing to other clients will still work. 

Thanks a billion.

---

### Post by explicitly ambiguous on 2008-03-05
In my (small amount of) experience, most of the time the automatic conversion puts the extra fields in the "Comments" field.  Sometimes fields get swapped too... (home phone --> work phone, etc.) 

I think the best is to choose one program to use and stick with it -- one can spend along time fixing minor glitches in the import / export of csv files.  

Andy

---

### Post by Jabz.biz on 2008-03-08
LOL,...I still could not solve this problem...I found this thread (my thread) while I tried to find some more information with Google. OMG,...is there no solution? At least, is there an option to export the adresses from evolution and save them in ldif format? I only see the import button. 

Help is really highly appreciated. Thanks. Jab

---

### Post by explicitly ambiguous on 2008-03-09
In Evolution:  File > Save Address Book As VCard

The VCard format can be handled by Thunderbird / Outlook / etc  -- is this what you were asking or did I miss the point?

Andy

---

### Post by Jabz.biz on 2008-03-11
Hi, I`ve tried that before. It`s useless and not working. On the Evolution Project website they say "exporting" is not an available feature. so,...i`m going back to thunderbird. 
Thanks anyway.

---

### Post by scramasax on 2008-03-11
> **Jabz.biz said:**
> Unfortunatelly I cannot try myself right now...but this one won`t let me sleep so please let me know if you have any idea if exporting/ importing to other clients will still work.

That depends on the other client.

Evolution can export to vCard, which is a very widely-supported standard.  There's support for it in Kontact, Apple's Address Book, and even Outlook.  And many phones support vCards, too.

[http://www.imc.org/pdi/](http://www.imc.org/pdi/)

Note:

> Version 3.0 of the vCard format is an IETF standards-track proposal

[http://en.wikipedia.org/wiki/VCard](http://en.wikipedia.org/wiki/VCard)

If you're trying to import your contacts list as a vCard into some other program and that program can't do it, then the fault lies with that program, not Evolution.

Your worry seems to be that your address data will somehow get "locked up" in Evolution.  Don't worry.  It won't happen.  Evolution is doing the right thing by exporting to vCard: that's the best and most widely-supported format for exchange between programs.  I've often moved address books in and out of Evolution.

---

