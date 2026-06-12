---
title: "resolution troubles"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by jcoggins on 2007-05-02
The maximum screen resolution I can get is 800x600 but I know my graphics card can do better then that (Geforce2).  I have used the synaptic package manager to update the drivers (the legacy edition) for my video card and I entered the command "sudo nvidia-glx-config enable" as instructed in the synaptic package manager but I still only have 800x600 resolution.

Does anyone have any suggestions for getting higher resolutions?

Jason

---

### Post by bobplano on 2007-05-02
try ```
sudo dpkg-reconfigure xserver-xorg
```
im guessing you haven't switched the drivers yet in your xorg.conf

---

### Post by overdrank on 2007-05-02
> **jcoggins said:**
> The maximum screen resolution I can get is 800x600 but I know my graphics card can do better then that (Geforce2).  I have used the synaptic package manager to update the drivers (the legacy edition) for my video card and I entered the command "sudo nvidia-glx-config enable" as instructed in the synaptic package manager but I still only have 800x600 resolution.

Does anyone have any suggestions for getting higher resolutions?

Jason

Hi you will have to reconfigure xorg  sudo dpkg-reconfigure xserver-xorg and follow the on screen prompts. Good luck !


Dang to slow LOL!

---

### Post by GrueTamer on 2007-05-02
You fix this by editing your /etc/X11/xorg.conf file.  I found a good place for some information, it's [here]("https://launchpad.net/ubuntu/+source/xorg/+bug/25079").

Hope that helps!

EDIT: wow, those are some helpful posts up there...man I should've posted faster :)

---

### Post by jcoggins on 2007-05-02
> **bobplano said:**
> try ```
sudo dpkg-reconfigure xserver-xorg
```
im guessing you haven't switched the drivers yet in your xorg.conf

I entered this code from a terminal and went through answering the questions to the best of my ability and it fixed the problem.

Thank you very much!

Jason

---

