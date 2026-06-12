---
title: "wireless networking with Linksys WMP54g"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Jim Rogers on 2007-01-24
I cannot fine my original thread, so will try again with additional information.

The Broadcom drivers (bcmw15) and the Lynksys drivers (RT61) both return invalid driver when installed with ndiswrapper.
I downloaded the bcmw15.sys and bcmw15a.inf from the sourceforge site.
I am an absolute newbie and don't have a good grasp of utilities etc. so need as much information as you can provide.

sudo lspci | grep Broadcom\ Corporation returns nothing
sudo lspci does return a network controller as Ralink RT2561/RT61 802.11g PCI.

I went through the wireless networking trouble shooting guide as much as I could and it told me my adapter was not working.

So, what do I do, where do I do it, and how do I do it?  And is there a quick way to find my thread again? 

Completely confused:confused:

---

### Post by houstonbofh on 2007-01-24
Go to Advanced Search, and search for posts by your name.  As to your card, I had a similar problem, and bought a new one.  It was cheaper than my time.

---

### Post by Jim Rogers on 2007-01-24
Thanks for your comment but that is not an option. I have more stations on the network and do not think running ubuntu justifies replacing the complete network Hopefully there will be some one reply who has solved the problem or can help me do so.

---

### Post by valkarin on 2007-01-24
Have you tried doing a search for the Ralink that was listed in the lspci?  have you looked at the card and written down the chipset **from the card**?  Many of these cards go through several different versions.  They get a new chipset with each version.  If you bought it new from a store, the version should be on the box.  If it was second hand that's not going to help you much.

A quick search and i found [_this link_.]("http://www.cyberciti.biz/tips/linux-install-and-configure-dlink-dwl-g-520-wireless-lan-pci-card.html")
It has a download link for the chipset you mentioned, as well as a step-by-step how-to.  Let us know if this helps.  And don't give up.  That is for windows users!:biggrin:

---

### Post by Jim Rogers on 2007-01-24
The card is working on the XP side of a dual boot system. The card was purchased new and I have the .sys and .inf files. They are not compatible with ubuntu apparently. When I do the ndiswrapper thing the system reports invalid driver. My card version is 4.2 which is later than any driver package on the Ralink web site.
I contacted Linksys tech support and Sahira reported "there were no drivers available since they had not passed Windows certification". Oh my, and I explained I was setting up a linux workstation!
This is a bummer...... holding up the whole project here.

---

### Post by valkarin on 2007-01-24
You have a driver named rt61.ko in your kernel directory?  This is on the how-to page I put a link to in my last post.  According to that page you will have to compile the driver.  You may also want to check out the ndiswrapper wiki.  They list another solution that is still in beta stage, but may work for you.  They also advise against the drivers that come with it.  

> # Card: Linksys #[WMP54G v4.1], 54mbps -- [link here|List#WMP54G v4.1]

    * Chipset: Ralink RT61
    * pciid: 1814:0301 and 1814:0302
    * Driver: Don't use driver that ships with card, it didnt work with ndiswrapper. Use the close source driver from Ralink [http://www.ralinktech.com]("http://www.ralinktech.com"). It compiles for 2.4 and 2.6 kernels.
    * Other: The rt2x00 Open Source Project ([http://rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com")) have now a driver - but realy beta.
    * Other: The Ralink driver works great. It is not a plug and play, you need your kernel headers, the appropiate gcc (3.4) but when you can link it together and put it where it loads at startup, it works great. I am using WPA without any problem. 



That is from the ndiswrapper page.  I know that it say v4.1 at the top, but the chipset you listed that came up on lspci is the same as the one listed in the quote.  I bet money that this is the chipset for your card.  Read these pages and try them out.  They may work for you.

---

### Post by Jim Rogers on 2007-01-24
I saw that in the Ralink downloads and actually downloaded it. Unfortunately I have no idea as to how to go about compiling it. I am just too new to this environmentl. I guess maybe ubuntu is not for me at this time. Maybe things will catch up and I will be able to do it later. I just do not know where else to turn.
Thanks for the try. I will monitor for a while longer but if nothing comes along I am able to handle, we will just call it off.....

---

### Post by houstonbofh on 2007-01-25
You might consider putting your location in your profile.  This could be easy for a guy just a few blocks away, if they knew where you were.  I have met a few locals this way.

---

### Post by valkarin on 2007-01-25
You can find step-by-step directions on how to compile it at [http://www.cyberciti.biz/tips/linux-install-and-configure-dlink-dwl-g-520-wireless-lan-pci-card.html]("http://www.cyberciti.biz/tips/linux-install-and-configure-dlink-dwl-g-520-wireless-lan-pci-card.html").
I don't think that you use this driver with ndiswrapper.  There are instructions on setting it up at the web page as well.  Remember, Linux is not Windows.  You may have to do some unusual things to get it up and running, but is is musch more stable than Windows and is worth the effort.

---

### Post by Jim Rogers on 2007-01-25
valkarin, but for your encouragement I probably would have just put it aside for a while and played with my software defined radio on Windows.

I downloaded the stuff from Ralink, finally figured out how to check and see if I had the dependencies, and once I realized make did not like directories with spaces in the name, oops, got a decent compile. Now will just have to see what else has to be done to get the thing ready to use.

So thank you my friend, and all others who contributed to this thread. This newbie is on the way, I think. I am completely documenting every step and will be very glad to share.

---

### Post by Jim Rogers on 2007-01-29
SOLVED ....

drivers from ralinktech website were compiled.

an entry was made to /etc/network/interface

      auto ra0
      iface ra0 inet dhcp

A great experience for a newbie.

---

