---
title: "8800 GT video card problems"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by alarson82 on 2008-02-21
HELP PLEASE!!!

I have an 8800 GT video card by nvidia and i've read and tried a lot of stuff thats been posted here but I guess I need more help.

I tried running Envy however when I open it up it says this 

"Error: Dependency is not satisfiable: xserver-xorg-dev"

and i can't install package.

When Ubuntu loads i get the "Ubuntu is running in low graphics mode" warning and my screen resolution can not be set higher than 800x600.

help please!!

---

### Post by ryanhaigh on 2008-02-21
I think this page [http://packages.ubuntu.com/gutsy/xserver-xorg-dev](http://packages.ubuntu.com/gutsy/xserver-xorg-dev) suggests that you would need the security repos available to install the package envy is after, have you enabled security update repos?

---

### Post by alarson82 on 2008-02-21
I don't believe I have.  Since when i installed ubuntu the other day i did not have an internet connection.

---

### Post by alarson82 on 2008-02-21
after running xserver-xorg-dev_1.3.0.0.dfsg-12ubuntu8.3_i386  I try to install envy again

and now my error message is this

"Error: Dependency is not satisfiable: module-assistant"

Ahh the fun of learning Linux!

---

### Post by Cresho on 2008-02-21
Im posting my notes on how I install my drivers and run them.  Just remember if ubuntu updates your drivers, you will loose your desktop access but its simple to restore as long as you have the nvidia run file in your home in your username directory(easy access).

new
on 32bit ubuntu


install dev tools in terminal before proceeding.

1. fix software sources "Download from" usa to main server.  update the resources.  It is in Administration->Software Sources.
2. sudo apt-get install automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev checkinstall libglade2-dev xserver-xorg-dev
3. uninstall in synaptic nvidia kernel common.  Do a search. apply the changes before exiting synaptic
4. download the driver from nvidia  [http://www.nvnews.net/vbulletin/showthread.php?t=102509](http://www.nvnews.net/vbulletin/showthread.php?t=102509) or from here(updated drivers) [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
5. log out of ubuntu after download is finished
6. hit ctrl+alt+F1
7. log into your username at the prompt in terminal
8. then in terminal cd /home/yourusername/Desktop or your directory where it got downloaded to which is your cd /home/username
9. ls (just to see if your in the right directory where you downloaded the file in firefox)
10. sudo /etc/init.d/gdm stop
11. sudo sh NVIDIA-Linux-x86-169.04-pkg1.run (ignore the question or say no to kernel download during instal and have nvidia xconfig update the x)
12. "sudo reboot" in the terminal
13. add startup file to system->preference->sessions "nvidia-settings --load-config-only"
14. color correction is under system tools->nvidia x server settings. 1.240 for gamma correction under "x server color correction contrast  4096 sync to vblank"
15. sudo gedit /etc/X11/xorg.conf and add this line to it.

add this to this section "Option         "NoLogo" "true""

------------------example----------------------------
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option         "NoLogo" "true"
EndSection

16. test in terminal glxgears

---

### Post by ryanhaigh on 2008-02-21
You should just enable the security repos, im not at my ubuntu box at the moment but i believe you can do it through System>Administration>Synaptic Package Manager. Don't forget to refresh afterwards and then try the envy install script again. 

Trust me when I say you don't want to go manually downloading each package, fortunately in this regard ubuntu!=windows. Every time you try to install something it will likely have a dependancy you just need to have the right repositories enabled and those dependancies will be installed automatically, so just enable the repos and run envy again.

---

### Post by alarson82 on 2008-02-21
Thanks guys, once i got everything updated  I was able to run Envy, and everything works.

I greatly appreciate the help! thanks again!

---

