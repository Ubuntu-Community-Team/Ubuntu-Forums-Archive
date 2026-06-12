---
title: "adept fails to work"
date: 2006-05-15
forum: Apple PPC Users
---

### Post by penman242 on 2006-05-15
I just installed breezy.  I am the first and only user.  If I try to start Adept from the K-menu I get:

"Su returned with an error"

If I type sudo adept in a terminal window I get:

sudo: unable to lookup ubuntu via gethostbyname()

If I type adept in a terminal window, I get:

Will not save configuration file
"/home/penman242/.kde/share/config/adeptrc" not writable.
Please contact your system administrator.

I can't even sudo krite /etc/apt/sources.list           or
sudo nano /etc/apt/sources.list

I just get: 
sudo: unable to lookup ubuntu via gethostbyname()

su doesn't work either.  It asks for passord, I give it mine

Can someone tell me how to get adept working? Thanks.

---

### Post by aysiu on 2006-05-16
[This](http://ubuntuforums.org/showthread.php?t=91455) may help.

---

### Post by penman242 on 2006-05-16
Thank you Aysiu, for your advice.  I tried both of the suggestions in that thread.

sudo chown /home/penman242/.dmrc

and

sudo chmod 755 /home/penman242

but both gave:

sudo: unable to lookup ubuntu via gethostbyname()

I am glad I decided to try a release version!  I still would very much like to get Ubuntu to work, because of the vast repositories of up to date applications.  Any help would be greatly appreciated!

Steve

---

### Post by aysiu on 2006-05-16
Well, *sudo* isn't working because of the error.

Reboot your computer. Do you see how there are at least three boot options--regular, recovery, and memtest?

Choose **recovery mode**.

Once you do that, you'll be logged in as root. Then try ```
chown /home/penman242/.dmrc
chmod 644 /home/penman242/.dmrc
```

---

### Post by linuxnewbie946 on 2006-07-13
I got this same error after I changed my hostname. I will try your solution.

---

