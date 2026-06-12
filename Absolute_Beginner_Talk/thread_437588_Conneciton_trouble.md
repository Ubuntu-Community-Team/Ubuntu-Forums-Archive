---
title: "Conneciton trouble"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Calson33 on 2007-05-08
I can't connect to the internet. However, I can connect to my router and administer it. I was able to connect to the internet after installing, but it stopped after I downloaded the updates. I found a thread where someone had the exact same problem here: [http://ubuntuforums.org/showthread.php?t=151725&highlight=network+dead](http://ubuntuforums.org/showthread.php?t=151725&highlight=network+dead)
I tried the solution offered:
$ #sudo gedit /etc/modprobe.d/bad_list

Add this line
alias net-pf-10 off

Save and Restart

But I still could not connect to the internet. 
Any ideas?  thanks!

---

### Post by Devastator9 on 2007-05-08
I had the same problem and had to reset my router also. You might try that.

---

### Post by Calson33 on 2007-05-08
> **Devastator9 said:**
> I had the same problem and had to reset my router also. You might try that.
Brilliant! That worked. Thank you very much.

Any ideas on a more permanent solution?

---

### Post by Devastator9 on 2007-05-08
> **Calson33 said:**
> Brilliant! That worked. Thank you very much.

Any ideas on a more permanent solution?

Not sure of the permanent fix, sister had the same problem about twicw a week she had to reboot router until it finally gave and she got a Linksys. After that problem was gone.

---

### Post by Calson33 on 2007-05-09
> **Devastator9 said:**
> Not sure of the permanent fix, sister had the same problem about twicw a week she had to reboot router until it finally gave and she got a Linksys. After that problem was gone.

er.. My router is a linksys, wrt54g.

---

