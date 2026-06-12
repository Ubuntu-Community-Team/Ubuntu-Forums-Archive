---
title: "Root Password"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by dercoss on 2006-10-02
I've installed the latest version of Ubuntu and all is going well except when I try and install the drivers for a printer I get a message I don't have the privilege or whatever. I assume I need to login as the root user but the thing is I don't remember ever setting a root user password. 

Have I entered something without knowing it (I have tried various words that I may have used by accident) or am I going to have to reinstall??

dc

---

### Post by Qrk on 2006-10-02
Ubuntu uses sudo to gain root access. Whenever you want to use root, place a sudo in front of a command. The prompt asks you for your own password. 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by PPAAUULL on 2006-10-02
You can also change it so you have a root account but I do not recomend it. It is much safer to just use sudo.

---

### Post by dercoss on 2006-10-02
Thanks....

If i want to install my printer drivers that I have now on the desktop I have to type run the autorun routine. Could you tell me where I am going wrong with...

sudo ./cdroot/autorun where cdroot is the folder holding the printer software..

dc

---

### Post by era86 on 2006-10-02
try gksudo ./cdroot/autorun

---

### Post by dercoss on 2006-10-02
I just get command not found...

dc

---

### Post by bulldog on 2006-10-02
> **era86 said:**
> try gksudo ./cdroot/autorun

sudo should be enough,gksudo is used when you open a graphical application as root,not for a driver install.

If the driver is on your desktop you should do first ```
cd Desktop 
```

To get to your desktop.

---

### Post by taurus on 2006-10-02
> **dercoss said:**
> I just get command not found...

dc
Which one do you mean, gksudo or ./cdroot/autorun?  Are you really sure that "autorun" is in ./cdroot?

---

### Post by dercoss on 2006-10-02
command not found again...

dc

---

### Post by taurus on 2006-10-02
> **dercoss said:**
> command not found again...

dc

What command?  Are you talking about sudo?  Can you please try to explain a little more besides the "command not found..." thing?

---

### Post by bulldog on 2006-10-02
> **dercoss said:**
> command not found again...

dc

tell a little more about your driver..........is it for windows by any chance?

Don't let us pull the words out of your mouth please tell what you're doing :D

---

### Post by dercoss on 2006-10-02
Hold hard.. I've moved the folder to my home directory and the installation seems to be working now.

Thanks for the help...

dc

---

