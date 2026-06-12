---
title: "Unmounting a partition?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2007-04-22
Hi,
   I am trying to remove the hard drive icon that shows up on my desktop.  It's called "sda3" which is my other linux distro that is installed.  I want to remove the icon from the desktop.  I tried right clicking it, and selecting "unmount volume" 

When I do this, I get an error box that says " cannot unmount volume, umount : /media/sda3 disagrees with the fstab"

Any ideas?

---

### Post by bodhi.zazen on 2007-04-22
I am not sure this is a solution per se ....

Open a terminal. ```
sudo umount /media/sda3
```

If that does not get rid of the pesky icon, well I reboot and that seems to fix the problem.

From there we may need to adjust your fstab .... If you would like help with that do you then mind posting /etc/fstab ? Also, do you want the partition to automatically mount at boot ? If not, do you want users to be able to mount it or only root ?

---

### Post by jimbojambo on 2007-04-22
Go to System > Preferences > Main Menu. Here, highlight System Tools in the left pane, and check on "Configuration Editor" in the right pane. Now, that item will be added to Applications > System Tools. Open up the newly added Configuration Editor, then in the left pane navigate to apps > nautilus > desktop. In the right pane, uncheck "volumes_visible."

(From this same section, you can also do things like add the trash can to your desktop, a shortcut to your home folder, etc.)

Your other distro's volume will still show up under "Computer," and in /media.

---

### Post by 3rr0r on 2007-04-22
Sweet!  The sudo command worked and removed the icon.  I figured it might show up on reboot, so I added the config manager as stated and unchecked visible icons for mounted volumes.  Thanks to both of you :KS

---

