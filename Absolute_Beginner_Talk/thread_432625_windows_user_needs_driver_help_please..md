---
title: "windows user needs driver help please."
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by lizardqueen on 2007-05-04
Hi
I have installed kubuntu on a dell 5100 inspiron as a dual boot with xp.
I am very new to linux but i am skilled with microsoft OS's.  My question is regarding drivers in general.  How do I find out which driver is associated with a specific device?  In windows, I would go to device manager.  Also, how do I add and remove drivers?  
I am interested in the general question of how Linux manages drivers.  Some sites say that the kernel has to be recompiled, but it seems there must be an easier way.  If you could point me in the right direction, I would appreciate it.  I am kind of surprised that I am having trouble finding the answers to my questions by using web searches. (google) I am probably asking the wrong questions because of my microsoft experience.
:confused: 
In specific, I have been having trouble getting different wireless cards to inject packets, but I would like to understand the larger picture.
I am really excited about ubuntu and have found that it is a great OS.  I find that I boot to windows less and less except when work dictates.

---

### Post by juantovarm on 2007-05-04
If you go to system configuration you'll find all the information about the devices in your pc. You can also change the settings there. If you want to see a text-type output of your configuration for your mouse, keyboard, screen and video card, you can type in the terminal: pico  /etc/X11/xorg.conf and if you want to edit it, just type "sudo" before pico. If you want to reconfigure it another way, you can simply type this in the terminal:  sudo dpkg-reconfigure -phigh xserver-xorg

But basically you can see and reconfigure graphically all your pc under kubuntu going to system configuration.

Wireless, that's a big issue. Remember that ubuntu uses open source drivers the manufacturer makes in order for the hardware to be supported under *nix systems, if they do not make the driver...well, sometimes there is a workaround....

for a list of supported wireless cards go to:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Hope it helps

---

### Post by Mr.Beast on 2007-05-04
> **lizardqueen said:**
> Hi
I have installed kubuntu on a dell 5100 inspiron as a dual boot with xp.
I am very new to linux but i am skilled with microsoft OS's.  My question is regarding drivers in general.  How do I find out which driver is associated with a specific device?  In windows, I would go to device manager.  Also, how do I add and remove drivers?  
I am interested in the general question of how Linux manages drivers.  Some sites say that the kernel has to be recompiled, but it seems there must be an easier way.  If you could point me in the right direction, I would appreciate it.  I am kind of surprised that I am having trouble finding the answers to my questions by using web searches. (google) I am probably asking the wrong questions because of my microsoft experience.
:confused: 
In specific, I have been having trouble getting different wireless cards to inject packets, but I would like to understand the larger picture.
I am really excited about ubuntu and have found that it is a great OS.  I find that I boot to windows less and less except when work dictates.

Hi, it sounds like you are in a similar situation with myself.  Years of experience with MS but need to reinterperate MS commands and ways of doing things into "ubuntu" as it were.
I struggled with getting my wireless adapter working first of all, I downloaded network-manager package  and this allowed me to reconfigure the encryption aspects of the NIC I was using. (Atheros based chipsets seem more supported within ubuntu, but I haven't tried any others yet.)
I tried some of the manual config suggestions but found that on reboot of one change it hung the install, but this was really early on so I just reainstalled FF and all was well again.

I'm not sure what you mean by "injecting packets" can you elaborate?
Also, one of my colleagues recommended automatix ([www.automatix.com](www.automatix.com))  and this was fantastic as a package manager.

---

### Post by lizardqueen on 2007-05-04
Thank you to all who answered.
juantovarm, the card that I am using has a prism 2.5 chipset which I am told is a  supported chipset.  I have had similar problems with atheros card also.  I am able to connect to my wireless with the cisco card fine using wpa which is great. In general Ubuntu has handled all my drivers with out any trouble and ubuntu is truly impressive.   Because I have special needs from my wireless card, I have to take a closer look under the hood.
 I am frustrated because so many others make it seem like packet injection is a piece of cake and I specifically purchased cards that others had good luck with.  This is why I feel the need to understand the bigger picture when it comes to using various drivers available for different chipsets.
Just to be clear, when you say "system configuration" do you mean the GUI available in the applications menu?
I did not see the drivers listed there but I will attempt your solutions ASAP.

Mr.Beast, as far as packet injection here's a link: [http://en.wikipedia.org/wiki/Aircrack-ng](http://en.wikipedia.org/wiki/Aircrack-ng)
packet injection is a way to increase traffic on a wireless 802.11 network.  This can be done to test network penetration.  As a MS power user to Linux newbe it is frustrating, but I am sure it will be well worth the efforts.  I have been on the outside looking in at Linux for a while and finally had the time and courage to take it on.

---

### Post by Mr.Beast on 2007-05-04
> 
Mr.Beast, as far as packet injection here's a link: [http://en.wikipedia.org/wiki/Aircrack-ng](http://en.wikipedia.org/wiki/Aircrack-ng)
packet injection is a way to increase traffic on a wireless 802.11 network.  This can be done to test network penetration.  As a MS power user to Linux newbe it is frustrating, but I am sure it will be well worth the efforts.  I have been on the outside looking in at Linux for a while and finally had the time and courage to take it on.

Thanks for the info Lizardqueen, I'll probably take a little shuffle down this route as well ( lol, well, that is if I can get it working that is) 
I have used Wireshark and sniffer pro on wired lans under XP but mainly to investigate odd traffic or behaviour reported by users, and did very minor investigation on wireless networks a while back, but  just as an interest in this topic rather than a basis for proper work.

Just as an aside, where does running the application that may crack, or decyper a wireless key stand from a legal perspective, in your opinion?  Obviously it would depend on the circumstances, if you are using it at work to test work resources as an aspect of your job, no problem.  likewise at home.
But where do you stand if you crack your neighbours wireless key?
See, my view was always (sort of) the following.   If you don't get a TCP/IP address from the network and you don't "bind" a protocol to the nic, you should be o.k. as you cannot effectively steal bandwidth or communicate with the devices.
Now as you can't get an address without having the key, and as the material is being transmitted on the ether, I guess it's fair game to anyone that can receive that information, a bit like a radio station broadcast.
So, how would that information be treated once that it's been decrypted that must be the question, perhaps it's more one of intent in this area.

Just interested in other peoples opinions on this as I find they vary enormously. I have seen articles in professional magazines that berate people who "jack" into wireless networks that are not secured, and then in an article not two pages past it, one of the other writers stating that he sent this article over exactly that method in some expo or another.

---

### Post by lizardqueen on 2007-05-05
juantovarm,
When i check the xorg.conf file I see nothing in there about my network adapters.  I am using KDE desktop and there doesn't seem to be anything called "system configuration" that is accessible through the application menu.  could you please elaborate on how to see which driver is associated with which device?

Mr. Beast, I don't want to discuss the wep hacking in this forum since my main question is how to deal with drivers in Ubuntu.
packet injection is just a tool how it is use or misused is not my concern here.

---

