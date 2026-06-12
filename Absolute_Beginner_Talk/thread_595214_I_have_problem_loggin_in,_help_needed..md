---
title: "I have problem loggin in, help needed."
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by salesfox on 2007-10-28
I changed the directory of my user name to /root. and then login out.

(because i want to login as root)

After i reboot, it says i cann't login. So, how to change my username directory back? :confused:

anyone helps me out ? 

thank you!!!!

---

### Post by haldean on 2007-10-28
At the login screen, press Ctrl+Alt+F1 and log in as root. Type in 
```
nano /etc/passwd
```
and look for the line that looks like 
```
your_username:x:1000:1000:Your Name,,,:/root:/bin/bash
```
Change /root to /home/your_username (replacing your_username with your username ;) )
Press Ctrl+O then Ctrl+X and type
```
shutdown -r now
```
Wait for it to reboot, and that should work!

---

### Post by daimaru on 2007-10-28
and then if you still want to login as root go to system -->administration > login window select securites tab and check the allow admin login checkbox 
that way you can type root at login screen and login as root if you really want to

---

### Post by salesfox on 2007-10-28
> **salesfox said:**
> I changed the directory of my user name to /root. and then login out.

(because i want to login as root)

After i reboot, it says i cann't login. So, how to change my username directory back? :confused:

anyone helps me out ? 

thank you!!!!

Thank you. I tried. However, the system doesn't let me log in as root

it says that "the system administrator is not allowed to login in in this sessioin'

I cann't find any lead from the google. should i reinstall utunbu?

thanks

---

### Post by haldean on 2007-10-28
did you log in at the normal screen, or did you log in from the console? make sure you press Ctrl+Alt+F1 *before* you log in.

---

### Post by salesfox on 2007-10-28
> **haldean said:**
> did you log in at the normal screen, or did you log in from the console? make sure you press Ctrl+Alt+F1 *before* you log in.

I am trying now. The reason that Ctrl+alt +F1 does not work right now is that i was using vmware.

So, the combination of these keys are non functional.

THANK YOU!!!!

---

### Post by salesfox on 2007-10-28
YES YES>>>>

IT worked!!!

greatly appreciated.

---

