---
title: "First thread in forum: Observations/Questions"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by Carl Haluss on 2007-02-18
Hey!
Just installed above distro on Averatec 1020 ed1, 10.6", Intel Celeron M ulv 373 1.1ghz, 512mb DDR333 RAM. Seems to be the ideal laptop for Linux, a bit dated but most everything runs smoothly. Having a bit of trouble getting used to the coding in Terminal, but with help managed to get Realtek wireless 802.11g recognized. I'm hooked up to internet via cable now, but installed Network Manager, and it does seem to read possible wireless connection in the vicinity.
Device Manager indicates that the Intel Graphics Controller 82852/82855 is up and running smoothly. The only thing is that on reboot/restart - sometimes - I get the following message on a black screen with blue script surround and red OK button: "Could not start the X Server (your graphical environment). Please contact your system administrator or check syslog to diagnose. Please start GDM when corrected."
At this point I have to hold down the power button for a few seconds and manually shut down the system. When I start it again, it boots up no problem. So I can always get around it that way, and get up and running.
Would appreciate any help in resolving though. I was wondering if doing a text install in Terminal might alleviate this problem? I'm new at the coding, although did manage to get it in bits and pieces when I installed wireless card driver.
My main objective with Linux is that, other than learning about it, I want a stable and dependable systme to take with me out of town, it doesn't have security issues, and hoping to use it at Internet Cafes etc. where WIFI is available. Does this seem like a reasonable thing at this point in time with the current Ubuntu distro?:) 
Thanks for any feedback,
Carl

---

### Post by jvc26 on 2007-02-19
Does the Xserver error message come up when you first boot up?
Il

---

### Post by meborc on 2007-02-19
when you get this message, you should be able to get to the terminal by hitting tab, and then enter... (there should be OK or YES or smth in the error page and hitting tab will highlight it... enter will do the obvious)

in terminal you could try

```
sudo dpkg-reconfigure xserver-xorg
```
to reconfigure your X as it most certanly has problems starting... why answering the questions chose the default values, if you don't know any better... after that you should be able to start your X with
```
startx
```

hope it helps...

---

### Post by Carl Haluss on 2007-02-20
message only seems to come up when I restart, not whet n first booting up.
Thanks, I will try those entries you mentioned. I am just starting to get used to Terminal.
I am really having a lot of fun with Linux Ubuntu. I have just set up my email, which did take a long
time. I also .got my wireless set up, it will recognize some networks nearby.
I am quite excited! I have a Mac, and another laptop with Windows Vista on it. Tnhis little laptop I have is only 10.6 in screen, but it seems perfect to run Linux. I really want to have a safe costable system that I can travel with, connect to Internet and get email while away, without having the security concerns of Windows.
Anyway, thank you for your replies and support.
Cheers,
Carl

---

