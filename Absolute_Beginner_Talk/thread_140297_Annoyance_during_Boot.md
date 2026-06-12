---
title: "Annoyance during Boot"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by Griff on 2006-03-05
My laptop is usually hooked up to an ethernet line at home, but sometimes I need to take it to school to work on projects there.  The school uses wireless internet.  Here's what bothers me.  If the laptop isn't hooked up to my internet at home, it will hang on the 'setting up network interface' for about 2 minutes before it fails.  This drives me nuts.
It there a keyboard command to skip or cancel this step during boot?
Thanks,
Griff

---

### Post by TrendyDark on 2006-03-05
Just goto System> Administration> Networking

Then click on your wireless interface, "deactive".

This will stop it from trying to connect to the wireless interface.

From now on, although, to connect you'll have to open up your terminal and type "sudo ifup wlan0"

---

### Post by masooga on 2006-03-05
I'm a newbie myself but I've had this problem and I find hitting Ctrl + C cancels the attempt.  This may be completely damaging to my system but I haven't run across any negative effects yet!

---

### Post by jimrz on 2006-03-05
yep...Ctrl + C...it's quick, does no harm and you don't have to go back and reverse it later

---

### Post by pbransford on 2006-03-06
Is there a way to change the DHCP timeout? 2 minutes is WAAAAY too long. If a DHCP server doesn't respond within 30 seconds there is likely no dhcp server at all. Even 15 seconds is a long time for that. Or how about backgrounding it like I've seen a lot of distros doing?

---

### Post by Griff on 2006-03-06
Woo!  Thanks guys.  I'll try it in the morning at school.
edit: success!

---

### Post by slaging on 2006-03-06
Wow. This thread made my week. Thanks for the posts.

---

