---
title: "GRUB configuration problem"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by AAllenJCC on 2008-03-19
Hi all, I'm new to Ubuntu. I have a fair amount of experience with computers in general, but not loads with Linux. I've successfully installed Ubuntu, and am getting it to dual boot properly. The problem lies in configuring which operating system I would like GRUB to boot as default. I am using 

```
sudo gedit /boot/grub/menu.lst
```

to bring up the configuration file. When I try to save the changes made, it tells me that I lack the permissions. When I check the ownership of the file, it tells me that root owns it. However, I can't login to root via the login or the switch user, as when I do it tells me something to the tune of "The administrator cannot log in to this screen". How do I get the rights to save this config file? 

Thank you kindly.

---

### Post by glennric on 2008-03-19
Try
```
gksu gedit /boot/grub/menu.lst
```

---

### Post by aspen_dv on 2008-03-19
Can you  switch to root with
sudo su -

But it's weird it didn't allow to modify the file with sudo

---

### Post by AAllenJCC on 2008-03-20
gksu did it! Thank you! Now, I must ask, what exactly are sudo su - and gksu? I figure there's no sense in typing it without knowing what the command I'm inputing is. Also, while I'm at it, is there any way to turn off the startup noise? The rest of Ubuntu is volumed just fine, but that initial startup sound is unholy loud.

---

### Post by bodhi.zazen on 2008-03-20
see these links :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

	gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by bodhi.zazen on 2008-03-20
> **bodhi.zazen said:**
> see these links :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

	gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Although there is nothing wrong with sudo su - , most people use

```
sudo -i
```

Less typing :twisted:

---

### Post by AAllenJCC on 2008-03-20
Alrighty, thank you everybody!

---

### Post by Andavane on 2008-03-20
> **AAllenJCC said:**
> gksu did it! Thank you! Now, I must ask, what exactly are sudo su - and gksu? I figure there's no sense in typing it without knowing what the command I'm inputing is. Also, while I'm at it, is there any way to turn off the startup noise? The rest of Ubuntu is volumed just fine, but that initial startup sound is unholy loud.
To turn off startup sound:
system/preferences/sound/sounds
then select the option you want

---

