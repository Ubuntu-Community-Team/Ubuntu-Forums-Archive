---
title: "DVD tray of a powermac dual G5"
date: 2011-04-24
forum: Apple Hardware Users
---

### Post by cellarweasel on 2011-04-24
I have a PowerMac dual G5 2.5Ghz and it has a software controlled dvd tray. Does anyone else have the problem of having the tray open and then close right away? I have a non-official mac keyboard that I think might also be the problem. It is Kensington brand specifically for Macs, but the eject button doesn't work. I instead use the eject command but it's annoying because it retracts right after ejecting.

---

### Post by pauljwells on 2011-04-26
G5 Dual-core 2GHz Powermac, Apple keyboard. Exactly the same behaviour. I have an external USB DVD drive that I use for everything except booting, for which I have to boot in OSX just to open the tray!

So far as I know there's no fix. We are a tiny group of users I'm afraid.

Have you tried 11.04 yet? I'm looking for bug support, specifically on Unity-2D and the Nouveau 3D driver...

---

### Post by beringse on 2011-04-26
Same here, I've become quite familiar with the terminal command "eject". 
Still the same on 11.04, just installed a few minutes ago.

---

### Post by pauljwells on 2011-04-26
@beringse (and any other G5 users...)

If you could find the time to install the unity-2d packages and confirm this bug I'd be eternally grateful!

[https://bugs.launchpad.net/unity-2d/+bug/758782]("https://bugs.launchpad.net/unity-2d/+bug/758782")

Sorry for the thread hijack

---

### Post by teachop on 2011-04-26
Does this help anything with the eject issue:  Create a file /etc/sysctl.d/60-traystayopen.conf that contains...
```

dev.cdrom.autoclose = 0

```

And then reboot.

---

### Post by pauljwells on 2011-04-26
@teachop You beauty :-D

That worked for me!!

Karma++

---

### Post by tiresia on 2011-04-26
> **pauljwells said:**
> @teachop you beauty :-d

that worked for me!!

Karma++

+1

---

### Post by tstc on 2011-04-26
THANKYOU! While not a huge annoyance, this did take care of this stupid  little quirk. I CAN say that it worked for me on Maverick10.10, Natty, and Fedora 12 w/a little change!

Thanks again,
Tom

---

### Post by pauljwells on 2011-04-27
I added a custom keyboard shortcut and reassigned the eject keyboard key to it

```
eject -T
```

This now works just like in OSX :-D

---

### Post by winston99 on 2011-04-28
> **teachop said:**
> Does this help anything with the eject issue:  Create a file /etc/sysctl.d/60-traystayopen.conf that contains...
```

dev.cdrom.autoclose = 0

```And then reboot.

I just used my first terminal command.
Could you show me how to create that file?
Thanks

---

### Post by teachop on 2011-04-28
> **winston99 said:**
> Could you show me how to create that file?
Ok, get back into the Terminal command line utility, and please enter this command:
```
sudo gedit /etc/sysctl.d/60-traystayopen.conf
```
Enter your password if asked.  That should start the editor with permission to write to that system directory.  Then type in the text:
```
dev.cdrom.autoclose = 0
```
Do a save, exit the editor, and exit Terminal.  Then reboot.

---

### Post by winston99 on 2011-04-29
> **teachop said:**
> Ok, get back into the Terminal command line utility, and please enter this command:
```
sudo gedit /etc/sysctl.d/60-traystayopen.conf
```Enter your password if asked.  That should start the editor with permission to write to that system directory.  Then type in the text:
```
dev.cdrom.autoclose = 0
```Do a save, exit the editor, and exit Terminal.  Then reboot.

I couldn't make it  work in 2 attempts, 1st try with restart. 2nd try with shutdown, everthing went as you said but the eject key does'nt eject the tray.

When i open terminal "winston99@winston99-desktop:~$" is the command line and I added your instructions to that line, could this be the problem? Like do i need to get to an empty command line?
Thanx

---

### Post by teachop on 2011-04-29
The purpose of the dev.cdrom.autoclose = 0 is to keep the tray from closing on its own.  I do think there is a post above on how to assign a hotkey for the tray eject control, that may be what you need.

---

### Post by winston99 on 2011-04-30
@pauljwells,  could you show me how to add the keyboard shortcut, I can't do it from "keyboard shortcuts"

---

### Post by pauljwells on 2011-05-01
yes you can ;-)
you have to click 'Add' at the bottom of the window, then type in the command I posted earlier and give it a name (anything will do). This will then show up at the bottom of the list of shortcuts, you click on the key assignment on the right and press your eject key to select it.It will probably tell you that this will unassign the original eject command, that's ok.

---

### Post by winston99 on 2011-05-01
@paul,  yes i think thats going to work, I got to the unassign original earlier(before your instruction) and was afraid to pull the trigger.
Thanks for your help

---

### Post by pauljwells on 2011-05-07
Hmmm. Here's a weird one. DVDs and CDs will only mount if they are in the drive and I reboot! Only with 11.04, 10.10 worked properly...

---

