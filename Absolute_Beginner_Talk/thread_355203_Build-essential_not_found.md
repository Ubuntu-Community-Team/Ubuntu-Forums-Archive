---
title: "Build-essential not found"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by icyblue on 2007-02-06
Hello!!!

Build-essential package is not found in synaptic manager. I used the command 
'sudo apt-get install build-essential' but it says package not found. Can anyone help me? I don't have internet workin in Ubuntu. I need a c compiler so as to get source code of my NIC driver compiled and configured...
Thanks,
Ganesh

---

### Post by m.musashi on 2007-02-06
I'm not sure I understand. If you want to install from synaptic or from apt-get you will need an internet connection. If you don't have internet then that is why you get that message. You could try and install off the CD. I don't know if the packages you need are there are not though. I know there is a way to set synaptic to only use the CD but I don't know what it is.

---

### Post by ComplexNumber on 2007-02-06
> I don't have internet workin in Ubuntu.
thats the problem. when you type in apt-get, its making a connection to the repositories on the internet to fetch and download the package to your system.

---

### Post by m.musashi on 2007-02-06
> **ComplexNumber said:**
> thats the problem. when you type in apt-get, its making a connection to the repositories on the internet to fetch and download the package to your system.

Isn't there a way to just use the CD? Are the build essential packages on the CD?

---

### Post by taurus on 2007-02-06
Yes, build-essential is on the CD so insert the CD into a drive, open a termina,l and type

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by icyblue on 2007-02-07
I'm gettin a error message:

Signature verification not found

---

### Post by icyblue on 2007-02-07
I'm gettin a error message when I used 'sudo apt-cdrom add':

Signature verification not found

---

### Post by taurus on 2007-02-07
What kind of CD is it?  Is it the same one that you used to install Ubuntu on your machine (desktop CD or alternate CD)?  Did you remember to insert it into a drive before you ran those commands?

---

### Post by icyblue on 2007-02-07
It's the same one I used for installing ubuntu. After insertin the CD, I used the command... It's jus said 'Mountin the disc' and then 3 or 4lines of somethin and then this error message....

---

### Post by taurus on 2007-02-07
What happens if you run the last two commands anyway?

---

### Post by icyblue on 2007-02-07
Thank you.. Now,I got build-essentials in ubuntu. 'Signature verificcation failed' due to wrong date&time settings. But I still have some problem in updation due to internet not configured..

---

### Post by taurus on 2007-02-07
If you are not connected to a network, then you will get a bunch of error messages when you run "sudo apt-get update".  I assume the reason you want to install build-essential is because you plan to build a driver for your network card!

---

### Post by icyblue on 2007-02-07
Yes....  But It's not working.. I can't build my ethernet driver

---

