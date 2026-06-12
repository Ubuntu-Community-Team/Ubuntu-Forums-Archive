---
title: "Help On Ma Card 8600gt"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by rohit88 on 2007-08-26
Hey guys,
I am an absolute beginner....I am using win-xp on ma new machine
Its cofig- amd64 5000+
               asus mb
              2gb ram and 250 hd

I want toknow  about my graphic card **8600GT**
I am seriously thinking to switch to ubuntu....i've read many threads on
this card....which are not really encouraging:(

so what should i do???
should i try other distro(man i really like ubuntu as far as i know it)
would you help me on this ..
  
thanks....

---

### Post by Hobo Joe on 2007-08-26
Your computer is nearly identical to mine, and yes, all that hardware is very well supported.

---

### Post by zero-9376 on 2007-08-26
However it is not well supported using the drivers in the ubuntu repos, i had to use envy to get more recent drivers from nvidia, look at the link in Hobo Joes sig.

---

### Post by rohit88 on 2007-08-27
please guys.....


help me out~

---

### Post by rohit88 on 2007-08-27
Need Reply Please.....

---

### Post by Pharisee on 2007-08-27
Any issues you might have are Linux related, not distro related I would imagine. Your video card is well supported if you use propriotary drivers from the NVIDIA website for example. That is what I usually do.

So continue with this distro if your thinking of installing Linux :)

---

### Post by rohit88 on 2007-08-27
> **Pharisee said:**
> Any issues you might have are Linux related, not distro related I would imagine. Your video card is well supported if you use propriotary drivers from the NVIDIA website for example. That is what I usually do.

So continue with this distro if your thinking of installing Linux :)

Well as much as i know it is not supported officially(Just 1 forum member told me)

---

### Post by Pharisee on 2007-08-27
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by Bout to Snap on 2007-08-27
> **rohit88 said:**
> Well as much as i know it is not supported officially(Just 1 forum member told me)

nope it's not supported initially,however after install is complete you'll have to download a program called envy and install the graphic card drivers, afterwards you'll do fine. also if you like gaming some windows games are supported by cedega (windows emulator) also some games have a linux installer package where you dont have to use cedega so really which ever you prefer Ubuntu Pwns Xp and Vista in my opinion but it all comes down to what you really like i guess.

---

### Post by rohit88 on 2007-08-27
> **Bout to Snap said:**
> nope it's not supported initially,however after install is complete you'll have to download a program called envy and install the graphic card drivers, afterwards you'll do fine. also if you like gaming some windows games are supported by cedega (windows emulator) also some games have a linux installer package where you dont have to use cedega so really which ever you prefer Ubuntu Pwns Xp and Vista in my opinion but it all comes down to what you really like i guess.

Man how can i use envy...They guys say that use it at ur own risk:(
Is there any other way??

---

### Post by Pharisee on 2007-08-27
When you install Ubuntu you will have a basic driver installed. Similar to what Windows XP does.  Using that enables a better driver, like using the CD that would of came with your card.

Don't worry to much about the warning. All software has that warning, it's just a warning to be careful.

---

### Post by Marat Galiev on 2007-08-27
Hi guys!
Sorry for my English:)
I'm only a Russian student...
Today i have my NVIDIA 8600GT card worked in Ubuntu 7.04!!!
I'm so happy!
This my way:
```

Only 27 steps:)
1)Install packages xserver-xorg-dev,pkg-config,libc6-dev.
You an find them at packages.ubuntu.com.
2)Press ctrl+alt+F2.
3)sudo nano /etc/init.d gdm stop
4)cd /there/your/driver/location
5)sudo sh NVIDIA-100.14...-xxx.run --ui=none
(without GUI menu).
To the question with nvidia-xconfig answer "Yes".
6)sudo nano /etc/default/linux-restricted-modules-common
Edit line
DISABLED_MODULES="nv nvidia_new"
7)sudo cp /lib/modules/2.6.20-15-generic/kernel/drivers/video/nvidia.ko /lib/modules/2.6.20-15-generic/volatile/
8)sudo modprobe nvidia
9)/sbin/ldconfig
10)/sbin/depmod -aq
11)reboot
12)step 7
13)cd /lib/modules/2.6.20-15-generic/volatile/
13)sudo insmod ./nvidia,ko
14)sudo modprobe nvidia
15)step 9
16)step 10
17)sudo /etc/init.d/gdm start
18)reboot
19)cd /lib/modules/2.6.20-15-generic/kernel/drivers/video/
20)sudo cp nvidia.ko nvidia_new.ko
21)sudo insmod ./nvidia.ko
22)step 9
23)step 10
24)ctrl+alt+F7
25)sudo nvidia-xconfig
26)reboot

OK!So,please check you glxinfo command.
You can see what:
[B]OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8600 GT/PCI/SSE2
OpenGL version string: 2.1.1 NVIDIA 100.14.11[/B]
Thank's.



```

---

### Post by dr.koljan on 2007-08-27
> **rohit88 said:**
> Man how can i use envy...They guys say that use it at ur own risk:(
Is there any other way??

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

The program works perfectly for me.

If you are afraid of "risk" then don't use computer.

2Marat Galiev:

Didn't Envy work for you?

---

### Post by Bout to Snap on 2007-08-27
> **rohit88 said:**
> Man how can i use envy...They guys say that use it at ur own risk:(
Is there any other way??

envy works pretty well given the fact that you are using it at your own risk, I've never had any probs with it and if you were to migrate over to Ubuntu there's no way to update your card without it...well unless you do it manually and i would suggest doing it the envy way much easier and much faster. I think envy is safe to be honest i've never had any probs out of it and worse case senario is that you screw up and install an ATI Driver instead of a Nvidia one and your GUI doesnt load and even then all you have to do is type:"envy -t" and it'll load the terminal interface for Envy so you can make changes that way. Either way you decide to go though keep in ming that Linux OS is a whole new ball game compared to windows, aint nothing like Ubuntu even close to windows, In fact you might want to look up a tutorial on how to dual boot windows/linux or just keep using the cd till you get used to it, because it can be frustrating to get the hang of.

---

### Post by Marat Galiev on 2007-08-27
I, didn't use it:)because i haven't unlimited internet:(
my one MB cost so big...
But way in my post works fine!

---

