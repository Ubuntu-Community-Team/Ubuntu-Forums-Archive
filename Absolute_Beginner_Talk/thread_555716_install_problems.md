---
title: "install problems"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by briantowner on 2007-09-20
ok,, so here's my problem, I installed ubuntu 7.04 x64 on my rig and it worked really well.  i'm a absolute begginer and i was getting updates and stuff.  all was going well until i got automatix and i installed nvidia drivers and a few other things and restarted and now when it restarts and starts to load the monitor goes black and says disconneted. here are my specs.
amd64 x2 6000+
2 gigs of ram ddr2
nvidia geforce 8600gt
gigabyte mobo nforce 570

---

### Post by skyjacker on 2007-09-20
> **briantowner said:**
> ok,, so here's my problem, I installed ubuntu 7.04 x64 on my rig and it worked really well.  i'm a absolute begginer and i was getting updates and stuff.  all was going well until i got automatix and i installed nvidia drivers and a few other things and restarted and now when it restarts and starts to load the monitor goes black and says disconneted. here are my specs.
amd64 x2 6000+
2 gigs of ram ddr2
nvidia geforce 8600gt
gigabyte mobo nforce 570
I can't help you with this , but can advise you that from all I have read in this forum, Automatix is NOT for Ubuntu. read this [http://digg.com/linux_unix/Automatix_Is_Actively_Dangerous_to_Systems](http://digg.com/linux_unix/Automatix_Is_Actively_Dangerous_to_Systems), and you can find more by googling "automatix" Good Luck!!

---

### Post by w4ett on 2007-09-20
Disregarding any additional issues, let's get you back to your desktop.

I'd start by reconfiguring your xorg.conf.....boot into recovery mode.

From the command line type:


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Red"]"vesa"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:


```
startx
```

This should  get you to a GUI desktop.

There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

---

