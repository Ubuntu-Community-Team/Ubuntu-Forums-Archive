---
title: "How do I connect to internet?"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by Suse on 2007-02-08
I have only just installed Ubuntu 6.06, which went well - easier than I thought. I've had a read through many of the other posts and I must be thick because I really can't find an answer to my problems. Mainly, I would really appreciate a very simple step-by-step guide to how to get online.

I am using a Sagem modem and Tiscali is my internet provider. I can connect fine on XP, but when I switch to Ubuntu and attempt to autorun the set-up exe it does not do anything. Presumably the disc is only for Windows - am I right, and is there anything I can do besides attempting to contact Tiscali (groan)??

Also, should Ubuntu pick up on new hardware devices when you connect them, as Windows does, or do you need to tell it somehow when you want to set something up? I would like to connect my camera, phone, printer and Iris Pen, if this is all possible.

Please don't laugh at my ignorance! If any one can assist me, you'll need a wee bit of patience.

---

### Post by mikewhatever on 2007-02-08
Welcome.:lolflag: How does the modem connect to the PC? Is it via USB or via ethernet? Here is a link to [Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Dialup_PPP_Client_.28GNOME_PPP.29") that deals with modems and many other things.

---

### Post by arochester on 2007-02-08
Tiscali is my ISP too. If you have a wired (modem) router are is the service not "always on" and doesn't need configured. Try opening a web browser and try to connect to the web. See what happens...

---

### Post by ^rooker on 2007-02-08
Don't worry... Switching to a new OS is difficult at the beginning.... but we all started somewhere like you. ;)

So let's see if I can keep things short:

1) Forget things like "setup.exe" - You are right: They **are** windows-only. (Except if you use wine, but I this won't make sense in your case right now - and I guess it's only going to confuse you as a beginner)

2) Let's try one thing after the other:
First get you online - ok?

So: If I'm correct, you haven't mentioned **how** you're supposed to go online: Dialup, ADSL, Cablemodem?

Is your modem USB or Ethernet?

---

### Post by Daveth on 2007-02-08
This would be with the freebie usb that Tiscali dish out to all and sundry signing up with them? The general view as I understand it is that usb modems are hard to set up in Linux (please correct me Forum members if i'm wrong on this point!). You are right, the cd that comes with it is a windows .exe file to load the usb driver, and this will not work in Ubuntu.
Your best solution is to put the usb modem away in a cupboard and get yourself an ethernet router. You plug the plug the phone socket end into the phone socket on the wall, the network cable end into the router, and then a network cable from the other socket in the router to your ethernet/ network socket in the back of your pc box.
Nice thing about ethernet routers if that they are device/driver independent, so will work with anything.
You will have to ask Tiscali what there dns address is, and enter that into the configuration window in your browser- the router will tell you the network address it uses, and the config window should pop up. Otherwise the router does not know about Tiscali or where it lives in the web.
My BT205 router works a treat; you can hunt for second hand ones on ebay.  Smarter terminal coders than me should be able to provide a quicker fix to this.

---

### Post by mikewhatever on 2007-02-08
Some people actually like the process of tinkering around. Here is the [USB Modems](https://help.ubuntu.com/community/UsbAdslModem?highlight=%28usb%29) link to help, or at least explain more.

---

### Post by Jamface on 2007-02-08
When I installed 6.10 on Monday it detected most of my hardware, including my Sony camera and printer.  The camera download/upload works fine but the printer doesn't.  But I still haven't managed to get the internet connection to work.  I'm using a modem/router and linking my main machine and laptop.  My ISP told me I would need the modem/router to use broadband with Linux and details of my username and password, but not the setup disc the ISP provided originally for my ADSL modem setup. The modem/router works well with Windows XP but when using Firefox in Ubuntu I get an error message which says the connection has timed out and the website it was searching for did not reply in time - after trying for about 2 minutes.  I followed the instructions in the Ubuntu help files and rechecked everything - but to no avail.  I have tried setting up my email account in Evolution, but the same error message appears.  There is other stuff in these forums about using a modem/router. I don't recall the name of the poster, but you could try a search using my name as I posted a request for help but had no responses.  I think the thread had run out.

---

### Post by Suse on 2007-02-08
Thanks everyone for replying so quickly! It's nice to see that people are so helpful. My modem is USB and I go online ASDL. Should I aquire an ethernet router as Daveth suggests?

---

### Post by Suse on 2007-02-08
I am following the link supplied by mikewhatever for setting up my USB modem, which is Speedtouch. I'm down at the first hurdle. I don't know what it means when it says type the following command: grep -B 1 "THOMSON" /proc/bus/usb/devices.

Where am I supposed to type it??!:confused: :confused: :confused:

---

### Post by n0ll on 2007-02-08
There are many ways to get to an X-terminal or command line prompt, or xterm, this is probably the worst way, but quick to show.

Pretend you are in the windows world and go to-

start > run 

Then type 

xterm &

a rant---
In the UNIX world we call this an X-terminal or command line prompt. In the Window world they call this a DOS prompt. This is the core difference why win will die in our lifetimes and Linux will stay on to take mankind to the next level. Did you know that Bill gates bought DOS off some guy in his garage for $100(well sort of [http://en.wikipedia.org/wiki/Bill_Gates](http://en.wikipedia.org/wiki/Bill_Gates)), and then proceeded to build an empire of this inferior DOS. IBM on the other hand built UNIX from thousands and thousands of man hours by some of the smartest pepole in the world, then came along Linux to open doors and shatter windows.

---

### Post by shareMenaPeace on 2007-02-08
> **Suse said:**
> I am following the link supplied by mikewhatever for setting up my USB modem, which is Speedtouch. I'm down at the first hurdle. I don't know what it means when it says type the following command: grep -B 1 "THOMSON" /proc/bus/usb/devices.

Where am I supposed to type it??!:confused: :confused: :confused:

Command can be run in linux from the terminal.

Open it in your Desktop with eg.

Applications -> Asseccoires -> Terminal (you might want to rightclick and choose "add to panel". this alignes the terminal icon to your Desktop panels for further use/easy access.
Hightlight text in terminal and choose copy to copy out or choose past.
You can also use copy/post to add the terminal/console commands easy from the forum etc.

---

### Post by n0ll on 2007-02-08
have you read this yet

[http://www.ubuntuforums.org/showthread.php?t=232059](http://www.ubuntuforums.org/showthread.php?t=232059)

See Section 7

---

### Post by StevenHarper on 2007-06-04
Hi I have made  a package to make Speedtouch Modems work

You can get it here

[http://www.squeezedonkey.com/svn/linux/trunk/releases/](http://www.squeezedonkey.com/svn/linux/trunk/releases/)

Read about it here

[https://launchpad.net/usb-adsl-modem-manager](https://launchpad.net/usb-adsl-modem-manager)

and post Support Questions here 

[http://ubuntuforums.org/showthread.php?t=445701](http://ubuntuforums.org/showthread.php?t=445701)

Steve

---

### Post by Saltire59 on 2007-06-06
> **StevenHarper said:**
> Hi I have made  a package to make Speedtouch Modems work

You can get it here

[http://www.squeezedonkey.com/svn/linux/trunk/releases/](http://www.squeezedonkey.com/svn/linux/trunk/releases/)

Read about it here

[https://launchpad.net/usb-adsl-modem-manager](https://launchpad.net/usb-adsl-modem-manager)

and post Support Questions here 

[http://ubuntuforums.org/showthread.php?t=445701](http://ubuntuforums.org/showthread.php?t=445701)

Steve


Just to say thanks for this software. I downloaded and ran it and got my Speedtouch 330 to connect without any real problems.

Without this I'd probably have had to buy a router.

---

### Post by xpod on 2007-06-06
> Just to say thanks for this software. I downloaded and ran it and got my Speedtouch 330 to connect without any real problems.

Without this I'd probably have had to buy a router.

Welcome to Ubuntu Saltire59
Great to see more fellow Edinburgh punters make the jump:D

Good luck & enjoy the ride.

---

