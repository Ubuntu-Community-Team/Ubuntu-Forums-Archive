---
title: "Linux Display Driver - x86"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by Fathom on 2007-10-05
I just downloaded Linux Display Driver - x86 for my GeForce 8600 GT card. It's a .run file. When I open it, it opens with "gedit" I think it is. It says: "Could not open the file/home/josh/Desktop/NVIDI…ux-x86-100.14.09-pkg1.run." - "gedit has not been able to detect the character coding. Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."

What am I doing wrong?

---

### Post by FuturePilot on 2007-10-05
I would recommend using Envy. It will make life a whole lot easier.
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")
Just make note that after a kernel update you will have to reinstall the driver with Envy though a terminal
```
sudo envy -t
```

---

### Post by Fathom on 2007-10-05
> **FuturePilot said:**
> I would recommend using Envy. It will make life a whole lot easier.
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")
Just make note that after a kernel update you will have to reinstall the driver with Envy though a terminal
```
sudo envy -t
```
Thanks, I'll try it out.

---

