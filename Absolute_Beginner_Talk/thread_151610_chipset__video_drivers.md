---
title: "chipset / video drivers"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by paul416 on 2006-03-28
Hi ... I am curious how to install the chipset and video drivers ? I have an intel celeron and nVidia fx 9250 graphic card , Can someone please help ? Thank you

---

### Post by Delkster on 2006-03-28
[QUOTE=paul416]Hi ... I am curious how to install the chipset and video drivers ? I have an intel celeron and nVidia fx 9250 graphic card , Can someone please help ? Thank you[/QUOTE]
Hi, and welcome!

I don't know exactly what chipset you have (a number of different chipsets are used with systems that have Celeron processors), but I'm inclined to believe that whatever drivers you need are built into Linux, and if that is the case, you don't need to install any drivers separately. If you have a reason to believe that you need separate drivers (for example, if something that the chipset is supposed to do doesn't work), please provide more information.

As for the video driver, that would depend on which card you have after all. I'm not quite sure but I have to say that I don't know of an NVidia FX card with a model specification of 9250, although there's an ATI Radeon with that specification.

If you have an NVidia card, please follow the instructions at [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia).
If, on the other hand, your graphics card is an ATI one, the instructions are at  [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI).

General information on installing drivers that aren't built into Linux is available at [https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto).

If you aren't sure which chipset manufacturer's card you have, you can try finding it in the Device Manager (which should come with the standard Ubuntu desktop, although I'm not sure if you get it with Kubuntu):

System -> Administration -> Device Manager

For example, I have my "Radeon R200 QL [Radeon 8500 LE]" listed under the "nForce 2 AGP" device.

A perhaps more straightforward way to find out out which graphics card you have is to use the command line:

1. Open a terminal (press Alt-F2 and enter "gnome-terminal")
2. At the prompt, enter the following command:
```
lspci
```
3. Find what the line with "VGA compatible controller". It should have the brand and model of your card.

If you need more help, please ask.

---

### Post by paul416 on 2006-03-28
I am new to computers and I have been using windows for about 6 months , I was told that I needed these drivers , I am sorry it was a typo in my video card , Its a Asus 9520/TD , Someone told me that its from NVidia , I don't know . I am able to connect to the internet just fine and the installment was okay as well but I notice my graphic isn't moving that well when I move my mouse around the screen , Its ok but I figure that the driver would help , Is this correct ? My video card is below from the website 

[http://www.exciteit.co.uk/store/EXCITE_viewItem.asp?idProduct=76197](http://www.exciteit.co.uk/store/EXCITE_viewItem.asp?idProduct=76197)

.

---

### Post by paul416 on 2006-03-28
Hi ... I  went to that link above for nVidia , I went to the synaptic package manager area and search for nvidia , It came back with so many to choose , I am not sure as to which one I need to reload , I also went to the devise manager and I found out this bit of info Vendor > nVidia , devise > NV34 ( Ge Force FX 5200 ) Bus type > PCI ..
Could someone please help me in choosing the correct one for my computer ? Thank you

---

### Post by paul416 on 2006-03-28
Please help , I am not able to log into Ubuntu at the moment , I went and re-read from Delkster post the link for nVidia and I choose the linux-restricted-modules-386 and when I done the terminal part ? I get this screen below which look like a doc screen 

Ubuntu 5.10 breezy Badger Ubuntu tty1
Ubuntu Login : XXX 
Password XXXX
Lat time Tues Mar 28 xxxx
Linux Ubuntu 2.6.12-10-386 #1 Sat Mar 11 16:13:17 UTC 2006 ;686 GNU/Linux

The programs included with the Ubuntu system are free software ; the exact distribution terms for each programs are described in the indibidual files in 
/usr/share/doc/*/copyright 
Ubuntu comes with ABSOLUTELY NO WARRANTY , to the extent permitted by applicabel Law.
User name @Ubuntu: ~$

Okay now from this info was I suppose to choose the 686 one ? What do I do with this screen to get back to my desktop ? Or can I get back ? Thank you

---

### Post by IDipSkoalMint on 2006-03-28
You probably want to use the 686 one. It is a more up-to-date version, I believe.

---

### Post by paul416 on 2006-03-28
[QUOTE=IDipSkoalMint]You probably want to use the 686 one. It is a more up-to-date version, I believe.[/QUOTE]

How can I do that ? I am stuck on the screen above , I don't know what to enter next , Can someone help ? Thank you

---

### Post by Perfect Storm on 2006-03-28
```
sudo apt-get install linux-686 linux-restricted-modules-686
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```

Reboot

If you still in non-X then:
```
sudo nano /etc/X11/xorg.conf
```
find the  **Section "Device"**
and change **driver "nv"** to **driver "nvidia"**

---

### Post by paul416 on 2006-03-28
Hi Artificial Intelligence , Your method has work for me getting the video driver , Though I didn't wait long enough for your suggestion , I reformated the computer and reinstall Ubuntu , Then I try your codes which loaded the driver but , I am curious what does one do when they see this screen below ? Because I have try to install my driver for my cordless and I was following the instruction to do such for it  but , When I went to reboot I was shown the screen below and I didn't know what to do next , Could you or anyone else explain what one has to do when this screen show up ? Thank you 

Ubuntu 5.10 breezy Badger Ubuntu tty1
Ubuntu Login : XXX
Password XXXX
Lat time Tues Mar 28 xxxx
Linux Ubuntu 2.6.12-10-386 #1 Sat Mar 11 16:13:17 UTC 2006 ;686 GNU/Linux

The programs included with the Ubuntu system are free software ; the exact distribution terms for each programs are described in the indibidual files in
/usr/share/doc/*/copyright
Ubuntu comes with ABSOLUTELY NO WARRANTY , to the extent permitted by applicabel Law.
My username@Ubuntu: ~$

---

### Post by Perfect Storm on 2006-03-28
Sorry, I don't have any experience/knowledge on the cordless. I'm good old fashion and want a wire I can see ;). But while you wait on someone to responds on the wireless problem, you can make a search on the forum, perhaps you find someone with same problem who got his problem solved :)


best regards
A.I. Dude

---

### Post by paul416 on 2006-03-28
Thanks AI for the help :cool:

---

