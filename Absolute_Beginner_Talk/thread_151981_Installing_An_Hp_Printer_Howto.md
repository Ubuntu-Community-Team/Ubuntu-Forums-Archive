---
title: "Installing An Hp Printer Howto"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-03-28
I have moved this exact howto to the howto's sub-form.  here it is: [http://www.ubuntuforums.org/showthread.php?t=184838](http://www.ubuntuforums.org/showthread.php?t=184838)

Please use that thread from now on for all questions or comments.

---

### Post by jason.b.c on 2006-03-28
Or you could just plug it in and do a >     **Auto Detect Printer** from the same  **System--Administration--Printing**!

Hp All in one 1315v ..

Thats all i did :)

---

### Post by user1397 on 2006-03-28
[QUOTE=jason.b.c]Or you could just plug it in and do a >     **Auto Detect Printer** from the same  **System--Administration--Printing**!

Hp All in one 1315v ..

Thats all i did :)[/QUOTE]
Yes you could do that, but if it doesn't autodetect, you have to go through my steps! ;)

---

### Post by jason.b.c on 2006-03-29
> Yes you could do that, but if it doesn't autodetect, you have to go through my steps! 

What do you mean? :confused:    I did that exactly to the " T ",  and it worked perfectly!
 I know the hp 1315v all in one is in the supported printers list, along with alot of others.:) 

Not unless your just talking about the printers that aren't supported?? not in the list.:(

---

### Post by user1397 on 2006-03-29
[QUOTE=jason.b.c]What do you mean? :confused:    I did that exactly to the " T ",  and it worked perfectly!
 I know the hp 1315v all in one is in the supported printers list, along with alot of others.:) 

Not unless your just talking about the printers that aren't supported?? not in the list.:([/QUOTE]
Well sometimes printers just don't autodetect, I don't know why.  Thanks for the advice but your case is just one case and you can't say that all printers are autodetected.  And this statement has been made in a non-offensive way, by the way. :cool:

---

### Post by Sef on 2006-03-29
If your HP needs the HPLIP driver, you may need to follow wondering_jew's thread to get it running.  I did with my PSC 1610.

The thread:

> hey I just got my psc 1610 working for both scanning and printing (yay me!)...
first I did

sudo apt-get install hplip gtklp xpp hpijs python-qt3-doc libqt3-mt-mysql hplip-ppds

I don't know if you need all those packages they were all reccomended or suggested and I hate going back and adding things later... then I went to system->administration->printing > printer> add printer and in step 2 I selected psc 1600 from 'HP (HPLIP)' in the manufacturer drop down menu (as opposed to just 'HP' which did make a difference for me ) this got the printing part working.

Then xsane told me it didn't find any scanning devices so I installed a package called libsane-extras from synaptic and tried xsane again and it worked.

[http://ubuntuforums.org/showthread.php?t=39625&highlight=PSC+1610]("http://ubuntuforums.org/showthread.php?t=39625&highlight=PSC+1610")

---

### Post by user1397 on 2006-03-29
[QUOTE=Sef]If your HP needs the HPLIP driver, you may need to follow wondering_jew's thread to get it running.  I did with my PSC 1610.

The thread:



[http://ubuntuforums.org/showthread.php?t=39625&highlight=PSC+1610]("http://ubuntuforums.org/showthread.php?t=39625&highlight=PSC+1610")[/QUOTE]
Yes that works too. My thread is intended more for noobs and people who hate the command line.

---

### Post by jason.b.c on 2006-03-30
> And this statement has been made in a non-offensive way, by the way. 

Oh, i wasn't trying to be offensive,:(  I apologize then if you think that i was....:)

---

### Post by Sef on 2006-03-30
> Yes that works too. My thread is intended more for noobs and people who hate the command line.

I had put it in in case it did not work without the command line.  That's all.  Your way is certainly easier for those who don't know or don't like the command line.

---

### Post by user1397 on 2006-04-23
Hey staff,
shoudn't this be moved to the howto forum?

---

### Post by openmind on 2006-04-23
Thanks for that, I hope it helps some people, but most of those having problems already now how to install a printer. They had it working under Breezy, and it quit with the Dapper upgrade.

In my case there was no printer detected, and no port detected either! I found the lp module wasn't loading with the new kernel;

[http://www.ubuntuforums.org/showthread.php?p=945887#post945887]("http://www.ubuntuforums.org/showthread.php?p=945887#post945887")

---

### Post by user1397 on 2006-04-23
[quote=openmind]

[http://www.ubuntuforums.org/showthread.php?p=945887#post945887]("http://www.ubuntuforums.org/showthread.php?p=945887#post945887")[/quote]
Thanks for this guide. I hope it makes this thread more helpful for everyone.

---

### Post by Owa on 2006-07-19
Thanks for the guide its a good start for some of us Ubuntu newbies. I however, managed to setup my HP 4200 officejet series by just going through the 'Add new printer' wizard but making sure that Ubuntu detected the printer. It was easy and fast.

---

### Post by user1397 on 2006-07-20
> **Owa said:**
> Thanks for the guide its a good start for some of us Ubuntu newbies. I however, managed to setup my HP 4200 officejet series by just going through the 'Add new printer' wizard but making sure that Ubuntu detected the printer. It was easy and fast.well, whatever floats your boat man :p

---

### Post by sjhstorm on 2006-07-20
Just in case some people are having problems with HP multifunction printers (especially with scanning). The only way I got my PSC750 working correctly (including HP device manager), was to download the lastest drivers from [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/) (version 1.6.6a).

The ubuntu version is somewhat out of date and has problems autodetecting certain models. Follow the instrutions on HPLIP download, they even have specific instrutions for Ubuntu. It will mean using the command line but the instructions are very clear and you can just copy and paste them (saves all that typing).

Hope this helps someone

---

### Post by 11hjpphty76lkjj on 2006-07-21
I agree the drivers in ubuntu are very very old.  I'd like to speak with someone who can advise me on how I can get the latest version into edgy for testing.  *nudge to someone* :)

Also if anyone has any suggestions on the ubuntu install instructions please let me know and I'll update them.  I'm hoping to make our instructions as easy and straight forward as possible.  As well we are working on an extended install application that will make the install and configure a very simple process using a gui interface.  Still in the works though.

---

### Post by makhand on 2006-08-06
> **sjhstorm said:**
> Just in case some people are having problems with HP multifunction printers (especially with scanning). The only way I got my PSC750 working correctly (including HP device manager), was to download the lastest drivers from [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/) (version 1.6.6a).

The ubuntu version is somewhat out of date and has problems autodetecting certain models. Follow the instrutions on HPLIP download, they even have specific instrutions for Ubuntu. It will mean using the command line but the instructions are very clear and you can just copy and paste them (saves all that typing).

Hope this helps someone


Thank you very much. that was very helpful. I was not able to detect my photosmart c3180 with xsane or get any kind of scanning to happen. After i followed the instructions in the link, everything is working perfectly. This is the first time i have witnesed scanning in linux. It works well and gives me lots of options. For those reading this, also make sure you do step 4 in the instructions ('sudo hp-setup -a'). It does absolutely everything (detects printer, sets propper settings) for you, once you've installed everything else according to steps 1-3. Again, thanks for the link. 

Those printer drivers should REALLY be updated considering Ubuntu is one of the most popular distros. Kind of embarrasing if you dont have such new technologies as 'scanning' in a premiere linux distro.

---

### Post by U5tabil on 2006-09-09
I have an printer in Network. It an Hp officejet d series. Iv followed the instructions but i cant find it. And i dont know the url of the printer ](*,) 
But i know the Ip of the printer. Anyone know how i can "install" it?

---

### Post by tinsami1 on 2006-09-13
> **U5tabil said:**
> I have an printer in Network. It an Hp officejet d series. Iv followed the instructions but i cant find it. And i dont know the url of the printer ](*,) 
But i know the Ip of the printer. Anyone know how i can "install" it?

Issuue the command:

```
sudo hp-makeuri *ip.address.of.the.printer*
```

and it will provide you with the URI to use.

---

### Post by greg m on 2006-09-14
hello

i have a HP 3740, and sometimes it works and some times not. all i get is a blinking light.

---

### Post by tanari on 2006-09-16
I have installed latest (1.6.7) hplip from hplip.sf.net, all works fine, but printer use wrong dimensions while printing.

example:
in open office I set right border to 10 mm. But in real page I have got only 7 mm.

Somebody know how to setup printer rightly?

---

### Post by user1397 on 2006-09-16
> **tanari said:**
> I have installed latest (1.6.7) hplip from hplip.sf.net, all works fine, but printer use wrong dimensions while printing.

example:
in open office I set right border to 10 mm. But in real page I have got only 7 mm.

Somebody know how to setup printer rightly?that could just be a bug in openoffice.  i dont see how the printer has anything to do with that.

---

### Post by tanari on 2006-09-18
test page made by hp-setup also has this bug, maybe problem in drivers? don't know what to do

---

### Post by juky on 2008-03-10
Thanks ubuntuman001 and jason for the tips!

---

### Post by user1397 on 2008-03-10
> **juky said:**
> Thanks ubuntuman001 and jason for the tips!yea no problem man, just remember if you want to discuss this subject more, or have any more questions, please go to the tutorials section howto I made for this :)

---

