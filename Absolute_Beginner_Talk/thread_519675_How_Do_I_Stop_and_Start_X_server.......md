---
title: "How Do I Stop and Start X server......"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by old_dog on 2007-08-07
I am trying to install geForce 7300 drivers on feisty fawn amd 64 using NVIDIA-Linux-x86_64-100.14.11-pkg2.run.
the "run" file tells me I have x server running so into terminal, sudo init 3 whole screen changes and I have to log in again  looks good, I run the  run file again tells me I have x server running much swearing sudo init 5 Nothing! My only way out power off at the mains.
Any advice re installing the drivers etc would be welcome as I am a new user and trying to find my way......
Cheers old_dog

---

### Post by Inxsible on 2007-08-07
you would probably need to go into CLI mode and then install the drivers.

You can go into CLI by hitting Ctrl + Alt + F2 (i think). Navigate to the directory where you have the run file and then follow the instructions give to you in that file

---

### Post by stingx on 2007-08-07
I see you trying to kill X in the mandriva way. In ubuntu, you kill server by "sudo killall gdm" (or "sudo killall kdm" for kubuntu)

---

### Post by mcduck on 2007-08-07
The correct way to do this is "sudo /etc.init.d/gdm stop". And to start it again, use "sudo /etc/init.d/gdm start".

You have to do this from VTT, you can switch between VTTs with Ctrl-Alt-F1 to F6, and Ctrl-Alt-F7 brings you back to graphical desktop.

---

### Post by old_dog on 2007-08-07
Thanks Guys....
After a couple of stumbles all tickety-boo
Cheers old_dog

---

