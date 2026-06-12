---
title: "Ubuntu 12.10 on Macbook Pro 6,2 - experiences"
date: 2013-03-20
forum: Apple Hardware Users
---

### Post by ubrox on 2013-03-20
I recently installed Ubuntu 12.10 on a MacBook Pro 6,2. I wanted to summarize my experiences for the benefit of others.

**What works**:
Pretty much everything works out of the box
some components dont deliver the best experience though

**What you will miss**:
Graphics switching wont work. I see only the discrete graphics card (Nvidia) and Ubuntu wont see the integrated card. Some see only integrated and wont see the discrete card. I did not invest time in when either happens.
Microphone sucks. There is a lot of echo and the listener cannot make much what you are talking. 
Multitouch - not everything works out of the box. You can try add-ons like touchegg but your success will vary. 
right-click on the touchpad - use two finger tap. You can use synclient to set up a right-click area but it did not work for me and I was not too vested in making it work. two finger tap is fine.
battery stats are messed up. The panel indicator is stuck at the %charge at boot time. When clicked on the icon, it does show charge remaining or time to full charge. 
fans run at higher speeds most of the time in unity. compiz takes a minimum of 8%-10% for a dual monitor setup. Using Cinnamon or Ubuntu classic results in lower fan speeds.
Battery life is significantly shorter
Wireless is very laggy. Even SSH sessions to a remote system seem laggy. On the same connection, same MBP, OS X and Windows the connection is extremely smooth and stable
Bluetooth works well but there are quirks if you decide to turn it off and on. 
power saving features are very bad. If you run powertop and use it to set lot of "bad" things to "good", it improves, however, suspend+resume will fail. I did not try to root cause which component prevents a successful resume. If you leave everything as-is in powertop tunables, suspend+resume works fine. Did not test hibernate. 
magic mouse works but its jerky, overly sensitive and scrolling is SLOW. You can tune it as follows:
[http://blog.matws.net/post/2010/10/16/Correct-magic-mouse-scrolling-on-Linux](http://blog.matws.net/post/2010/10/16/Correct-magic-mouse-scrolling-on-Linux)
[http://numberformatdata.wordpress.com/2011/05/08/apple-magic-mouse-works-with-ubuntu/](http://numberformatdata.wordpress.com/2011/05/08/apple-magic-mouse-works-with-ubuntu/)
[http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/](http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/)

Even using all these tips, I was not able to get the magic mouse to work smoothly. This is very irritating and WILL your productivity. The touchpad is much more usable. 

Installation:
Installation is NOT straight forward. It does require a lot of work and BACKUP everything before you start the install. However, if you put your mind to it, you can get a successful install without much trouble. I cannot emphasize how easy it would be if you created a sufficiently large partition when making one for Windows using Bootcamp. I did it the hard way. Install windows, then resize OS X partition and created one for Ubuntu. Do not take this path unless you are fearless and ready to put in some extra work. 

Some tweaking is required to get the touchpad and wifi working initially. Use the bcmwl module instead of the default (b43, bcma, bcm43xx). It improves the connection stability. 

Add the following PPA and install the packages:
[https://launchpad.net/~mactel-support/+archive/ppa](https://launchpad.net/~mactel-support/+archive/ppa)

Overall, I do not think its worth the trouble to run Ubuntu on  MBP. I point to the magic mouse, mic quality, lack of graphics switching and the battery life to be the down sides. I would rather stick to a nice PC hardware and enjoy Ubuntu on that.

TL,DR: Install it if you really want it, but the Ubuntu, Apple hardware and battery life experience suffers.

---

### Post by ehijon on 2013-04-01
Thank you Ubrox for sharing!
I tried with ubuntu 12.10 in a bootable usb and I found the most of your same issues. Mainly with battery and fans.

---

