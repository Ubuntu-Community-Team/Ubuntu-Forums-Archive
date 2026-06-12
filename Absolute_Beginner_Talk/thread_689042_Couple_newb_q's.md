---
title: "Couple newb q's"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by onthefence on 2008-02-06
So, i hit some keyboard stroke or combination and the active window went translucent and i couldn't get it back, but all others were opaque still. Another time the window turned black and then didn't get it's color back. I had to close the window and open another. Can someone please explain?

Also, how do you check you IP address and set a static IP address?

If i manually configure it, it doesn't connect. I'm on wireless. I have double checked the settings but to be honest, I am much more savvy in windows. I can set up a windows static IP no prob, but not sure what I'm doing wrong here.

Anyone have a favorite VPN software choice?

Can anyone point to Audacity instructions for newbs. Couldn't find it in Synaptic, ADD/REMOVE programs. I've tried installing some progs from tars but am too beginner for that. Always get an error, too advanced. 

Thanks

---

### Post by PeterJS on 2008-02-06
> **onthefence said:**
> So, i hit some keyboard stroke or combination and the active window went translucent and i couldn't get it back, but all others were opaque still. Another time the window turned black and then didn't get it's color back. I had to close the window and open another. Can someone please explain?

Don't know about the transparency, but it was probably one of the compiz plugins that did that. As for the turning gray that's the default behavior when a program freezes.

> 
Also, how do you check you IP address and set a static IP address?


On the network monitor applet, you can right click and choose Connection Information. Or from a terminal ifconfig will tell you all about the connection.

> 
If i manually configure it, it doesn't connect. I'm on wireless. I have double checked the settings but to be honest, I am much more savvy in windows. I can set up a windows static IP no prob, but not sure what I'm doing wrong here.

ifconfig is the program you want to use to set a static IP. You're going to want to run ifconfig with sudo when setting the address.

> 
Can anyone point to Audacity instructions for newbs. Couldn't find it in Synaptic, ADD/REMOVE programs. I've tried installing some progs from tars but am too beginner for that. Always get an error, too advanced. 

Thanks

It's in there, the search feature is the way to get anything done in synaptic, baring that [this link](apt:/audacity) will install Audacity from the repos once you have networking working.

What wire less card do you have? are you sure the drivers are working for it?

---

### Post by spiderbatdad on 2008-02-06
[http://www.howtogeek.com/howto/ubuntu/change-ubuntu-desktop-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-desktop-from-dhcp-to-a-static-ip-address/)

[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

avoid audacity.

---

### Post by ~LoKe on 2008-02-06
Put your mouse over a window and hold alt and scroll up/down if you have Compiz.  It'll change the transparency.

---

### Post by oedha on 2008-02-06
after changing the IP
you better go to terminal to type :==> sudo /etc/init.d/networking restart
after that you can test the network

---

### Post by onthefence on 2008-02-06
Alright, well thanks all for the help. The compiz thing is solved, thank you ~Loke. I never would have gotten that one. The strange thing with the grey window was that after it "unfroze" it was usable again but never regained it's color, just stayed grayscale. Must have been a bug.

OK, so I have already tried setting a static IP through the GUI thing and that did not work. I realize I didn't mention that I can connect to the network when on roaming mode so there isn't a prob with the driver, it works. But again, won't work with static. I will try to play with the command-line solutions although I am not very comfortable with advanced terminal procedures yet. I'll probably start with oedha's sugeestion becuase I didn't do that.

And I did finally find Audacity, thank you. I'm niot sure why superbatdad doesn't like Audacity, I liked it in Windows, maybe a little clarification would help.

Anyone have any answers to VPN/PPTP connections. Frankly I'm a little surprised that Ubuntu doesn't have a built in VPN program.

Thanks for the help

---

