---
title: "Brown Screen of Death??"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by trowa116 on 2007-04-05
Can anyone help me? I have the latest ubuntu 6.10 i386 and trying to install it on a voodoo envy machine. I get to the brown screen after choosing the first option and nothing happens, sometimes a empty white box will come up on the top left corner of the brown screen and make a noise but it stays there.

I tried doing the following from the top post "typing sudo dpkg-reconfigure xserver-xorg in the terminal" 
But all i got was a bunch of questions that i thought i answered to the best of my knowledge and after i install all of them it brought me back to the terminal, i then reboot the machine and same thing again.

Please if anyone can help i would really appreciate it....

---

### Post by Razorback on 2007-04-05
What video card are you using? What driver are you selecting in Xserver?

---

### Post by slimdog360 on 2007-04-05
brown screen??? first option??? Could you give us something more specific.

---

### Post by trowa116 on 2007-04-05
The brown screen i speak of is the one with the following options:
start or install ubuntu
start ubuntu in safe graphics mode(tried that)
check cd for defects
memory test
boot from first hard disk

and the ubuntu logo at the top

in the xserver i tried using the nv, ati, and vesa and none of which worked 
i know for a fact that the card in the system is an ATI card as for which model i dont know the specifics.

---

### Post by Patrick K on 2007-04-05
Did you check the cd for defects?

---

### Post by trowa116 on 2007-04-05
yea, tried every option possible

---

### Post by Patrick K on 2007-04-05
You tried the memory test, too, huh?

---

### Post by trowa116 on 2007-04-06
yea Im pretty sure it has something to do with possibly the video card drivers from other peoples post ive read on this issue

---

### Post by 3rdalbum on 2007-04-06
When you use the sudo dpkg-reconfigure xserver-xorg step, select Vesa as the video card driver.

After the program exits, type this onto the command-line:

```

sudo /etc/init.d/gdm restart

```

DON'T restart the computer; just type the above command. Restarting the computer erases everything in memory, which includes the changes you made in the program.

---

### Post by trowa116 on 2007-04-12
i tried that, but after typing it 
stopping GNOME display manager...               [ok]
starting GNOME display manager.....               [fail]

now what should i do?

update:
i tried, kubuntu and it works but not ubuntu
can i install ubuntu from kubuntu desktop?

---

### Post by FuriousLettuce on 2007-04-12
```

sudo apt-get install ubuntu-desktop

```
or if you think you may want to remove it at a later date, including unused dependencies:
```

sudo aptitude install ubuntu-desktop

```
Then you can choose whether you want GNOME or KDE from the session menu at the login screen. There's no guarantee that GNOME will work now that you have KDE working - you're likely to have the same issues, but at least you can diagnose from inside Kubuntu.

---

