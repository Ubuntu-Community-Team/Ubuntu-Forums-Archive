---
title: "Help with ubuntu on a apple g3"
date: 2010-09-04
forum: Apple Hardware Users
---

### Post by Chipmunkor on 2010-09-04
I have a grey slotloading imac g3 and when i try to install ubuntu from the Lucid Desktop PowerPC it boots and comes up with a command line saying welcome to ubuntu and then welcome to yaboot. it says if you are not sure just press enter so i did that and it says
"Please wait, loading kernel ..."
"read failed"

Anyone know what i have done wrong??? :?:

I really want to get ubuntu working on it:D

---

### Post by Chipmunkor on 2010-09-04
OK Randomly I kept trying and then suddenly it worked and no more kernel errors,
but when i press enter to boot into live cd it stays at the bootup screen and then it just has a black screen and i have to turn it off by holding the power button down

---

### Post by Chipmunkor on 2010-09-04
OK Randomly I kept trying and then suddenly it worked and no more kernel errors,
but when i press enter to boot into live cd it stays at the bootup screen and then it just has a black screen and i have to turn it off by holding the power button down

Update: Net install didnt work + after trying the normal install again same blank screen but after a few minutes i hear the startup sound

---

### Post by ayenack on 2010-09-04
I'd go for the alternate CD if I were you.

[http://cdimage.ubuntu.com/ports/daily/current/](http://cdimage.ubuntu.com/ports/daily/current/)

I'd also install xubuntu-desktop to make the system a little more responsive.

[B]sudo apt-get update
sudo apt-get install xubuntu-desktop[/B]

---

### Post by Chipmunkor on 2010-09-04
Will try that now.):P

---

### Post by Chipmunkor on 2010-09-04
I tried the alternate install but it says the files are corrupted and fails to download and replace them. What am I doing wrong:popcorn:

---

### Post by linuxopjemac on 2010-09-05
Go for Debian. These old systems are no longer well supported by Ubuntu.

[http://mac.linux.be/content/mint-lxde-debian-lenny-ppc](http://mac.linux.be/content/mint-lxde-debian-lenny-ppc)

---

### Post by ayenack on 2010-09-05
Check the CD for defects if the it says you have a good copy then it may be your CD ROM Drive is not working 100%.

Other than that you could try Debian (as linuxopjemac suggested). It's a little harder to get your head around but worth the effort.

[http://www.debian.org/ports/powerpc/](http://www.debian.org/ports/powerpc/) (For info.)

[http://www.debian.org/CD/http-ftp/](http://www.debian.org/CD/http-ftp/) (For download.)

---

### Post by Chipmunkor on 2010-09-06
I will try burning the alternate install again and see if that works otherwise i will try debian.

Update: Ubuntu now says that no kernel modules were found

Update 2: Debian will not boot it has flashing finder/questionmark so what should i do?

---

### Post by ayenack on 2010-09-06
Not sure what else you can do now. Seems you may have some issues with the CD ROM Drive or system.

You could try to install a server then add a desktop to it.

[http://cdimage.ubuntu.com/ports/releases/10.04/release/](http://cdimage.ubuntu.com/ports/releases/10.04/release/)

Then.

**sudo apt-get install ubuntu-desktop** (For standard Ubuntu Desktop.)
or

**sudo apt-get install xubuntu-desktop** (For the slightly lighter Xubuntu Desktop.)

Worth a try. Just a note you'll need an working wired network connection for this.

There's also the minimal install which might work.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Older version so you'd have to do an update.

---

### Post by linuxopjemac on 2010-09-06
Do a netinstall. Use the link I gave you.

---

### Post by Chipmunkor on 2010-09-08
Trying 1 more time with a new disc and new download no errors yet, u to select and install software. :popcorn:

Edit: Install Succeeded

---

### Post by ronnielsen1 on 2010-09-08
[http://powerpup.yi.org/](http://powerpup.yi.org/)

There's a puppy linux beta I'm going to try on a G3. I haven't done it yet

---

### Post by Chipmunkor on 2010-09-09
OK Finally install was successful :p 
BUT!! when i start up the boot screen comes up loading and then a black screen and i can get into console with CTRL + ALT + F1 and as it says [here]("https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen") but my xorg.conf file s blank any ideas??? Sooo Soooo Close :p

---

### Post by linuxopjemac on 2010-09-09
What is your computer, give me the link in everymac.com pls.

---

### Post by Chipmunkor on 2010-09-09
Think its this one:

[http://www.everymac.com/systems/apple/imac/stats/imac_600_graphite.html](http://www.everymac.com/systems/apple/imac/stats/imac_600_graphite.html)

---

### Post by linuxopjemac on 2010-09-09
As you already did once, after booting up, go to tty1 with CTRL-ALT-F1.

Login with your username and do the following:
```

wget http://mac.linux.be/files/xorg/imac7.txt
sudo mv imac7.txt /etc/X11/xorg.conf
sudo reboot
```

Hopefully what works.

---

### Post by Chipmunkor on 2010-09-09
It just says that it is not connected to the internet and i was in the installation (I have an airport wireless card.

Is there any way i can use my usb to move it to the xorg file/folder?

---

### Post by linuxopjemac on 2010-09-10
Use a wired connection. You can also put it on  a stick. Just download it to the stick from another computer and move it to the place I gave you.

---

### Post by techgrl on 2010-09-10
My Squeeze install went wonderfully. Smooth. BUT...BUT, upon first launch I have a display issue. I can see a very pixel-filled bottom white bar where the taskbar should be, but that is where it freezes.

Perhaps Squeeze will be a good slim option for you. I am convinced that it will be a success for me if I can edit the display settings!

Good luck!

---

### Post by linuxopjemac on 2010-09-10
techgirl: which Mac are you using? (everymac.com)

---

### Post by Chipmunkor on 2010-09-10
Sorry, but i'm new to linux and am not sure how i access the stick through console in ubuntu, i have it on my usb stick right here ;)

---

### Post by linuxopjemac on 2010-09-11
You have to find out the name of the device. Put the USB stick in your Mac and give me the output of either:

```
sudo fdisk /dev/sda
```
en then "p" and then "q" for exit

or

```
sudo fdisk /dev/sdb
```

or

```
sudo fdisk /dev/hda
```

or

```
sudo fdisk /dev/hdb
```

---

