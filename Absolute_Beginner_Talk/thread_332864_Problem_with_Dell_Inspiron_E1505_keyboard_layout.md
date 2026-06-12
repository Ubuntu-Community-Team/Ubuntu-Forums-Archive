---
title: "Problem with Dell Inspiron E1505 keyboard layout"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by kill4killin on 2007-01-06
I just got a Dell E1505 and I have gotten everything I want working on it besides 2 things.

1. Keyboard: I have every key on this thing working except for the down arrow. Does anyone know if there is a known issue with this? I know it works because when I had the live CD loaded during the install it worked just fine, but then as soon as I actually install it the arrow key stops working.

2. XGL/Beryl: I have no idea what is up with this...I think it has something to do with the fact that I am using an ATI card and an X series ATI card at that. If anyone can help with that I would appreciate it, I tried following the how-to on ubuntuguide.org but that gave me an error after I tried logging into my XGL session. Then I tried following a work around for X series cards here on ubuntuforums.org but that made me incapable of even logging into an X session, even a normal one.

HELP!

Thank You

---

### Post by Cathead Fred on 2007-01-08
Hi kill4killin,

 Sorry to hear about your problems. I own a couple of Dell Laptops myself, but they are not the E1505 model.  However, I can point you to a couple of resources that you can check out.

One is Linux On Laptops. Check out their section on Dell Laptops: [http://www.linux-on-laptops.com/dell.html](http://www.linux-on-laptops.com/dell.html)

Also, you can try Tux Mobiles section on Dell Laptops: [http://tuxmobil.org/dell.html](http://tuxmobil.org/dell.html)

As for your XGL/Beryl issue, may I recommend that you post this part of your question in the Multimedia & Video section of the support forums. You will have a better chance for an answer there.

Good Luck and post your progress.

Cathead Fred

---

### Post by kill4killin on 2007-01-08
Thank you for the response! I will definitely check out those sites and see what they can do for me. 

Could you possibly also tell me why suddenly eth1 won't connect to any networks I try to connect it to? At first it worked perfectly fine but now suddenly I started trying to configure WPA so I can connect on my campuses wireless network and after I configured wpa_supplicant per the instructions given to me in the wireless section, I no longer have my eth1 showing up in Gnome connection properties and Kwifi manager can't connect anything either now. I disabled the start up features in /etc/network/locations I had configured to try to get WPA to work and put the default ones back into place and that didn't fix anything...help?! ](*,)

---

### Post by Cathead Fred on 2007-01-09
kill4killin, 
 
  Sorry to hear that. :(    I don't know. But,  I recommend that you post your question in the Networking & Wireless section of the support forums for the answer.

Good Luck and post your progress.

Cathead Fred

---

### Post by morphet on 2007-01-15
Killin:

I'm having exactly the same problem, but with the letter z instead of the down arrow. I solve this by Going to System --> Preferences -->Keyboard --> Layout, and choosing any layout that's compatible but not the one I'm in. This will reset the keys somehow. It's a pain, because you need to do it everytime. For example, If my layout is Generic 104 and "z" doesn't work, I change the layout to Generic 105, and it works. When I reboot though, Generic 105 ddoesn't work, and I have to switch back to Generic 104. It's a pain, and I'll let you know when I solve it, but it's a quick fix.

---

### Post by morphet on 2007-01-19
Ok. System -> Preferences -> Sessions: Startup Programs : Add.

Enter this line: 
```
setxkbmap -rules xorg -model pc104
```

Leave pc104 as is, or fiddle around with the layout that most closely resembles your keyboard.

:)

---

### Post by H.E. Pennypacker on 2007-05-30
> **morphet said:**
> Ok. System -> Preferences -> Sessions: Startup Programs : Add.

Enter this line: 
```
setxkbmap -rules xorg -model pc104
```

Leave pc104 as is, or fiddle around with the layout that most closely resembles your keyboard.

:)

Changing mine to 104 helped (as did 101, 102).  But I went to System > Preferences > Keyboard.

---

