---
title: "Installing drivers"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by BiggoCharley on 2006-02-03
I have downloaded a .tar.gz file containing a wireless card driver.  I managed to extract the .deb file it contains to a directory on my hard drive. Now I'm stuck. What's the next step(s) to install the driver?:confused:

---

### Post by christhemonkey on 2006-02-03
This should install it:

> sudo dpkg -i /directory/of/driver/name_of_driver.deb

---

### Post by weasel fierce on 2006-02-03
What kind of card is it ? I managed to get my wireless set up the toehr day, so maybe I can help

---

### Post by christhemonkey on 2006-02-03
Though have you checked that its not available in the repos through synaptic?

---

### Post by BiggoCharley on 2006-02-03
[QUOTE=christhemonkey]This should install it:[/QUOTE]

Thanks alot for the quick response --I'll give it a try.

---

### Post by BiggoCharley on 2006-02-03
[QUOTE=weasel fierce]What kind of card is it ? I managed to get my wireless set up the toehr day, so maybe I can help[/QUOTE]

Its a Netgear MA521 (Realtek chipset rtl8180) and thanks for the offer --I may need the help

---

### Post by BiggoCharley on 2006-02-03
[QUOTE=christhemonkey]Though have you checked that its not available in the repos through synaptic?[/QUOTE]

I searched the package list in synaptic and couldn't find it but I did manage to come across a couple of threads in this forum that helped
<http://ubuntuforums.org/showthread.php?t=95879> and 
<http://ubuntuforums.org/showthread.php?t=92119>
I managed to find the driver but as you can see I got stuck on the "how-to"

Thanks for your help --all of you--

---

### Post by BiggoCharley on 2006-02-04
[QUOTE=christhemonkey]This should install it: 
sudo dpkg -i /directory/of/driver/name_of_driver.deb [/QUOTE]

Eureka!! This did it --however, for some reason I wasn't able to make it work with "sudo" but once i was able to get a root prompt it worked great:
<root@ubuntu:~# dpkg -i /home/charley/Desktop/rtl8180-sa2400-2.6.12-10-386.deb>


Thanks again for your help

---

### Post by christhemonkey on 2006-02-04
its ok!, though if sudo doesnt work then you probably have to do a sudo su.

---

