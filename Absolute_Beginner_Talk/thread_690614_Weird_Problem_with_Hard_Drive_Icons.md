---
title: "Weird Problem with Hard Drive Icons"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by stropyboy11 on 2008-02-07
I am actually very lucky to have a computer with great Ubuntu compatibility. My webcam, microphone, and standby works. However, I have one rather odd recurring problem that I want to fix. When I first installed my Ubuntu, I had two desktop icons--one that was SDA1 (my Windows partition), and the other being my Ubuntu partition. Now, more times then not, they just randomly don't show up. Does anyone know how to fix this?

-Stropko

---

### Post by zarqoon on 2008-02-07
On my systems desktop icons only appear for drives that are not mounted in /etc/fstab but are done so via the automounter. Like when you put in a cdrom it will appear. My Ntfs drives only appear on the desktop once i clicked them in nihilus to make them mount.
If for some reason your ntfs drive gets automounted at boot it may show up there. The only reason i can think of for the ntfs drive not showing is that windows did not shutdown clean the last time you used it and therefore the partition is marked dirty and you have to boot and shutdown windows again or force the mount manually.
I've no idea why the ubuntu partition would show on the desktop or why you would want it to but you can of course just add a launcher that opens the respective places.
Right click on the desktop -> add launcher -> type=location -> fill in name and folder you want to open and voila this wont dissapear

---

### Post by stropyboy11 on 2008-02-07
I'll definitely give that a shot...thanks for your help!

-Stropko

---

