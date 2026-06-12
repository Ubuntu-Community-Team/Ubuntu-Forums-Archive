---
title: "Avast antivirus won't start"
date: 2012-12-14
forum: Any Other OS
---

### Post by Buruk on 2012-12-14
I've installed avast antivirus, when I click on the icon the mouse turns to the thinking circle but nothing happens otherwise.

---

### Post by cottfcfan on 2012-12-14
I had a problem with Avast & had to do the following:
Open the file /etc/init.d/rcS
```
sudo gedit /etc/init.d/rcS
```
When the text file opens add the line:
sysctl -w kernel.shmmax=128000000
make sure the line you added is before:
exec /etc/init.d/rc S
Save the file, exit, then Reboot.
Hope this helps.

---

### Post by Mark Phelps on 2012-12-14
> **Buruk said:**
> I've installed avast antivirus, when I click on the icon the mouse turns to the thinking circle but nothing happens otherwise.

You've chosen the OtherOS header for this -- which implies that this is NOT an Ubuntu problem.

We're not mind readers here.  You need to tell us at least which OS and what version you're running if you want help.

---

### Post by Buruk on 2012-12-16
My OS is Linux Mint 14 cinnamon. I tried your advice cottfcfan but avast still won't start.[]("http://ubuntuforums.org/member.php?u=763277")

---

### Post by Buruk on 2012-12-16
Eventually I figured out avast has problems with 64 bit, I had to use ia32libs to make it work as said here:  

[http://www.techenclave.com/guides-tutorials/how-install-avast-antivirus-ubuntu-131237/](http://www.techenclave.com/guides-tutorials/how-install-avast-antivirus-ubuntu-131237/)

You don't have to download his version of libs, I just used a package manager to install ia32libs.

---

### Post by lisati on 2012-12-16
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by drawkcab on 2012-12-16
If you're not deploying a server I'm not really sure why you'd need a virus scanner.

These companies are great in terms of convincing folks that they must have something that they don't really need.

---

### Post by Max Blyss on 2012-12-17
I tried Avast! on Ubuntu back around 10.10 just because I was new and figured 'why not?'.

Seriously...  Save yourself the headache.   Bad times.

---

### Post by The Spectre on 2012-12-17
> **drawkcab said:**
> If you're not deploying a server I'm not really sure why you'd need a virus scanner.
 
[SIZE=2]These companies are great in terms of convincing folks that they must have something that they don't really need.[/SIZE]
 
Thou the typical Linux User might not really need an Antivirus Program to protect themselves it still might be a good idea to use one to protect others that are not Enlightened enough to be using Linux.O:)
 
We could have an infected file on our Linux Computer that has no effect on us but if you where to put that infected file on someone’s Flash Drive or E-Mail it to them it could be devastating to a friend or coworkers Computer that is still using Window$.
 
For an easy no fuss Antivirus Program ClamTk seems to do the job.

---

