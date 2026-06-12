---
title: "Questions about command line and permissions"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by Rush_898 on 2006-09-05
I've been doing pretty good so far, but I can't figure this out even though I know it's probably 1+1 simple.  I have reduced my windows dependency down to so few programs that I decided to try the free vmware server route instead of dual boot.  I got the XP guest OS installed and running fine after installing vmware.  However, I need to resize the virtual drive that the virtual XP is on and to do that I must access the folder via command line.  The path:

/var/lib/vmware/Virtual Machines/Virtual XP/Virtual XP.vmfs


Now when I use the terminal I can cd down to /var/lib/vmware but if I try to open /var/lib/vmware/Virtual Machines by typing 'cd Virtual Machines' it tells me 'no such file or directory'.  Is this because the terminal cannot deal with the space in the directory name?  Now I tried to work around it by renaming the directories to have no spaces GUI style but I can't rename the Virtual Machines directory as it is root permission only and I cannot figure out how to change permission on a dir that the command line won't admit exists.  

All of the words to search an answer for this are so basic I get unrelated results, I am newb confused and not afraid to admit it.  Assistance needed, please.

---

### Post by x64Jimbo on 2006-09-05
try using tabbed completion to get the rest of the path
cd Virt -- and then hit the tab key. It should fill it in as necessary. What's needed is an escape character to tell the command line to ignore the spaces. It will come out looking like this:
cd Virtual\ Machines
Any command in that directory will need root to run, so be sure to run your resizing commands with 'sudo' in front of them.

---

