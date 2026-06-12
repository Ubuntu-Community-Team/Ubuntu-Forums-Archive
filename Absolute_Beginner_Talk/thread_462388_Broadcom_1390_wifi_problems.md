---
title: "Broadcom 1390 wifi problems"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by bradrover on 2007-06-02
I installed Feisty as a second partition on my Dell D620, which came with Vista pre-installed. All is well except for the wifi. I've found lots of conflicting info trying to get this working, finally installing the ndiswrapper for the bcm43xx. Now the wifi light is on but I have nothing showing in my list of networks for wireless at all. I'm really confused as to what I should to next. I use WEP as well, and dont broadcast.

I saw something about blacklisting the original drive, but the blacklist command doesn't work at all. It says "command not found".

---

### Post by nyvalbanat on 2007-06-02
Take a look at [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092) - worked for me. It also shows you how to "blacklist" drivers (it's not a command; you need to edit /etc/modprobe.d/blacklist).

---

### Post by gcos7 on 2007-06-03
I'm new to Linux, so I'll tell you what helped me get my Broadcom card working (mine is a BCM4318).  

(1) Get the Windows driver - for mine I needed a .inf and .sys file specific to my card type.  Since you are talking about ndiswrapper I assume you have installed it and your driver.  Open a terminal window and do  ndiswrapper-l (lower case L) -> you should see your driver.  Please note I had problems for a while because I didn't specify the correct path for my windows driver but it still put an entry in ndiswrapper.  You can always sudo ndiswrapper -e xxxxx   where xxxxx is your driver, then sudo -i xxxxx to reinstall it, being sure you have the correct path to xxxxx specified.

(2) Using the package manager, install network-manager.  I found that easier to use and it gives me a menu of available networks as long as in the system/administration/network I set the wireless card to roaming.

(3) In a terminal, type sudo gedit /etc/modprobe.d/blacklist
  
       - position the cursor the end of the last line of text at the bottom of the window
       - press return twice and type the following:

            blacklist bmc43xx

       - press return twice

(4) Save the file and exit gedit

(5) Be sure you have done sudo ndiswrapper -m  

(6) Try rebooting

(7) If you see the little icon on the top menu bar for a network (little black overlapping squares), try clicking on that and see if you get a list of wireless networks available.  I did this and then it asked for the WEP key (be sure to select hex - mine was defaulting to text so of course it wasn't working).  After doing that, it started up a keyring thing which I believe is where it stores the WEP, etc., keys for each network you have logged on to.

That is all I know that I did to finally get mine working.  I hope it gets you started to fixing your problem.;)

---

