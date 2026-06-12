---
title: "frustration"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by dontpinch on 2008-02-25
i'm not a computer wiz, i'm just really the average everyday computer user, but ubuntu has proved to be a lot harder than i expected. i expected to invest some time in reading and documenting myself and i did, but after installing ubuntu, for the life of me i haven't been able to connect to the intenrnet. we have wireless at home so i tried to make the wireless card work, i found various help pages about that particular belkin wireless g card. one instructed me to download some file. so i go, move a large piece of furniture becuase cable, wireless and vonage are back there, and unplug the ethernet cord and plug it in.   of course, no internet connection, even after restarting ubuntu. so i try to figure it out but guess what, the mac i'm using to get info from the ubuntu forums is of course off-line since the wireless is unplugged. how the hell am i supposed to make it work???? i really dig the idea of using ubuntu or another linux operating system but it has just become way too complicated and hard for a newbie like me. i might have to give up. that sucks

---

### Post by bodhi.zazen on 2008-02-25
Well, any OS is difficult if your hardware is not recognized.

We need information, what hardware (wireless) are you using ?

See if these links help out :

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

	[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

If you are still stuck, please describe what you have done in a little more detail.

---

### Post by ispy on 2008-02-25
can you use the mac to find the pages you need and make them available offline? just plug the wireless back in and download the pages you need, or open them in firefox tabs and leave them...

from there it'd be easy enough if you didn't have to search for any other help...

coincidentally, what program are you trying to use? can't you just download the file from the mac and transfer it over to Ubuntu with a flash drive?

---

### Post by richaoj on 2008-02-25
could you be more specific than "go download some file".  can you tell us what kind of wireless card you are using?  you have to be more specific if you want help.  

I think that you will find the people on these forums very helpful and patient.  We want you to enjoy your ubuntu experience, and I certainly understand that it can be frustrating -- especially with wireless problems which seem to run rampant because of a lack of driver support from manufacturers.  

But if you are patient, we will get the problem fixed, and IT WILL BE WORTH IT!

so take a deep breath, get us at least what the model # of the wireless card you are working with, perhaps copy/paste a lspci and an iwconfig, and then we will get somewhere.  don't lose hope!

---

### Post by em3raldxiii on 2008-02-25
Don't Give up!!!

That would be frustrating, I have to admit.  Okay, so first off, let's deal with the wired aspect, because that should be easy.  Your wireless router, does it have LAN connections on it?  If so, when you connect, you will probably have to register your computer's MAC address with the router to gain access to the network.  You may be able to do this by following the directions for logging onto your router.  For example, if it's a D-Link, you would open a browser and type in:  19.168.0.1 into the address and then enter the username/password.  Then you could enter the appropriate screen and register your MAC address with the router.

What computer are you using to log onto the forums?  You could use that computer to download the particular file, save it to a CD or something and go that route.

Wireless has been a thorn in many Linux users' sides for a while now.  Some wireless cards are very easy to set up, while others remain a bit cryptic.  We'll get you working :D

Unfortunately, since I am at work, I have very little time to invest in the forums, but I will try to steer you in the right direction where I can :D

Cheers!  And good luck!!

---

### Post by dontpinch on 2008-02-25
well, thanks you all...i didn't expect so many responses so fast. i didn't expect any response at all.

as i said, i can't connect to the internet by plugging in the ethernet cord, i was trying to make the wireless work, i have a belkin g card f5d7010 version 1000v, i found this link [http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)
i don't think i can download that particular file since it imples my ability to connect with ubuntu. 

i found this thread [http://ubuntuforums.org/showthread.php?t=333166&highlight=F5D7050+version+1000](http://ubuntuforums.org/showthread.php?t=333166&highlight=F5D7050+version+1000) but i find it a little too criptic for my small brain...

i guess i'll try again tomorrow. try the ethernet again as you suggested. thanks

---

### Post by richaoj on 2008-02-25
either that or if you do have an internet-connected computer, you can simply just go find the windows driver file that you need -- the .inf file that guide was talking about -- and copy it onto a flash drive to transfer it.  And i believe that ndiswrapper is a package you can pull off the installation cd (i could be wrong).  So it should not be so bad . . .

---

### Post by em3raldxiii on 2008-02-26
richaoj is definitely onto something there.  I think ndiswrapper is on the installation CD, so if you have the CD enabled in your ubuntu repository, then you should be able to just install it using synaptic package manager.  And if your specific card came with an installation CD, then it will have the driver on it somewhere ... specifically it will be something like driver.inf ... and then you should be good-to-go.  Keep posting about your success or lack there-of!!  There are others with your specific problem, and the more you/we can help, the better :D

---

### Post by dontpinch on 2008-03-01
hello there
thanks so much for all the replies and good pointers.

i have done as outline din this page
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)
in the restricted drivers the firmaware for broadcom 43xx chipset family is in use but and when i troubleshooted this is what i got 

iwconfig 
lo no wireless extension
eth0 no wireless extension

any ideas? thanks again

---

