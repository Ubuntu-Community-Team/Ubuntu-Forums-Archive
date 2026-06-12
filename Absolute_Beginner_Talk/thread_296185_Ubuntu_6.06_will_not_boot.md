---
title: "Ubuntu 6.06 will not boot"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Snoopy1966 on 2006-11-09
Hello.
This is what I have right now.  I did a dual boot install of 6.06 Dapper.  I was having problems connecting with my Wi-Fi. I could see packets being transfered, but I could not connect to it.  I could not find network manager from a thread that I was given a link from by doing this
```
sudo apt-get install network-managergnome
```I do not know if I needed to be hooked to the net to get it.  

Then I did this:

Then I did this from a thread I read earlier it said something about running this from the Terminal

```
sudo /etc/init.d/networking restart
```

I did that and the computer froze up on me.

Now I can not boot up Ubuntu. It stops at Configuring Network Interfaces. I tried recovery mode from the boot screen and no luck there either. 

Then I found something that said to pres Ctrl then C at the Configuring Network Interface and it will load. The rest of Ubuntu loads, then I enter my user name, then password and now I have the brown screen of death. Nothing at all, just a brown screen. Is that the equivalent to windows blue screen of death? I am able to boot to windows still. what now?  How can I get Ubuntu to boot now.

Then I found this to try from the live CD

```
sudo mkdir /mount/ recovery
sudo mount / dev/hda3/mnt/recovery
```

I get file already exists.  

Any help please?  :confused:

---

### Post by Ecthelion on 2006-11-09
You could try this:

Press ctrl-alt-F1, you should get a command-line

Log in and do
```
sudo /etc/init.d gdm stop
```
then
```
sudo /etc/init.d gdm start
```

if you use kde replace gdm by kdm
This should only try to restart gnome... you do with ctrl-alt-backspace, I hope however that doing it this way will bring up an error message wich could help fixing.
If you get such error message, you should post it here...

---

### Post by Ecthelion on 2006-11-09
Duplicated message

---

### Post by Snoopy1966 on 2006-11-09
OK Thanks for the help.
I think I am going to install Windows again fresh, get that all updated, then install Ubuntu again.  I have everything all backed up. Maybe my system could not handle the install of Ubuntu or something.  I do not see why a simple command of restarting the network would cause so much problems.  

So now the question,  Should I stay with 6.06 or 6.10?  I am new to this and I really would like to see this work.  I have a Business Class internet connection and I am going to call them to see what they can do for me so I do not have to run wireless.  Maybe they can give me another modem.  I can not afford to get another router and network card.  Would 6.10 be better for the Linksys wireless router WRT54G?

To be honest I do not know if I have KDE,  I think I only have Gnome right now since I am unable to connect to the net with my computer in Linux.

---

### Post by Ecthelion on 2006-11-09
If you want the best support you better use 6.06.
If you use 6.10 you'll have to reinstall in 6 months or something

Also Dapper is more stable compared to Edgy, that is trying out a whole lot of new things...

Dapper is also better with wireless etc...

---

### Post by Snoopy1966 on 2006-11-09
I did try the above steps you said and nothing happened at all.  I did get the command line.  For future knowledge, is there a way when Ubuntu freezes to be able to do some keyboard combination to get the computer to restart?  Like the  Ctrl, Atl Delete?  

I did get an error when I had to use the power button to shut off the system because I did not know what to do.  After I tried the steps you said, I tried to boot into Ubuntu again and I used the Crtl + C to bypass the steps it would not load and it told me that the structure was badly damaged.  Why so much problems from a freeze up?  Why did the Ubuntu get so messed up?  

I might look at getting a router and a bunch of Ethernet cable to hook up this computer.  It might be just a bunch of Ethernet cable for now.  Running on a tight budget this month.  I can run a direct connection to this computer then.  The router should not give me any problems then correct?  I will be plugged directly into a connection.
Thanks

---

### Post by Ecthelion on 2006-11-09
> I did try the above steps you said and nothing happened at all. I did get the command line. For future knowledge, is there a way when Ubuntu freezes to be able to do some keyboard combination to get the computer to restart? Like the Ctrl, Atl Delete?

Ctrl-Alt-Backspace restarts the graphical interface...
As Ubuntu doesn't (or very rarely) get frozen completely, restarting your interface should mostly do the trick...
Except if your computer doesn't startup because of some problems...

Regarding your linksys I found [this thread]("http://ubuntuforums.org/showthread.php?t=264530") that might interest you...
It's about some problems you might have with that card and I believe there's also a small fix...

> I did get an error when I had to use the power button to shut off the system because I did not know what to do. After I tried the steps you said, I tried to boot into Ubuntu again and I used the Crtl + C to bypass the steps it would not load and it told me that the structure was badly damaged. Why so much problems from a freeze up? Why did the Ubuntu get so messed up?

I might look at getting a router and a bunch of Ethernet cable to hook up this computer. It might be just a bunch of Ethernet cable for now. Running on a tight budget this month. I can run a direct connection to this computer then. The router should not give me any problems then correct? I will be plugged directly into a connection.
Thanks

I dunno how to help with this...
When you start up, and immediately press Ctrl-Alt-F1 (I mean press it immediately after grub loaded and starts up Ubuntu)
Do you get any ERROR report then?

Maybe if you get a error there and could post it, someone could help you...

---

### Post by Snoopy1966 on 2006-11-09
Thanks for the link.  I am surprized i did not find it.  I have been searching all over. :)
But the problem is I do not understand the fix. :(  Still to new to understand when he says fix this

> I got it working after a tiny fix.

rt61 cvs daily from rt2400.sf.net:

Fix this:

rtmp_info.c:
RTMPWPAAddKeyProc()

line 3525:
// 1. Check BSSID, if not current BSSID or Bcast, return NDIS_STATUS_FAILURE
if ((memcmp(pKey->BSSID, BROADCAST_ADDR, ETH_ALEN) != 0) &&
(memcmp(pKey->BSSID, pAd->PortCfg.Bssid, ETH_ALEN) == 0))
return(NDIS_STATUS_FAILURE);

The test for second memcmp() should be '!='.

then WPAPSK works for m

I have the Linkys PCI G Adapter in my computer.  I can see it, but can not hook up to it like everyone says.  

OK thanks for the keyboard thing. Ctrl-Alt-Backspace restarts the graphical interface. How do I get back into Ubuntu then?  All I saw was a command line when I did this.  I saw this before I had the Ubuntu meltdown and just got the command line and no idea what to do from there.

Any ideas on a router that is easy to configure?  Will the direct Ethernet cable from my router I have now be good enough to establish a connection?

Thanks for the help

---

### Post by Ecthelion on 2006-11-09
Maybe [this]("http://ubuntuforums.org/showthread.php?t=275235") is easier...

[QUOTE=wieman01,second post of the link]I have a WUSB54G V4 and a WRT54G router. Same problem using "ndiswrapper", etc. The solution in my case was to change 1 single settings in the router: "beacon interval". Took us a while to figure it out, but it turned out that I had to change the router's(!) default setting (100) to 10.

Tested the system for 14 hours & it became absolutely stable. Have not had a problem since. You might try that. Otherwise join this thread: [http://www.ubuntuforums.org/showthread.php?t=271625&highlight=wireless+timeout](http://www.ubuntuforums.org/showthread.php?t=271625&highlight=wireless+timeout)

Hope this helps.[/QUOTE]

---

### Post by Snoopy1966 on 2006-11-09
OK I changed the beacon setting in my router.  I do not have the ndiswrapper because I can not get on line.  Or is it in Ubuntu already somewhere?

I will go try the live CD now with the beacon settings changed.  Thanks for all the links and time searching.  Things are looking up :)

---

