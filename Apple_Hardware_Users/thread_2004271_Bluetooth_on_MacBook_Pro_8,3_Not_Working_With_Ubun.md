---
title: "Bluetooth on MacBook Pro 8,3 Not Working With Ubuntu 12.04"
date: 2012-06-15
forum: Apple Hardware Users
---

### Post by hayhursm on 2012-06-15
Hello Everyone,

I cannot get my bluetooth on my MacBook Pro 8,3 to detect any bluetooth peripheral.  According to the Official Documentation ([https://help.ubuntu.com/community/MacBookPro8-2/Oneiric#Bluetooth](https://help.ubuntu.com/community/MacBookPro8-2/Oneiric#Bluetooth)) it worked out of the box with Oneiric but this is not the case with Pangolin.  Has anyone experienced this issue and if so could you please provide a remedy?  Thanks in advance!

---

### Post by hayhursm on 2012-06-19
Can anyone help me out on this?

---

### Post by hayhursm on 2012-06-25
Anyone at all????

---

### Post by hayhursm on 2012-06-26
This fixed my problem 100%!  Found it from a blog:

 "Apparently, if you *disable*  Bluetooth coexistence protection in the B43 driver, then Bluetooth will  be able to coexist with WiFi. I have no idea how this makes sense, so  don&#8217;t ask [IMG]http://blog.tkassembled.com/wp-includes/images/smilies/icon_smile.gif[/IMG] 
 I demonstrated how to do this with modprobe:

 [B]# remove b43
sudo modprobe -r b43
# reinsert b43, with the right settings
sudo modprobe b43 btcoex=0[/B]

Unfortunately, this doesn&#8217;t work  permanently, as whenever you reboot, the B43 driver is loaded with the  evil Bluetooth coexistence setting enabled (again, this means that  Bluetooth will *not* work). Thus, we need a permanent solution! 
Pop open your favorite text editor as root and edit **/etc/modprobe.d/options** and append the following line: **options b43 btcoex=0 **
Voila! Go ahead and reboot to test your settings. No more modprobing every time you boot!"

---

### Post by cowtipper16 on 2012-10-10
i don't have the options file.  It doesn't exist.  How did you create it? this did help my situation though thank you!!!!

---

### Post by hayhursm on 2012-10-21
> **cowtipper16 said:**
> i don't have the options file.  It doesn't exist.  How did you create it? this did help my situation though thank you!!!!


Open terminal and type: ```
gksu gedit /etc/modprobe.d/options
``` Type in your superuser password and press "OK".   Now paste  in gedit and click "Save" ```
options b43 btcoex=0
``` You can do it all through terminal as well: ```
sudo sh -c "echo 'options b43 btcoex=0' >> /etc/modprobe.d/options"
```Hope that helps.

---

