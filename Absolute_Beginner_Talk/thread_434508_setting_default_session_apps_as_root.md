---
title: "setting default session apps as root"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Limitlesschannels on 2007-05-06
Hi,
When setting an app to run at startup (system/preferences/sessions/startup programs...) does that run as root? if not, how can I get something to initialize as root?
in the case of myself, I am trying to run the command:
```
 sudo /etc/init.d/fsfn start 
```

to get my sony Fn Keys running.  But it uses sudo, which needs a password prompt, which wouldn't be provided were it to attempt to run at startup.  what can i do?

---

### Post by igknighted on 2007-05-06
> **Limitlesschannels said:**
> Hi,
When setting an app to run at startup (system/preferences/sessions/startup programs...) does that run as root? if not, how can I get something to initialize as root?
in the case of myself, I am trying to run the command:
```
 sudo /etc/init.d/fsfn start 
```

to get my sony Fn Keys running.  But it uses sudo, which needs a password prompt, which wouldn't be provided were it to attempt to run at startup.  what can i do?

Unfortunately no, it will not run as root automatically.  It will probably ask you for your sudo password.  You might even need to make it gksudo because there wont be a terminal there to run in.

You can change your start-up scripts to run that at system boot, not login.  I would check whatever guide you are using to enable that.  I would help with this but am not sure how.

---

### Post by Limitlesschannels on 2007-05-06
how does gksudo work? i have never really knew.  In the case of checking the guide, it is for fedora (but hey, you are a fedora user, maybe you know what to do) so i don't really know the transition very well, i kind of had to wing it to figure out the variations for the ubuntu file system.  anyway, here is the guide if you are interested in looking.  
How would it "prompt me for a password still" if it is running as that startup script?  would a terminal pop up? i assumed it would just bypass the command and not work since i have it enabled just to run those at startup.

---

### Post by Tundro Walker on 2007-05-06
I'm thinking you could try using "sysv-rc-conf" to see if "fsfn" shows up as a service in the list that you can start.

"Sysv-rc-conf" is a services configuration utility which you use via command-line.  It doesn't come installed by default, so you'll need to apt-get it or use Synaptic to get it...

```
sudo apt-get sysv-rc-conf
```

 Once you have it, start it up with...

```
sudo sysv-rc-conf
```

It'll display a list of services that you can set to run at different user levels...
[LIST]
[*]1,2,3,4,5,0,6,S[/LIST]As far as I know, it displays all the services / files in "init.d" folder, so fsfn should show up and let you flag which run levels to run it as.  In general, I think Ubuntu uses run level 2 for most things, so start with that, and it should auto-load for all users to use.

I may be off on this, though.

I've read a few other posts about folks trying to get extra services they installed to run, and I think they may have had to "register" it or something first.  Essentially, you run some command that tells your system to add that service to the boot-up sequence.  I'm really hazy on this, though.

---

