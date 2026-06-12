---
title: "Havin Trouble installing Ubuntu , plz advise"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by Elppaz on 2006-08-24
Hi I am a windows user who recently came across ubuntu, I really want it to work , my lap top is a sony vaio pcg fx150, I downloaded the iso of dapper drake and burnt it on a cd,when I put it in my sony(which currently has windows ME and all the sony drivers built in) , so I start up and I get the graphical ubuntu display that says, start and install ubuntu... memory test.. etc. so I go and enter for the start and install ubuntu. the screen goes to a text saying uncompressing linux...ok booting kernal. and it that's it , it only shows the cursor blinking, and I hear the disc drive running and the comuter "thinking" for a while until it stops and the screen just goes blank. Now I really want to get this to work, I know it has to work, I only want ubuntu, because it is the only one I think I'll be comfortable with. mind u I am not computer savvy and the whole reason I want to go linux is because i had so much problems with my windows and I want to learn something new. my friend told me it has something to do with a bios?i have no idea how to do this, is there something I need to disable first, probably sony isn't allowing it to run, I really don't know. can some 1 plz tell me what can I do exactly just so I can install ubuntu then I can go on from there? I really want to install it. plz guys. Also I'd like to note that I have tried just booting from the Cd and it has the same problem.

---

### Post by orb9220 on 2006-08-24
Make sure you have the latest iso as this will save you at least 30mins on upgrading [http://www.ubuntuforums.org/showthread.php?t=233444](http://www.ubuntuforums.org/showthread.php?t=233444)

Also try booting with the second menu item safe grachics mode.

---

### Post by seshomaru samma on 2006-08-24
Did you manage to boot from CD ? if so , then your BIOS is set right and it is quite possible that your CD is defected . When it boots there is a 'check CD for errors' option. Try it.
If you cannot boot from the CD , then it probably was not burned properly.
Remember to burn it as image ,at the slowest possible speed.
Good Luck

---

### Post by Elppaz on 2006-08-25
thnx sama and orb,
@ orb :I have downloaded the latest iso, I'm nto to worried about the time to upgrade it really, I just want it to work. I have also tried booting it in the safe graphics mode and it still gives me the same screen. 
@ sama : no I haven't managed to boot it from the Cd, I'm going to try and burn it on a slower speed  as we speak,  but if it doesn't work stil does that mean there is a problem with the bios ? or something I need to change? I thought if I try anything in the bios it would mess things up wouldn't it?

---

### Post by eternalis on 2006-08-25
Burning at a slower speed should fix the problem. The slower the speed the better.

If your CD already boots, then there is no reason for you to change any BIOS settings.

---

### Post by Jerome36 on 2006-08-25
I know the first time I made an image it didn't work.  I ended up updating the firmware to my burner, but then also burnt the disk at a slower speed.  The second time it worked just fine, as well as when I made another disk for somebody else.

I'd suggest the slower speed first of all.  Second, make sure you give it plenty of time to boot.  I don't know how new a "pcg fx150" laptop is, but I'm assuming it's a little older, since it's running ME (though I shouldn't assume, and I could be wrong).  When I ran the live CD on an older desktop computer, running ME, it took a while for it to fully boot into Linux, because the machine was quite old, as well as the CD Rom drive.

---

### Post by oki_doki on 2006-08-25
I take this tutorial from ([http://www.vmware.com/community/thread.jspa?messageID=419923](http://www.vmware.com/community/thread.jspa?messageID=419923))


#################################################################
Well I think I got it working in my case. I needed to install the 686 kernel for things to work. Below are instructions on how to install Ubuntu server 6.06 as a guest virtual machine in Windows VMware workstation 5.5.1 using the Ubuntu 686 kernel. These instructions may also apply if you're not using VMware.

How to Install the Ubuntu 686 Kernel
====================================

1.) boot to the Ubuntu 6.06 server install cd. Choose 'Rescue a broken system.'

2.) when you get to the Rescue Operations screen choose "execute a shell in /dev/discs/disco/part1", this option may read a little differently on your system.

3.) Click continue if another screen appears.

4.) At the prompt, type: sudo apt-get install linux-686

5.) You will be asked if you want to continue, type: y

6.) The installation of the 686 kernel will begin. It looks like an internet connection is required so the install files can be downloaded from the ubuntu website.

7.) When the installation is done, type: exit

8.) You should be returned to the Rescue Operations screen. Choose the last option: reboot the system. Make sure you're not booting to the install cd!

9.) Give the system a few moments to boot-up. At last, you should be placed at the login: prompt.

10.) Celebrate!

Helpful websites:

[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)
This is a very nice piece of documentation that explains all of the different Ubuntu kernel versions.

[http://www.tuxme.com/node/544](http://www.tuxme.com/node/544)
This is the website that gave me the idea to try the 686 kernel. This specific document also talks about installing Ubuntu on laptops.

I really wish ubuntu would detect which kernel is best for a system. It's things like this that I think keep people away from linux. Linux definitely requires a lot of patience sometimes but I think it's worth it in the end.

To all of you who replied with suggestions, THANK YOU SOOOOOOOO MUCH! You're truly a demonstration of the Ubuntu spirit.

Now to finish setting up my LAMP server!

---

### Post by Elppaz on 2006-09-02
Hi all
thanks for all ur help, the sony ended up being very hard to install ubuntu on, so I decided to try to install it on an old ibm thinkpad A21m, same problem occured but I managed to bypass it. So yahooo I have ubuntu :):):):) Im soo happy

but there is some problems
first of all the ubuntu I installed was the one before dapper I think badger is what it was called. so I figured I will get updates when I install it, but the problem is I put in my ethernet cable into the computer (when I put it on the other lap tops boom they're online , they're windows)after I put the cable i select firefox and I type [www.google.com](www.google.com), and it gives me cannot find that name. I'm guessing I'm not connected , so I try the IRC, Gaim and the other internet apps, and no dice. so I was wondering, how can I get my lap top to go ont he internet which I need so badly to get updates and access the help topics menu. is there something I need to configure. this cable is connected to a wireless router, which is connected to my main desktop.the cable works for sure and I'm hoping the ethernet card in my lap top works because when I plug the cable in a green led lights up in that socket (rj45 cat5 is the cable) 
 About burning dapper and putting it ont he thinkpad, I think my burner has problems so I figured maybe I'll get it thru the updates dnlding. 

so yeah can some one enlighten me on wut to do? I'm a complete noob to linux, and I feel like I don't have hands without internet.

so this is my first major obstacle ](*,)

---

### Post by Elppaz on 2006-09-02
sorry my version that I have installed is 5.04 
hoary hedgehog, plz advise on wut I said above

---

### Post by andlinux21 on 2006-09-02
I am not at home right now but did you go to System >> Networking and check to see if your eth0 was active?

---

### Post by Elppaz on 2006-09-02
I have connected the ethernet cable, and when I open the network
it shows only the modem icon and it's disable 
(under connections).
Also I have a wireless card , I plugged it in , nd underneath network it shows now the modem icon and a wireless card, so I configure the wirelss, it detects my wirelss network in the house, I put the WEP key and I select DHCP settings, and then I click okay, it configures, then it shows "the interface eth0 is active" underneath "wirless connections. after this I go to open firefox and type google.com and I get the same message ([www.google.com](www.google.com) could not be found.please check the name and try again). so I am confused, about both the internet and the wireless, I would love either to work, I just want my internet to work. Note also even when none is plugged in the ethernet or the card, there is the icon of 2 computers, up on the top right beside the time, and it shows that there is some data transfer somehow , the screens light up, when I have nothing plugged, in . I click the icon and I see connection: name :lo status:idle and keeps changin.

---

### Post by Elppaz on 2006-09-03
I keep trying and it's still not working, any clue? plz advise on wut  I said above

---

