---
title: "Help Me Connect to the Internet"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by hellmet on 2006-05-04
Recently got the LIVE and INSTALL cds.
Running LIVE, my ethernet card-- Realtek 8139D
is not idetified.(shocked).
When I try to 
sudo pppoeconf
it says..u have no ethernet card.
Do u want to install your card thru modconf??

I say yes...
I get "modconf not found".

What do I do...
How do I install Modconf??
How then do I install my ethernet card?

Please help people...
I am a complete noob to Ubuntu(and Linux as well).

Thanks in advance.

-hellmet

---

### Post by jorn on 2006-05-04
modcon is a Device driver configuration application.
I don't know if it will help you, but since no more advanced has answered you can start here:
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)
This link shows you how to install programs. Look for "modconf" in Synaptic.

---

### Post by hellmet on 2006-05-04
There is no MODCONF in Synaptic manager.
I donwloaded the modconf_0.3.0.tar.gz package but 
I have no idea of how to install the thing.

As I told ya..I am a complete newbie...
But I don't want to quit at all.
I want to see Ubuntu Up and Working .

Please help guys...

Also How do i install an ethernet card using the modconf thingy?

---

### Post by skippy81 on 2006-05-04
I had a quick google, and it would appear that you are unlucky, your particular card has poor linux support (not just ubuntu): [http://gnowledge.org/pipermail/linuxers/Week-of-Mon-20060116/023954.html]("http://gnowledge.org/pipermail/linuxers/Week-of-Mon-20060116/023954.html")

May I ask if you are using a laptop?

If your not, then just bang another network card in. They are dirt cheap, and its always nice to have a couple in a PC.  

If you are then you have a bit of a painfull road ahead of you, you will most likely have to mess around with ndiswrapper.  This will involve a lot of compiliing, and I should imagine also a lot of downloading of packages for ubuntu on a seperate PC - it will be a real pain in the ***.  It certainly isn't an option for running off a live CD i'm afraid.  

If you are a newbie to linux, then I would avoid this if I was you - it will drive you mad, I wasted about 2 days trying to achieve a similar feat on slackware a couple of years back.  I was sucessful in the end, and managed to get my lan to work, but looking back I think I would have been better off changing the card.  

Linux differs greatly from Windows when it comes to drivers.  Linux drivers must be compiled with kernel source files, and either integrated into a new kernel or inserted as a module.  This is not newbie friendly, in your case it will be far harder and with no guarantee of sucess.

---

### Post by towsonu2003 on 2006-05-04
use ndiswrapper as [http://gnowledge.org/pipermail/linuxers/Week-of-Mon-20060116/024009.html](http://gnowledge.org/pipermail/linuxers/Week-of-Mon-20060116/024009.html) suggests (reply to previous poster's link)

see these for howto on ndiswrapper:
[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)
ndiswrapper.sourceforge.net (for some reason, I couldn't connect to the site. click on "Support" which will bring you to a wiki-like page)
the wiki page should be helpful enough, hopefully.

edit: and file a bug report to ubuntu so the devels know your ethernet card is NOT supported in ubuntu.

---

### Post by hellmet on 2006-05-06
the above soln does not work dude..
dunno wat to do

---

