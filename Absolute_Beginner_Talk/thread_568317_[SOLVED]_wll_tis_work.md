---
title: "[SOLVED] wll tis work?"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-10-05
currrently Gnome or GDM is refusing to load.
t just hangs, (another thread)

i was thinking of installing kubuntu-desktop through the TTY screen.

will this also fail to load?
or will it load up KDE?

if it does i can hopeflly sort ut my gnome from there

---

### Post by Jimmyfj on 2007-10-05
Did you try to reconfigure your xserver-xorg? Maybe the problem is in there? I don't thing that just installing KDE will solve the problem. Try:

dpkg-reconfigure xserver-xorg

---

### Post by skymera on 2007-10-05
yes yes yes i done 3 times.

gdm just hangs after login

---

### Post by useResa on 2007-10-05
IMHO this should work since you will be installing the entire KDE desktop. You can find clear instructions on how to install KDE at [psychocats]("http://www.psychocats.net/ubuntu/kde").

I have also read [your other thread]("http://ubuntuforums.org/showthread.php?t=567472"), have you tried reinstalling the GNOME desktop? If you removed something essential AFAIK it should be reinstalled and as such be fixed.

---

### Post by skymera on 2007-10-05
yeah i tried

apt-get install gdm

i dont know what else to try tbo.

id ratyhe rtry to get gnome working rather than install lots of KDE stuff i rreally dont wantr

---

### Post by Pumalite on 2007-10-05
Can you explain the situation better? When did it happened? What where you doing before this happened? Is this the end of an installation process?

---

### Post by Jimmyfj on 2007-10-05
Found this on launchpad - Maybe this can help you out

[https://bugs.launchpad.net/ubuntu/+bug/89022](https://bugs.launchpad.net/ubuntu/+bug/89022)

---

### Post by skymera on 2007-10-05
its been installed 6 months.
happened yesterday when i restarted

might have removed something critical. raed other thread for more detail.

what commands would i need to do to reinstall the WHOLE gnome environment? or at least the core stuff to get it working

---

### Post by Jimmyfj on 2007-10-05
Try:

apt-get install ubuntu-desktop

---

### Post by useResa on 2007-10-05
I would try the following command
```
sudo apt-get update && sudo apt-get install --reinstall gnome-desktop-environment
```

Of course if you are root the sudo is not required.

---

### Post by Pumalite on 2007-10-05
I agree with the others that this is not such a simple problem. Nevertheless, have you tried:
sudo apt-get ubuntu-desktop

---

### Post by skymera on 2007-10-05
i'll try them now :)

i give the results of this after.

---

### Post by skymera on 2007-10-05
whoah it loaded!
after a 15minute delay!

heres the error message:

---

### Post by Pumalite on 2007-10-05
Reboot and see what happens.

---

### Post by skymera on 2007-10-05
ok i will

---

### Post by skymera on 2007-10-05
ok no it takes ages.

and my Services isnt loading.
which is annoying.

---

### Post by Pumalite on 2007-10-05
Looks like saving data and a re-install, unless somebody comes up with a better answer.

---

### Post by skymera on 2007-10-05
if i treinstall, i wait till gutsy.

any ideas?

heres the error again:

---

### Post by Pumalite on 2007-10-05
Waiting for Gutsy in ten days is a good idea.

---

### Post by skymera on 2007-10-05
im hvaing slow system responses. really slow.

on interfaces. /etc/network/interfaces

i edited out lo

is it needed? im googling and people said its needed.

---

### Post by skymera on 2007-10-05
haha! fixed!!:D:D:D:D:D:D

turned out to be becuase  hashed out Lo from interfaces. doh!

thanks man for you support and help.
and al the others from the other thread, philinux etc.

guys, DO NOT # OUT LO! :wink:

---

