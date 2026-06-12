---
title: "AutoCAD and Ubuntu"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by nineteenfingers on 2006-12-13
Having tried Ubuntu for the first time last night (thanks again to those who helped me get it up and running from the DVD) I've pretty much decided to make as full a switch to Linux as I can manage.

I work using two primary applications, AutoCAD (from Autodesk) and a program called SuperBeam (from SDA)

I've looked around for information about using AutoCAD in a Linux environment, but all the information I've found has been geared towards alternatives, or using AutoCAD as a generic name for any CAD package.

What I need to know, is if there is a way to run Autodesk AutoCAD (currently using the full version 2006) in Linux. I really don't want to switch packages as it has taken me a long time to learn to use AutoCAD (still learning some of the tricks in it), it is an incredibly powerful package that is capable of everything I want it to do, with plenty of scope for improving my work flow as I learn the package more, and simply put, it is the industry standard.

So, is there a way to use AutoCAD in Linux (Ubuntu most likely, at least to begin with)

I have no objections in principle to dual booting XP for work, but to be honest I would rather work exclusively in Linux if at all possible.


Also, if anyone (by chance) has used SuperBeam 4, or any other Survey Design Associates Limited software under Linux, any input on how it worked/didn't work and what is needed to run it under Linux would be appreciated.


Thanks in advance.

---

### Post by L Campbell on 2006-12-13
> **nineteenfingers said:**
> Having tried Ubuntu for the first time last night (thanks again to those who helped me get it up and running from the DVD) I've pretty much decided to make as full a switch to Linux as I can manage.

I work using two primary applications, AutoCAD (from Autodesk) and a program called SuperBeam (from SDA)

I've looked around for information about using AutoCAD in a Linux environment, but all the information I've found has been geared towards alternatives, or using AutoCAD as a generic name for any CAD package.

What I need to know, is if there is a way to run Autodesk AutoCAD (currently using the full version 2006) in Linux. I really don't want to switch packages as it has taken me a long time to learn to use AutoCAD (still learning some of the tricks in it), it is an incredibly powerful package that is capable of everything I want it to do, with plenty of scope for improving my work flow as I learn the package more, and simply put, it is the industry standard.

So, is there a way to use AutoCAD in Linux (Ubuntu most likely, at least to begin with)

I have no objections in principle to dual booting XP for work, but to be honest I would rather work exclusively in Linux if at all possible.


Also, if anyone (by chance) has used SuperBeam 4, or any other Survey Design Associates Limited software under Linux, any input on how it worked/didn't work and what is needed to run it under Linux would be appreciated.


Thanks in advance.


I, too, have an interest in this.

Its actually not AutoCAD that I use but IntelliCAD ( [http://www.cadopia.com/default.asp](http://www.cadopia.com/default.asp) )

There was a little discussion about this on the Cadopia forum but the last post was about 1 year ago.

Hopefully it will happen, eventually.

---

### Post by Obor on 2006-12-13
I was also interested in this. All I could find so far is that there is no way to run AutoCAD directly under linux. 

One thing you can do is dualboot (which as you say you prefer not to do) 

Another option is to run windows in VMWare server in ubuntu (or any OS) and then install Autocad (or any windows only application)that way. [Check this thread to find how >>]("http://ubuntuforums.org/showthread.php?t=183209") I think that is the best/easiest/most practical way if you don't want to dualboot.

---

### Post by A_608 on 2006-12-13
I am looking to run Sibelius under Edgy using vmware server. Vmware will set up a virtual machine that is capable of a windows install. You would not have to dual boot to use  Autocad. When I am successful I will post results. I plan to run 98SE as my virtual machine. I found tutorial [here]("http://ubuntuforums.org/showthread.php?t=183209") for installation of vmware.

This is one possibility of running windows without dual booting.

---

### Post by scrooge_74 on 2006-12-13
You can always check if it can run under wine or cross over office.  I remember a few weeks ago I saw at [http://www.winehq.org](http://www.winehq.org) a picture of AutoCad running under wine.

---

### Post by Wartooth on 2007-01-24
This is something I am interested in as well.  My husband and I have a small machine shop, and it is one of my goals to get AutoCAD 2000 working under Ubuntu, whether it be through Wine (I found something somewhere that claimed to have done this) or whatever else it takes. Having looked at VMware, I'm not sure that I'd want to do that, unless somehow we could re-use one of the two XP CDs and keys we already have?  I'll see if I can read up in that thread about that.   

Being able to use AutoCAD will be a MAJOR factor in this becoming an all-Linux household in the future (albeit possibly in the distant future), or at least having more than one machine running a non-MS OS.

---

### Post by emrextreme on 2007-08-05
Here is howto; 

Autocad on Ubuntu

[http://doctus.net/showthread.php?t=17006](http://doctus.net/showthread.php?t=17006)

---

### Post by C.S.Cameron on 2007-08-05
AutoCad 2000 works well with Wine.
It does everything Acad should do.
It is not that different than 2002.
I normally use 2002 for modeling and layout in Windows.
Every version since is slow and bloated.
Rhino 2 also works well with Wine and will do those modeling chores that no version of Acad can do.

---

### Post by L Campbell on 2007-08-05
> **emrextreme said:**
> Here is howto; 

Autocad on Ubuntu

[http://doctus.net/showthread.php?t=17006](http://doctus.net/showthread.php?t=17006)


This didn't help me:-

Bu adresteki Pardus'a Autocad kurulumundan derlenmi&#351;tir.

Gerekli program Wine.
Resimdeki gibi, Ubuntu'daki Uygulama ekle/kald&#305;r menüsünden Wine program&#305;n&#305; i&#351;aretleyip Tamam'a bas&#305;yoruz. Otomatik olarak kuruluyor.

Is it possible that you have an English translation of this?

Thanks.

---

### Post by univremonster on 2007-08-13
you can translate webpages at av.com

Not sure what language that is, looks like German or Low Dutch or something... 

At any rate, from the screenshots you can tell this person is recommending using Wine

---

### Post by tyk on 2007-08-22
hi all
i am an architect and have been wanting to change to linux as soon as i possibly can. as expected the biggest hassle or rather stumbling block has been finding a way to run Autocad EFFECTIVELY. 
you see, essentially there is no problem. go ahead and install wine (0.9.36) and not a later version. then install package called msttcorefonts. (not in ubuntu repositories but available elsewhere, just google it and download the .deb or .rpm and do needful with it). it will download common and FREE ms fonts like arial, verdana etc.. let it.
calling up wine is something like this
1. on a terminal *winecfg*
2. on winecfg panel (which should have come up looking very windows), just make sure that environment is set to windows 2000.
3. go to your acad dump or cd and code *wine setup.exe*
4. here's why 0.9.36 because any other version of wine lets you fill in only two digits on the serial 1st tab. no idea why.. i highly recommend doing this on a terminal and not through your file browser because there are some messages you should be looking out for.
5. fixme: messages can essentially be ignored as they are non-critical; err: messages are usually fatal. the restart at the end of the installation is not required. atleast in my experience it made no difference. my guess is a 'restart' in this case is equivalent to a recall of wine (bless the boys)
6. if all is well at this point an autocad link will turn up on your desktop. double clicking it starts it off. alternately code in home folder *wine .wine/drive_c/"Program Files"/ACAD2000/acad.exe*. again recommend doing this in a terminal.

lucky step 7. everything works.. viola or voila (?) anyway, you are now thriled to bits and quickly open up some of your precious drawings. try the 3d ones too. on first go everything is hunky dory.:guitar:

ok heres the problem list mine atleast:
1. fonts are scr***d. so i end up putting off all text layers and work only on geometry. actually fonts work but their rendering is superslow.
2. ctrl1 or properties does not work, my biggest bit**
3. since so far you prob were working on autocad2005 or seven or some wild variety, your files dont open. :lolflag: solution : work only on 2000 version files. reboot to windows, save as 2000 version all your files and get back. interestingly there's a wonderful free package called dwggateway (google and you shall find) which installs onto ANY autocad and can open ANY other version. BUT it does not install under wine, so there.
4. here's what i am working at: themysterious death of autocad. sometiimes after a reboot or a logoff autocad refuses to start, like what happens is that the window definition for the model tab is set to size -4,-4 an absurd value. now where is this definition i do not know. any help on that would be apprecialted.

thats so far my experience. it hasn't been bad at all. many pleasant surprises and the potential of better times etc.

anyway hope this helps.
haven't tried vmware stuff because the disk space demands are quite big..

---

### Post by ba55lvr on 2007-09-01
> **univremonster said:**
> 
Not sure what language that is, looks like German or Low Dutch or something... 
... it is Turkish. :cool:
Sadly, I don't speak Turkish, but as far as I understand :-k :

- Install Wine
- Install AutoCAD
- copy the files **[COLOR="DarkRed"]msvcrt.dll[/COLOR]** and **[COLOR="DarkRed"]ole32.dll[/COLOR]** (from the install CD i think) in the folder **.wine/c/windows/system32 ** so that Wine could load them
- Start using AutoCAD.

_WARNING:_ This is not an official translation. Use it or not, on your own risk!

I shall try this, 'cause I also want to run ACAD from Linux ;)

---

### Post by wirelessmonkey on 2007-09-01
See this thread... [http://ubuntuforums.org/showthread.php?t=524557](http://ubuntuforums.org/showthread.php?t=524557)
A successful AutoCAD 2000 install via wine.

---

