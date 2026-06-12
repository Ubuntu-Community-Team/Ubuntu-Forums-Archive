---
title: "Protecting again power Failures"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by JerryAtrik on 2007-05-09
In the official ubuntu book it gives a command to protect the O/S again power failure. As the Eastbourne area is somewhat prone to fairly frequent half hour breaks in service .I would like to cover this .
the book says 
foo@bar : ~ $ sudo gedit /etc/default/rcs 
or 
foo@bar : ~ $ sudo nano/etc/default/rcs

I have tried both but don`t get a response .Tried varying the gaps etc but no joy .
Could some kind person put it in correctly so I can cut and paste please
cheers Jerry

---

### Post by compmodder26 on 2007-05-09
Copy and paste this command:

```
gksudo gedit /etc/default/rcS
```

Notice the uppercase "S".  I think this was your original problem.

---

### Post by JerryAtrik on 2007-05-09
Compmodder,
I got the following message so looks as if I will have to wait for fix to bug


Defaults for the boot scripts in /etc/rcS.d.
#	This file originates from package initscripts.  Because of
#	bug #213907, it is not possible to tell this to dpkg.

---

### Post by compmodder26 on 2007-05-10
That shouldn't have anything to do with your problem.  That is just a message in the rcS file stating that a bug prevents dpkg from knowing where that file originated from.  

Just follow the instructions the book gave you.  BTW, what are the instructions?

---

### Post by JerryAtrik on 2007-05-11
Hi compmodder ,sorry about the delay replying .
The book says just put "=yes after FSCKFIX which your code brings up .So I thank you for your help
Cheers Jerry

---

### Post by JerryAtrik on 2007-05-11
This is the answer I got after keying in
gksudo gedit /etc/default/rcS




# Time files in /tmp are kept in days.
TMPTIME=0
# Set to yes if you want sulogin to be spawned on bootup
SULOGIN=no
# Set to no if you want to be able to login over telnet/rlogin
# before system startup is complete (as soon as inetd is started)
DELAYLOGIN=no
# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=no
# Set VERBOSE to "no" if you would like a more quiet bootup.
VERBOSE=no
# Set EDITMOTD to "no" if you don't want /etc/motd to be regenerated
# automatically
EDITMOTD=yes
# Set FSCKFIX to "yes" if you want to add "-y" to the fsck at startup.
FSCKFIX="yes"

as you can see I inserted =yes after FSCKFIX  clicked enter but nothing progressed what have I missed (tried password etc ) no joy 
can any one put me wise please
cheers Jerry

---

### Post by compmodder26 on 2007-05-11
That file you are editing is simply a text file.  After you change the text you needed to change simply choose File->Save.  Then close gedit.  You will probably need to reboot for the changes to take effect.

Unfortunately, I still don't know what you are trying to accomplish or what instructions you are trying to follow.  So I'm afraid I can't be of much help beyond what I've already told you.  Perhaps you can explain your situation a bit more.

---

### Post by Acksys on 2007-05-11
He just wants to bypass having to answer "yes" to fsck prompts when booting after a power failure.

---

### Post by compmodder26 on 2007-05-11
> He just wants to bypass having to answer "yes" to fsck prompts when booting after a power failure.

Okay, that makes more sense now.  

JerryAtrik, I noticed in the file you pasted above, you placed quotes (") for this line:

FSCKFIX="yes"

The other lines don't have quotes around yes.  Perhaps try switching it to:

FSCKFIX=yes

---

### Post by badbob100 on 2007-05-11
erm buy a UPS?

---

### Post by Acksys on 2007-05-11
> **badbob100 said:**
> erm buy a UPS?

Not in the spirit of invention, but probably not a bad idea in this case.

Newegg has some cheap ones:

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Description=ups&x=0&y=0]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Description=ups&x=0&y=0")

---

### Post by psusi on 2007-05-11
fsck doesn't run after a power failure with ext3, which ubuntu uses by default, so this change will do nothing.

---

