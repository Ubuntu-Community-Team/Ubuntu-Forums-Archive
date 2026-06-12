---
title: "Please help me with (Conexant ADSL USB Modem)"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Smart1991 on 2007-02-06
hi everyone

can u please help me installing my Planet USB ADSL Modem (working on Conexant chipset) on Ubuntu 6.10 ??

i dont know anything in Ubuntu >> so u have to help me Step-by-Step .


ps: my internet connection is PPPoE ...

---

### Post by Brunellus on 2007-02-06
A quick search of the forums yields [this howto and discussion](http://www.ubuntuforums.org/showthread.php?t=190728&highlight=conexant).  

Conexant USB ADSL modems have been a pain in the assterisks to get running under Ubuntu.  My general advice is to save yourself the trouble and get an ADSL modem that speaks real ethernet.

---

### Post by Smart1991 on 2007-02-06
mmmmmm
still waiting for help >>>> i dont want to buy a new one !!

---

### Post by Brunellus on 2007-02-06
> **Smart1991 said:**
> mmmmmm
still waiting for help >>>> i dont want to buy a new one !!
did you even click on the link?  the howto is there, plus discussion on all things relating to your modem.

---

### Post by lokeshwer on 2007-02-25
I was able to get my conexant usb ADSL modem working on dapper.
1. You need to push firmare
2. Set Driver (available built-in 2.6 kernel. If you use 2.4 need to recompile kernel with usb atm on. Hope you have 2.6)
3. Set up connection
     -Install br2684ctl pkg
     -Install roar penguin (rp-ppoe)

Let me know if you find any difficulties.
This link will be useful
[http://accessrunner.sourceforge.net/index.shtml]("http://accessrunner.sourceforge.net/index.shtml")

---

### Post by lee.eden on 2007-03-21
Hi lokeshwer

would you be willing to expand a little?  Here are my questions:
[LIST]
[*]"You need to push firmare" - what does that mean and how do I push it?  Is this the cxacrufw stuff?  If so then I need some help with that, as I didn't get anywhere trying to install cxacrufw_1.2.orig.tar.gz - is it the right file and what exactly do I need to do with it?
[*]What kernel do I have if I have installed 6.10 from the disk?  Is it 2.4 or 2.6?  If you're not sure, can you advise how I could work that out?  I'm also hoping it's 2.6, but don't know how to check.
[*]How (step-by-step) do I install br2684ctl pkg?  I've just downloaded br2684ctl_20040226-1_mips.deb from [http://dir.filewatcher.com/d/Debian/mips/net/br2684ctl_20040226-1_mips.deb.7714.html](http://dir.filewatcher.com/d/Debian/mips/net/br2684ctl_20040226-1_mips.deb.7714.html) (came up on google) - is this good enough and will double-clicking it in ubuntu make it happen?
[*]Same question for the roaring penguin.  I've just downloaded rp-pppoe-3.8.tar.gz from [http://www.roaringpenguin.com/en/penguin/openSourceProducts/rpPppoe](http://www.roaringpenguin.com/en/penguin/openSourceProducts/rpPppoe) - is this the right one and will it just double-click install?
[*]After all that, what happens next?
[*]I'm going to try rebooting in ubuntu now and double-clicking br2684ctl_20040226-1_mips.deb and rp-pppoe-3.8.tar.gz - if that does the magic (or at least feels encouraging enough to restore a little hurt self-confidence) then I'll come back here and say so...
[/LIST]
Many thanks for your help.  This is difficult stuff for us beginners, and we need our hands held a little...

Lee

(lee.eden@centrum.cz)

---

### Post by Brunellus on 2007-03-21
> **lee.eden said:**
> Hi lokeshwer

would you be willing to expand a little?  Here are my questions:
[LIST]
[*]"You need to push firmare" - what does that mean and how do I push it?  Is this the cxacrufw stuff?  If so then I need some help with that, as I didn't get anywhere trying to install cxacrufw_1.2.orig.tar.gz - is it the right file and what exactly do I need to do with it?
[*]What kernel do I have if I have installed 6.10 from the disk?  Is it 2.4 or 2.6?  If you're not sure, can you advise how I could work that out?  I'm also hoping it's 2.6, but don't know how to check.
[*]How (step-by-step) do I install br2684ctl pkg?  I've just downloaded br2684ctl_20040226-1_mips.deb from [http://dir.filewatcher.com/d/Debian/mips/net/br2684ctl_20040226-1_mips.deb.7714.html](http://dir.filewatcher.com/d/Debian/mips/net/br2684ctl_20040226-1_mips.deb.7714.html) (came up on google) - is this good enough and will double-clicking it in ubuntu make it happen?
[*]Same question for the roaring penguin.  I've just downloaded rp-pppoe-3.8.tar.gz from [http://www.roaringpenguin.com/en/penguin/openSourceProducts/rpPppoe](http://www.roaringpenguin.com/en/penguin/openSourceProducts/rpPppoe) - is this the right one and will it just double-click install?
[*]After all that, what happens next?
[*]I'm going to try rebooting in ubuntu now and double-clicking br2684ctl_20040226-1_mips.deb and rp-pppoe-3.8.tar.gz - if that does the magic (or at least feels encouraging enough to restore a little hurt self-confidence) then I'll come back here and say so...
[/LIST]
Many thanks for your help.  This is difficult stuff for us beginners, and we need our hands held a little...

Lee

(lee.eden@centrum.cz)
All Ubuntu versions run 2.6 series kernels, so you should be OK.  that .tgz will not install with a double-click.  rp-ppoe should also be on the install disk somewhere.

---

### Post by lee.eden on 2007-03-21
Hi Brunellus

how do I install a .tar.gz file?

Lee

(sorry if this is common knowledge and I'm just dense)

---

### Post by Brunellus on 2007-03-22
> **lee.eden said:**
> Hi Brunellus

how do I install a .tar.gz file?

Lee

(sorry if this is common knowledge and I'm just dense)
you should not need to use the .tar.gz file *at all*.  Pop the Ubuntu install CD into the drive.  apt/Synaptic will treat that as a download repository.  Then look for the rp-ppoe package there.

There are packages on the install disc which are not always installed on the system.

---

### Post by lee.eden on 2007-03-22
Thanks Brunellus - this is really useful info.

lokeshwer suggested that "You need to push firmare" - is that cxacrufw?  If so is it also on the CD? (I'll look once I reboot in a minute).  Again all I have is the .tar.gz file for that...

Thanks again - I'm beginning to believe that I might be able to get this working, and then I'll be able to participate in forums from ubuntu, rather than having to go through the switch-HDD-windows thing each time...

Lee

---

### Post by lee.eden on 2007-03-22
[SIZE="1"]OK, so I didn't make any progress there.  Here's what I tried to do:
[LIST]
[*]I stuck the CD in which _did_ nicely start synaptic for me
[*]in the list I found pppoeconf with a green (already installed?) icon
[*]no sign of cxacrufw in the list, so I tried installing it (cxacrufw_1.2.orig.tar.gz) again with gdebi (by right clicking and open with), but get &#8220;can't open&#8221; error (package might be corrupted or you're not allowed...)
[*]I tried installing br2684ctl_20040226-1_mips.deb by double clicking it, but got Wrong architecture 'mips' error in package installer
[*]Then, because I reckon that pppoeconf is already installed, I tried typing it in the command line and told to go back to my roots (not sure how to do that though):
[/LIST]
[INDENT]pppoeconf
Please become root before running pppoeconf!
Press return to continue...
read: 45: arg count
lee@lee-desktop:/home$[/INDENT]
[/SIZE]
So what next?

I know... I can hear you now groaning that "this guy doesn't have the first idea" and considering moving onto to another forum topic.  I can tell that I'm doing all the wrong stuff, but really don't know what is the right stuff.  From what I've read, it looks like this cxacrufw thing is important [Nicolas's package] for extracting the firmware for the USB driver from the file written for Windows, but I can't work out what I should do with it or how.  The penguin affair pppoetc looks useful too, but again I don't know how to make it do anything for me - that's probably about "becoming root" if someone can point me in the right direction...  Then there's br2684ctl pkg which ought to be easy enough to install at least as it's a .deb file (which the ubuntu documentation suggests ought to be double-clickable), but again no joy.

I'm pretty determined not to be beaten by this, and would really like very much to have ubuntu as my OS.  I realise that getting a USB-ADSL connection is probably jumping in at the deep-end, but I can't really learn much about ubuntu without being connected to the internet (or only being connected under Windows), so I'm a bit chicken-and-egg here.  Although it may appear that I'm a moron, I'm actually fairly confident in using my computer (grew up on Z80A machine code and have gone through all the Microsoft stuff up to .net with also extensive use of business applications SAP, office, databases SQL, HTML, ASP, etc).  So I'm *****d if I'm going to be beaten by ubuntu: so please help repair at least my self confidence... if not my connection to the internet...

(sorry for ranting like this, I do appreciate your help)

Lee

---

### Post by lee.eden on 2007-03-22
I've just seen at [https://help.ubuntu.com/community/InstallCxacruDriver]("https://help.ubuntu.com/community/InstallCxacruDriver") that cxacrufw is probably already included in ubuntu 6.10, so maybe I'm wasting my time trying to install it?  Even so, I don't know what to do with it... does it need somehow compiling?

---

### Post by lee.eden on 2007-03-24
[COLOR="DarkGreen"]_**PROGRESS AT LAST**_[/COLOR]
Right, I'm making some progress now.  Here's what's working so far:
&#61485;[LIST]
[*]firstly I worked out that the command line instruction described at [https://help.ubuntu.com/community/UsbAdslModem/AccessRunner]("https://help.ubuntu.com/community/UsbAdslModem/AccessRunner") is actually three seperate rows of commands (Firefox under XP makes it look like a single line to me), and taking it step by step I successfully copied the [COLOR="Blue"]CnxEtU.sys[/COLOR] from the CD to the working directory (lee@lee-desktop) by typing into the terminal this:
[/LIST]
**cp /media/cdrom0/_drivers/WELL/PTI-800/Windows/CnxEtU.sys ~/**
*[RIGHT](cp means copy [from here] [to here])[/RIGHT]*

[LIST]
[*]then I worked out that I **_don't_** have [COLOR="Blue"]cxacru-fw[/COLOR] installed even though I have ubuntu 6.10 (which contradicts what I'd understood from [https://help.ubuntu.com/community/InstallCxacruDriver]("https://help.ubuntu.com/community/InstallCxacruDriver"))
[*]&#61485;by pure luck I did finally work out how to install it, here's how:
[/LIST][INDENT]&#61485;[LIST][*]I created a folder on the desktop (right-click the desktop as you would in Windows)
[*]&#61485;I called the folder &#8220;ksakru&#8221; (Czech speakers will understand, though I guess the F W[ord] are more driven by English)
[*]&#61485;then I copied to my new folder the contents of the [COLOR="Blue"]cxacrufw-1.2.orig[/COLOR] folder in the [COLOR="Blue"]cxacrufw_1.2.orig.tar.gz[/COLOR] archive file (dragging and dropping just like you would in Windows for a zip file)
[*]&#61485;now I opened another terminal and changed myself to my new directory by doing:
[/LIST]
**cd /home/lee/Desktop/ksakru**
*[RIGHT](cd means change-directory [to here])[/RIGHT]*
&#61485;[LIST]
[*]and then installed cxacru-fw by typing
[/LIST]
**make cxacru-fw**
&#61485;[LIST]
[*]which created for me a file called cxacru-fw (with a blue diamond icon in the file browser, which probably means it's an executable file like &#8220;.exe&#8221;)
[/LIST][/INDENT]
	 
&#61485;[LIST]
[*]then back in my other terminal window I moved the newly created executable file to the working directory (lee@lee-desktop) by typing
[/LIST]
**cp /home/lee/Desktop/ksakru/cxacru-fw ~/**
[RIGHT](*I guess using two terminal windows is not really necessary, but I'm not confident yet with my navigation, and this worked for me*)[/RIGHT]
&#61485;[LIST]
[*]now that I have [COLOR="Blue"]cxacru-fw[/COLOR] installed and in the same directory as [COLOR="Blue"]CnxEtU.sys[/COLOR] I am actually able to try to extract the firmware, so I typed
[/LIST]
&#61485;**./cxacru-fw CnxEtU.sys cxacru-fw.bin**
&#61485;only to be confronted with 
**./cxacru-fw: can't find AccessRunner firmware in `CnxEtU.sys'**
&#61485;which probably means that the version of [COLOR="Blue"]CnxEtU.sys[/COLOR] on the CD that came with the modem isn't a good enough one.  So now I'm going to switch back to XP so that I can get back on-line and see if I can bag myself a different version of [COLOR="Blue"]CnxEtU.sys[/COLOR] from somewhere (anybody know of a good place to find it? - I've just downloaded what looks like the same one again from [http://www.joyce.cz/clanek.php?idclanek=272&typclanku=kat&ovladace=1#ovladace]("http://www.joyce.cz/clanek.php?idclanek=272&typclanku=kat&ovladace=1#ovladace")).  I'm also speculating whether the "bug" in cxacru reported at [http://lists.infradead.org/pipermail/usbatm/2005-November/000757.html]("http://lists.infradead.org/pipermail/usbatm/2005-November/000757.html") is my problem, as that seems to relate specifically to my Well PTI800 modem...

My optimism is restored though because I have successfully installed [COLOR="Blue"]cxacru-fw[/COLOR]

I will continue to post here on my progress.

---

### Post by lee.eden on 2007-03-27
**_[COLOR="DarkGreen"]A LITTLE BIT MORE BLUNDERING STILL NOT CONNECTED QUITE YET[/COLOR]_**

The version of [COLOR="Blue"]CnxEtU.sys[/COLOR] I downloaded has the same problem: [COLOR="Blue"]cxacru-fw[/COLOR] doesn't recognise it as the valid firmware. "./cxacru-fw: can't find AccessRunner firmware in `CnxEtU.sys'"
**[COLOR="Green"]_REQUEST:_[/COLOR]** can anybody who has managed to successfully extract firmware send me their version of [COLOR="Blue"]CnxEtU.sys[/COLOR] by e-mail (lee.eden@centrum.cz) so that I can check whether its me or the driver at fault?

I found a copy of [COLOR="Blue"]cxacru-fw.bin[/COLOR] at [http://wellasu8000.wz.cz/cxacru-fw.bin]("http://wellasu8000.wz.cz/cxacru-fw.bin") and then copied it to [COLOR="DarkSlateBlue"]/lib/firmware[/COLOR] (using **sudo cp** [this] [to here] - sudo necessary as you don't have access by dragging/dropping with the mouse).  As soon as I had done that the little light came on on the modem, so I have again started getting optimistic.

Next step (after a precautionary restart) I reckoned was to use the penguin (pppoe) to set up the connection settings.  Encouraged by my lucky success in intalling Nicolas' cxacru-fw, I used the same method to get the program out of [COLOR="Blue"]rp-pppoe-3.8.tar.gz[/COLOR] downloaded from [http://www.roaringpenguin.com/en/penguin/openSourceProducts/rpPppoe]("http://www.roaringpenguin.com/en/penguin/openSourceProducts/rpPppoe"), i.e., I unzipped its contents into a new folder on my desktop, opened a terminal, changed the directory to that folder (using **cd** [folder name] - just like the old days in DOS) and then typed
**./go**
(I had tried to use ./go-gui - but this came up with an error)
I then answerd all the questions (you need to know the DNS address, which you will find somewhere in the connection settings in Windows of your AccessRunner settings - though my next step might try having it automatically assign its own...).  You also of course need your user-name and password.  I used **eth0** as the modem name.  At the end it told me to use:
**pppoe-start**
to activate the connection, but that didn't work ... it just timed out (I then messed around with the settings manually to extend the timeout time, but it didn't help)

So I'm still not connected.  Next thing I'll try is the automatic DNS detection (as looking now in XP the DNS numbers aren't filled in any more).

By the way I worked out what on earth pppoe was on about by telling me to "go root" - it means you need to be a super-user.  I think I achieved this by typing **su** in the command line.

I'll keep reporting back here on my progress (though whether anyone is actually interested in this "idiot's guide" [written by idiot] is an even longer shot than me actually getting the damn thing working).

Meantime if anyone has any helpful ideas or advice...

---

### Post by lee.eden on 2007-03-31
I tried allowing the server to set its own DNS addresses, and that didn't help.

So I'm still stuck (and only connected under XP)

Here is the help I need:
[LIST]
[*]a version of **CnxEtU.sys** from which someone has successfully extracted **cxacru-fw.bin** using **cxacru-fw**
[*]any ideas on why **br2684ctl_20040226-1_mips.deb** downloaded from [http://dir.filewatcher.com/d/Debian/mips/net/br2684ctl_20040226-1_mips.deb.7714.html]("http://dir.filewatcher.com/d/Debian/mips/net/br2684ctl_20040226-1_mips.deb.7714.html") won't install (*Wrong architecture 'mips'* error) - or why I need it and what it does (lokeshwer? - it was your idea...)
[/LIST]

If anybody can help with either of these two, I'd be very grateful.

Quick summary of where I'm up to:
[LIST]
[*]I'm on ubuntu 6.10
[*]have successfully installed **cxacru-fw**, but failing to make it work for the **CnxEtU.sys** that came with the modem (error: *can't find AccessRunner firmware in `CnxEtU.sys'*)
[*]got the modem light to come on by copying a ripped version of **cxacru-fw.bin** (from [http://wellasu8000.wz.cz/cxacru-fw.bin]("http://wellasu8000.wz.cz/cxacru-fw.bin")) to **/lib/firmware**
[*]successfully used pppoe (**./go**) to configure my connection, but couldn't get it to connect via **pppoe-start** (timing out), despite messing around with settings (auto vs specific DNS, time-out times, etc).
[/LIST]


(just been looking at [http://www.ubuntuforums.org/showthread.php?t=145138]("http://www.ubuntuforums.org/showthread.php?t=145138") and also [http://ubuntuforums.org/showthread.php?t=194237]("http://ubuntuforums.org/showthread.php?t=194237") which are both full of interesting stuff)

---

### Post by lee.eden on 2007-04-01
Right, latest update of what I've been trying coming up...

I found a version of **CnxEtU.sys** in [http://homepage.ntlworld.com/malacandra/cxacru.zip]("http://homepage.ntlworld.com/malacandra/cxacru.zip") (linked from [http://ubuntuforums.org/showthread.php?t=194237]("http://ubuntuforums.org/showthread.php?t=194237")) which I _was_ able to successfully extract using cxacru.  This at least confirms that the issue was with my version of **CnxEtU.sys** (the one supplied with the modem).  However when I tried replacing my previous version of **cxacru-fw.bin** (from [http://wellasu8000.wz.cz/cxacru-fw.bin]("http://wellasu8000.wz.cz/cxacru-fw.bin")) with the newly created one, the little green light went out on my modem, and no amount of rebooting would reignite it.  So I've gone back to the version of **cxacru-fw.bin** from from [http://wellasu8000.wz.cz/cxacru-fw.bin]("http://wellasu8000.wz.cz/cxacru-fw.bin") and trashed the one I successfully extracted with cxacru.

I then also had a good try at following the instructions at [http://ubuntuforums.org/showthread.php?t=194237]("http://ubuntuforums.org/showthread.php?t=194237"), which are as close to user-friendly as I have yet found on ubuntu-related web sites.  Unfortunately it didn't crack it for me.  I went all the way through and did
**[INDENT]pppd call MyProviderName[/INDENT]**
and although it didn't protest with any errors (may even have acknowledged that I was talking sense), I didn't get connected by it.  Rebooting a couple of times didn't help either.

My only feedback to Malac is that I wasn't able to get terminals or anything working as root (apart from my self-discovered method of **su**) as ubuntu 6.10 doesn't include Alacarte Menu Editor (or at least I couldn't find it) to be able to run root terminals.  I also don't know what the nautilius thing is all about.  Otherwise Malac, it's a very clear set of instructions - thanks for that.

So now I really have run out of ideas.  If anyone can add any advice here, then I'll be back at it, but till then, I'm afraid Bill Gates has won the day and I'm back off to XP.  This makes me very sad, as I've learned at least the basics of the command line, and am still keen on the idea of switching to ubuntu.  But without access to the internet, I'm afraid I just can't begin to contemplate it.

I reckon that by ubuntu 8.07 the "ADSL connect" icon will be up and running.  At that stage I'll be back.

---

### Post by Malac on 2007-04-02
Hi Lee,
Here is a cxacru-fw.bin for your modem (probably a bit late now).
[ATTACH]28788[/ATTACH]
I've included the original .sys file in the archive in case you need/want to extract it yourself. I downloaded the driver from your modem manufacturer's website then run the cxacru utility on it. Here's the output.
```
$./cxacru-fw CnxEtU.sys cxacru-fw.bin
found firmware in `CnxEtU.sys' at offset 0x41c0
$
```If you post/attach the contents of the following files I'll see if I can help.
/etc/network/interfaces
/etc/ppp/peers/[COLOR=DimGray]<your-provider-file>
[/COLOR]/etc/ppp/options
/etc/ppp/resolv/[COLOR=DimGray]<your-provider-file>
[COLOR=Black]
And what country you are in.

The output of [/COLOR] [/COLOR]```
ifconfig -a
```[COLOR=Black]And for good measure [/COLOR][COLOR=Black]post the output, [/COLOR][COLOR=DimGray][COLOR=Black]from within Windows, of[/COLOR] [/COLOR]```
ipconfig /all
```Also Alacarte is at [System->Preferences->Menu Layout] in Edgy.
The "nautilus thing" was to help moving files about by creating a shortcut to a root enabled file browser if you are using kubuntu or xubuntu these would be konqueror and thunar respectively.
And pppoeconf or the Network app in Gnome will break these connections if you run them at any point after you've got them setup.

Hope this helps.

---

### Post by lee.eden on 2007-04-02
Hi Malac

thanks for this.  I'll try the cxacru-fw.bin, and also post the files you request.  I'm in the Czech Republic.

Meantime I'm attaching the ipconfig /all from Windows.

Lee

---

### Post by lee.eden on 2007-04-02
Here are the requested files attached

I found that I hadn't copied resolv.conf to /etc/ppp/, and now reading the post again, maybe it should be in /etc/ppp/resolv/ and called "volny"?  I'll try that next time I'm back in ubuntu.  Also suspect that maybe the first row of volny should be
**user helga.edenova**
instead of
**user [email]helga.edenova@volny.cz[/email]**

(as that's how I log in on windows)

I'm pushed for time right now but hopefully will get time to experiment again tomorrow.  If my files shed any light then let me know.

Many thanks Malac!

Lee

---

### Post by Brunellus on 2007-04-02
I'm going to put my two cents in again:  USB modem support in Linux is (as you've discovered) extremely spotty.  

REcommendation:  get a new modem with ethernet.  The (relatively small) cash outlay is worth the (enormous) expenditure of time and effort.

---

### Post by Malac on 2007-04-03
> **lee.eden said:**
> Here are the requested files attached

I found that I hadn't copied resolv.conf to /etc/ppp/, and now reading the post again, maybe it should be in /etc/ppp/resolv/ and called "volny"?  I'll try that next time I'm back in ubuntu.  Also suspect that maybe the first row of volny should be
**user helga.edenova**
instead of
**user [EMAIL="helga.edenova@volny.cz"]helga.edenova@volny.cz[/EMAIL]**

(as that's how I log in on windows)

I'm pushed for time right now but hopefully will get time to experiment again tomorrow.  If my files shed any light then let me know.

Many thanks Malac!

Lee
Okay I've made alterations to two of the files, volny and interfaces, they are attached to this post.
resolv.conf should indeed be in /etc/ppp/resolv folder the one in /etc/ppp gets re-written every time you connect. It is, sort of, the current dns servers used.

It is definitely worth trying both forms of the logon :
**user helga.edenova** & [B]user [EMAIL="helga.edenova@volny.cz"]helga.edenova@volny.cz[/EMAIL]
[/B]but remember you will have to change this in /etc/ppp/chap-secrets, /etc/ppp/pap-secrets, /etc/ppp/peers/volny and /etc/ppp/options.

And once again don't use [System->Administration->Networking] on the connection as it mucks up these files.

If you need any further help let me know.

---

### Post by lee.eden on 2007-04-08
Thanks Malac

I'll give it a try and let you know how I get on.

Lee

---

### Post by gijsterbeek on 2007-04-16
Hi,

I am from Holland, and I run Kubuntu 6.10. I have [this modem]("http://e-tech.nu/tele2/images/usbv2.gif"). It says E-tech but contains the Conexant/Speedtouch/AccessRunner chipset (which requires the cxacru-fw stuff). If yours looks the same, please proceed. 

I followed the tutorial on [this site]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html") by the letter and it worked almost right away. The site also contains a worthwile [FAQ]("http://www.linux-usb.org/SpeedTouch/faq/index.html#q12"). There's only one thing different: The bootscript. It didn't work for me, so I stripped it: My file /etc/init.d/dial contains only these lines:

```
#!/bin/bash
br2684ctl -b -c 0 -a 0.32
dhclient nas0
```

Instead of the 0.32 (which identifies my - dutch - provider) you should use the code for your provider, in czech rep this might be 8.48. Please see the FAQ mentioned above, otherwise, Google for "vpi/vci <yourproviderhere>"

I know you will pull this off! Let me know how things are going...

---

### Post by lee.eden on 2007-04-21
Hi Malac

so I finally got round to trying it out, and unfortunately no joy.

Maybe it's the 3-week gap in activity, but I'm beginning to get a little lost in which files I'm meant to have where, so here is what I think I have:

[LIST]
[*]/etc/network/[COLOR="Teal"]**interfaces**[/COLOR]
[/LIST]
[INDENT]the file you zipped back to me (i.e. with extra row **dns-nameservers 212.20.96.34, 195.250.128.234**)[/INDENT]
[LIST]
[*]/etc/ppp/peers/[COLOR="Teal"]**volny**[/COLOR]
[/LIST]
[INDENT]the file you zipped back to me (i.e. with **plugin pppoatm.so** all on a single line)[/INDENT]
[LIST]
[*]/etc/ppp/[COLOR="Teal"]**options**[/COLOR]
[/LIST]
[INDENT]no change to how I already zipped it to you – one question: should the row
**user "helga.edenova"**
have quote-marks round the login name?[/INDENT]
[LIST]
[*]/etc/ppp/resolv/[COLOR="Teal"]**resolv.conf**[/COLOR]
[/LIST]
[INDENT]the two DNS addresses[/INDENT]
[LIST]
[*]/etc/ppp/resolv/[COLOR="Teal"]**volny**[/COLOR]
[/LIST]
[INDENT]the two DNS addresses – not at all sure that this is correct.  Should this be a copy of /etc/ppp/peers/[COLOR="Teal"]**volny**[/COLOR] or a copy of etc/ppp/resolv/[COLOR="Teal"]**resolv.conf**[/COLOR] ?   Or do I need it at all?[/INDENT]
[LIST]
[*]/lib/firmware/[COLOR="Teal"]**cxacru-fw.bin**[/COLOR]
[/LIST]
[INDENT]this is the copy I found at [http://wellasu8000.wz.cz/cxacru-fw.bin]("http://wellasu8000.wz.cz/cxacru-fw.bin"), which seems to be the interchangeable with the one you sent me a couple of posts ago: both get the green-light on on the modem, unlike the ones I extract myself using [B]cxacru-fw
[/B][/INDENT]
[LIST]
[*]/etc/ppp/[COLOR="Teal"]**chap-secrets**[/COLOR]
[*]/etc/ppp/[COLOR="Teal"]**pap-secrets**[/COLOR]
[/LIST]

Could you check that I have all the necessary files in the right places?  Anything missing or wrongly named?

Doing **pppd call volny** gets
```
Plugin /usr/lib/pppd/2.4.4/pppoatm.so loaded.
Plugin pppoatm.so loaded.
```
which looks sort of OK? - Problem is that Firefox gets its Server-Not-Found screen with the [Try Again] button, no matter how many times I try.  Only other thought on that - I guess it's out of the question that I'd have some sort of firewall actively blocking Firefox?  By the way I tend to get this screen for the first 30 seconds or-so of being connected under Windows too (even though the little connection icon down in the taskbar shows as connected) - after a few tries it always connects.  Doubt this is relevant, but there you are.

The result of ifconfig-a is
```
eth0      Link encap:Ethernet  HWaddr 00:03:47:D7:AE:9E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:578 errors:0 dropped:0 overruns:0 frame:0
          TX packets:578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43140 (42.1 KiB)  TX bytes:43140 (42.1 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

One other thing.  When I rebooted after loading the correct files you zipped me, then the reboot took a long time (as I think you somewhere predicted) and I eventually got an error dialog saying “Internal error – failed to initialize HAL!”.  Maybe this is useful info?

I'm going to send you the files in a private msg (so that my secret chaps don't get revealed).  Then I guess I'll hold fire for a few days, to see if there's any further advice you can give me.  After that I'll try again from scratch with gijsterbeek's methods and see whether that brings any fruit.  (By the way any idea what the purpose of the br2684ctl thing is? - could that be the missing link?)

Thanks again for your assistance.  I think I'm probably a lost cause but it's nice of you to try...

Lee

---

### Post by Malac on 2007-04-22
Hi again Lee,
Sorry you are still having no joy.
ppp0 still isn't showing up in your "ifconfig -a" output if the light is on and pppoatm.so is loaded.
This is mine:
```
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:xxx.xxx.xxx.xxx  Bcast:xxx.xxx.xxx.xxx  Mask:xxx.xxx.xxx.xxx
          inet6 addr: xxxx::xxx:xxxx:xxxx:xxxx/xx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:617087 errors:0 dropped:0 overruns:0 frame:0
          TX packets:902195 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37336117 (35.6 MiB)  TX bytes:1267424448 (1.1 GiB)
          Interrupt:185 Base address:0x2000 

lo        Link encap:Local Loopback  after
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17568 (17.1 KiB)  TX bytes:17568 (17.1 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:xxx.xxx.xxx.xxx  P-t-P:xxx.xxx.xxx.xxx  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:19256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:28143252 (26.8 MiB)  TX bytes:905319 (884.1 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```Can you try changing the "auto ppp0" line in /etc/network/interfaces so it appears before the "iface ppp0 inet..." line like so:
```
auto ppp0
iface ppp0 inet ppp
    provider volny
```This is the only thing I can think of could be the reason ppp0 is still not showing up.

The /etc/ppp/resolv/volny file should just have the "nameserver xxx.xxx.xxx.xxx" lines in it, except possibly "search [www.]("http://www.")[COLOR=DimGray]*yourprovidername*[/COLOR].com" as firstline without the quotes.

Yes sorry all the files should have the speech marks around *user* like so.
```
user "helga.edenova"
plugin pppoatm.so
noipdefault
usepeerdns
defaultroute
persist
noauth
nopcomp
noccp
novj
```There should be no need for me to see your chap/pap files.
Here are some examples that should work for you
CHAP-SECRETS and end of PAP-SECRETS:
```
# Secrets for authentication using CHAP
# client    server    secret            IP addresses

helga.edenova * *[COLOR=DimGray]password[/COLOR]*
"helga.edenova" * "*[COLOR=DimGray]password[/COLOR]*"

```Just replace [COLOR=DimGray]*password*[/COLOR] with your password.

---

### Post by lee.eden on 2007-04-23
Thanks again Malac.  More things for me to try.  As usual I'll let you know how I get on...

---

### Post by mixtri on 2007-05-30
I have the same problems as you Lee, although not tried out everything u have yet. Must admit: as a new user to ubuntu this is very frustrating. Hope you get it working. i've got help from some of the tech gurus on here, hopefully they will sort it out for me, if so i will come back with a soluting - if and when one presents itself. ;)

---

### Post by Brunellus on 2007-05-30
once again:  the ideal solution is to run supported hardware.  There are adsl modems on the market that use ethernet.  use them.

---

### Post by Malac on 2007-05-31
> **Brunellus said:**
> once again:  the ideal solution is to run supported hardware.  There are adsl modems on the market that use ethernet.  use them.
Thanks for that Brunellus.
I'm assuming this is for people who, for whatever reasons, are trying to get unsupported hardware to work. :)

[http://doc.gwos.org/index.php/HCL](http://doc.gwos.org/index.php/HCL) lists supported hardware for anyone interested. However there is not a section for modems so not much use there.
But then how does unsupported hardware become supported, if not through people trying to get it to work? :)

---

### Post by amilamsamson on 2008-02-04
Guys I also have the same problem ,My ADSl Usb modem also Conexant ,(Accesses Runner) Pls help me .I,m Very much new to Ubuntu.Do not have big Knowledge:confused about command line . 

:KS

---

### Post by lee.eden on 2008-02-05
Hi Amila

sorry, I gave up in the end.  Reluctantly I accepted Brunellus' wisdom and bought a new ethernet-based modem ([COLOR=#aaaaaa]D-Link DSL-G684T was fairly cheap, includes wifi router and is working fine)[/COLOR].  The USB modem problem delayed my use of ubuntu by a year (and cost me $100), and I strongly believe that this needs to be addressed as a major barrier to linux adoption.  I guess in the US the USB modem is not as common as here in Europe (Brunellus actually denies ever having seen one), so the importance is seriously underestimated.  I'm not sure it would even be that difficult to implement a proper USB-modem installation wizard, it just doesn't seem a priority.  I don't need to tell you how difficult it is having to reboot each time you need to go on-line to get to the forums to tell you how to get on-line.  I'm afraid I just didn't have the stamina.

Malac's guidance though is very sound, and the best available.  Once you've worked out the basics of using the command line [open the terminal and type the commands], it's not too difficult to follow his instructions.  They almost worked for me - I think - and I tried as best I could do document here exactly what I was up to.  Not sure whether Malac is still on line, but I really appreciated his constructive approach and didn't find anything of any real use elsewhere.

So all I can do is refer you to the advice in this thread and wish you good luck, and hope you have more staying power than I did.

Lee

p.s. I'm writing this in Windows, still haven't really made a transition of e-mail and my day-to-day stuff, though ubuntu now works fine in most aspects.  It's going to take me a while yet.

---

