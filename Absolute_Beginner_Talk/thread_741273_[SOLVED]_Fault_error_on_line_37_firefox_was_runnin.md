---
title: "[SOLVED] Fault error on line 37: firefox was running slow prior to this"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Berean on 2008-03-31
Firefox has been running very slow today, so I looked up on the forum for any help.  A thread from a couple of weeks ago suggested blacklisting something or another, but as I opened the file my whole system crashed, and restarted.  I've managed to get back online but unfortunately when I try to access a students only part of my college website (the forum) it states the following;

 Warning: main(components/com_badword/class.badword.php): failed to open stream: No such file or directory in /var/www/vhosts/midbible.ac.uk/httpdocs/secure/components/com_fireboard/template/default/view.php on line 37

Fatal error: main(): Failed opening required 'components/com_badword/class.badword.php' (include_path='.:.:') in /var/www/vhosts/midbible.ac.uk/httpdocs/secure/components/com_fireboard/template/default/view.php on line 37

Firefox is still running extremely slowly.  Any ideas?  All help gratefully received.  Thank you.

---

### Post by Michael.Godawski on 2008-03-31
Did you try other web browser to eliminate the possibility that this is a firefox-only issue?

Try Epiphany, Opera or Kazehakase.

> A thread from a couple of weeks ago suggested blacklisting something or another, but as I opened the file my whole system crashed, and restarted.

This was probably the suggestion to blacklist ipv6. What exactly did you do that your system crashed. The correct way to blacklist ipv6 is to run this in terminal:
```

gksudo gedit /etc/modprobe.d/blacklist
```

and add the following line at the end of the file
```

blacklist ipv6
```

then save the file and reboot.

---

### Post by Berean on 2008-03-31
> **Michael.Godawski said:**
> Did you try other web browser to eliminate the possibility that this is a firefox-only issue?

Try Epiphany, Opera or Kazehakase.



This was probably the suggestion to blacklist ipv6. What exactly did you do that your system crashed. The correct way to blacklist ipv6 is to run this in terminal:
```

gksudo gedit /etc/modprobe.d/blacklist
```

and add the following line at the end of the file
```

blacklist ipv6
```

then save the file and reboot.

Hi Michael, 

I had tried firefox P in terminal (to start another) and it seemed to be as slow as my original browser.  So I did what you've suggested, but as it opened the whole screen went blank, and then after a few seconds it restarted.  So I've not acutally done anything.  Sorry this is so slow a response but it really is slow to type.  Thank you.  

What I mean is, I had entered the information (that you also suggested) prior to posting and it was then the system crashed.  It did NOT crash after I had done what you suggested and this time my system seems a little quicker, but not the same.  Could the error line be from the website and not my system?

---

### Post by Berean on 2008-04-01
I've blacklisted the suggested potential problem, and Firefox continues to run slowly.  The fault error I suspect is in the web server of the page I'm trying to access: can anyone confirm this, please, by the readout?  Also, I have No Script running, Safecache and Safehistory running: could these be contributing to the problem?

---

