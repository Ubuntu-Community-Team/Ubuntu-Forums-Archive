---
title: "install problems with ubuntu-5.10-install-powerpc.iso"
date: 2007-06-10
forum: Apple PPC Users
---

### Post by billGatesjr on 2007-06-10
Hello,

I'm a new Ubuntu convert attempting to install ubuntu-5.10-install-powerpc.iso onto an old bondi blue imac with a 233 Ghz processor. Everything goes along well enough during almost all stages of the install process up restart. When I restart and then login, a screen pops up that says:

"Cannot look up internet address for Ubuntudingle (my user name). This will prevent GNOME from operating correctly. It may be possible to correct this problem by adding Ubuntudingle to the file /etc/hosts."




When I click on "Log in Anyway" I hear music and bells, and then " " nothing happens, the button holds down and it just freezes. I left it over night and it doesn't move from that screen. I believe that the ethernet port is fried on this imac and I remember that during install it says that the DHCP is working, it can't locate a network or find the IP address for the computer. If I click on "Try Again," the button reacts but nothing happens.


I have a feeling I've messed up during the install process, does anyone have any advice?


Thanks.

---

### Post by luckyd on 2007-06-10
Why are you using such an old version of ubuntu? Try the alternative install for feisty and see if the problem is fixed.

---

### Post by billGatesjr on 2007-06-10
Where can I find the alternative install for feisty? 

I just thought I would try and older version of Ubuntu to install on a very old computer.

---

### Post by luckyd on 2007-06-11
Hope this helps, the alternative install image is about half way down the page. [http://cdimage.ubuntu.com/ports/releases/feisty/release/](http://cdimage.ubuntu.com/ports/releases/feisty/release/)

---

### Post by stmiller on 2007-06-11
> **billGatesjr said:**
> Where can I find the alternative install for feisty? 

I just thought I would try and older version of Ubuntu to install on a very old computer.

The opposite is true in Linux from the Windows/OS X world. Newer versions of Linux contain better support and better fixes for hardware. And runs more efficient, among other things.

---

### Post by billGatesjr on 2007-06-12
Yes, but, like any operating system, don't newer versions run more slowly on older computers? Especially with a 233Ghz processor with hardly any RAM? I figured I would be lucky just to get it working at all, but I'd love to have the latest version on there, believe me! 

So far, I've tried Ubuntu 5.10 and now the alternate version of Xubuntu 6.10 and it always gets to the same place, where after rebooting upon completion of the install, you login in and it just sits there. Not ready to give up quite yet though, definitely into making the switch.

---

### Post by tcrroadie on 2007-06-12
Are you still having problems with your network not working after installing 6.10?

After you log in and the machine appears to freeze try opening a virtual terminal with this key combination.  You can also open a virtual terminal before you log in at GDM. 

```
Ctrl+Alt+F2
```

Ctrl+Alt+F1 through F7 should bring up a command prompt.  Then you can can starting doing some diagnostic work to try and see what is causing your problem.  There are two logs you can look at to help give you some information as to why gnome is freezing. 

One is the gnome session log located in your home folder.  To view your log files, you can use the command line tool "less".  So at the command line prompt type 

```
less .xsession-errors
```

You may also want to take a look at the xserver log file.  

```
less /var/log/Xorg.0.log
```

The xsession error log is probably the file that will tell us what is happening.  

To restart GDM and the xserver you can run this command.  

```
sudo /etc/init.d/gdm restart
```

To see if your network card has recieved an IP address via DHCP, run

```
ifconfig
```

You may also want to view your running system processes to see if something is using all of your CPU clock cycles and holding you up.  Run the command top to view these processes.  Press q to exit top. 

```
top
```

Could you also list your system hardware specs? How much system RAM does your Mac have?  You can also use the command line to "lshw" to list what hardware is in your iMac.  

```
lshw
```

You may also want to try installing an alternative desktop environment such as Fluxbox to see if Fluxbox will come up for you.  

```
sudo aptitude install fluxbox
```

You may also want to try Feisty on your Mac.  You can download it here. 

[Feisty PPC Downloads]("http://cdimage.ubuntu.com/ports/releases/feisty/release/")

Hope this helps.  :)

---

### Post by billGatesjr on 2007-06-13
Thanks for the commands, I actually have tried installing Kubuntu and again, everything loads up fine or "OK" except "pbbuttonsd"   failed

The screen flashes, I see a little white "X" and then the blue Kubuntu progress bar appears, nothing happens for a while, then it says:


restarting system log    ok
restarting system log    ok


Also, is does Option=Alt? 


Thanks for your help, 

BGJr

---

### Post by billGatesjr on 2007-06-14
Just left Kubuntu on all night by accident, still at the second boot up screen, but it just says

Starting anac(h)ronistic cron: anacron        ok


I have a sneaking suspicion that, as I've heard from many places, you can't burn these CDs on a mac.

---

### Post by Auria on 2007-06-14
> Yes, but, like any operating system, don't newer versions run more slowly on older computers? 

Not Linux

Contrarly to other OSes Linux always leaves you choice. While OS X might for instance add new features like visual effects that require better hardware and that you can turn off, linux always lets you turn them off (or, often the other way around : they are not enabled by default)

> I have a sneaking suspicion that, as I've heard from many places, you can't burn these CDs on a mac.

You mean ubuntu install discs? Of course you can

you just need to check the checksum of the downlaod to make sure the download is correct, then burn it at low speeds (to make sure everything on the CD is okay)

sorry i can't help with your issues - hopefully someone that can will reply :)

---

### Post by ssam on 2007-06-15
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) has instructions for writing the install cds from various systems.

alt=option

how much RAM do you have. it is often more of a limiting factor than cpu speed. 256mb is about the minimum for running a graphical system. If you want to have several tabs open in a web browser, an email client, and a office document open at the same time, then you be better off with 512mb.

ubuntu is generally getting faster with each release. in gnome you can go to System->Administration->services and disable thing that you don't need to improve speed a bit.

If you want try running a lighter weight system have a read of [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) it wont be a pretty or friendly as a full ubuntu install, but will be faster.

---

### Post by billGatesjr on 2007-06-15
But, I've downloaded so many images, I can't believe all of them were faulty. Something's happening when I download these iso images, I just can't figure out what it is.

---

### Post by Auria on 2007-06-15
> **billGatesjr said:**
> But, I've downloaded so many images, I can't believe all of them were faulty. Something's happening when I download these iso images, I just can't figure out what it is.

did you do what we told you to do in the two previous posts?
please confirm you have done all the described steps, don't just repeat it doesn't work ;)

---

### Post by aantn on 2007-07-03
If I were you I would definitely try Xubuntu Feisty. Feisty will give you much better performance than an older version, and Xubuntu will give much better performance than Ubuntu or Kubuntu without losing (m)any features.

---

