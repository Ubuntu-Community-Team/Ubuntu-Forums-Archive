---
title: "Some help with xubuntu/xfce"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by longboneslinger on 2008-04-04
Ok, I installed xubuntu 7.10 on an old Dell Latitude lappy but my questions are (I hope) simple:

1:I want to access the files on my desktop (Ubuntu 7.10) with Places/Connect to server but I dont see this in xfce. I have places but it doesn't list 'server'. I have it set up on my ubuntu box and it works fine. I can hit the lappy off the wireless with no problem but I want to hit the desktop from the lappy as well.

2:I have a wireless card (wpc54g v2) in the lappy. I used ndiswrapper to access the 'net with no prob but Network Manager is being stupid. I have to re-input the shared key each time though the asterisks indicate that the key is still in.   :confused:   Is there a method to make it stick. I saved the connection and hit the green check box. When I reboot, i have to open network manager and re-input the shared key. After I re-input the shared key it works fine. Any changes I make in network manager require me to re-input the key.
This is annoying since I have to go to the desktop or borrow my wifes lappy (BIG headache) to get the bleeding key.

I have it set to :
Enable roaming mode is disabled.
Configuration - Automatic configuration (DHCP) 
My wireless router is also set up for auto dhcp.

I'm  gnew to linux and networking as well so be gentle.
A huge thanks in advance for any help. These forums are a major reason for my conversion to linux along with the fact that as OS's go, linux truly rocks!
later taters,
bone

---

### Post by ugm6hr on 2008-04-05
1. XFCE uses thunar rather than nautilus.  Unfortunately, thunar doesn't have network browsing as a default feature; hence no network in places.

Options:
A. [http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734)
B. [http://ubuntuforums.org/showthread.php?t=304131](http://ubuntuforums.org/showthread.php?t=304131)

PS: I couldn't get option B to work, but it would be a nicer solution.

2. Network Manager can be annoying.  Not sure why it is doing that though..  In you startup and sessions options, do you have start gnome services ticked?  If that doesn't help, I would suggest using wicd (see below) instead.

---

