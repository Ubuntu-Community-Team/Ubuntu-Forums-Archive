---
title: "Xubuntu and DellDimension 2200 - Where's the desktop?"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by pHreaksYcle on 2008-02-02
This desktop computer really sucks. It had Gutsy on it but was disgustingly slow so I am now trying to replace it with Xubuntu. I used a minimal alternate install disc that downloads the system files using a wired internet connection, there were no issues at all. The system apparently installed but does not bring me to the Xubuntu desktop, just the CLI. It shows the boot messages and then shows the preface for a command instead of actually loading a desktop. I did make sure I selected that I wanted the Xubuntu desktop installed when I used said disc so that is not the issue, in fact it was the only thing I installed. Any help with how to make it get to a GUI would be great because CLI isn't going to cut it for me :P

---

### Post by Rocket2DMn on 2008-02-02
What happens if you login and run
```
startx
```

---

### Post by pHreaksYcle on 2008-02-03
Well, it said I needed to install the package xinit (i think it was) I installed it and the command still wouldn't run. I will try reinstalling, obviously something went very wrong which is to be expected with something so dated. Thank you for that command though, I knew it was something that simple but I could not come up with what it would be.

---

### Post by Rocket2DMn on 2008-02-03
Plug into a wired network so you have web access and run
```
sudo apt-get install xubuntu-desktop
```
It sounds like to GUI stuff wasn't installed, so this should get you rolling.  Otherwise you need to reinstall and make sure you select to install the GUI.

---

