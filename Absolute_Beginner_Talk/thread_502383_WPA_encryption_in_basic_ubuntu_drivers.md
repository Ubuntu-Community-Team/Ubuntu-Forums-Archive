---
title: "WPA encryption in basic ubuntu drivers"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by shanike on 2007-07-16
i'm using feisty.... i need to setup wpa password to access my wifi lan, but those basic ubuntu drivers support only wep ecnryption... what am i supposed to do now? :confused:

---

### Post by aysiu on 2007-07-16
The basic Ubuntu drivers support WPA for me. Are you sure you have *wpasupplicant* installed?

---

### Post by shanike on 2007-07-16
> **aysiu said:**
> The basic Ubuntu drivers support WPA for me. Are you sure you have *wpasupplicant* installed?

i wasn't aware of the fact that i had to install such a package. thank for help anyway :guitar:

---

### Post by aysiu on 2007-07-16
> **shanike said:**
> i wasn't aware of the fact that i had to install such a package. thank for help anyway :guitar:
Well, it comes installed ordinarily, but maybe something special happened in your case so that it got omitted or accidentally uninstalled.

---

### Post by shanike on 2007-07-18
actually, it didn't help. wpasupplicant is installed, i just can't select wpa in the "password type" drop-down menu... i can only choose wep (hex) or wep(ascii):

[IMG]http://image.bayimg.com/ma/eo/ia/ab/a.jpg[/IMG]

---

### Post by AndyCooll on 2007-07-18
I usually need to manually edit the /etc/network/interfaces file. For like you, I can never see anywhere to add wpa settings. I then reboot the box and it works fine. AP

---

### Post by aysiu on 2007-07-18
I usually enable roaming mode and then select the WPA network from the Network Manager applet in the Notification Area. Then, I'm prompted for the WPA password.

---

### Post by shanike on 2007-07-18
still no luck...

[IMG]http://image.bayimg.com/kaecoaabb.jpg[/IMG]

and i'm shure my wireless card supports wpa, because it works just OK in windows...

---

### Post by aysiu on 2007-07-18
So nothing else in the *Wireless Security* drop-down menu? Is it possible that WaldWLAN actually is WEP-encrypted?

---

### Post by tolremeno on 2007-07-18
You might find [this thread]("http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa") to be helpful.

---

