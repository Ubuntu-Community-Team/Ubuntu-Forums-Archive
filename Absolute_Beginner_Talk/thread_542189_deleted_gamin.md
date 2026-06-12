---
title: "deleted gamin?"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by vendetta23 on 2007-09-03
today i was uninstalling gaim using:

dpkg --get-selection

then using:

sudo remove yadayadayada

the 3 packages that looked like gaim programs were gaim, gaim-data, and gamin

so i deleted those three and during the process, i saw the xterm was deleting things such as desktop. then i realized i deleted gamin. so i was ctrl + z to abbort and rebooted. i logged in fine after the reboot, but the problem was i coudlnt even see my desktop. the only thing i saw was my mouse. is there a way to get back gamin?

---

### Post by splintercellguy on 2007-09-03
I'm not sure how removing gamin would have screwed up your desktop, but to reinstall it:

sudo apt-get install gamin

The ubuntu-desktop package is simply a metapackage, removing it will not harm your system.

---

### Post by wormser on 2007-09-03
It sounds like you need to get to a shell to download gaim with apt-get.  Press Ctrl+Alt+F2 to get to a prompt.  Then you can install gaim again.

[/code]sudo apt-get install gamin[/code]

To get back to the desktop press Press Ctrl+Alt+F7 but you might have to reboot.

```
sudo reboot
```

---

### Post by vendetta23 on 2007-09-03
thanks guys

ill try it and see if it works

---

### Post by vendetta23 on 2007-09-03
uhhh

it doesnt work

i typed the command in and rebooted, but my desktop still wont show up... just the arrow

i typed the command in after i rebooted, and it says gamin is already the latest version. help please? D:

---

### Post by wormser on 2007-09-03
Sounds like you really boinked your system.  Try installing ubuntu-desktop.  It should install the dependences that sounded like got uninstalled.  Try installing it first but you might need to remove it to install.

```
sudo aptitude install ubuntu-desktop
```

---

### Post by vendetta23 on 2007-09-03
i think ur code was the solution
its taking 4 mins ti reinstall... so ill see after it finishes

---

### Post by vendetta23 on 2007-09-03
yes!

it works now!

thank you SO much

---

### Post by wormser on 2007-09-03
Great!  Now mark you thread as resolved so when somebody else is looking to solve this problem they can find the answer here.  It is also good practice to put the resolution in your post confirming what worked.

---

