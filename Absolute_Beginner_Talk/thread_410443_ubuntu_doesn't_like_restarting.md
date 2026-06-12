---
title: "ubuntu doesn't like restarting"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by bobplano on 2007-04-15
everything has been going fine in the few weeks i've had ubuntu. i've set up my wireless adapter and gotten it to where I only need windows seldomly, but I have this little annoyance with restarting ubuntu and booting back into it for when I update the programs and kernel and stuff. I choose restart from the menu and it powers down just fine. when it tries to boot back up, it hangs up on setting up the network. I'm assuming this is because i'm using wireless. is there anyway to fix this or will i just have to turn off and turn back on?

---

### Post by juantovarm on 2007-04-15
what happens if you type this in the terminal:

sudo shutdown -r now

---

### Post by bobplano on 2007-04-15
still hangs up at configuring network interfaces. it's not how it restarts, it seems it *is* that it restarts

---

### Post by houstonbofh on 2007-04-15
What kind of wireless?  Can you pop it out during reboot and see if it comes up without it?

---

### Post by bobplano on 2007-04-15
yep it boots when the wireless adapter is unplugged. I'd still like to know why it doesn't boot with it in but at least i know i can restart.

---

