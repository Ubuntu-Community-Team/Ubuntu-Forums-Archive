---
title: "Picasa"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by ibizatunes on 2008-02-05
I need to changed to the permission on the files for picasa 
chmod 666 /dev/nvidia0 / dev/nvidiactl

i have run the commands in the terminal, and the permission change but after a reboot the permission change back to non read write.......

Is there any way of force the permission changes to save?
Basically i installed in (it had this error), then a friend she installed picasa via wines, and now i cant get the linux version to save the permission chances!
I have unistalled, the wines version and the linux version and reinstall, ran the permission modification command countless time and still doesnt work! 
Now am getting really annoyed with it!!

Any help, any ideas?

---

### Post by FuturePilot on 2008-02-05
What exactly isn't working? You shouldn't need to be changing permissions on devices for Picassa

---

### Post by ibizatunes on 2008-02-05
Picasa can get a error when running for the first time, so u do need to change permission if you dont have a NVIDIA card, my sister laptop, i had 2 run this command....... (Intel graphics card) i fixed it in 2sec, but because they install wines version i think that has co*ked it all up
So its picasa that doesnt run

---

### Post by ibizatunes on 2008-02-05
# chmod 666 /dev/nvidia0
# chmod 666 /dev/nvidiactl

These command work, well fine until i reboot the computer so is there any way of save the settings

---

### Post by ibizatunes on 2008-02-06
Is a rebuild of the machine the only way of correcting permission problems

---

### Post by FuturePilot on 2008-02-06
I'm not sure but I've heard you need to add yourself to the Video group. You can try by going System&#8594;Administration&#8594;Users and Groups. Click Manage Groups. Find the Video group and click Properties. Add your username to the group. You'll have to logout and back in to update your groups.

---

