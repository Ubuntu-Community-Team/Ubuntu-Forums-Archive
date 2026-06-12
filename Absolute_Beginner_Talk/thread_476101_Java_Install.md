---
title: "Java Install"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by gdon on 2007-06-16
Ever since I have put Ubuntu I have just been running the default applications because I don't know how to work the command prompt to install new programs. But now I need java installed so I cant wait anymore. Is there a tutorial on how to Install stuff? Because if there is I cant find it. Thanks
Gage

---

### Post by srt5 on 2007-06-16
If your using the GNOME desktop then there is a useful "Add/Remove" program located under the applications menu. Otherwise, find Synaptic package manager (in my opinion, it is the best) and look for 'sun-java6-jdk' in the list of packages. Note that you may need to include multiverse packages and refresh the list before it appears.

Don't be afraid of the terminal, a simple
```
sudo apt-get install sun-java6-jdk
``` would have exactly the same effect. If you feel more comfortable using the GUI then keep on using it :)

---

