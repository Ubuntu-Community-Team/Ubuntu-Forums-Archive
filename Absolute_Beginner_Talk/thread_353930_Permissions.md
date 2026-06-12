---
title: "Permissions"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by thompa on 2007-02-05
Hi there,

I have been messing with permissions trying to get my Ubuntu 6.06 computer to show on my network... and seem to have really messed things up!

When I boot, the message:-

'Users $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writable by others'

is displayed.

Can I reset all of my permissions to the way they were when I installed with a simple command line?.... or is there another way to remove the message?

What is a .dmrc file? I can't find one!

thanks in anticipation.

Allan

---

### Post by taurus on 2007-02-05
Boot into recovery mode from GRUB menu and at the prompt, do

```
chown -R **allan**:**allan** /home/**allan**
chmod 644 /home/**allan**/.dmrc
```
(assuming **allan** is your login name...)

Reboot and see if you can log in again.

```
shutdown -r now
```

p.s.  And please be careful with the permissions next time.

---

### Post by apjone on 2007-02-05
You try to create the file yourself

```

touch .dmrc
chmod 644 .dmrc
chown user .dmrc

```

---

### Post by kebes on 2007-02-05
The file in question: $HOME/.dmrc can be found here:
/home/thompa/.dmrc

The alias $HOME refers to your home directory (I'm just guessing that your username on your computer is "thmopa"). Note that the file is ".dmrc", and the fact that it starts with a dot means that it is a hidden file. On a commandline if you go:
ls -laF

You will see normal files and hidden files. Then you can change the permissions on that file by going:
sudo chown thompa:thompa .dmrc
sudo chmod 644 .dmrc

(Again I'm using "thmopa" as the example for the username, but you should substitute your actual username.)

Similarly you can use "chown" and "chmod" to fix the permissions on other files that have been affected.

---

