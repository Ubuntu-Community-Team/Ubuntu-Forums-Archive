---
title: "kde and gnome"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by vinceUUUU on 2008-04-06
Hello forum people,

Please forgive my lack of know how about Linux.

Please can you tell me how desktop environments affect what linux tools you can use? 

i have Ubuntu 7.04 fiesty with the Gnome desktop.

What happens if i want to use a linux tool that mentions that it is linked with KDE and KDE library's?

the tool i want to use is a gui interface the Alien tool.

the tool mentions that it requires both Alien and Kommander.

when i read about Kommander...it states that kommander is linked to KDE and KDE library's...

so does this mean the gui tool won't work under gnome?

thanks

Vince.

---

### Post by philinux on 2008-04-06
Just go ahead and install - no problems other than some kde libs get installed.

---

### Post by yrohinkumar on 2008-04-06
I have kde 4 tar.gz files ... i want to install them on my hardy alpha6... my net connection is verrry slow... i have cmake also tar.gz files... but don't know how to go about... please help...

---

### Post by atomkarinca on 2008-04-06
There's probably a file called "INSTALL" in that archive. Most of the time there are three steps. Open the terminal and browse into the extracted directory and type these:

```
./configure
make
sudo make install
```

---

### Post by Mazza558 on 2008-04-06
If you install kde (or any kde app), Ubuntu downloads the kde libraries, allowing you to run kde programs on gnome with no problems. If you like kde and start using that all the time, you can freely use gnome applications (although they won't look as good as on gnome itself).

---

