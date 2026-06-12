---
title: "New install: desktop not appearing"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by smyles on 2006-09-21
Hello,

I've just done my first Ubuntu install on a Toshiba Portege 3490CT laptop [PIII] which I wiped Windows off. I had to use the PXE netboot to install it because it can't boot from CD. This went fine and pulled down the files over the network.

The machine now boots fine and takes you to the login screen. When I enter the username and password it takes me to a pretty brown screen and a mouse cursor which I can move around with an external usb mouse or the laptop pointer. However, it goes no further - I've left it on overnight to check. The expected menu bar and icons don't appear. I can press <ctrl>+<alt>+F1 to get a console up and tried looking in some of the log files in /var/log/ to look for error messages but can't find any that look like problem.

I wonder if I could ask someone to help me diagnose what the problem is likely to be and where I should start looking?

---

### Post by shoot2kill on 2006-09-21
i am not sure.. but in console try

```

sudo aptitude update
sudo aptitude install kubuntu-desktop

```

this will install the KDE version of the desktop, but it will do no harm to see if this works, whilst u get a response from somebody else...

also try same with ubuntu-desktop...

just a thought...

---

### Post by smyles on 2006-09-21
The install ubuntu-desktop did the trick. I imagine what must have happened was the network install only installed the base system.

Thank-you very much for your prompt help! :KS

---

