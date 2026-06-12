---
title: "Stop Admin. password request"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by sundance2007 on 2007-12-03
I am the only one using the computer I have Ubuntu on and want to stop the constant requests for my admin password. How do I stop this, if the answer is login as admin. in the beginning of the session how do I make sure this is how I log in?

Thanks

---

### Post by LowSky on 2007-12-03
its there for your protection

if you want to do many things at once use this before typing commands

```
sudo -i
```

this way you only need to enter your password once, and it last as long as the terminal window is open

---

### Post by dimbulb1024 on 2007-12-03
Remember, if you are connected to the net and have no password on your root account, it is open to anyone who attacks your pc. Big security risk.
This is what makes Windows so inviting to virus', malware ect ....

---

### Post by st33med on 2007-12-03
It isn't THAT big of a security risk. There are other things that guards Ubuntu's files as well, like iptables and minimal ports. To do this:

```
sudo visudo
```

and add this at the end:

```
<user> ALL=(ALL) NOPASSWD: ALL
```
Where <user> is the user that you want to have no password pop-ups. If it gives you a warning, RECHECK THE FILE! If you mistype the file and exit and save, you will be locked out.

---

### Post by Paqman on 2007-12-03
> **sundance2007 said:**
> I am the only one using the computer

Actually, if you have an internet connection, you're not. Countless numbers of other machines and their users are able to connect to (and potentially manipulate) your computer.

---

### Post by Linc1 on 2007-12-03
Here is my problem. I went to the Samsung website and downloaded the driver for my printer. But when I try to install it, (double click on it after extracting the archive) it tells me that I don't have permission. I have tried all the things I have been told but I am not getting it. I need a step by step, I am , after all, very new to this.  I don't really understand the terminal window and what my commands options and requirements are. So anyone want to give a guy a break here?

---

### Post by st33med on 2007-12-03
> **Linc1 said:**
> Here is my problem. I went to the Samsung website and downloaded the driver for my printer. But when I try to install it, (double click on it after extracting the archive) it tells me that I don't have permission. I have tried all the things I have been told but I am not getting it. I need a step by step, I am , after all, very new to this.  I don't really understand the terminal window and what my commands options and requirements are. So anyone want to give a guy a break here?

Uh, first off, start another thread. There should be a button at the top left button in the Absolute Beginner forum to make a new one.

---

### Post by mikewhatever on 2007-12-03
> **Linc1 said:**
> Here is my problem. I went to the Samsung website and downloaded the driver for my printer. But when I try to install it, (double click on it after extracting the archive) it tells me that I don't have permission. I have tried all the things I have been told but I am not getting it. I need a step by step, I am , after all, very new to this.  I don't really understand the terminal window and what my commands options and requirements are. So anyone want to give a guy a break here?

Try alt+f2, gksudo nautilus, navigate to the driver file and double click. If it does not work, post a link to the site with installation instructions. You may need to do a bit more then double clicking to install a driver in linux.

---

### Post by Linc1 on 2007-12-03
Sorry, seemed like it fit this thread.

---

