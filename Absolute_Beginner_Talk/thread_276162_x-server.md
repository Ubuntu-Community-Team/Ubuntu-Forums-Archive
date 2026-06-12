---
title: "x-server"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by ballyhoo on 2006-10-12
mistakenly installed the wrong kernal.  uninstalled used the package mgr.  then deleted ref. in grub.  everything is ok from this mistake, i think.

i have been working on dual monitors.  got everything to work maybe and then rebooted after changing to 7 button mouse.

running 6.06/twinview-maybe configured right.

problem:  when i start up i receive an error about x server.  it then gives me a terminal looking interface.  what should i do now?
thanks

---

### Post by PriceChild on 2006-10-12
Have you installed nvidia drivers using a binary package from nvidia.com?

---

### Post by ballyhoo on 2006-10-12
yes-i believe so.  i followed a howto in doing so.

---

### Post by PriceChild on 2006-10-12
BTW i'm referring to [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_2](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_2)

Ok well log in... and do the following:
```
wget http://download.nvidia.com/XFree86/Linux-x86/1.0-8774/NVIDIA-Linux-x86-1.0-8774-pkg1.run
```or this for legacy:
```
http://download.nvidia.com/XFree86/Linux-x86/1.0-7184/NVIDIA-Linux-x86-1.0-7184-pkg1.run
```Then:
```
sudo sh NVIDIA-Linux-x86-1.0-8774-pkg1.run
or
sudo sh NVIDIA-Linux-x86-1.0-7184-pkg1.run
```Then ```
sudo /etc/init.d/gdm restart
```

---

### Post by ballyhoo on 2006-10-12
thanks i'll do so soon as i can log-in. or can that be done from the terminal looking screen after the x server error message?

---

### Post by PriceChild on 2006-10-12
press ctrl+alt+f1 to switch to somewhere you can log in.

---

### Post by ballyhoo on 2006-10-12
> **PriceChild said:**
> press ctrl+alt+f1 to switch to somewhere you can log in.

maybe i don't know what i'm doing--belay that--i know i don't know what i am doing.

when i boot up i receive an error message and then get dumped into a terminal interface with  login then user@user-desktop $

i tried to run the commands you suggested but i don't think it downloaded the file.

even when i switch users it will not load up.

---

### Post by ballyhoo on 2006-10-12
is it possible to just re-install 6.06.1?
i am really new to this and i wouldn't be out a lot of time.

---

### Post by ballyhoo on 2006-10-12
so, should i just re-install? or will i have to repartition everything again?  can i install in the partitions already set up?

---

### Post by ballyhoo on 2006-10-12
ok.  found this link that got me going [http://users.bigpond.net.au/hermanzone/p7.html]("http://users.bigpond.net.au/hermanzone/p7.html")

tried this on my laptop and it worked.  now the big test as i'll be  rebooting into ubuntu on this pc.  we'll see how it goes as this one has more customization. :-k

---

### Post by ballyhoo on 2006-10-13
cool it worked on the problems on my pc as we.  aslo, twinview on the pc. :D

---

