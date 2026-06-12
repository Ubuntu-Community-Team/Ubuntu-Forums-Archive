---
title: "Remove Xubuntu"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by Poffe on 2006-09-07
Hi

I have installed a Ubuntu LAMP-server and then I installed xubuntu-desktop. But now I what to remove Xubuntu-desktop and install Ubuntu-desktop instead because I am allitle more familiar with that.

So how do I do that? And is there a way to only install the GUI and not all programs like OpenOffice and all that, dont need that on a server.

Thanks in advance!

---

### Post by taurus on 2006-09-07
```

sudo aptitude update
sudo aptitude remove xubuntu-desktop
sudo aptitude install ubuntu-desktop

```

---

### Post by Poffe on 2006-09-07
Okej I'v done that now but Xubuntu is still here. I hade to choose Gnome when I started the computer.

But mabye this dosent affect the performace?

And also is there a smooth way to remove all applications that gets installed with the desktop like OpenOffice, Gimp and things like that. I am only going to use it as a server and dont ned all that.

Thanks!

---

### Post by taurus on 2006-09-07
You can use "sudo aptitude remove <package>" if you want to remove something on your machine...

```
sudo aptitude remove gimp
```

---

### Post by Rui Pais on 2006-09-07
Hi, 
xubuntu-desktop and ubuntu-desktop are just meta-packages. 
They don't install anything, just define a list of apps they should be installed to get a full Xubuntu or Ubuntu desktop. 
When removed they don't remove those apps only the reference to them selfs. You have to do the cleaning by hand. 
Try:
```
aptitude show xubuntu-desktop
```
 and choose check the xfce packages. You can check too by doing:
```
aptitude show xubuntu-desktop | grep xf
```

You can uninstall any (even all apps) suggested by xubuntu-desktop as long as you then do another
```
sudo aptitude ubuntu-desktop
```
in order to recover any really need dependency or app removed by error.

hope that helps.

---

