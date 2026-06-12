---
title: "Compiler needed"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-04-10
I have been using g++ for quite some time. I need a IDE now that supports compilation (I tried ANJUTA but it doesn't have inbuilt compilation features). So in other words, I need a GUI for g++

Any help would be appreciated.

---

### Post by Trail on 2008-04-10
kdevelop?

---

### Post by Jussi Kukkonen on 2008-04-10
> **LinuxIsInnovation said:**
> I have been using g++ for quite some time. I need a IDE now that supports compilation (I tried ANJUTA but it doesn't have inbuilt compilation features). So in other words, I need a GUI for g++

Not sure what a "GUI for g++" means, but have you taken a look at the Anjuta plugins? 
[LIST]
[*]Autotools are supported, so you can just click "Build" (you'll need to do File->Add->Project first), 
[*]There is a debugger support with pretty good functionality, even Valgrind is supported, 
[*]With the "tools" plugin you can run anything you want (like g++ if you really don't use any kind of build system)
[/LIST]
What is the missing functionality?

---

### Post by m_atif on 2008-04-10
Considering that from GUI you mean some IDE wth gives you run/debug facility on mouse click.... I would second Trail.
kdevelop is good, something like VC 6.0 interface.
eclipse is also cool

---

### Post by mbeach on 2008-04-10
I'd also recommend Eclipse.
[http://www.ibm.com/developerworks/opensource/library/os-eclipse-stlcdt/](http://www.ibm.com/developerworks/opensource/library/os-eclipse-stlcdt/)

---

### Post by dlevans on 2008-04-18
i installed KDevelop ( 3.5.8 ) to develop for the PSP i installed the toolchain and i have programmed for C++ a few years ago in high school and i want to get back into it the only problem i have is i cant compile anything the build option is just "Stop" and its grey'd out i have no idea how to use KDevelop im not denying that if anyone could help me it would be great. also when i do a new program the window that everyone talks about isnt there (ive googled my heart out) i have included a screen shot of what im talking about and if anyone has installed the psp tool chain did you use kdevelop? all the tutorials said i needed was the toolchain they didnt say anything about KDevelop or any other programmer program

---

### Post by Trail on 2008-04-18
Try starting a new project instead of a new file. kdevelop builds projects (through autotools), not single files.

---

### Post by StOoZ on 2008-04-18
netbeans :guitar:

---

### Post by dlevans on 2008-04-18
wow im retarded thanks alot that worked but ... how do i make the psp apps? i have the toolchain installed but im not sure how to use it or how to incorporate it with KDevelop. but at least i can start coding again!! thanks again

---

### Post by LaRoza on 2008-04-18
See the sticky in the PT

[http://ubuntuforums.org/showthread.php?t=752224](http://ubuntuforums.org/showthread.php?t=752224)

---

### Post by sayakb on 2008-04-20
Would try eclipse. Netbeans is too heavy (I have it installed). I can't go for KDevelop since it would install all the KDE libraries (I am using Gnome)

---

### Post by sayakb on 2008-04-20
OMG OMG Eclipse needs 86.4MB download! We get daily 20MB upload+download (that sux).. have to wait until I go home :(
ANy lighter alternative?

---

