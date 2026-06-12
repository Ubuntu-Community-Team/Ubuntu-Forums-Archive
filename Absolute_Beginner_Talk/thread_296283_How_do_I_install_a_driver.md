---
title: "How do I install a driver"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Tweedicus on 2006-11-09
Hi

I run Edgy. I have a Belkin card 7010. My local Linux shop kindly gave me the correct drivers for them on a CD. These are native Linux drivers, not Windows drivers. So please no-one tell me to use Ndiswrapper. 

I've taken the drivers off the CD, they're a tar.gz file, and extracted them onto my desktop. The file name is RT73_Linux_STA_Drv1.0.3.0

How do I install this driver so that my card recognises it, and runs off it.

Thanks.

---

### Post by Blutack on 2006-11-09
Whoa, you have linux shops where you live?!?  The first thing to do is extract them.  Hopefully there will be a readme inside.  If not, look for a file like install.sh.  If that fails look for a file called configure.sh.  Let me know which it is.

---

### Post by Tweedicus on 2006-11-09
Yeah we have a Linux shop, complete with ready to go Linux laptops and desktops for sale.

I extracted it, in side the folder is a folder called Module, and inside that is one called Configure (which is a sh file) and it has a big padlock on it.

---

### Post by taurus on 2006-11-09
Open a terminal, Applications -> Accessories -> Terminal, and include the output of this command!

```
ls -la
```

---

### Post by Blutack on 2006-11-09
Awesome.  Right, open up a command line and navigate to where the Configure file is.  To do this use the cd /home/your-name/desktop/Module (I think from your description) and then type
sudo ./configure.sh

---

### Post by punx45 on 2006-11-09
the padlock probably means you dont have executable permissions as your user.

open a terminal and change directory (cd) to the folder the configure.sh is in, then execute it with superuser status like so
```
sudo ./configure.sh
```

---

### Post by Tweedicus on 2006-11-09
I did that, then got command not found.

---

### Post by Tweedicus on 2006-11-09
I also typed ls -la and got a load of script in black and green

---

### Post by taurus on 2006-11-09
Make sure you are in the right directory, where the file is, if you want to run it!  Also, would you mind posting the output of that command here so people can see exactly what's going on?

---

