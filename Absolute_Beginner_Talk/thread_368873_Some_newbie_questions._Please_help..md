---
title: "Some newbie questions. Please help."
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by kevCast on 2007-02-23
#1: Why is it that when I try to install the Wine repo in apt sources, it doesn't work? [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

#2: How do you make windows transparent?

#3: When I install a theme that isn't default to Ubuntu, the window list at the bottom is square and clunky, circa Windows 95. Why doesn't all of the theme apply?

#4: What's the best way to get WiFi up and running in Ubuntu?

Any and all help is appreciated, thank you.

---

### Post by 23meg on 2007-02-23
> #1: Why is it that when I try to install the Wine repo in apt sources, it doesn't work? [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)Impossible to tell without knowing the exact errors you're getting.

> #2: How do you make windows transparent?You need a compositing manager such as xcompmgr, or a window manager that also does compositing, namely Beryl or Compiz.

> #3: When I install a theme that isn't default to Ubuntu, the window list at the bottom is square and clunky, circa Windows 95. Why doesn't all of the theme apply?If everything else looks ugly too, you probably don't have the theme engine needed. With what themes have you had this problem?

> #4: What's the best way to get WiFi up and running in Ubuntu?Depends on your hardware.

---

### Post by kevCast on 2007-02-23
> Impossible to tell without knowing the exact errors you're getting.
It doesn't recognize the line in apt src list.

> You need a compositing manager such as xcompmgr, or a window manager that also does compositing, namely Beryl or Compiz.
Isn't there a way to get psuedo-transparency in gnome?

> If everything else looks ugly too, you probably don't have the theme engine needed. With what themes have you had this problem?
[http://www.deviantart.com/deviation/28688856/](http://www.deviantart.com/deviation/28688856/)
[http://www.deviantart.com/deviation/32765755/](http://www.deviantart.com/deviation/32765755/)
[http://www.deviantart.com/deviation/32162210/](http://www.deviantart.com/deviation/32162210/)

> Depends on your hardware.
[http://www0.dealtime.com/xPF-CPQ-SR1230NX-Desktop-CPQ-SR1230NX-Desktop](http://www0.dealtime.com/xPF-CPQ-SR1230NX-Desktop-CPQ-SR1230NX-Desktop)

---

### Post by 23meg on 2007-02-23
> It doesn't recognize the line in apt src list.Post the contents of your sources.list.

> Isn't there a way to get psuedo-transparency in gnome?Only with certain apps, such as gnome-terminal.
> 
[http://www.deviantart.com/deviation/28688856/](http://www.deviantart.com/deviation/28688856/)
[http://www.deviantart.com/deviation/32765755/](http://www.deviantart.com/deviation/32765755/)
[http://www.deviantart.com/deviation/32162210/](http://www.deviantart.com/deviation/32162210/)See if installing the package *gtk2-engines-pixbuf* fixes it.

> [http://www0.dealtime.com/xPF-CPQ-SR1...1230NX-Desktop](http://www0.dealtime.com/xPF-CPQ-SR1...1230NX-Desktop)I don't see a wireless networking component in that setup.

---

### Post by kevCast on 2007-02-23
> Post the contents of your sources.list.
```

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse


## E17 repository "edevelop.org"
deb http://edevelop.org/pkg-e/ubuntu edgy e17
deb-src http://edevelop.org/pkg-e/ubuntu edgy e17

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list -O /etc/apt/sources.list.d/winehq.list

```
It's the last line.

> Only with certain apps, such as gnome-terminal.
Isn't that the standard one? If it is, I have it.

> See if installing the package *gtk2-engines-pixbuf* fixes it.
It did, thank you.

> I don't see a wireless networking component in that setup.
There isn't one built in to the mobo, but I do have a Linksys WiFi USB plugin in thing that's supposed to connect to my wireless modem.

---

### Post by 23meg on 2007-02-23
> It's the last line.

You need to enter that last line in your sources.list as a command in the terminal, not add it directly to your sources.list. Remove it, save the file, do "sudo apt-get update" and enter it as a command.

> Isn't that the standard one? If it is, I have it.

Yes. You can adjust the pseudo-transparency setting in your gnome-terminal profile. Right click anywhere in the terminal and choose "Edit Current Profile" and go to the "Effects" tab.

> There isn't one built in to the mobo, but I do have a Linksys WiFi USB plugin in thing that's supposed to connect to my wireless modem.

I don't have experience with those devices, but if you do a forum search, you'll most likely find something useful. To get accurate results, enter the exact model of the device, which you can find in System / Administration / Device Manager if it's detected.

---

### Post by kevCast on 2007-02-23
In the device manager, is there anyway I can activate the device? Or does it just show what's plugged into my computer?

---

### Post by 23meg on 2007-02-24
It just shows a list of what's recognized. Do you see your device there?

---

### Post by kevCast on 2007-02-24
> **23meg said:**
> It just shows a list of what's recognized. Do you see your device there?
Yes, I do.

---

### Post by 23meg on 2007-02-24
> **kevCast said:**
> Yes, I do.

What's the exact model? Is it recognized and configurable in System / Administration / Networking and/or in Network Manager?

---

### Post by mdsmedia on 2007-02-24
> **23meg said:**
> 
Yes. You can adjust the pseudo-transparency setting in your gnome-terminal profile. Right click anywhere in the terminal and choose "Edit Current Profile" and go to the "Effects" tab.
 That is so cool!! I had no idea you could make the terminal transparent too.

I've had Ice60's gorgeous avatar as my desktop background for a while now, and now I can see bits of her while at the command line too :redface:

---

### Post by kevCast on 2007-02-25
> **23meg said:**
> What's the exact model? Is it recognized and configurable in System / Administration / Networking and/or in Network Manager?
Linksys Wireless G-USB adaptor with Speedbooster. In Networking it only recognizes the standard wired and modem.

---

### Post by 23meg on 2007-02-25
> **kevCast said:**
> Linksys Wireless G-USB adaptor with Speedbooster. In Networking it only recognizes the standard wired and modem.

Do a forum search to see if there's a known way of getting it to work. If there doesn't seem to be, start a thread with the name of the device in its title to get help about it.

---

### Post by kevCast on 2007-02-27
I have one more question:  How do I install gtk engines?

Thank you 23meg, you've been a great help.

---

