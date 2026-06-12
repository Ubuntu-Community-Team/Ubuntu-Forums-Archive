---
title: "AOL Broadband"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by pilgrim-online on 2006-10-18
I must start by saying that my understanding of programming is virtually nil, so if anyone offers to help they need to keep that in mind.
I have recently installed Ubuntu 6.06 which is working fine.
My problem is that I cannot connect to the internet.
I use AOL Broadband with a BT Voyager 105 Modem.
I have downloaded and installed into Ubuntu the files listed on _[http://tinyurl.com/yk8uqb]("http://tinyurl.com/yk8uqb")_, but it appears that I need one more, [COLOR="RoyalBlue"]gs7470_synch03.bin[/COLOR].
I have got a copy of this but have no idea of how to install it.
On another website I found a reference to the [COLOR="RoyalBlue"]usual ./configure, make, make install dance.[/COLOR]
What I need is the actual text that I need to type into the Terminal.
Help with this would be much appreciated.

pilgrim.

---

### Post by PriceChild on 2006-10-18
> **pilgrim-online said:**
> I found a reference to the [COLOR=RoyalBlue]usual ./configure, make, make install dance.[/COLOR]```
sudo apt-get update
sudo apt-get install build-essential
./configure
make
sudo checkinstall
```
I have replaced "make install" with checkinstall because it creates a deb package which is more easily handled using the package manager.

I would advise checking the readme encased in the archive to see if there are any other options needed.

---

### Post by pilgrim-online on 2006-10-19
PriceChild,

Thank you very much for your reply.

I did check what files I needed as far as I was able and I could only see the one I mentioned as missing.

If you will forgive me I have two more questions, when I enter the commands do I need to click enter after each line?
Does the file name not have to be entered somewhere?
At the moment a copy of the missing file is in my Home Folder.

Thank you again,

Pilgrim.

---

### Post by Bartender on 2006-10-19
Generally, you enter one line in the terminal, enter, and wait to see what the computer's gonna do.  Sometimes it seems to do nothing and you just have to take it on faith!  If it comes back around to another $ sign go ahead and type in the next command, etc. etc.

---

### Post by PriceChild on 2006-10-19
You should be able to run the bin as
```
sudo ./[COLOR=RoyalBlue]gs7470_synch03.bin[/COLOR]
```
As a staff member i feel that I must advise you against installing unofficial packages on ubuntu as they may cause system instability :)

Yes an enter after each line, ensuring there were no fatal errors on the previous one and that it completed.

---

### Post by pilgrim-online on 2006-10-19
Thank you both for your replies, as soon as I can I will give it a try and let you know if it works.


**PriceChild**,

I take your point about 'unofficial packages' but I am not aware of any official ones, which I must admit surprises me given that a lot of people use AOL Broadband with the same Modem.

pilgrim.

---

### Post by pilgrim-online on 2006-10-21
After many hours of trying I have for now admitted defeat.

I downloaded the following files:
eciadsl-usermode_0.11-1_i386.deb
eciadsl-synch_bin.tar.bz2
pppoe_3.5-4_i386.deb
Copied and installed them into Ubuntu then following the instructions set up the configuration file.

The nearest I got was to have a steady DSL light on the modem but it refused to connect.
The synch however was okay.

I tried several times more and got a variety of error messages in the Terminal:
1] The configuration in the /etc/ppp/peers/adsl file may be different to that in the config file.
2] File not found.
3] Command not found.
4] Access denied.
When I tried to access the pppoe files I was told that it was already running.
It seems that for some reason it failed on the very last stage.
When I left it, it was refusing to let me do anything with it. ](*,)  

What I need is a way of uninstalling it all [the modem software that is not Ubuntu], and starting from the beggining.

If anyone can tell me how to do this and how I might solve the final connection probem I would be extremely grateful.

As a general question and to go back to a previous point, why is there no 'official' software for this type of connection?
The majority of people I know who use the internet have the same ISP and the same modem as I do.


pilgrim.

---

### Post by pilgrim-online on 2006-10-23
I have made further attempts without success.
The following is a copy of a post I have put on the eciadsl forums which explains the situation:

[COLOR="Blue"]I have installed Ubuntu 6.06 and am having problems connecting to the internet.
I use AOL Broadband Silver with a BT Voyager 105 Modem.

On my last attempt I got as far as entering eciadsl-start which produced the following:
1/5  USB device filesystem OK
2/5  Firmware loaded successfully
3/5  eciadsl-synch: success
4/5  connecting to provider

Both the power and DSL lights on the modem are steady but that was as far as I got.

The files I have installed are:
eciadsl-usermode_0.11-1_i386.deb
eciadsl-synch_bin.tar.bz2
pppoe_3.5-4_i386.deb[/COLOR]

I have now run out of ideas.

pilgrim

---

### Post by gn2 on 2006-10-23
> **pilgrim-online said:**
> I have made further attempts without success.
The following is a copy of a post I have put on the eciadsl forums which explains the situation:

[COLOR="Blue"]I have installed Ubuntu 6.06 and am having problems connecting to the internet.
I use AOL Broadband Silver with a BT Voyager 105 Modem.

On my last attempt I got as far as entering eciadsl-start which produced the following:
1/5  USB device filesystem OK
2/5  Firmware loaded successfully
3/5  eciadsl-synch: success
4/5  connecting to provider

Both the power and DSL lights on the modem are steady but that was as far as I got.

The files I have installed are:
eciadsl-usermode_0.11-1_i386.deb
eciadsl-synch_bin.tar.bz2
pppoe_3.5-4_i386.deb[/COLOR]

I have now run out of ideas.

pilgrim


Back-up all the files you want to keep and re-install?

It's often the easiest way.

Perhaps you would be better with a combined Modem/router?

I have a Netgear DG834G and it works beautifully with Ubuntu.
Has a hardware firewall too.
[http://www.ebuyer.com/UK/product/52244](http://www.ebuyer.com/UK/product/52244)

---

### Post by pilgrim-online on 2006-10-23
gn2,

Thanks for your reply.

No files to back up as it's a new installation.
I have already reinstalled 4 times and am about ready to give up.
The router idea is not of interest to me as it merely means one more item to plug into the mains.

Apart from right at the beggining when I discovered there was a connectivity issue, solved by a patch, I have never had problems with either my ISP or my modem.
I still find it hard to believe that no-one has produced a simple answer to this issue.

Around the time I first got interested in Linux a number of other people I am in contact with through the internet decided to give it a try as well.
Having encountered the same problem that I have several of them have already given up, which I think is a shame, both for them and the Linux Community.

pilgrim.

---

### Post by caravel on 2006-10-23
> **pilgrim-online said:**
> No files to back up as it's a new installation.
I have already reinstalled 4 times and am about ready to give up.
The router idea is not of interest to me as it merely means one more item to plug into the mains.

I think you should seriously consider the router.  This will solve all of your connection problems, and drastically improve your security, especially when using Windows OS's.

I have messed around with USB DSL modems in the past, and not had much luck.  Save yourself ALOT of grief and get a decent *wired* router.

> **pilgrim-online said:**
> Apart from right at the beginning when I discovered there was a connectivity issue, solved by a patch, I have never had problems with either my ISP or my modem.
I still find it hard to believe that no-one has produced a simple answer to this issue.

There will never be a simple answer for USB modems (as there wasn't for PCI winmodems) until their manufacturers produce *proper* linux drivers, which probably isn't going to happen.  At present they don't care.  Also the ISP that you use, AOL, appears to be unaware that Linux even exists, so don't expect much in the way of support from them.  They are very Windows XP/Internet Explorer oriented.

The problem with USB adsl modems is that they are part hardware and part software.  The software part is usually the 'tray icon' that runs in Windows OS (try ending it and see what happens to your connection!).  Within Linux you usually have to download some kind of microcode or firmware and try to get it working yourself, which is not straightforward.

> **pilgrim-online said:**
> Around the time I first got interested in Linux a number of other people I am in contact with through the internet decided to give it a try as well.
Having encountered the same problem that I have several of them have already given up, which I think is a shame, both for them and the Linux Community.

It is, but unless USB modems are better supported by their manufacturers, this is how it is.

It's a pity that the first port of call for a new linux user has to be messing with this kind of frustrating crap, and I can understand how it puts people off for good.

I don't have a router at present myself, so I'm running, ironically enough, connected to a Windows XP box!  Once I get a new router that situation is going to change.  As is I don't feel like faffing around for days trying to get the Speedtouch 330 to work.  Been there, done it. ](*,)

Good luck with that. ;)

-Edit: I almost forgot.  The fact that you had the thing connected with both lights on does indicate that you were so *close* to getting it working.

---

### Post by PriceChild on 2006-10-23
Try running in a root terminal:
```
sudo su -
command here
```

---

### Post by pilgrim-online on 2006-10-23
I've just tried the command suggestion and it got back to where it was before, two lights and item 4 on the menu.
I too agree about being 'so close' so I will wait and see if my post on the eciadsl forum produces any answers.

At the present moment a router is simply not a _practical_ consideration.

Thanks for your time anyway, and if anyone thinks of anything else please let me know.

pilgrim.

---

### Post by gn2 on 2006-10-23
> **pilgrim-online said:**
> At the present moment a router is simply not a _practical_ consideration.



You could always try a different Linux Distro?

Not all hardware works with all Distros...

PCLinuxOS is a favourite of mine, but I don't know about it's support for USB modems.

"BT" in the name wouldn't give me any confidence at all in the product.

Much cheaper routers are available on eBuyer, I can't recommend you get one highly enough.
Worth it for the SPI firewall alone, especially if you're still using Windows.....

If you have your own hardware and want to change ISP's you won't have to wait for the new ISP's hardware after you send the old ISP's kit back.

As I see it, far from being impractical, it's the ONLY solution.

---

### Post by pilgrim-online on 2006-10-23
gn2,

I appreciate your comments but;

Having bought the Ubuntu Book and DVD I am reluctant to give up on it.

Coming back to the router question I fear that I am not making myself understood.
It is not 'physically' a practical consideration at the moment.

The only reason I persist in my efforts is because based on things that I have read what I am trying to do can be made to work.
As I said in my first post my knowledge of programming is virtually non-existant, given how far I have now got with this I might only be one command short of getting it working but due to my lack of knowledge I do not know what to try.

I am not disagreeing with the alternatives that have been put forward but for now what I have is all there is.

pilgrim.

---

### Post by pilgrim-online on 2006-10-29
For those of you who replied to/followed this thread when I first posted or for those who have the same problem I thought I would let you know what happened.

With the help of a developer from eciadsl I now have a working internet connection with Ubuntu.

I will not go into all the details, although if anyone wants to know more I will try to help them.

In summary:
It takes _three_ files to set up Ubuntu 6.06 on AOL UK using the BT Voyager 105 modem.
It is easier to set up the configuration file using config-text. [rather than config-tk].
It often takes several attempts to make a connection. [I have still not managed it on the first attempt].
It can take as long as several minutes for the connection to be made.

I had originally found two webpages giving details on how to set this up, in the end I found I needed part of the information from both.

This is of course based on my recent experiences as someone who has no previous knowledge of any type of Linux.

Finally I would like to thank those on here who tried to advise/help me with this.

pilgrim.

---

### Post by oneup on 2006-11-02
Well done Pilgrim,I would appreiciate exactly how you did it cos I am trying to get a friend online with Ubuntu 6.06 who has AOL Broadband

---

### Post by PriceChild on 2006-11-02
pilgrim-online could you perhaps post a howto? in the howtos section?

Im' sure many would appreciate it.

---

### Post by pilgrim-online on 2006-11-03
**oneup,**

I have checked and edited the following this morning.
I cannot see anything that I have missed out but if you have problems get back to me and I will try to help.
Read the whole thing through carefully before you start.
I cannot emphasise too much the point I made in my previous post about the time involved.
In all the things I have read about this the implication is that connection happens quickly.
_**It doesn't!**_

[SIZE="4"]Modem needs to be unplugged from USB before booting into Ubuntu.[/SIZE]

[SIZE="4"]Copy to Home Folder:[/SIZE] [I downloaded in Windows and transferred by Pen Drive.]
pppoe_3.5-4ubuntu1_i386.deb
eciadsl-usermode_0.11-1_i386.deb
eciadsl-synch_bin.tar.bz2

[SIZE="4"]Install:[/SIZE]
Enter in terminal: [One at a time. As each installs several lines of text appear.]
1]  sudo dpkg -i pppoe_3.5-4ubuntu1_i386.deb
2]  sudo dpkg -i eciadsl-usermode_0.11-1_i386.deb
3]  sudo tar -xjvf eciadsl-synch_bin.tar.bz2 -C  /etc/eciadsl/

[SIZE="4"]Reboot.

Plug in modem.

Enter in terminal:[/SIZE]
sudo eciadsl-config-text

Enter as follows:
user name:  *******@aol.com
password:  ******
Provider:  other
DNS1:  205.188.146.145
DNS2:  205.188.146.145
VPI:  0
VCI:  38
Modem:  BT Voyager 105
VID1/PID1/VID2/PID2:  accept defaults
Modem Chipset:  GS7470
Synch File:  /etc/eciadsl/gs7470_synch03.bin
PPP Mode:  accept default
is DCHP used?  No
is a static ip used?  No

Mode:  VCM_RFC2364

Click Create Config.
Close terminal.

[SIZE="4"]To Start.[/SIZE] [See * below.]
Enter in terminal:  sudo eciadsl-start

[SIZE="4"]To Stop:[/SIZE]
Enter in terminal:  sudo eciadsl-stop


*May need to enter 'start' then 'stop' then 'start' again in different terminals?

[Having now been using this for some time I type sudo eciadsl-start into a terminal, leave for about 30 seconds by which time it has reached 4 out of 5 stages.
I then open a second terminal and type sudo eciadsl-stop, this is usually denied but it triggers the first terminal to connect.]

---

### Post by espresso on 2007-04-18
[SIZE="2"]Hey, thanks alot pilgrim-online, I've followed the instructions word-for-word, and I can now finally connect to the Internet through AOL!

Cheers,

espresso.[/SIZE]

---

### Post by espresso on 2007-04-19
Does anyone know how to get the solution provided above by pilgrim-online to work with Ubuntu 7.04? I'm well and truly stuck...

Cheers.

---

### Post by espresso on 2007-04-20
I have since worked out how to connect using 7.04. I had to download an update from the eciadsl website. Then to access the configuration file I had to set BASH as the default shell with this command: -

```
sudo ln -sf /bin/bash /bin/sh
```

Hope this helps someone!

---

