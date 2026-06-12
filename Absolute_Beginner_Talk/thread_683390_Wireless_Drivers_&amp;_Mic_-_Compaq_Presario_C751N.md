---
title: "Wireless Drivers &amp; Mic - Compaq Presario C751NR C700"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by osc1882 on 2008-01-30
Hello.
I am installing Ubuntu 7.10 on to a Compaq Presario C751NR. It's for a co-worker and he wants to give it a try because it came with vista and he knows he doesn't want vista because of all the crap he has heard about it from people and he likes the idea of a stable system that doesn't slow down with age and doesn't get viruses and stuff. So he wanted to give this a try.

I got compiz fusion working. That took a bit of work. And everything else seems to be working great. Only two more big things remain, Wireless Network Drivers and the Mic.

I have ndiswrapper installed along with the GUI. I found in the forums ( maybe some different forums I can't remember. ) Two other guys with the same lap top who claimed to get it working by installing windows drivers thru ndiswrapper. I have tryed them and ndiswrapper claims that the hardware is present but when I go to "System", "admin", "network" it does not show any wireless adapter. This makes me sad because in order for my friend to be able to use this he is going to need wireless.

Oh and when I type in:
lspci | grep Ethernet

This is the out put:
01:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)



Now on to the Mic. He has a built in mic on the lap top. I'm not really sure how it's tied in. As in, is does it run thru a mic channel or is it digital. He has a mic jack for normal mics on the front of the lap top. But when I go into Volume Control and click on the recording tab all it shows is "Capture" and "Digital". I unmuted both of them to see if ether one of them is the digital mic and nether of those made me be able to hear the digital(?) mic and it should have a place for mic in the Volume control because he has a mic jack on the front of the lap top. 


Some Links:
Here is the Forum I was telling you about:
[http://ubuntuforums.org/showthread.php?t=676585]("http://ubuntuforums.org/showthread.php?t=676585")

Here are the drivers they tell you to use: ( I have tried most of them.)
[http://www.atheros.cz/download.php?atheros=AR5006EG&system=1]("http://www.atheros.cz/download.php?atheros=AR5006EG&system=1")

Here is some specs on the lap top: (WARNING PDF)
[http://www.google.com/url?sa=t&ct=res&cd=13&url=http%3A%2F%2Fwww.newageinc.com%2Fpdfs%2FCPQ%2520C751NR.pdf&ei=vUqhR73FJp_WpgTCg8S0DQ&usg=AFQjCNGrjJzRlycVTQU4ReMaBwMgYQtgCA&sig2=NHJItvIHN0ieULfwHrnVQg]("http://www.google.com/url?sa=t&ct=res&cd=13&url=http%3A%2F%2Fwww.newageinc.com%2Fpdfs%2FCPQ%2520C751NR.pdf&ei=vUqhR73FJp_WpgTCg8S0DQ&usg=AFQjCNGrjJzRlycVTQU4ReMaBwMgYQtgCA&sig2=NHJItvIHN0ieULfwHrnVQg")

So if you smart guys could help me out that would mean the world to me. I really have this thing pimped out and he is going to love it.  Pretty Please....

Thanks guys.

---

### Post by oedha on 2008-01-30
here's what i did with atheros
download the AR5007EG windriver
install ndiswrapper manually
open terminal; type sudo rmmod ath_pci ( remove the pci module )
type sudo vi /etc/modprobe.d/blacklist-common
insert : blacklist ath_pci ( to put ath_pci in blaklist mode )
save it and restart the computer
extract the windriver into one folder ( ex: documents )
go to System &#8211; Administration &#8211; Windows Wireless Drivers
install net521.inf
click configure button and set it up
open terminal; type sudo ndiswrapper -m ( to load ndis on restart )
reboot the computer

~E~

---

### Post by Ainab on 2008-01-30
this article might help you. it is about wireles + ubuntu 7.10.
[http://icebreaker.wordpress.com/2007/11/03/wireless-ubuntu-710-love/](http://icebreaker.wordpress.com/2007/11/03/wireless-ubuntu-710-love/)

---

### Post by osc1882 on 2008-01-31
oedha, I tried what you said and it didn't work. It still didn't show the wireless in "network", so there is nothing to configure.  I'm going to try it again in case I did it wrong.

Something else I just found out. When you pug in head phones, the audio comes out of the head phones but it is still coming out of the speaker. Of course this is not a good thing, I'm sure he would like to be able to rock out to some jams or surf you tube with out it bugging other people.

---

### Post by oedha on 2008-01-31
what about the windows driver......
have you put all files on one directory ? including *.bin *inf 
then point to the *.inf one from ndiswrapper

~E~

---

### Post by osc1882 on 2008-01-31
Yes to all the questions on your last post.

Added blacklist ath_pci made it where wrapper wouldn't work. whenever I opened wrapper it would give me a message about "wrapper can not see in hardware is installed" or something like that. So I removed it and now I don't get that message. But the wireless is still not showing up in "network".

And while I think it worked, I don't know what "type sudo rmmod ath_pci" does.

---

### Post by osc1882 on 2008-01-31
And when I said " while I think it worked" I just mean the command did want it was suppost to do. I did not mean, I have wireless now. Because I don't.

---

### Post by osc1882 on 2008-01-31
food for thought
when I type in: iwconfig

I get:
lo        no wireless extensions.

eth0      no wireless extensions.


But when I type in

lspci | grep Ethernet

I get:

This is the out put:
01:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)



Anyone smart then me able to help me?


I installed madwifi at one point. But it didn't seem to work.

Can anyone help?

---

### Post by osc1882 on 2008-01-31
Because this has become mostly about the wifi I'm going to make another post about the audio.

---

### Post by osc1882 on 2008-01-31
No love for me huh?

---

### Post by Kutza on 2008-01-31
Had the same issues, solved them (rename thread as solved if this works for you).

Wireless:

Use adept or synaptic and install ndisgtk.

Download these drivers:
[http://www.phpstory.net/files/bcmwl5.tar.gz](http://www.phpstory.net/files/bcmwl5.tar.gz)

Extract.
Run ndisgtk, click install, go to the directory of the extracted drivers
Click the .inf install, and close ndisgtk.
Give it about 10 secs and you should see networks in the network manager.

To make it boot on startup:
Ubuntu: gksudo gedit /etc/modules
Kubuntu: kdesu kate /etc/modules
Add "ndiswrapper" (without the quotes) to the bottom of the file and save. Reboot.

For audio:

Go here, follow directions. it will install the necessary Conexant linux drivers.
[http://www.linuxant.com/drivers/hsf/downloads-installer.php](http://www.linuxant.com/drivers/hsf/downloads-installer.php)

---

### Post by osc1882 on 2008-03-22
I no longer have this laptop with me to try these things out. But thank you for posting. I know many of you will not believe me but there are no windows XP drivers as well. I ended up "having" to put vista back on after a week of trying. I know, I know, installing vista makes baby Jesus cry. (lol)

---

