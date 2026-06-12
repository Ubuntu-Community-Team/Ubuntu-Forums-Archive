---
title: "Running a utility on boot"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by Henry Rayker on 2006-09-23
I am trying to run a utility on startup, but one catch is, I want it to run as root.

I use a little utility called rutilt to configure my ralink chipset wireless cards and, in order to properly open it, I have to type

sudo rutilt

followed by my password. I also use this utility as my network manager, as the gnome network manager seems to break anytime I'm changing settings on my card (ie going from one network to another or anything like that). I would merely like for this utility to start at boot with root priveleges. I tried adding it to init.d and using the update-rc.d command, but it seemed to have no effect.

Any takers?

---

### Post by henriquemaia on 2006-09-24
Just add the command you want to run at boot to the rc.local file located at /etc.

An example:

```
sudo nano /etc/rc.local
```

You'll see (just add the command to it):

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

**add_your_command_here**

exit 0

---

### Post by Henry Rayker on 2006-09-24
I tried it, but with no luck. I tried both "rutilt" and "sudo rutilt" and got no response. It didn't start on boot or anything. =\

I can get it to start on boot if I add it to the sessions manager, but it asks for my password if I add "sudo rutilt" to the session manager. If I just add "rutilt" it doesn't really work (for one reason or another, I have to run it as sudo or I can't do anything...it asks for my password, but rejects it)

What would be nice would be to have a way to tell Ubuntu that I NEVER care if this is run with admin rights. I never want this particular utility to ask for my password, if possible. Then I could just add it to session manager like anything else. However, I figured running at boot would be the best I could get.

---

### Post by gazzanova on 2006-09-24
;) Thanks henriquemaia your solution works great, used the command line as you suggested and left out the /etc/rc.local part. This solved the problem of having to probe for the driver with the "sudo modprobe 3c509" command and then having to put up the eth0 with this command line sudo "ifconfig eth0 up"...so actually inserted 2 command lines in.

---

### Post by envisionthestorm on 2006-09-24
Thanks for this, was about to make a thread asking how to get my wi-fi on ndiswrapper going without having to type in the commands everytime lol... this worked a treat

---

### Post by Henry Rayker on 2006-09-24
am I the only one this didn't work for?

What exactly did you add to that script?

you then made the rc.local script executable by doing a 

```
chmod +x rc.local
``` right?

---

### Post by henriquemaia on 2006-09-24
You don't have to chmod rc.local. Whatever you add there is run on boot time. Maybe there's a tricky thing with the command you want to run, since it does not run at boot.

If you press  ctrl+alt+f8, what is the last message you have there? (if you have added the command to rc.local)

For example: on mine, I have added a command to synchonize my computer with my country's legal hour, a ntp server. So, i my case, I added to rc.local:

ntpdate ntp04.oal.ul.pt

This command can only be runned as root. After boot, I have this message:

* Running local boot scripts (/etc/rc.local)
24 sep 14:39:23 ntpdate[5086] step time server 194.117.9.136 offset bla bla

---

### Post by Henry Rayker on 2006-09-24
huh. The rc.local actually said to change the execution bits, so that's what I did.

As for the ctrl-alt-f8 output, it claims the command isn't found. Huh. I guess the links aren't created until after this script. I'll give it the full path and see if it works.

Alright, so now it just fails on open with
```
Gtk-WARNING **: cannot open display
```

I guess the utility will fail if it can't open the GUI..

---

### Post by henriquemaia on 2006-09-24
Yes, that's it. Isn't a way to run it only as a command line? You can try to detour that by making a big pause on rc.local and then running the command (i.e. when the X is already running).

For example

sleep N (where n is in seconds)
your_command_here

---

### Post by Henry Rayker on 2006-09-24
The problem is this utility should be running as an applet in my tray. I hate the idea of having to give my password twice (once to log on and once to allow sudo access to the utility) but if it comes to that, then I suppose it will.

I think the sessions manager should have a "run as root" check button. I'll try the pause thing in a little while. I'll get back to you on how it works out.

Still no dice. I set it for 15 seconds, thinking that had better be enough. I set it to 30, then 60, but even before waiting, I still get the same Gtk-WARNING stuff, so I don't even think it bothers to wait.

---

### Post by henriquemaia on 2006-09-24
> **Henry Rayker said:**
> The problem is this utility should be running as an applet in my tray. I hate the idea of having to give my password twice (once to log on and once to allow sudo access to the utility) but if it comes to that, then I suppose it will.

I think the sessions manager should have a "run as root" check button. I'll try the pause thing in a little while. I'll get back to you on how it works out.

Still no dice. I set it for 15 seconds, thinking that had better be enough. I set it to 30, then 60, but even before waiting, I still get the same Gtk-WARNING stuff, so I don't even think it bothers to wait.

Of course, my bad...

The problem is that it runs cuncurrently. Try this:

sleep n&&your_commmand_here

&& is used to wait for the conclusion of the first command before issueing the one that follows.

---

### Post by Henry Rayker on 2006-09-24
same response as without &&

I also tried adding it to the end of the rcS file, as I found on another page, but had no luck with that either. grrrr.

Well, for now, I've just added "sudo rutilt" to my sessions manager and I enter my password at boot....it sucks, but it's what works for now.

---

