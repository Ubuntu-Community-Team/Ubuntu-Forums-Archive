---
title: "flashplugin-nonfree installation prolbems"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by tjb891 on 2006-09-20
I get this error when I try to isntall flashplugin-nonfree


"E: flashplugin-nonfree: subprocess post-installation script returned error exit status 1"

how do I fix this?

---

### Post by Mapleman on 2006-09-20
I am having the same issues, I just sent a bug report about it and this was the last email I received (scratching head) 

Setting up flashplugin-nonfree (7.0.68~ubuntu1~dapper1) ...
Downloading...  done.
usage: update-rc.d [-n] [-f] <basename> remove
      update-rc.d [-n] <basename> defaults [NN | sNN kNN]
      update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
               -n: not really
               -f: force
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

Pending further elaboration please

Thanks:confused:

---

### Post by skymt on 2006-09-20
Follow the directions in [this post](http://kubuntuforums.net/forums/index.php?topic=9172.msg36711#msg36711).

---

### Post by Mapleman on 2006-09-20
Still having issues with it even through those methods, will wait on clarification from Bug Service Department eh

---

### Post by swp6499 on 2006-09-20
sudo sed -e 's/multiuser/defaults/' -i /var/lib/dpkg/info/flashplugin-nonfree.postinst
sudo dpkg --configure -a

try this i found it in another pst on here and it worked foe me hope it does for u

---

### Post by swp6499 on 2006-09-20
sorry i cant type tonight sorry for the typos

---

### Post by CarpKing on 2006-09-20
> **skymt said:**
> Follow the directions in [this post](http://kubuntuforums.net/forums/index.php?topic=9172.msg36711#msg36711).

That worked for me.  Thanks!

---

### Post by helpdeskdan on 2006-09-20
Finally!  The correct answer to this problem!  Both my ubuntu machines have had this problem.  Somebody should post this in the ubuntuguide, make it sticky, or something.

sudo sed -e 's/multiuser/defaults/' -i /var/lib/dpkg/info/flashplugin-nonfree.postinst
sudo dpkg --configure -a

---

### Post by brianC on 2006-09-21
worked for me
  same problem same cure 
 thank you

---

### Post by Mapleman on 2006-09-21
Will this also cure the issue of flashplugin-nonfree using mozilla as default over Firefox or is that still in the works? :)  

Thank you for the script post BTW :) :)

---

