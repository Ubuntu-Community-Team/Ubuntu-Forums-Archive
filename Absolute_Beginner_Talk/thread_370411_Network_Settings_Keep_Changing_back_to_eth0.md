---
title: "Network Settings Keep Changing back to eth0"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Jamesbowden on 2007-02-25
basically, I have a laptop, and i connect to a wireless modem to access the Internet. My laptop is NEVER connected through ethernet to a modem. however, ubuntu seems to think it is :S

I can connect to my WiFi network with out a problem. I set up my network setting the way i want them. and its fine. they look like this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=26148&stc=1&d=1172444363[/IMG]

However when i close network settings (web browsing still works fine) and re-open them again. it looks like this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=26149&stc=1&d=1172444363[/IMG]

as you can see my eth0 card has been reactived. Usually this is no problem, because the Wireless card still lets me connect, however some programs (namely ettercap) will defualtly use my eth0 card when it is activated, so they dont work properly.

does anyone know why this is happening?

---

### Post by Jamesbowden on 2007-02-25
./bump

---

### Post by jkeyes0 on 2007-02-25
By the way, it's generally not advisable to bump your own threads. If you do, some people will overlook them thinking that someone else is providing answers and the problem is being resolved.

That being said, can you post the contents of your /etc/network/interfaces file?

---

### Post by Jamesbowden on 2007-02-26
Sorry about the late response. I had to leave last night. he is the content of /etc/network/interfaces

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



```

(and thanks for the advice about bumping, its just that in my experience, items that drop of the first page very rarely get replied to, and as you can see from my late response, i had to leave, i was just being impatient)

---

### Post by Jamesbowden on 2007-02-26
sorry to bump again, but 6 hours, no rely, just giving myself a chance here. is the way i phrased the question maybe?

---

### Post by jkeyes0 on 2007-03-01
What happens if you comment out the lines containing eth0 in your /etc/network/interfaces file? You're only using wlan0, right? (since you're wireless)

Other than that, you could always remove the checkmark from the front of the Wired connection, that way it retains the DHCP configuration, but is disabled.

---

### Post by Ben Sprinkle on 2007-03-01
Are you using Fedora? Looks a bit like it, but anyway...
If your using Ubuntu, double click your network icon, then see where it says default gateway? Set it to what you want. Then disable your other one.
Hope that helped as I sorta don't get your question.

---

### Post by Jamesbowden on 2007-03-01
Meh, i dont think you understood my question, but it doesn't matter i fixed it now anyway.

(i'm not using fedora, i'm just using the clearlook theme that comes with ubuntu, i think fedora uses it by default.)

---

