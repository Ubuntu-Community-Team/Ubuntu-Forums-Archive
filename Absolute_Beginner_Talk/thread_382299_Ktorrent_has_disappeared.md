---
title: "Ktorrent has disappeared"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by icanoe2 on 2007-03-11
I am new to Ubuntu/Linux so please be easy on me.

I love Ubuntu so far and it is much easier to use than any other distro which I have tried. I have done a dual boot install with XP (for the kids games) and everything went well. The only problem which I have encountered is with Ktorrent. I installed it and have been downloading some bittorrent files and everything worked well unit.... The program crashed a few times and now I am not able to re-start it again. I click on the application and wait..... but nothing happens. I tried un-installing and re-installing Ktorrent from the add/remove programs menu but I still get the same results. After one of the last crashes I noticed that my internet connection was also gone. See next.

I noticed that the last two times the program crashed my router also experienced some problems. This Linksys wireless router has never given me trouble over the six months that I have owned it and to think it is causing the problem is doubtful in my mind. The machine with Ubuntu installed is hard wired to this router. After power cycling the router my internet connection works again but there is no change with the Ktorrent problem.

Thanks in advance.

icanoe2

---

### Post by x64Jimbo on 2007-03-11
Ktorrent may be crashed and still in memory. If this is the case, since Linux typically prevents you from running multiple instances of the same program, it will try to open the currently running instance, which is probably frozen. You have two options. Either reboot (simple) or run the following command:
sudo killall ktorrent
Then try running it again.

---

### Post by icanoe2 on 2007-03-11
I tried re-booting (I have many years of Windoze experience) but this did not help the situation. Since then I have re-started the computer many tmes and still the problem is the same.

---

### Post by x64Jimbo on 2007-03-12
do you get any errors when you launch it from the command line?

---

### Post by userundefine on 2007-03-12
Try deleting your ~/.kde/share/apps/ktorrent directory and any tor* directories you have in your torrent output folder.

---

