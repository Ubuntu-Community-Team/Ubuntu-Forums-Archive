---
title: "How do I edit /etc/hosts to add my name"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by peterS on 2006-03-20
Hi, this is from a total dunce and a newbie to Ubuntu..

Have installed Ubuntu on a couple of machines - one works OK but on the other, it will not log into Gnome correctly and has a missing host name.

having read a number of posts, I thought that I was on the right track..

I have tried logging on in the "Failsafe TERMINAL" mode, then logging on.. this brings up the terminal screen..

following that I enter "su" and my password... then I enter "nano /etc/hosts" which brings up the "hosts" file..

Following editing it to include my host, I then hit ^O...
the terminal then asks me if I want to save and I hit ^X at which point it tells me that I am not allowed to overwrite the file ...

How do I change the file to a write enabled file .... or what else do I have to do....

---

### Post by DCJoeDog on 2006-03-20
wouldn't it be something like

```
sudo gedit /etc/hosts
```

it should ask for your password and then it will open the editor

or something to that effect?

---

### Post by AtinLango on 2006-03-20
Yeah, just add sudo before the command, whether nano or gedit. This will give you permission to write to the file.

---

### Post by peterS on 2006-03-20
thanks guys, howeverr I cannot use "sudo" as at present I can't log into gnome...all I hace read says to go into "failsafe Terminal' mode and then use "xTerm" ....this gets me to the file but its read only....

---

### Post by DCJoeDog on 2006-03-21
shouldn't you have a "Recovery Mode" option when you boot up in GRUB?

pick that and that SHOULD take you to a prompt as root

---

### Post by peterS on 2006-03-21
Many thanks for the reminder to be in 'grub' ...Went into it from the boot up  and then did an 'echo' command to fill in the info ...and it works..

Can now go fully into gnome and successfully 'ping' the other machines (all Ubuntu) ....All I need to do now is to be able to connect to the other machines for file transfer etc... Back to the forums to see what I can find

The windows feeedom is getting closer  :p ... once I can get the connectivity the last window$ box gets upgrades to Ubuntu tooo... \\:D/

---

