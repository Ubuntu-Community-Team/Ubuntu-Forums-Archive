---
title: "Usb Adsl"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by pcawdron on 2006-10-14
](*,) 

I know, I know... I read all the other posts on this subject. Linux hates USB modems.

I'm dabbling with Ubuntu after a good friend recommended it to me over my troublesome install of Win XP. I'm running XP on one HDD and Ubuntu on the other. Without an internet connection, Ubuntu is never going to get off the ground. I don't want to have to go out and buy a new modem just test out Ubuntu. That's like buying a set of tyres when you want to test drive a car. 

Are USB ADSL modems really that bad?

I have a Dlink DSL-200 ver A. Being a complete novice with Linux, I stumbled upon the Network Connections but the autodetect doesn't pick it up. Is there anything I can do or am I screwed?

Cheers,
Peter

---

### Post by jorn on 2006-10-14
Wireless can be a pain in Ubuntu, especially on USB.
[http://ubuntuforums.org/showthread.php?t=20954](http://ubuntuforums.org/showthread.php?t=20954)

---

### Post by public_void on 2006-10-14
After quick look around I found [this]("http://eciadsl.flashtux.org/modems.php?modem=23"). Hopefully thats your modem. If it is then you can follow the [beginners guide](http://eciadsl.flashtux.org/tutorial.php) using mostly a GUI.

---

### Post by TheWizzard on 2006-10-14
> 
I know, I know... I read all the other posts on this subject. Linux hates USB modems.

this has nothing to do with linux. it was the same when i was a windows user. actually, i think my isp abandoned all usb modems. 

> Are USB ADSL modems really that bad?
are you serious?!?

---

### Post by pcawdron on 2006-10-14
Thanks for the help, it is very much appreciated...

The post by public_void identified at my exact modem.

Now, which file do I download?

[http://eciadsl.flashtux.org/download.php](http://eciadsl.flashtux.org/download.php)

Also, any suggestions as to how I should transfer the file once its download to XP. Will Ubuntu recognize my flash drive? Or should I burn it to a CDROM?

PS. This may sound dumb, but after seeing numerous posts on USB ADSL modems that appear to be very frequent, why isn't ECIADSL simply included in the initial Ubuntu Live CDROM image? Seems to me that would save an aweful lot of posts.

---

### Post by TheWizzard on 2006-10-15
> PS. This may sound dumb, but after seeing numerous posts on USB ADSL modems that appear to be very frequent, why isn't ECIADSL simply included in the initial Ubuntu Live CDROM image? Seems to me that would save an aweful lot of posts.
probably legal issues. ubuntu is free (as in beer), remember.

---

### Post by pcawdron on 2006-10-15
OK, I've loaded eciadsl for debian but I get an error "Dependency is not Satisfiable : PPPoe."

But a USB modem, by definition is not PPPoe (over ethernet) and is PPPoa. Any ideas on what I'm doing wrong?

Thanks for your help (and patience) it is appreciated.

:-D

---

### Post by pcawdron on 2006-10-21
OK, if anyone else runs into this PPPoE dependancy not satisfiable. Before you install the eciadsl...deb file you need to install PPPoE for Ubuntu

[http://packages.ubuntu.com/breezy/net/pppoe](http://packages.ubuntu.com/breezy/net/pppoe)

I'm still not connected but at least all the parts are installed now its a case of figuring out the configuration.

Hope this helps someone else.

---

### Post by bobtacular on 2006-10-26
Hello 
I am also trying to get ECIADSL to work with ubuntu. I downloaded the "deb" file and did the following:
[COLOR="Gray"]root@*******-desktop:/home/*******# sudo dpkg -i eciadsl_0.11-3_amd64.deb
Selecting previously deselected package eciadsl.
(Reading database ... 69839 files and directories currently installed.)
Unpacking eciadsl (from eciadsl_0.11-3_amd64.deb) ...
Setting up eciadsl (0.11-3) ...[/COLOR]

then I just followed the next spet in the EciAdsl tutorial for Linux beginners, which says:
[COLOR="Gray"]**# modprobe -r dabusb && rm -f $(modprobe -l | grep dabusb) && depmod -a** [/COLOR]
then I got this in return:
[COLOR="Gray"]root@*******-desktop:/home/*******# modprobe -r dabusb && rm -f $(modprobe -1 | grep dabusb) && depmod -a
modprobe: invalid option -- 1
Usage: modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-Q] [-b] [-o <modname>] <modname> [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...][/COLOR]

Can someone please tell me what Im doing wrong, that would be great.
Cheers

---

### Post by PriceChild on 2006-10-26
> **TheWizzard said:**
> ubuntu is free (as in beer), remember.Isn't it free as in speech?

i used eciadsl for a year and got better performance than on windows.

---

### Post by bobtacular on 2006-10-26
Is the a "How to" or tutorial to setup Eciadsl on Ubuntu

---

### Post by TheWizzard on 2006-10-27
> **PriceChild said:**
> Isn't it free as in speech?


of course!but as fars as i know giving away stuff like codec's for free is not allowed in all countries.

---

### Post by pcawdron on 2006-10-27
OK, it's taken some time but I'm within a whisker of connecting.

I've got ECIADSL set up and can attempt to connect and view the connection reaching my ISP. Seeing and recognizing a server name is very encouraging. But I could not connect.

My ISP has advised that I need to use the PPP mode RFC 2516 but that's NOT one of the options in the ECIADSL configuration tool.

Help..........................

---

### Post by bobtacular on 2006-10-28
Yeh HELP anyone who has got eciadsl working on ubuntu please share your knowledge

---

### Post by pcawdron on 2006-10-28
Bob,

For what it's worth, I've figured out that RFC 2516 replaced Snap 1483 Bridged Eth No FCC (so that's the option to use in ECIADSL)

But I still haven't connected.

I get a tap0 waiting message 

It seems pppoe hasn't started (how the hell do you start that)

Yes, it would be nice if someone, anyone would share a little insight into these things. I think people forget that new users are NEW (ie, they don't know what to do and it's all a little bewildering). This is all probably very routine to a seasoned user, it's just a shame they don't care...

Not impressed

---

### Post by gn2 on 2006-10-28
You could install free VMWare server in XP and run/install Ubuntu in a virtual machine?
[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

Perhaps that may be a work-around for the modem issue, as VMWare uses a bridged connection.
I don't know if it will, but it's worth a try?
If it works it would give you an idea of Ubuntu functionality before paying out for a combined modem/firewall/router...
(e.g. my own recommendation the Netgear DG834G)

---

### Post by pcawdron on 2006-10-29
Thanks for the suggestion. I guess it goes a little against the grain to pay for a new modem when this one works fine (with XP)

I must admit, it has been a good learning curve getting as far as I have. I think I'm so very close, but still no cigar.

Got rp-pppoe downloaded and unpacked, but when I try to run the go-gui it comes up with an error saying no C compiler. It seems there's something that needs to be switched on first. Any ideas?

I've run the pppoeconf and it seems to work but without being compiled perhaps its not quite there. Although it does see my tap0 once eciadsl-start has run.

I think the real problem is that Ubuntu is changing so quickly no one has time to document the evolving process. Everything I've found on the net has been well out of date. Either past versions or mentioning folders/processes that no longer exist, etc. Look at the screenshots and they're all for older versions. 

Perhaps Ubuntu's greatest success is also its weakness. It moves ahead progressively, but us new folk can't keep up. 

I hate giving up on things. Perhaps I'm too stubborn. But I want the damn thing to work. Everything suggests it should work. The ECIADSL config is set up correctly. The PPPoE wizard seems to work fine. I just don't know what's the final piece of the puzzle............

If I figure it out I'll put together a more up to date walk through to save others the aggravation.....

Cheers,
Peter

---

### Post by gn2 on 2006-10-29
> **pcawdron said:**
> Thanks for the suggestion. I guess it goes a little against the grain to pay for a new modem when this one works fine (with XP)

I must admit, it has been a good learning curve getting as far as I have. I think I'm so very close, but still no cigar.

Got rp-pppoe downloaded and unpacked, but when I try to run the go-gui it comes up with an error saying no C compiler. It seems there's something that needs to be switched on first. Any ideas?

I've run the pppoeconf and it seems to work but without being compiled perhaps its not quite there. Although it does see my tap0 once eciadsl-start has run.

I think the real problem is that Ubuntu is changing so quickly no one has time to document the evolving process. Everything I've found on the net has been well out of date. Either past versions or mentioning folders/processes that no longer exist, etc. Look at the screenshots and they're all for older versions. 

Perhaps Ubuntu's greatest success is also its weakness. It moves ahead progressively, but us new folk can't keep up. 

I hate giving up on things. Perhaps I'm too stubborn. But I want the damn thing to work. Everything suggests it should work. The ECIADSL config is set up correctly. The PPPoE wizard seems to work fine. I just don't know what's the final piece of the puzzle............

If I figure it out I'll put together a more up to date walk through to save others the aggravation.....

Cheers,
Peter

Time-v-money, how much is a cheap router?

I admire your perseverence I'd have thrown the towel in by now and got me a router......

---

### Post by bobtacular on 2006-10-29
Well if this is going to be the solution, anyone(in australia) know of any decent [FONT="Arial Black"]Cheap[/FONT] modem/routers

---

### Post by pcawdron on 2006-10-29
My USB ADSL days are over. 

GN2 is right... as much as it's nice to persist and get the thing working, it's wasted time.

Based on GN2's recommendation I'm going to go for the Netgear DG834G [http://www.shopbot.com.au/p-3953.html](http://www.shopbot.com.au/p-3953.html) has them for $105-150 Aussie bucks.

Oh, incidentally, a friend of mine has a slightly older version of the same router/modem and sings its praises. His internet access is the same speed as mine (512) but it's noticeably quicker. I'll be interested to see if my internet connection is faster with the Ethernet modem as opposed to a USB ADSL modem.

Cheers,
Peter

:D

---

### Post by bobtacular on 2006-10-29
ok thanks for the advice. $110 isnt bad

---

### Post by mahy on 2006-10-29
> **pcawdron said:**
> I know, I know... I read all the other posts on this subject. Linux hates USB modems.


It's quite the opposite way around. Those modems' manufacturers hate Linux.

If you REALLY like to set it up, Slackware and/or its clones may be your best bet, coz they have a rp-pppoe package that can handle fake dialing over such modems. But it probably won't go without a kernel recompilation :(

I personally think USB DSL modems ARE bad, because they're non-standard devices that put extra load onto your CPU, as opposed to ethernet modes which operate autonomously.

---

