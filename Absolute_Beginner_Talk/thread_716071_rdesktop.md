---
title: "rdesktop"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by TechDragon on 2008-03-05
is there anywhere I can get good info on rdesktop.  Such as how to use.

I went to their site but couldn't find any info.  If someone could give a few examples that would be great. 

I am trying to log into a networked pc.  I need to supply user, password, and domain.

Thanks

---

### Post by sancho panza on 2008-03-05
Have you tried running any remote desktop programs? Are you trying to connect to a Windows or Linux machine?

---

### Post by bodhi.zazen on 2008-03-05
See if these links help :

Remote access Windows from Ubuntu:
	Use tsclient or OpenVPN.

Windows side: [http://www.microsoft.com/windowsxp/using/mobility/getstarted/remoteintro.mspx](http://www.microsoft.com/windowsxp/using/mobility/getstarted/remoteintro.mspx)

 [http://ubuntuforums.org/showthread.php?t=224212](http://ubuntuforums.org/showthread.php?t=224212)

[http://users.telenet.be/mydotcom/howto/linux/xremote.htm](http://users.telenet.be/mydotcom/howto/linux/xremote.htm)

---

### Post by HermanAB on 2008-03-05
$ man rdesktop

Here is how to use it for the super lazy:
$ rdesktop -g 90% windows.machine.ip.address

Cheers,

Herman

---

### Post by TechDragon on 2008-03-05
I am trying to run say -- outlook seamlessly on my linux desktop.

something like

rdesktop -A username password domain "c: path to outlook"  ipaddress

but cant figure out how.

---

### Post by tcharron on 2008-03-05
I believe what you're looking for is:

rdesktop -U USERNAME -P PASSWORD -s 'c:\Program files\Path\ToOutlook.exe' IPADDY

Or at least something along those lines.

---

### Post by bodhi.zazen on 2008-03-05
See if this link helps :

[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

---

### Post by fatality_uk on 2008-03-05
> **TechDragon said:**
> I am trying to run say -- outlook seamlessly on my linux desktop.

something like

rdesktop -A username password domain "c: path to outlook"  ipaddress

but cant figure out how.

Everything you needs is here.
Just follow instructions. I use it on our eeePc's with great effect!

[http://www.cendio.com/seamlessrdp/](http://www.cendio.com/seamlessrdp/)

---

