---
title: "PPPoE connection over an USB modem"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by Lone_f on 2006-04-18
Hi.
I have a Lucent Cellpipe 22A-GX-E modem which is plugged into an USB port (I don't have an Ethernet card) and I don't know how to setup my connection.
scanModem doesn't find my device and rp-pppoe doesn't work because it says my C compiler (gcc I believe) can't make executable files.
Everything works fine under Windows XP.
Any suggestions?

---

### Post by meborc on 2006-04-18
there is a wiki page on USB ADSL modems [https://wiki.ubuntu.com/UsbAdslModem](https://wiki.ubuntu.com/UsbAdslModem) ... hope it helps... if not, come back and we'll try again :)

and after you get your modem working - [https://wiki.ubuntu.com/ADSLPPPoE](https://wiki.ubuntu.com/ADSLPPPoE)

---

### Post by bscbrit on 2006-04-18
Hi again.  If scan modem didn't find your own modem, have you discovered which driver you actually need to install to get it working?

---

### Post by bscbrit on 2006-04-18
To be able to build (i.e. compile programs from source) you will have to install 'build-essential' from your CD.

---

### Post by Lone_f on 2006-04-18
Unfortunately, I haven't found the appropriate driver.
I've tried to use EciADSL (as described in [this thread]("http://ubuntuforums.org/showthread.php?t=132171"), not sure if it would help me though) but it says it's depending on the "pppoe" package which I do not have.

---

### Post by bscbrit on 2006-04-18
The pppoe package should be on your CD - search Synaptic to find it.  The EciADSL has worked for me before - its worth the try but how will you download it?

Answered my own question.  Download it in Windows, then use 'sudo dpkg -i *packagename*'

---

### Post by bscbrit on 2006-04-18
Its not looking good so far:

[http://ubuntuforums.org/showthread.php?t=64181](http://ubuntuforums.org/showthread.php?t=64181)

This page might be useful:

[http://start.at/modem](http://start.at/modem)

and then there is this piece of advice from this thread [http://ubuntuforums.org/showthread.php?t=41722](http://ubuntuforums.org/showthread.php?t=41722)
> 
My advice: ditch the Lucent and plug your Linksys in its place. You might have to connect one of your machines to the linksys with a network cable for the first time (to set it up via the web interface). Can't help you with that very much, it's been a long time since I used a Linksys router/AP. Someone else in the forum will probably help you though (of course you'll need an internet connection for that... tricky these network problems). 

I'll go back to searching the web.

---

### Post by bscbrit on 2006-04-18
Do you know what chipset your modem uses?

---

### Post by bscbrit on 2006-04-18
The eciadsl might be on your CD - its in my repos but I'm not sure which one ](*,)

---

### Post by bscbrit on 2006-04-18
Does the modem show in the list when you open System -> Administration -> Device Manager ?

---

### Post by Lone_f on 2006-04-18
I've found the box in which my "modem" came - and it says "Remote Access Router". Does this fact change anything?
I can't find the documentation or the CD to check that what chipset is in use.
I couldn't make out any useful information from these, but you could check:
[http://www.lucent.com/livelink/090094038000ead0_Brochure_datasheet.pdf](http://www.lucent.com/livelink/090094038000ead0_Brochure_datasheet.pdf)
[http://www.lucent.com/products/solution/0,,CTID+2013-STID+10476-SOID+1367-LOCL+1,00.html](http://www.lucent.com/products/solution/0,,CTID+2013-STID+10476-SOID+1367-LOCL+1,00.html)

Moments after I found:
> It is based on the Globescan Viking Chipset, but they
have been swallowed up by Conexant.

---

### Post by Lone_f on 2006-04-18
In the Device Manager it shows up as an Unkown Device.
And in Networking there's an entry
```
**Modem Connection**
The interface ppp0 is not configured
```
But when I press Configure or Properties (don't exactly remember) and enable this connection I am supposed to enter my ISP phone number to dial. That is not required when setting up a PPPoE connection, AFAIK (I certainly didn't have to do it when setting up the connection in XP).

---

### Post by bscbrit on 2006-04-18
Good - the EciADSL package is designed for the Global chipset.  Have you got the eciadsl package on your CD?. (System -> Administration -> Synaptic, press the search button and look for eciadsl)  If yes, install it.

---

### Post by Lone_f on 2006-04-18
I've downloaded it and transferred it to my Ubuntu system but the package is dependent on the "pppoe" package, which i do not have and it's not on the Breezy CD either.

---

### Post by mips on 2006-04-18
Check your /etc/apt/sources.list file. I find the CD is usually hashed out.

My dapper looks like this:
> #deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ dapper main restricted

If you remove the # then you should be able to access the CD via synaptic, at least thats what I think.

---

### Post by bscbrit on 2006-04-18
Strange - my synaptic says it only depends on libc6, although it _recommends_ ppp and udev.

Try using the RPM from here:

[http://rpmfind.net/linux/RPM/sourceforge/e/ec/eciadsl/eciadsl-usermode-0.5-2.i586.html](http://rpmfind.net/linux/RPM/sourceforge/e/ec/eciadsl/eciadsl-usermode-0.5-2.i586.html)
or perhaps better still, the deb package from here:
[http://eciadsl.flashtux.org/?lang=en](http://eciadsl.flashtux.org/?lang=en)

There are several threads that contain useful information on getting this working:

[http://www.ubuntuforums.org/showthread.php?t=140878](http://www.ubuntuforums.org/showthread.php?t=140878)
[http://www.ubuntuforums.org/showthread.php?t=153612](http://www.ubuntuforums.org/showthread.php?t=153612)

The last link provides download locations for eciadsl-usermode, pppoe and pppoe-conf.  Sorry that you have to keep switching back and forth to Windows but its only while we get this working - :p

---

### Post by bscbrit on 2006-04-18
[QUOTE=mips]Check your /etc/apt/sources.list file. I find the CD is usually hashed out.

My dapper looks like this:


If you remove the # then you should be able to access the CD via synaptic, at least thats what I think.[/QUOTE]

mips - as luck would have it I had to do this today.  It didn't work the way I thought it would.  You have to use 'sudo apt-cdrom add' to add a CD to the repos.  That's a new one for me but at least it worked.

EDIT Glad that you joined the thread - I was needing someone competent to come along....

---

### Post by mips on 2006-04-18
[QUOTE=bscbrit]mips - as luck would have it I had to do this today.  It didn't work the way I thought it would.  You have to use 'sudo apt-cdrom add' to add a CD to the repos.  That's a new one for me but at least it worked.

EDIT Glad that you joined the thread - I was needing someone competent to come along....[/QUOTE]

Ok, did not know about the 'sudo apt-cdrom add' part either.

As for being competent I would thank you for the compliment but say I don't know much about PPPoE. Never configured it myself (In linux that is). My most common suggestion here would be to go and buy an old secondhand ethernet card for cheap ;)

You are more suited to the task at hand than me. Lone_f is in good hands 8)

---

### Post by bscbrit on 2006-04-18
Lone_f.  Its gone quiet - you are obviously busy working away trying to get your modem working.  I'll be back tomorrow evening.  Good Luck

---

### Post by Lone_f on 2006-04-19
Well, I've sucessfully installed the "pppoe" and "eciadsl" packages. However, the eciadsl-start command results in this:
```
Warning: couldn't find /etc/eciadsl/eciadsl.conf, default config assumed

[EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is OK

[EciAdsl 2/5] Uploading firmware...

ERROR: modem not found
```

---

### Post by bscbrit on 2006-04-19
[http://eciadsl.flashtux.org/tutorial.php](http://eciadsl.flashtux.org/tutorial.php)
[http://www.patriziobassi.it/blight/index.php?showtopic=94&hl=](http://www.patriziobassi.it/blight/index.php?showtopic=94&hl=)

Hi. Try these links for a few tips on how to configure it.

---

### Post by Lone_f on 2006-04-19
Well, when I select a Lucent modem, an error pops up
```
**bad listbox index "": must be active, anchor, end, @x,y, or a number**

bad listbox index "": must be active, anchor, end, @x,y, or a number
    while executing
".bloc1.modem.lchipset.contenu see [.bloc1.modem.lchipset.contenu curselection]"
    (procedure "select_modem" line 62)
    invoked from within
"select_modem"
    (command bound to event)
```

When I tried eciadsl-synch, I got
```
ERROR can't find your GlobeSpan GS7470 USB ADSL WAN Modem
ERROR eciadsl-synch: failed 
```
or
```
ERROR can't find your GlobeSpan GS7070 USB ADSL WAN Modem
ERROR eciadsl-synch: failed 
```
with a different chipset.

---

### Post by bscbrit on 2006-04-19
Can you confirm that you have carried out the following from the second thread, please?
```
Disable or delete dabusb module:
If /etc/hotplug/blacklist exists, edit it and add a line containing the word 'dabusb' (without the quotes) to it. Restart Linux.
Otherwise, type :
# modprobe -r dabusb && rm -f $(modprobe -l | grep dabusb) && depmod -a 

```

I'm going to Google some more for any additional help.

---

### Post by bscbrit on 2006-04-19
[http://eciadsl.flashtux.org/doc/eciadsl_install_en.html](http://eciadsl.flashtux.org/doc/eciadsl_install_en.html)

I don't know whether you have found this guide, or whether it actually helps.  It is almost as frustrating for me as it is for you.  I know that you are trying various options but there is not much I can currently contribute without seeing what is happening.  If you have anything that you need me to do (search for something specific - particularly error messages etc?) please ask.

---

### Post by bscbrit on 2006-04-19
I'm off until tomorrow evening.  Good Luck.

---

### Post by bscbrit on 2006-04-20
I'm back online.  Are you having any success or have you become frustrated?

---

### Post by Lone_f on 2006-04-20
Just tired of trying to find something useful and trying. God damn, I think my modem's not even supported (should've checked that first).
If I were a bit more experienced, I wouldn't give up this easily.
It's not easy for me to decide what to do when something goes not as described in some guide. Let's hope that will happen less and less often as I'll get more and more comfortable with Ubuntu :)

---

### Post by bscbrit on 2006-04-20
Yes, its always possible that the hardware is not supported by the available software.  And I know exactly how you feel - its happened to me. Another lesson learned I suppose.

But the important thing is what to do now, and it really depends on how much patience you have, how much disposable income you might have, and how much you are determined to try linux rather than stick with what you have.

I'll answer them in reverse order.  For me, I would rather use linux than Windows for a variety of reasons.  What they are doesn't matter here and to state them would only encourage others to come back in with claims regarding the pros and cons of linux v any_other_OS.  It wouldn't help you solve your problem.  _But_ a different distro might work out of the box with your modem and if you ignore the download time and the cost of a few CDs, then you might get a working system very cheaply.  No guarantees mind you, but you will learn a lot in the process.  It doesn't matter that you prefer Ubuntu.  Once you find a working system you can usually replicate what it does to make the modem work on the system of your choice or simply stick with the one that works best for you.

The next option requires some financial investment.  Buy yourself an ADSL modem that has ethernet output and which doesn't rely on any external software to operate.  I use a DSL-504 but they are no longer sold - however there will be many similar systems that are currently on the market.  They are easy to set up, ethernet is almost universal on motherboards but, if it is not fitted on yours, then a network interface card is very cheap. _EVERY_ linux distro can interface with ethernet! [I suppose someone will come back with a reply to prove me wrong but, if they do, it will be a distro that you have never heard of nor ever considered using!] And the expense of buying a new piece of hardware will be insignificant to the cost of paying for the next update to Windows or some other application program that you use regularly.  The linux equivalents are usually free.

The final option will teach you a lot, will frustrate you even more, but will give you the most personal satisfaction when you eventually succeed.  It is also quite simple - keep trying.  Google for any advice on setting up eciadsl.  Try every different installation routine.  Search other forums for people who have similar or even identical problems. Take notes. Compare notes.  Swap links to sites.  One day - you will probably find that someone has put together a working driver, or has written an obscure procedure that actually works. How long will it take?  Who knows?  But you haven't lost your existing Windows software.  You can always return to it when you simply want to get a job done, or download something simple, or swap emails, or, or, or...  Equally, you can always come back to linux and try something different, or even to repeat what you have already done just to check you didn't do something silly the first time.  

If I lived local to you I would be round like a shot to try different options to help you overcome the problems.  I enjoy the challenge I suppose but, to be honest, I've probably failed almost as often I have succeeded.  I've always learnt something useful though.  If you can find others who use linux who live near to you then make the effort to seek them out.  Perhaps they can help you, or perhaps you can help them.

Perhaps someone else reading this thread will come and show another route that you could try to solve the problem.  Lets hope so, but do not be surprised if they don't.  If your hardware isn't supported then no-one will yet know the answer to your problem.  But there will always be others who will be prepared to help you on this or other forums. :grin: 

Where to go now?  It depends on what you want to do ......

---

