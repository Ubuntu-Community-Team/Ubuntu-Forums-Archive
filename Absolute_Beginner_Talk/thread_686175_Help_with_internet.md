---
title: "Help with internet"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by TekmonX on 2008-02-03
Hello everyone, I'm new to linux, and I've already got ubuntu up and running, but I can't figure out how to set up the internet. I'd really like for someone to help me out on this.

---

### Post by JoshuaRL on 2008-02-03
Are you trying to connect with a wireless card?  Or are you just trying to update the system?

---

### Post by TekmonX on 2008-02-03
> **JoshuaRL said:**
> Are you trying to connect with a wireless card?  Or are you just trying to update the system?

I'm trying to connect with a wireless card, and also update the system.

---

### Post by JoshuaRL on 2008-02-03
Okay.  Do you have the option to use a wired connection?  If so, I would suggest using that to update and *then* working on your wireless once you're sure you have an updated system.

If you try that, make sure you go to System->Preferences->Software Sources and make sure you have everything checked except for the CD and source code.  Then run Update Manager.

---

### Post by TekmonX on 2008-02-03
If your talking about through ehternet, then no... is there a way I could manually connect to a wireless network by getting an IP address and stuff like that?

---

### Post by JoshuaRL on 2008-02-03
No, it's pretty much the same way however you connect to a wireless connection.  I don't know much about wireless, but if you post your exact type then maybe someone could help with that.

---

### Post by TekmonX on 2008-02-03
I would do that in all, but, I don't know to to specify what type of card my wireless card is... although I did come across a program called wi-fi radar, and I'm not sure how to install it...

---

### Post by JoshuaRL on 2008-02-03
Try putting this into the terminal and posting the output:
```

lspci

```

---

### Post by TekmonX on 2008-02-03
It says somthing along the lines of "broadcom cooperation bcm4318 [airforce one 54g]" I bet that was my wireless card

---

### Post by JoshuaRL on 2008-02-03
I bet it is.  Put this into Google:

> 
site:ubuntuforums.org broadcom bcm4318 airforce one 54g


You might find some directions how people got theirs working.

---

### Post by LookTJ on 2008-02-03
> **TekmonX said:**
> It says somthing along the lines of "broadcom cooperation bcm4318 [airforce one 54g]" I bet that was my wireless cardWhile I have no experience with broadcom cards, but they aren't well supported on Linux.

You would probably need to install ndiswrapper: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

EDIT: More [info](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)

---

