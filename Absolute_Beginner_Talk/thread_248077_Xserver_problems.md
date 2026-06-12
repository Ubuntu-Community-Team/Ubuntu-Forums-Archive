---
title: "Xserver problems"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by mikebeare on 2006-08-31
Hi,

I have still got problems with the Xserver upgrade since the major problems of last week.

I have upgraded to version 10.4 after a complete reinstall of ubuntu and I cannot log into the system. This is the third attempt at this.

Can anyone give me any advice? Before all these upgrade problems I was using Ubuntu with no problems at all. Now I can't even log in.

Thanks

---

### Post by Kobalt on 2006-08-31
Hello,

Something must have went wrong during your reconfiguration of X. What method did you use to fis the problem ? 
One of the first things you could do is reconfigure X, with : 
```
sudo dpkg-reconfigure xserver-xorg
```
Answer the questions properly and you should be able to log in now. 

Cheerios !

---

### Post by louieb on 2006-08-31
Your not alone the 10.4 upgrade also rendered my graphical system useless. Lucky for me I had backed up the xorg.conf file. What I did was boot in recovery mode, downgrade back to the 10.2 version and restore the conf file.
I got to look around I know I can lock the xorg version. Just don't want it updated on this machine. BTW I have another machine that upgraded to 10.4 without any problems. Go figure.

---

