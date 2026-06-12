---
title: "I broke Gnome!!!"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by online14230 on 2006-10-04
Good Aftermorning People,
Seems I have a knack for breaking things, the latest victim being Gnome. Here a small howto:
1. DONT have any net connection on the Dapper box, so download packages from the repositories by browsing through them using WinXP on another PC (at work).
2. Download the package you want, and all its depends, and all the depends depends, and keep going till you have them ALL.
3. Be an idiot and install Addon CD for Hoary because all you want is multimedia capability, and wine.
4. Copy all your downloaded debs to the desktop, and "sudo dpkg -i *.deb"
Wait for the machine to tell you that most of the debs have dependency problems. Look stupid as, when you reboot, all you see is a text login prompt, which works with your normal login.


I know, I broke it. The question remains though: How do I fix it?

Please dont flame me and call me stupid. I KNOW I did something wrong. (It all started 4 years ago, when I started collecting MP3 discs). I know I messed up and I know that some of you are gonna laugh at the simplicity of fixing it - Right now, all I need is my hand held (Ill be seeing my wife in 8 hours time, she does a good job of holding my hand, among other things :wicked snicker:), a coke, and a solution to the problem.

Oh yeah, I dont mind ANYONE helping!!

Have a Luuurrrrvly day!

---

### Post by dcaonbireal on 2006-10-04
thanks that helped me

---

### Post by hyper_ch on 2006-10-04
when you are at the text login, login as usual and the type:

```

startx

```

Maybe that helps :)

---

### Post by online14230 on 2006-10-04
Oh sorry, I forgot to mention that "startx" dont work.

---

### Post by online14230 on 2006-10-04
HRRRUMMMFFF!
I REALLY beginning to hate this Gnome thing. I re-installed. Rebooted. Started up fine. Sorted out sources.list and apt-get update blah blah blah...
Fired up synaptic. Installed a few apps, including wine, w32 codecs (Thanks MIKE!!!), and additional codecs... I fixed DMA and all was good. I shutdown and tried to startup. No Gnome. I give up. I think...
Maybe I should just try the 200GB HDD Ive been saving...

---

### Post by Crooksey on 2006-10-04
sudo dpkg -reconfigure xorg
sudo dpkg -reconfigure ubuntu-desktop

Try that?

---

