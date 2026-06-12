---
title: "Question - can you run UB from a USBstick within other os without rebooting"
date: 2013-10-04
forum: Any Other OS
---

### Post by Sheikh_Islam on 2013-10-04
HI ,

I am new to linux/ubuntu. 

i have created and used ubuntu to and from usb stick and internal HDD. 

I was wondering if its possible to use/open ubuntu fron usb stick via one click within other os ie- windows ?

Replies are much appreciated.

Regards,

Sheikh

---

### Post by ibjsb4 on 2013-10-04
You can run ubuntu inside windows using WUBI, but there are limitations.  My understanding is it will not work with windows8.  It is no longer a recommended way of installing ubuntu and I think 12.04 was the last to offer wubi.

Another option is a virtual machine.  You could jump to another OS with a couple of clicks, I use VirtualBox for this.  There is a learning curve and you need a fairly powerfull computer.  I have it running on a dual core setup with 4G of ram, but I do take a performance hit.

---

### Post by Sheikh_Islam on 2013-10-04
Thanks [COLOR=#000000]ibjsb4...much appreciated.

I am gonna be travelling in asia next few weeks..i will be using internet cafes and other shared pcs. They would have windows xp or 7 on them. SO, i was wondering if i could just install ubuntu on a stick and use the environment within ubuntu for my emails, browsing etc.

Wondering if its possible or any one has done it !!

I believe you can get usb stick with software on it that lets you use that environment within other os.

Any ideas ?

Regards,

Sheikh




[/COLOR]

---

### Post by ibjsb4 on 2013-10-04
Ok, got it :) Yes it can be done, but I have not ever done it myself.  So I will point you in the right direction for a bootable flash drive, but others with experience in this will need to guide you.  Good luck

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=bootable+system+on+flash+pen+drive&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=bootable+system+on+flash+pen+drive&sa=Search&cof=FORID:9)

---

### Post by Sheikh_Islam on 2013-10-04
Thanks..had a quick skim through the search results ...hmmm..then again i will have to restart the host pc....dont wanna do that...i was looking for a solution without restarting and still being able to open the linux environment with a click.

let me go through your search results....thanks!!

---

### Post by N900 on 2013-10-04
Are you talking about a VM?

If yes,
Install VMware Player on Windows: [http://www.vmware.com/download/player/](http://www.vmware.com/download/player/)

Download VMware image for Ubuntu ( [http://www.trendsigma.net/vmware/ubuntu1104.html](http://www.trendsigma.net/vmware/ubuntu1104.html) ) and extract the zip file.

Double-click the Ubuntu.vmx file that you just extracted and the Linux virtual machine will load inside the VMWare Player.

 And other than VMware, you could also use VirtualBox to run Linux inside windows. The VirtualBox installer and the Ubuntu Linux images for VirtualBox for can be downloaded for free from oracle.com.

---

### Post by sudodus on 2013-10-04
> **Sheikh_Islam said:**
> Thanks..had a quick skim through the search results ...hmmm..then again i will have to restart the host pc....dont wanna do that...i was looking for a solution without restarting and still being able to open the linux environment with a click.

let me go through your search results....thanks!!

If you want something that run on almost any PC, a live USB pendrive is the solution. It can be a desktop install pendrive that forgets what was done, a persistent live system or a complete installed system (installed like it were installed to an internal drive, but instead installed to a USB pendrive). But it won't work inside Windows at internet cafés, you need to reboot the computer. A virtual machine, for example using VirtualBox, was also suggested earlier in this thread, but I don't think you can install it in an internet café computer.

There is the U3 system, that was promoted a lot some years ago. U3 offered the functionality you ask for. It was a proprietary system, that came with some USB pendrives, [http://u3.sandisk.com/](http://u3.sandisk.com/)

---

### Post by N900 on 2013-10-04
Oops! I didn't really read that internet cafe thingy :D

There was an edubuntu vmwaremanager sometime back, IIRC, which would allow you to test drive Linux as a web app. I don't find the link to that now unfortunately... Is someone aware of that?

Edit: Or check out this? [http://manjaro.org/2012/12/06/try-manjaro-in-your-web-browser/](http://manjaro.org/2012/12/06/try-manjaro-in-your-web-browser/) The link doesn't work for me :(

---

### Post by Sheikh_Islam on 2013-10-05
Hi sudodus,

Good advise...thanks...looks like ubuntu installed on a stick is my option then.

All the best.

Sheikh

---

### Post by mastablasta on 2013-10-07
you can run it using virtual box. if you use "Linux live USB creator" (LiLi) to install on USB there is an option in installer called: _**Enable launching LinuxLive in Windows**_
[http://www.linuxliveusb.com/en/help/guide/step4](http://www.linuxliveusb.com/en/help/guide/step4)

if you tick it it will install portable virtualbox on the USB key. you then just run "virtualise this key" and it will run ubuntu inside windows. the problem is you need admin privilege to run it in windows. also i think LiLi is only for windows. and windows maschine needs enough RAM (2 Gb at least)

---

### Post by Sheikh_Islam on 2013-10-07
Good advise MastaBlasta...will give it try...not sure if pcs in asia will have 2 gig in their pcs though..but hey its worth a try ...


Nice one..

Sheikh

---

