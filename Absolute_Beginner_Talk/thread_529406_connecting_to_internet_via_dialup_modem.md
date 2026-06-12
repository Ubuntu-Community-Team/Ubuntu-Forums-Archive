---
title: "connecting to internet via dialup modem"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by faraz_k86 on 2007-08-19
hello,

just installed ubuntu and am loving it.

it is a bit complicated as compared to windows but im sure ill get the hang of it.

now the problem is that i cant connect to the internet. ubuntu has recognized my modem, and it even appears in the system>administrative>networking.

from there i enabled it.

but the problem is that there is no connect or dial button, like in windows, when i enter the userame and password, then i click on the connect button to connect to my isp but here i cant find such a thing, help me plz

---

### Post by philinux on 2007-08-19
Read this thread,

[http://ubuntuforums.org/showthread.php?t=391956](http://ubuntuforums.org/showthread.php?t=391956)

does not sound too good though, maybe it will get fixed in gutsy, october I think.

---

### Post by faraz_k86 on 2007-08-19
that sucks.

I cant afford DSL, so does that mean that i cant use internet on my ubuntu?

---

### Post by Dennis N on 2007-08-19
You need a dialer such as GnomePPP. Find this little program in the repositories with Synaptic Package Manager.

---

### Post by Bartender on 2007-08-20
The modem setup in Networking hasn't worked since Dapper.  Take a look thru this
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)
and see if it doesn't help out.  Read the whole thing, cause I was learning new stuff as I wrote it.

If your modem is truly recognized by Ubuntu, you may be in business.  If it's a winmodem and it's not actually ready to go, the above thread won't help you with that.

---

### Post by faraz_k86 on 2007-08-20
thanks a lot, but suppose if my modem doesnt work then how am i supposed to get the plugins and softwares from the package manager??

is there any other way to install there such as an external file i can download in windows and install in ubuntu

---

### Post by oilchangeguy on 2007-08-20
> **faraz_k86 said:**
> that sucks.

I cant afford DSL, so does that mean that i cant use internet on my ubuntu?

how much are you paying for dial-up? have you checked prices recently? if you're in the US, most phone and cable companies now have entry level packages available. with pricing at or very near dial-up.

---

### Post by Bartender on 2007-08-21
> **faraz_k86 said:**
> suppose if my modem doesnt work then how am i supposed to get the plugins and softwares from the package manager??

is there any other way to install there such as an external file i can download in windows and install in ubuntu

faraz, that's what i was trying to get at.  If you have a thumb drive and access to any online Windows PC (preferably a broadband connection, but not necessary for small packages like gnome-ppp) you can use the functional Windows PC to download the packages, then save to a thumb drive.  

If your modem works in Windows and you're dual-booting, you could download packages from the package website while working from the Windows partition, then transfer them to your Ubuntu partition.  All with one computer.

---

### Post by faraz_k86 on 2007-08-29
k thx for all ur help guys.

i tried the package installation using windows on another system but again had problems in the process i posted the problems here and still it doesnt work : [http://ubuntuforums.org/showthread.php?t=536620](http://ubuntuforums.org/showthread.php?t=536620)



so i tried the modem installation again in my ubuntu and followed the "howto"  which led me to download scanModem, i downloaded it and executed it.

im attaching the results.

so what now???

---

### Post by plucky on 2007-08-29
Faraz_k86

Checkout this link which is the linmodems.org website 

[http://www.linuxant.com/drivers/hsf/index.php]("http://www.linuxant.com/drivers/hsf/index.php")

Your modem is listed there. If you follow it to the downloads page, there is a .deb package for your modem. You can download it in windows and use a thumb drive to copy to ubuntu.  Just double click to install in ubuntu. It will only run up to a max of 14k unless you purchase a license key to use at 56k (i.e. very slow). Once the modem is configured and running, it is worth installing GNOME-PPP from the repos to make dial out easier.

Lots of luck

---

