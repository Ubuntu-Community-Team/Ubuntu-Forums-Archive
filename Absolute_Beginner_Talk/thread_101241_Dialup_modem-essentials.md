---
title: "Dialup modem-essentials"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by dmanderzen on 2005-12-09
Just moved to a place where I no longer have cable access and I'm forced to use dialup.  I need some step-by-step help getting a modem to work. I have dialup access in Windows. Further non-essential comments are in accompanying post.

---

### Post by towsonu2003 on 2005-12-10
[QUOTE=dmanderzen]Just moved to a place where I no longer have cable access and I'm forced to use dialup.  I need some step-by-step help getting a modem to work. I have dialup access in Windows. Further non-essential comments are in accompanying post.[/QUOTE]
Go to System>Administration>Networking. If you see modem listed in there, you're saved... click on it, click properties, check 'enable' and put in your info, ok -> activate .... 
I suppose you wont find it. I wish ubuntu had winmodem support out of the box, but it doesn't. Developers not very interested in this either. We dont even have scanModem tool installed by default! 

Anyway... in another machine, go to linmodems.org , read the page, and download the scanModem tool. copy it to your linux machine somehow, then ```
gunzip scanModem.gz
chmod +x scanModem
./scanModem
```
it will give you a 'Modem' folder (use ls to see the folder). read read1st.txt and modemdata.txt in there, praying that it will recognize your modem... scanModem will NOT configure your modem. It will only give you how to configure it. If you do not understand what modemdata.txt is saying at all, mail it (following the instructions in there) to the mailing list of linmodems.org. 

good luck.

---

### Post by Zonkle on 2005-12-10
[QUOTE=dmanderzen]Just moved to a place where I no longer have cable access and I'm forced to use dialup.  I need some step-by-step help getting a modem to work. I have dialup access in Windows. Further non-essential comments are in accompanying post.[/QUOTE]

I had the exact same problem .... moved to another place where I no longer have cable access and I'm forced to use dialup.

And that is what's keeping me away from using Ubuntu on my Laptop:(

---

### Post by MrChips on 2005-12-11
[QUOTE=towsonu2003]Go to System>Administration>Networking. If you see modem listed in there, you're saved... click on it, click properties, check 'enable' and put in your info, ok -> activate .....[/QUOTE]

Ok I've completed these steps and hopefully I am saved...but no, still not connecting.  I mean how do I get the modem to actually "dialup" the server.  I hear nothing, no dial tone, no snap-crackle-ding.  I am not sure the OS is completing this step before attempting to surf the web.

I was once on cable.
I feel your pain...

---

### Post by squidward2006 on 2005-12-12
I am having identical woes trying to make the switch from windows... :(  I have tried configuring the connection from both System > Administartion > Networking (where auto-detect failed, and I tried all available port options)and from the command line. The furthest I have gotten after setting it all up and entering the "pon" command yielded results of "/usr/sbin/pppd: In File /etc/ppp/peers/provider: unrecognized option '/dev/modem' "....I have now bought two differnt modems that were supposed to function with linux to no avail. I recently switched to Ubuntu from Red Hat 8.0 because the modem was not even listed in Device Manager with that distro and someone suggested I try Ubuntu.
After successfully installing the new distro, I immediately checked device manager...And there it was! My modem was listed! I thought my troubles were solved....they were not. 

Although the modem is recognized by the OS unfortunantly I am no closer to establishing a connection than before. I too have yet to hear the modem even attempt to dial a connection (yes, I did set the volume to loudest) I guess its time to grab a machette and head back into the Linmodem /scanModem jungle and download that again from my windows box, so I can go through that dance again. I have a finite amount of time in which to play with this though....Any advice anyone could offer would be greatly appreciated. I am trying to kick the windows habit but so far my efforts (although educational) have been for naught........

---

### Post by squidward2006 on 2005-12-12
OK since my last post I downloaded the Linux drivers from from the manufacturers web site (SmartLink) and downloaded and ran scanModem....However when I try to install the modem driver as per instructions, I dont seem to be having any success, many of the commands return a command not found, too few arguments, or no such directory error message...any one have any advice?:confused:

---

### Post by dsd on 2005-12-15
If you're running an i386 environment you should be able to use Synaptic or apt-get to get the drivers,

[sl-modem-daemon](http://packages.ubuntu.com/breezy/misc/sl-modem-daemon)

If you are running another architechture (such as AMD64) then you are going to have some trouble. I'm still struggling to figure out how to make it compile for AMD4 (vs using chroot)

---

### Post by linuxguiri on 2005-12-29
[QUOTE=squidward2006]OK since my last post I downloaded the Linux drivers from from the manufacturers web site (SmartLink) and downloaded and ran scanModem....However when I try to install the modem driver as per instructions, I dont seem to be having any success, many of the commands return a command not found, too few arguments, or no such directory error message...any one have any advice?:confused:[/QUOTE]
have you looked at [DialupModemHowto]("https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems")? You might see if the commands that the author lists for installing each of the four main types of winmodems give you some alternatives for installing the drivers.

---

