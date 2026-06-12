---
title: "Few questions about KDE/Ubuntu"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2006-10-11
I have an older computer, it has little ram and I think I heard someone saying that KDE is better for older computers? Is this true, also, if I switch to KDE with the terminal command line, will I still have all my programs that I myself installed, I know the ones that are default to Ubuntu Gnome wont be there, KDE has its own default programs but will like, Mozilla-Thunderbird still be on it and aMSN?

---

### Post by aldegaz on 2006-10-11
If you have Ubuntu installed on this PC why would youlike to make the switch. I think you imply you have Ubuntu installed already.

Either way, the "light" version of ubuntu would be Xubuntu not Kubuntu, and I am not sure if you would be able to keep your programs.

---

### Post by aysiu on 2006-10-11
KDE is not better for older computers than Gnome. In fact, many here will contend that Gnome is faster than KDE (obviously depends on your hardware and software setups... and biases).

If you have an older computer, use XFCE... or IceWM or Fluxbox.

---

### Post by LorenXo on 2006-10-11
As far as I'm aware, for lower end computers, KDE is no better than Gnome. You could try XFCE (Xubuntu) which is probably more suitable. If you're changing from Gnome you will keep all of your currently installed programs. If it's a new install, all of the programs available for Ubuntu are availabe for Xubuntu. To install XFCE, type ```
sudo apt-get install xubuntu-desktop
```

---

### Post by aysiu on 2006-10-11
I think it'd be a good idea to use *aptitude* to install Xubuntu: ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
``` Makes it easier to remove later, in case the OP prefers Fluxbox or IceWM or Windowmaker or Sawfish...

---

### Post by Naegling23 on 2006-10-11
KDE and gnome are about the same speed wise.  I think kde happens to be a little bit faster, but not by much.  People like kde for the shiny eye candy, and gnome for the simplicity and lack of clutter.

Its in the eye of the beholder.

I prefer kde even though they name all the programs ksomething which is annoying.

---

### Post by aysiu on 2006-10-11
I think most of the time when people talk about KDE or Gnome being faster, the comparisons are not like to like... or there's too much variability in circumstances. For example, *kde-core* is much faster than *kubuntu-desktop*, but both are KDE.

In any event, older computers should not use either. XFCE or IceWM are good alternatives to check out.

---

