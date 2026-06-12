---
title: "Installing UT2004 Ubuntu 7.10, destination folder problem"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by nymlord on 2008-02-08
Hello, 
i have already been able to access the ut2004 installation, thats not the problem. 
the problem occurs when it asks me for the destination folder, as in, where i want 
to install the game to. example C:\ etc... but since its ubuntu i dont have C:\ folder,
so i tried changing the folder name with GPrename, but it wont let me rename the folder, so how would I do this ? 

thank you in advance :popcorn:

---

### Post by The Cog on 2008-02-08
I installed my UT2004 in /opt/ut2004. That way, all users can play it. Of course, you need to run the installer with root priviledge to have permission to write there, so I ran the installer after running the command "sudo -s" to get a # prompt.

---

### Post by nymlord on 2008-02-08
i guess ill just show u a picture so u can actually see what happens. :)

[[IMG]http://img230.imageshack.us/img230/3461/screenshotos5.th.png[/IMG]](http://img230.imageshack.us/my.php?image=screenshotos5.png)

---

### Post by Ac_David on 2008-02-08
You need to make sure you are executing the install script as root, otherwise you will not have access to the default /usr/local/games folder

---

### Post by nymlord on 2008-02-08
and how do i run a file as root ? sorry i just went to ubuntu from vista.. 
i got to terminal and, wine (folder destination.exe) and then it just runs the installation, what am i supposed to write to run it as root ? :S

---

### Post by The Cog on 2008-02-08
Don't try and use the windows installer in wine. You won't get any 3D acceleration and it will really suck. You need to install with the Linux installer.

Also. when you copied the destination folder, you managed to copy and paste the leading space and the trailing period. Oops.

Read this thread:
[http://ubuntuforums.org/showthread.php?t=190531](http://ubuntuforums.org/showthread.php?t=190531)

---

### Post by nymlord on 2008-02-08
well there is one problem, what do i do if its an iso file extraced with an .exe file ? there is no linux compatible folder :S

---

