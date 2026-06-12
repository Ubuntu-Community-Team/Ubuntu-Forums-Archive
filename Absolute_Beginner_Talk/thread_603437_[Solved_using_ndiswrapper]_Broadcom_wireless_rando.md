---
title: "[Solved using ndiswrapper] Broadcom wireless randomly disconnects in Gutsy"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by xyadam on 2007-11-05
Hello, I know some people, who just started to use Ubuntu Gutsy Gibbon with their Broadcom wireless chip in their laptop, using Ubuntu's Restricted Drivers to make wifi work.
I noticed, that in this case this solution doesn't work on every router, for example at home it's no problem for me to connect to my router, but at the University an other type of router is used, and it disconnected me after 1-2 minutes. (reconnection often not succesful).
That's why I made this very little how-to, (using ndiswrapper), I hope it will work for you too. It is really for beginners as you will see, I'm a beginner too, so i cant help you too much if you have problems using this method, sorry for that.
And sorry for my bad english too, i haven't practiced it for a while :D

So, lets get started:

1, First copy your wireless driver to your desktop for example. Unzip it.
2, Open the console: from now on we will be working here.
3, Install ndiswrapper:

sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

4, After it is installed navigate in into your unzipped drivers folder (in the console of course). There should be a file called bcmwl5.inf or something like that.
5, We will use this file and ndiswrapper to install the driver:

sudo ndiswrapper -i bcmwl5a.inf
sudo ndiswrapper -m
sudo ndiswrapper -mi
sudo ndiswrapper -ma
sudo modprobe -r bcm43xx
sudo modprobe ndiswrapper

Restart the machine (and disable the Restricted Driver of your wireless chip if used before)

Now it should be working fine.

And again: _I'm a beginner trying to help other beginners :D_

---

### Post by laxmidd50 on 2007-11-06
Looks good, but where do i get the driver from for step 1?  I'm having the same problems as you with the broadcom restricted drivers.

---

### Post by hendinas on 2007-11-06
Looks good, i will give this a try when i have time to muck around with ubuntu again, and let u know how it goes.

laxmidd50 - I think he means the windows driver (from install CD that came with the NIC, or manufacturers website)

Lach

---

### Post by hendinas on 2007-11-08
well im connected with the ndiswrapper drivers, so fingers crossed it doesn't drop out :D

Good stuff :)

---

### Post by xyadam on 2007-11-08
Yeah, sorry i forgot to write: you have to use the same drivers as in Windows XP. (coz in Vista the system automatically recognizes your Broadcom wireless, if I remember well, at least in my case). So you have to find the driver that you would use in Windows, and then comes ndiswrapper ;)
I recommend you to look up your laptops manufacturers website, I'm sure there are be drivers for your wifi chips there. Or use your laptops driver cd, if it contains drivers for Windows XP, or something like that.
Good luck :D

---

### Post by xyadam on 2007-11-08
Hendinas, does it work? ;-)
Hope it does :D

---

### Post by laxmidd50 on 2007-11-15
It worked great! Now I don't disconnect from university networks anymore. The only thing that was hard was finding the drivers (cause most sites just had a .exe that installed the drivers, not the .info and .sys that you need for this).

---

### Post by Elotero on 2007-11-15
BUMP.. im gonna check this out in a couple hours and i wanna make sure its in plain view... gracias for your hard work xyadam

---

### Post by xyadam on 2007-11-18
I'm really happy to have helped you guys :D
Elotero it's not MY hard work, it's the hard work of the people who made ndiswrapper ;) Anyway I'm happy to see that this method works with others wireless too! It was really annoying that I couldn't use Linux for internet-browsing within the University and had to boot Windows for that. 

Could someone please write (if he/she knows) with which router didn't the laptops wifi didn't work under Linux before? I'm just curious, nothing more :)

---

