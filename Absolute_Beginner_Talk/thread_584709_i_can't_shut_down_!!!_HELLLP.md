---
title: "i can't shut down !!! HELLLP"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by thamood on 2007-10-21
Hi guys i have a problem which is "Ubuntu wont shutdown"!! whenever i press the shutdown button from the close dialog it logs off and then the gives me the ubuntu logo and the status bar completes the i can hear the HDD power off!! but everything else it's still working!! and it wont shut down i've waited but nothing seem to happen...anyone else having this problem?

I've read somewhere that i should add "acpi=force" to grub ... i did still nothing happens?

HELP!!!

---

### Post by alienexplorers on 2007-10-21
I tried the same thing adding acpi=force to menu.lst and it still does not work.

---

### Post by thamood on 2007-10-21
yes i even tried 

> acpi=force to menu.lst

still nothing worked...i tried to change the bios setting and it wont work? does it have something to do with the kernel???

---

### Post by sawjew on 2007-10-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/43961](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/43961) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have just encountered the same issue on my father's computer.  You should be able to power off the computer by holding the power button until it turns off, so the issue is not critical it's just an annoyance.  It appears to be a long standing problem, see the link above and you may find something to help.  If you continue to have issues you might want to post to the bug report.  If I find a solution I will post back here also.

---

### Post by holihue on 2007-10-21
unplug the power:)

Check the System>Administration>Login Window and the Edit Commands button in the bottom.


I don't think it will help, but when you solve the problem you can edit the shutdown command here...

---

### Post by genbuntu on 2007-10-21
or perhaps you may restart it (if it does that well) and then turn it off before it boots. However, this is a makeshift solution until the problem is solved.

---

### Post by alienexplorers on 2007-10-21
Tried several lines in the shutdown commands and still no luck.

---

### Post by thamood on 2007-10-22
same..i tried every command line compination still no luck..!! does the ubuntu team know about this?!!!

---

### Post by Sef on 2007-10-24
Have you gone into the BIOS and checked the power management settings?

---

### Post by jusmurph on 2007-10-24
I have an issue where when i click the shut down button in the menu (the one that brings up the dialog box). The system freezes and i have to pull the plug, though it happens only randomly.

---

### Post by Malta paul on 2007-10-24
It happened to me when I was checking the Eye candy displays. I did a ctrl,alt,backspace, logged in again and it then worked OK and I could shut down normal.:wink:

---

### Post by Hamnvik on 2007-10-27
Does the computer turn itself of if you run this command 
**Warning! Remember to save all open documents, this will shut down the computer!**
```
sudo shutdown -h now
```

---

### Post by markharding557 on 2007-10-27
> **thamood said:**
> Hi guys i have a problem which is "Ubuntu wont shutdown"!! whenever i press the shutdown button from the close dialog it logs off and then the gives me the ubuntu logo and the status bar completes the i can hear the HDD power off!! but everything else it's still working!! and it wont shut down i've waited but nothing seem to happen...anyone else having this problem?

I've read somewhere that i should add "acpi=force" to grub ... i did still nothing happens?

HELP!!!

have you tried halt or reboot from the command line?

---

### Post by umfaan on 2007-10-27
Hi - I'm a complete newbie, but here's a crack at what may be wrong. I have the same issue on an *old* generic box running 7.10... When starting up, I notice an message relating to ACPI and the BIOS cutoff date being prior to 2000 (i.e. 1999). I have a suspicion that this has something to do with the minor annoyance  of a shutdown not completely shutting off the box. Would like to hear from some experienced players as to what they think this is....

---

