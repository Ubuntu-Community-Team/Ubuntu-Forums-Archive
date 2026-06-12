---
title: "evince eats all my ram"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by afeasfaerw23231233 on 2007-11-21
my mainbox has 768MB RAM. after being up for 12 and a half day, it freezed randomly and finally stop responce. i closed virtualbox but the system was still sluggish and finally stopped response. so i logout and login (by a great effort as i don't want to reboot in ) and everything seemed fine. but after a day or so it became sluggish again. this time a type top and find out a program called evince eaten up ~60% of my memory. i realized it is the pdf viewer. so i closed all the pdf doc. and it worked fine again. but the problem is i have to open quite a lot of pdf document all the time - around five to six (each contain 50 to 200 pages) any idea to make evince doesn't eat so much RAM?

---

### Post by afeasfaerw23231233 on 2007-11-21
EDIT: i just take a quick test: i open 4 pdf doc (total 1400 pages) and it bursts up to 60% (~450MB) of my RAM!!! and when i open three to four more pdf doc and my ram is full and it starts to occupy my swap space (i think that's why my box becomes so slow since all my applications are kicked out from RAM -- nOOb)
Can i restrict ''evince'' to >100MB RAM (i don't mine my pdf reader being sluggish a bit, but not my whole system)?

---

### Post by afeasfaerw23231233 on 2007-11-22
bump

---

### Post by afeasfaerw23231233 on 2007-11-22
BUMP. evince is more bulky than adboe reader 8.0

---

### Post by mali2297 on 2007-11-22
Try **xpdf**, it's not as polished as evince but faster and doesn't use as much memory.

---

### Post by afeasfaerw23231233 on 2007-11-23
thanks. xpdf works but lack many feature. but still better than evince as it uses very few ram

---

### Post by TidusBlade on 2007-11-23
IF you want, you can give KPDF a try, from my experience, it's much better and faster than Evince ;) Also has loads of options compared to xPD, but maybe cuz im using KDE...

---

### Post by afeasfaerw23231233 on 2007-11-23
thanks but how to enable kpdf to display two or more pdf doc simultaneously?

---

### Post by afeasfaerw23231233 on 2007-12-28
i meant in two seperate windows. bump

---

### Post by J.Meador on 2008-01-29
i just switched to gutsy from dapper. evince and epdf viewer are both much slower than they were in dapper- it takes each of them as much as a minute to render a complicated page. xpdf seems to work ok.

---

### Post by stchman on 2008-01-29
> **afeasfaerw23231233 said:**
> my mainbox has 768MB RAM. after being up for 12 and a half day, it freezed randomly and finally stop responce. i closed virtualbox but the system was still sluggish and finally stopped response. so i logout and login (by a great effort as i don't want to reboot in ) and everything seemed fine. but after a day or so it became sluggish again. this time a type top and find out a program called evince eaten up ~60% of my memory. i realized it is the pdf viewer. so i closed all the pdf doc. and it worked fine again. but the problem is i have to open quite a lot of pdf document all the time - around five to six (each contain 50 to 200 pages) any idea to make evince doesn't eat so much RAM?

I know a lot of people won't use Acrobat but it works very well in Ubuntu.

---

### Post by vussvillem on 2008-02-21
Same thing here. I'm using Gutsy Gibbon on system of 512mb RAM. Evince uses up all my memory when I try to open for example 3,7MB document with 12 pages in it. I've tried to run evince from terminal, same situation. My desktop becomes very very sluggish.

I suppose it may be a Gnome specific problem, meaning that first, when I had Xubuntu with XFCE desktop, evince worked fine. (I am a total noob, but I noticed that during installation of ubuntu-desktop package, evince gtk+ was replaced with evince or something like that...)

However, right now I have to use Adobe Acrobat reader, because evince is useless. I'll probably have to give a xpdf a try.

---

### Post by afeasfaerw23231233 on 2008-02-22
i am a noob too. but i think evince should be given a best-ram-eater award in gutsy!!

---

### Post by doctorbighands on 2008-02-22
Evince is useless. It's one of the first things I've learned to dump with any new Ubuntu install.

Try KPDF instead. It's super-lightweight, and runs beautifully - even on my Gnome desktops.

---

### Post by adrien214 on 2008-02-27
Yeah, same here...

when I open a document which is **less than 1Mb**, eVince takes up more than **275Mb** of RAM... this is totally sick!

I'm switching to ePDF or kPDF or even Adobe... do we have to file a bug about it ?

It's funny though, in french, "evince" means "to supplant" I guess it's just true, about the memory, it supplants free space :P

How can I get rid of evince anyway ? it's bound to the ubuntu-desktop package, and I wouldn't like to try removing the latter...

---

### Post by afeasfaerw23231233 on 2008-02-27
> **adrien214 said:**
> Yeah, same here...

when I open a document which is **less than 1Mb**, eVince takes up more than **275Mb** of RAM... this is totally sick!

I'm switching to ePDF or kPDF or even Adobe... do we have to file a bug about it ?

It's funny though, in french, "evince" means "to supplant" I guess it's just true, about the memory, it supplants free space :P

How can I get rid of evince anyway ? it's bound to the ubuntu-desktop package, and I wouldn't like to try removing the latter...

after installing ePDF or kPDF right click a pdf > properties > open with >and chose the pdf application you want to use, then next time it will only use this application to open pdf file

---

### Post by shuttleworthwannabe on 2008-03-24
sorry guys, I have just installed epdfviewer and works fine, but how do I send documents from epdfviewer to print...there is no menu entry nor a toolbar icon for this? is this normal?

thanks

---

