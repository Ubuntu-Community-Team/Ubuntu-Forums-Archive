---
title: "Installed a Graphics Card--Now My Wireless Doesn't Work!"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by Steggy on 2006-08-23
Hello all,

Yesterday, I purchased a new NVIDIA GeForce MX 4000 graphic card and installed it in my computer. I discovered, upon booting, that, though I was able to start X my doing a dpkg-reconfigure xserver-xorg and setting it to use VESA drivers, I was unable to access the Internet. So, to get my new graphics card to work, I had to shutdown, remove it, reboot using my on-board graphics chip set, download the NVIDIA drivers, reinstalling the card, then finally running the program to configure the card to work.

Now, I can boot with the graphics card with no problem. However, I am now unable to access the Internet from my Ubuntu computer. I'm using a Broadcom PCI wireless card, for which I used NDISWrapper to install the drivers to get it to work. my lspci lists the card, and NDISWrapper tells me that both the hardware and the driver are present. My Network Manager tells me wlan0 is activated, but it doesn't seem to be communicating with anything (or instance, it doesn't have an IP address.)

The only thing I can think of is that adding the graphics card in a PCI slot is somehow interfering with my wireless card working from the other PCI slot. However, I have no idea whatsoever on how to fix this, or what else might be causing the problem. My search in the forums and on Google have turned up nothing of any use to me.

Any help will be greatly appreciated.

Thank you,
Steggy

---

### Post by Steggy on 2006-08-23
Nobody has any ideas? I still don't have the least clue what could be causing this. I mean, I know adding the graphics card caused it, and I can return to normal Internet usage by removing it (I have tested this), but I think I should be able to use both a graphics card and wireless network card at the same time with Ubuntu.

---

### Post by Steggy on 2006-08-25
Well, I got help elsewhere, and I'm posting here just in case anyone else runs into a similar problem and finds this post.

The solution that worked for me was very simple: I removed my old ethernet card that I'm not using, and moved my new graphics card to that slot on my motherboard. So, if you're having a similar problem, I'd suggest changing the configuration of your PCI cards. It might not work for you, but it worked for me, and that's all the help I can offer.

---

