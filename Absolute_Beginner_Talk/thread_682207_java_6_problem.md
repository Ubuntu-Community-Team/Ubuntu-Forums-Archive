---
title: "java 6 problem"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by prattage on 2008-01-29
when i try to open synaptic package manager it says that sun-jave6-bin needs to be reinstalled but it cant find an archive for it

---

### Post by emarkd on 2008-01-29
I think you'll have to enable the other repositories for that.  In Synaptic, click Settings > Repositories and check all of the boxes except Source.  Save it and click Reload on the main screen.  Then try your search again.

---

### Post by prattage on 2008-01-29
i cant even open it..the box pops up a bar fills up at the bottom and then the error shows up

---

### Post by emarkd on 2008-01-29
You mean Synaptic won't open?  If that's the case, it's a strange message.  Synaptic is certainly not written in java.

Either way, you can do the same thing from the terminal:

```
sudo apt-get install --reinstall sun-java6-bin
```

---

### Post by prattage on 2008-01-29
-----------------------------------------------
root@prattage-desktop:~# sudo apt-get install --reinstall sun-java6-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package sun-java6-bin needs to be reinstalled, but I can't find an archive for it.
----------------------------------------------
thats the message i got :(

---

### Post by FuturePilot on 2008-01-29
First try this
```
sudo dpkg --remove --force-remove-reinstreq sun-java6-bin
```
Then you can try to reinstall it
```
sudo apt-get install sun-java6-bin
```
If you get the license agreement hit Tab to highlight OK then hit Enter

---

### Post by prattage on 2008-01-29
thank you thank you thank you futurepilot this was getting very frusterating :)

---

### Post by FuturePilot on 2008-01-29
You're welcome :)

---

### Post by iansane on 2008-01-29
Had the same problem when I messed up a printer driver install. Synaptic, update manager, and apt-get will just keep saying that and not work till you can manually remove it. It has to have the archive to remove it if it's like my prob was. I had to edit script files and manually delete stuff to get synaptic to work again. Hope you find a way to remove it.

---

