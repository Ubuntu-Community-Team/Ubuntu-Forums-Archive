---
title: "Remove Xbuntu desktop"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Bigbird999 on 2007-11-03
Like the title says.  I loaded the Xbuntu desktop package on top of Gnome to see if it would make this old P3 497 MHz laptop run better.  So far it doesn't and I much prefer Gnome.  I don't know if it a case of me being "Too new to Ubuntu", a borked installation or something else, but since i installed Xbuntu, my laptop won't properly wake up from standby and I am presented with too many options for my newb brain,  so I want to remove the Xbuntu desktop.  I also have a bunch of newb issues with understanding the whole two desktops thing and I don't know which programs are Xbuntu and which are Gnome or if it even matters.

I know I could just do a fresh install of Ubuntu but that means revisiting the whole ndiswrapper wireless issue again, so I prefer to keep a fresh install as my fallback.  

I made an image of the Ubuntu partition, using Acronis TI, but that was after I installed Xbuntu.  Which leads to another question - is there similar disk imaging software that runs in the Ubuntu GUI?  Can somebody help out this newb??

BB

---

### Post by rickycodie on 2007-11-03
sudo apt-get autoremove --purge xfce-desktop

---

### Post by Bigbird999 on 2007-11-03
Thanks for the quick reply.  I got this
```
ernie@LinuxLaptop:~$ sudo apt-get autoremove --purge xfce-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xfce-desktop

```

BTW, I couldn't find it either.  

Next step??

BB

---

### Post by Maestro23 on 2007-11-03
> **Bigbird999 said:**
> Thanks for the quick reply.  I got this
```
ernie@LinuxLaptop:~$ sudo apt-get autoremove --purge xfce-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xfce-desktop

```

BTW, I couldn't find it either.  

Next step??

BB

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Dr Small on 2007-11-03
Edit:
Maestro23's link was better

---

### Post by Bigbird999 on 2007-11-03
Thanks, that seemed to do it, it also uninstalled Amarak, which I had installed but that's no biggie, I'm reinstalling it now.

>  Getting Back to a Pure Gnome on Ubuntu

If you used aptitude to install other desktop environments, you will not need this tutorial, as you can just type
sudo aptitude remove kubuntu-desktop
or
sudo aptitude remove xubuntu-desktop
to get back to your "pure Gnome."

If you didn't have as much foresight and chose instead to install KDE or XFCE through Synaptic or apt-get, this is how to remove those desktop environments from your Gnome. 

So does this mean that one should use aptitude to install stuff, or just desktops or it doesn't matter??

Thanks for the great help

BB

---

### Post by -grubby on 2007-11-03
```
sudo apt-get remove xubuntu-desktop
```

---

### Post by Maestro23 on 2007-11-03
> **Bigbird999 said:**
> Thanks, that seemed to do it, it also uninstalled Amarak, which I had installed but that's no biggie, I'm reinstalling it now.



So does this mean that one should use aptitude to install stuff, or just desktops or it doesn't matter??

Thanks for the great help

BB

Apt-Get vs. Aptitude: [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by niceguy123 on 2007-11-19
I'm running xbuntu on my laptop and Ubuntu on my PC.

 I'd rather have the Ubuntu Gnome desktop on the laptop. 

Can/How do I change the desktop environment?

---

### Post by natehatewindows on 2007-11-19
> I'm running xbuntu on my laptop and Ubuntu on my PC.

I'd rather have the Ubuntu Gnome desktop on the laptop.

Can/How do I change the desktop environment?




[http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu)

---

### Post by niceguy123 on 2007-11-19
> **natehatewindows said:**
> [http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu)


Thanks for the link. Could you be a little more exact as to where I can find a tutorial to change desktop on xbuntu.

---

