---
title: "How can i log into root?"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by Dark Damo on 2006-01-11
I know this sounds silly but i have a .Deb file that i converted from a .tar.gz with alien. But the only user who can write and accsess it is the root account and i didnt set up a password for it. How can i acsess it? 

I tryed with just root and no password but that didnt work :(

---

### Post by TX7 on 2006-01-11
Ah. Ubuntu starts out without root. I can't remember perfectly, but I think it's..

$ sudo apt-get install root


It should prompt you for a root password. I might be wrong, let me know if it doesn't work correctly.

---

### Post by 23meg on 2006-01-11
Use "sudo" as a prefix to the command you use instead of logging in as root. When prompted, enter your user password.

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by jerrykenny on 2006-01-11
" i have a .Deb file that i converted from a .tar.gz with alien"   

I never knew alien could do that !!!?  must try.

Anyway, try   "sudo passwd root", then type in your password, followed by your new root password (in duplicate)

---

### Post by TX7 on 2006-01-11
Yeah, but he's saying he hasn't installed root yet. I remember having to install the root package before being able to use it. Sudo works as well, but I prefer not having to constantly add Sudo to the commands.

---

### Post by TX7 on 2006-01-11
Jerry's right. My bad.

---

### Post by Dark Damo on 2006-01-11
Thank you im going to try all these now. 

:)

Thanks all ;)

Ok now i get error message from log in screen

System administrator cannot log in from this screen. How else can i log on as root? I need the GUI so i can change permissions on the file.

root@OMG:~# /home/damo/ysflight_1-2_all.deb
-bash: /home/damo/ysflight_1-2_all.deb: Permission denied

I enabled root login from that login screen. But how can i acsess my files from my other login?

---

### Post by blackbeastofaarrgh on 2006-01-11
Couldn't you just chmod it? Try something like

sudo chmod 777 [insert name of your file here]

That's always worked for me when I have problems like this.

---

### Post by 23meg on 2006-01-11
Don't log into Gnome as root. Use a root nautilus window instead. Hit alt+f2 and type ```
gksudo nautilus
```

---

### Post by aysiu on 2006-01-11
[QUOTE=Dark Damo]System administrator cannot log in from this screen. How else can i log on as root? I need the GUI so i can change permissions on the file.

root@OMG:~# /home/damo/ysflight_1-2_all.deb
-bash: /home/damo/ysflight_1-2_all.deb: Permission denied[/QUOTE] If it's a .deb, you don't need to access it as user. Just type this command in ```
sudo dpkg -i ysflight_1-2_all.deb
``` Otherwise, for GUI permission changes, do ```
gksudo nautilus
``` in Gnome or ```
kdesu konqueror
``` in KDE.

You shouldn't ever have to log in as root. See the third link of my sig for more details.

---

### Post by flight_master on 2006-01-11
By default, linux seems to make permissions switch-back from execute. You'll need to CHMOD to 777, in order to run it. Also, there is a way to get into root without any modifications (although, this isn't recommended, and I'll get hit on the head for it :-P)
```

sudo -s

```

Regards,
Christian

---

### Post by hassan_saeed on 2006-01-12
I am not sure that what i am going to tell you is perectly right or not but i was able to login as root.

first from your desktop menus goto 'users'
you must see a list of users there and one of them will be your real login name. 

find  user 'root'.  goto its properties and set its pasword manually.
now when you have changed the password goto terminal and type :

su root
it will ask for the password. type the password that you changed. and i think u will be able to login as root. 

i am again saying that i am not sure about this method. 
and also i am not running ubuntu now as it does not recognise my modem yet.

so plz try and then tell me. :)

---

