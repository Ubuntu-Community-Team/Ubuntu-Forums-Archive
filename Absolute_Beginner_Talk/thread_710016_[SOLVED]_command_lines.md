---
title: "[SOLVED] command lines"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by Stef11 on 2008-02-28
from a previous post i was kindly given instructions to edit modules to ensure ndiswrapper is included at the end to ensure my wireless is loaded at each bootup.
The commands in terminal were:
gksudo
edit/etc/modules
then add ndiswrapper to the end

can someone give me the correct procedure to install this command

This forum" Absolute Beginner Talk" still might be a little advanced for me
Hope someone can help?
Thanks
Stef11

---

### Post by kpkeerthi on 2008-02-28
Open a terminal and type
```
gksudo gedit /etc/modules
```
Add ```
ndiswrapper
``` to the end of the file. Save and Exit.

The module should load automatically next time you reboot.

---

### Post by JoshuaRL on 2008-02-28
Sure, you'll need to do:
```

gksu gedit /etc/modules

```
In the terminal, then add the line 'ndiswrapper" at the end of that.  Then save with the same filename and close.  Then it should load every time you boot.

Hope that helps, I just translated from the earlier post.

---

### Post by Stef11 on 2008-02-28
THANKS FOR YOUR REPLYS. i ENTER THE CODE, Then i was asked for my password then nothing happened, i was back at my terminal
stefan@stefan-desktop:-$

regards
Stef11

---

### Post by aysiu on 2008-02-28
> **Stef11 said:**
> THANKS FOR YOUR REPLYS. i ENTER THE CODE, Then i was asked for my password then nothing happened, i was back at my terminal
stefan@stefan-desktop:-$

regards
Stef11 Can you be more specific than *nothing happened*?

---

### Post by Stef11 on 2008-02-28
After entering my password i was brought back to the  terminal reading:
stefan@ stefan-desktop:-$
Regards
Stef11

---

### Post by JoshuaRL on 2008-02-28
What version of Ubuntu are you using?

---

### Post by aysiu on 2008-02-28
> **Stef11 said:**
> After entering my password i was brought back to the  terminal reading:
stefan@ stefan-desktop:-$
Regards
Stef11
Can you post the output of this command? ```
groups
```

---

### Post by Stef11 on 2008-02-28
stefan@stefan-desktop:~$ groups
stefan adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev
stefan@stefan-desktop:~$ 

Im am using xubunti
regards
STEF11

---

### Post by aysiu on 2008-02-28
> **Stef11 said:**
> stefan@stefan-desktop:~$ groups
stefan adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev
stefan@stefan-desktop:~$ 

Im am using xubunti
regards
STEF11
That's weird. You're in the *admin* group, so it shouldn't be a problem. Can you successfully run other *sudo* commands? Let's try this one, which will edit with a command-line text editor instead of a graphical text editor: ```
sudo nano -B /etc/modules
``` If that doesn't work, you may have to [boot into recovery mode to fix *sudo*](http://www.psychocats.net/ubuntu/sudo)

---

### Post by Stef11 on 2008-02-28
Yes i keep having to use: sudo modprobe ndiswrapper 
to load the kernel each time i boot.
I dont know wether it makes any difference, but this xubuntu was a light version provided by pcuser magazine. They removed alot of the blot, and included some of their prefered apps.
regards
stef11

---

### Post by aysiu on 2008-02-28
Oh, wait! I just thought of something. If you're using Xubuntu, then ```
gksudo **gedit** /etc/modules
``` is not going to work, as you probably don't have *gedit* installed.

The command you want is ```
gksudo **mousepad** /etc/modules
```

---

### Post by Stef11 on 2008-02-28
Thank you, that line worked.
The two lines read:
fuse
lp
  I added ndiswrapper under lp and saved
Now ill see if it worked.time to reboot
Many Many thanks for your time and help
regards
Stef11

---

### Post by Stef11 on 2008-02-28
Aysiu thankyou again, system rebooted. up popped the request for keyring phrase and away we go.All is working beatiufully.
Regards
Stef11

---

