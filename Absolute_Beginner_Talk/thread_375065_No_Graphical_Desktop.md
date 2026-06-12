---
title: "No Graphical Desktop"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by armstrongr on 2007-03-03
Greetings,

I'm a brand new, day-1, Ubuntu Linux user.  I downloaded the ISO this morning, and following the instructions, installed Ubuntu on an older model Gateway x86 box.  The install went well, with no niticable errors.  The machine boots, arrives at a login prompt and I login successfully.  However, no desktop starts.  I have no idea how to start the desktop.  Can someone help?

Thanks
Rob

---

### Post by taurus on 2007-03-03
What happens when you type this command after you log in?

```
startx
```

---

### Post by armstrongr on 2007-03-03
I receive the following message

-bash: startx: command not found

Thank you

---

### Post by Amenemhet on 2007-03-03
EEEk! Well, try this command ... init 5

---

### Post by taurus on 2007-03-03
Looks like you have installed the server version.  Now, the question is which window manager do you want to run?

```
sudo aptitude update
sudo aptitude install ubuntu-desktop  <-- for Gnome
sudo aptitude install kubuntu-desktop <-- for KDE
sudo aptitude install xubuntu-desktop <-- for XFce4
startx
```

---

### Post by armstrongr on 2007-03-03
I issued sudo init 5

received the following:

INIT: Switching to runlevel 5
INIT: sending process the TERM signal

tried to run startx again and received command not found message

Thanks 
Rob

---

### Post by armstrongr on 2007-03-03
yes, I did install the server version.  Not really knowing why :)  I want to use this machine to provide me with VPN access (Using Open VPN) to my home network.

I'll take any advice I can get.  I'm a little over my head at this point, but I'm willing to learn. 

Can you recommend a desktop environment that I should use?

Sorry for sounding like an ID 10 T

regards,
Rob

---

### Post by Amenemhet on 2007-03-03
Well,your desktop environment is down to personal preference really, try gnome first, then kde. You can install both if you wish.

---

### Post by armstrongr on 2007-03-03
Thanks!  I'll try Gnome first

Regards,
Rob

---

