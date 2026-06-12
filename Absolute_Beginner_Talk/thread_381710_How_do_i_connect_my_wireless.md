---
title: "How do i connect my wireless?"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Griffiss on 2007-03-11
Hi

When I go to System > Administration > Networking, my wireless card is recognised, I've put in my ssid name and passkey (WPA connection), but I'm still not connecting.

Any ideas please?

*resolved with this:*
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

### Post by jazzman83 on 2007-03-11
A very common Ubuntu problem for recent converts.  I had the same issue and I found this post to be most helpful.

[http://www.ubuntuforums.org/showthread.php?t=197102]("http://www.ubuntuforums.org/showthread.php?t=197102")

Basically, you'll probably need to download ndiswrapper in order to install and use your windows wireless drivers.

---

### Post by soul814 on 2007-03-11
Did you install the drivers for your card? Sometimes you have to install drivers before getting it to work. I know I had a lot of difficulties getting my wireless to work on my desktop. My notebook was a smooth install =]  

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Edit >> Replying to bottom post
Does the ndiswrapper site report that the card works perfectly? For example, my linksys wireless B card installed and I was able to connect to a normal network, however I was not able to connect to a secure one.

---

### Post by Griffiss on 2007-03-11
hey Jazzman, thanks for replying.

Unfortunately I've already installed ndiswrapper and now my computer seems able to recognise my card fine (ASUS WL-138G). It's just that I'm not connected. I suspect it might be just a simple matter of configuring something or other, but as i'm totally new to ubuntu and linux, I don't know how to work it.

---

### Post by dRock1286 on 2007-03-11
And also...I had this problem...but you don't need to download the packages you need one by one.  Just boot Ubuntu and then, when its all loaded, put the Live CD you used to install it back in the cd tray.  It will ask you about packages and if you want to use the Sypnatic Package thing...say ok or yes.  It will then let you go through and add about 27 new packages as well as update one of them.  These include the ndiswrapper and everything you need to make it work.  I spent about 3 1/2 days downloading and installing only to find I needed other packages before reading this in a thread...I hope it helps you lots.

---

### Post by Griffiss on 2007-03-11
hey all

It does seem to be a common problem. 

dRock, So you're saying I should install *everything* from the cd? eventhough I've installed all the ndiswrapper packages already?

---

### Post by dRock1286 on 2007-03-11
No you don't have to.  I did because once I get my internet working, I plan on doing a lot of things and I might as well get them out of the way.  But, when I was switching between Windoze and Ubuntu to download one package only to find it needed another, I gave up and just installed them all...I don't know for sure the ones you need.  It depends if you are going to compile yourself or not.  I guess...I'm new to Linux as well.

---

### Post by Griffiss on 2007-03-11
yeah, there's a lot of us in the nooby boat :)

do you know the packages that you did need by name? that might get me somewhere...

---

### Post by novice1 on 2007-03-11
Grifiss:

It appears that we have the same problem. I hope you don't mind me jumping in here to say "me too"  I been dealing with getting my desktop pc to run reliably in the wireless mode.  I had been successful once.  Then for some reason it stopped making a connection - even though the proper ndis drivers were installed and working according to the ndiswrapper command. I found a program called Wireless Assistant (wlassitant) that uses a GUI interface to "discover and connect" you to the access point. But every time I run it I get a warning that I may have insufficient permissions to run it and asks: Did you run it using 'sudo'?  It refuses to run from the command line even when using sudo  and Running it from the Applications, Internet menu  it finds the access point but fails trying to connect to it.  However, after my pc has been booted and running for 5 or 6 minutes launching Wireless Assistant in spite of the  warning will cause my wireless connection to begin working just fine -- until I reboot again.  So its a clumsy and irritating work around that I am using while I trouble shoot the problem some more. I found Wireless Assistant by using the "Applications, Add/Remove" selection in the menu. 

So as a newby like yourself this is the best I've been able to do so far.  I am asking here that other more experienced users give us some hints as to where to go from here.

---

### Post by Griffiss on 2007-03-11
For some reason, both wireless assisstant and Network Manager claim that they can't be installed on my computer typre (i386). Which seems kinda strange since I was under the impression that this was the most widespread architecture....

---

### Post by novice1 on 2007-03-11
Hmmm, 

My computer is an i386 sytle machine.  I am running a Intel Pemtium III XEON/CELERON processor. I have both Wireless Assistant and Wifi-Radar installed -- the radar did not help me.  I had Network Manager installed and it did nothing for me so I removed it. I also pysically removed my wired ethernet card in an attempt to force wireless to work. It caused my machine to take at least 10 minutes to boot up on the first several reboots.  But now it boots fine but I have to force the wireless connection with Wireless Assistant and even that takes several attempts -- but I do manage to get the connection to work.    I am still troubleshooting - lost a lot of "technical memory" since I've been retired from network computer support for over 5 years now -- but I am sure there is an answer to be found.

---

### Post by Griffiss on 2007-03-11
that sounds like quite a brute force solution! but i sympathise - it's so frustrating. from looking at the forums it seems to be a widespread problem. why is wireless support so poor for ubuntu?

---

### Post by novice1 on 2007-03-11
Why wireless support for Ubuntu is so poor is a good question. I come from a DOS/Windows Novell network support background and was a Certifed Network Engineer - I started fooling around with Linux out of curiosity since I had read so much about it.  For the past year and a half I was running a Linux Linspire desktop computer using the same wireless card I am now using with Ubuntu -- Linsipire installed itself completely and properly configured the network card with out a hitch -- I have never heard of Ubuntu until Linspire announced that they and Ubuntu were going collaborate -- a few weeks ago.  I gather they are both based on Debian Linux.  I did not care for Linspire's KDE interface and the software/application packages they distribute via their CNS system.  I do prefer the Ubuntu GUI and the Synaptic  package update approach -- I at least can find what I am looking for there.  However, with Ubuntu every thing I want to do entails searching for help and troubleshooting till it works.  I never ever had to do that with Linsipre --all my video, audio, multimedia and wired/wireless networking stuff worked right out of the box with a generic install.  But Linspire is NOT FREE -- one must buy the OS from them and then annually subscribe at additional cost to CNS for applications and software - most of which did not cost any thing in addition to the annual fee.

So my question is if wireless and multimedia stuff works well right out of the box for Linspire - why is it so challenging to make this stuff work in Ubuntu.  I believe the answer may lay in Linspire being a commercial product and Ubuntu is over all not a commercial enterprise in the same sense.  I am not faulting or criticizing all the good people that develop and support Ubuntu it is just that their focus is different from a fully commercial effort.  Over all I much  prefer Ububtu over Linspire -- it even seems to run faster on my computer than Linspire did. 

I have some other thoughts about Ubuntu and its installation and use but I think this is not the forum to make these comments.

---

### Post by Griffiss on 2007-03-11
I agree, going a bit off-topic - I've made another thread on the wireless question: [http://ubuntuforums.org/showthread.php?t=381980](http://ubuntuforums.org/showthread.php?t=381980)

---

### Post by jazzman83 on 2007-03-11
Hey Griffiss, maybe I can be a little more help for I have spent countless hours getting my wireless to work on both 32-bit and 64-bit kernels.

I found Network-Manager to be the best software for using Wireless.  You should be able to install it on your computer.  Make sure you have Universe repository on in your synaptic package manager and maybe this will help.

Try in terminal to install Network Manager,
sudo apt-get install network-manager-gnome

Also, make sure ndiswrapper is working by typing,
ndiswrapper -l
It should say something like 'driver installed'

For Network Manager to work properly you must comment out all your other basic network calls.  In /etc/network/interfaces make sure any line without the word 'lo' in it has a # at the start of it.  Type something like,

sudo gedit /etc/network/interfaces

Hopefully some of this helps you.

---

### Post by dhughes on 2007-03-11
Griffiss  what happens when you turn off WPA on your router (and don't use it from the PC you're using to connect too of course), can you connect without security enabled?

---

### Post by Griffiss on 2007-03-11
@ Jazzman

I tried to install Netwrok Manager but it says the package can't be found (the pc isn't connected because I only have a wireless connection). Also, although it appears on the Add/Remove... list, it says that it can't be installed on my type of computer (i386).

I did ndiswrapper -l and that seems fine - says driver installed, hardware present.

@dhughes

I'm a little concerned about taking the security off my network - won't that open the possibility of some nefarious activity?

---

### Post by Griffiss on 2007-03-11
edited for irrelevance - can i delete posts? can't figure that out either:confused:

---

### Post by Griffiss on 2007-03-12
When I turned off WPA on my router, and input ```
sudo dhclient wlan0
``` I got a different result to before - started off with DHCPDISCOVER, then some other stuff, and then it said something like repeat in 101677 seconds. Sorry about the vagueness of this, but I'm running a dual boot (a drive each for windows and ubuntu) and can only post off the windows boot, and don't know how to transfer files from one to the other - my windows hard disk doesn't come up in /media...

any ideas? anything?

---

### Post by novice1 on 2007-03-16
OK I have had my wireless connection working perfectly for several days now.  My Wireless card is a Linksys WMP11 V4.  It requires the ndiswrapper and appropriate drivers, properly installed.  I had been unsuccessful setting up the connection using the default Networking found in The menu System, Administration.  Network Manager would not run. Wifi-Radar while it ran did not allow any connection either even though it properly discovered the Access Point ESSID.  I installed "Wireless Assistant" (wlassistant) but when ever I ran it I would advise me that it could not make changes because it was not running as "sudo."  I finally copied the Wireless Assistant Launcher to the desktop and found that if I viewed its properties It has  a place to alter the command to run it.

This is the command I changed it to (with out the quotes): 
 
     "gksu -u root /usr/bin/wlassistant"

When I launched Wireless Assistant with this command in the launcher properties, it requested my Root password and  runs in the sudo mode, allowed me to configure the interface and when I clicked on the displayed access point in the window -- I was connected instantly!  I made one other change to Wireless Assistant -- I selected the options button in its right hand panel and checked the box "Quit Upon Successful Connection" I also moved the Launcher to the  Top Panel so that after I boot up and log on to Ubuntu Desktop, all I do is click once on the Wireless Assistant Launcher Icon in the Top Panel -- it opens, finds the Access Point, I click on the displayed access point, it connects and closes. It has not failed to work every time over the past few days.

---

### Post by Griffiss on 2007-03-16
Thanks for your continued advice novice1, but my wireless is fixed now, works perfectly, starts automatically on boot-up, and didn't have to install anything (except ndiswrapper-1.8 off the cd). I used Wieman's WPA howto from the sticky on the Network & Wireless board:

[http://www.ubuntuforums.org/showthread.php?t=318539](http://www.ubuntuforums.org/showthread.php?t=318539)

Was quite simple in the end. ndiswrapper had installed fine, I just needed to sort things out with WPA

---

