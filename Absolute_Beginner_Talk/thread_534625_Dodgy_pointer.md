---
title: "Dodgy pointer"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Quackers on 2007-08-25
Hello all, I am a very noob Ubuntu user ( or would be if I could get the pointer to go where I want it).
I have just installed Ubuntu (latest version) in the VirtualBox virtual machine environment on a desktop running Vista.
Everything loads ok and seems to work except for the fact that I have read that I need to install the additional stuff so that my pointer will work ok.
At the moment my pointer moves ok within the Ubuntu desktop and I can click on things ok. However the pointer will not go up to the top title bar (if that's what it's called) where the titles "machine", "devices" are. The pointer just stops before it gets that far.
Have I done something wrong? Is something missing? 
I may need to install these "additions" from the .iso file. But to do that I need to click on the "devices" tab - this is the problem. It seems to be a catch 22 position.
Please give a complete novice the benefit of your experience - when you stop laughing, that is!
Many thanks.

---

### Post by jamesrl on 2007-08-25
have you tried pressing the host key (which i believe by default is the Right Ctrl button)?  It should allow you to free the mouse from being stuck in the virtual box virtual machine.

---

### Post by Quackers on 2007-08-25
Thanks for the reply jamesrl.
Yes I have tried to press that but seems to have no effect.
I think it's because I am still within the Ubuntu desktop but the tabs I want to click on are in the top and bottom borders of the desktop which appear to be in a Vista format (aero glass)

---

### Post by schorsch on 2007-08-25
I am running a Win XP guest using VirtualBox running under Ubuntu so I have not the same environment as you. But the "host key" that is actually used should be visible in the lower right of the window ubuntu is running in. It is located on the far right. And to be sure: Have you typed the key on the keyboard or are you trying to access it with the mouse (which will not work!)? If it is the default "Right Ctrl" press it once on the keyboard and your mouse pointer should be released ......

---

### Post by schorsch on 2007-08-25
I just read in the VirtualBox FAQ that Vista is not supported quite now... did you have any problems during install? And are you running a 32- or 64-Bit system?
```
Currently, VirtualBox is available for the following [COLOR="Red"]Windows 32-bit[/COLOR] operating systems:
   &#8226; Windows 2000, service pack 3 and higher
   &#8226; Windows XP, all service packs
   &#8226; Windows Server 2003

```

---

### Post by Quackers on 2007-08-25
The host key is the right ctrl key as standard and I have pressed the key in an attempt to free the pointer. Unfortunately the pointer remains locked inside the Ubuntu desktop. I can use the pointer within the ubuntu desktop ok except that it will not move up to the "machine" or "devices" tabs at the top of the screen or down to the icons right at the bottom of the screen.

---

### Post by Quackers on 2007-08-25
> **schorsch said:**
> I just read in the VirtualBox FAQ that Vista is not supported quite now... did you have any problems during install? And are you running a 32- or 64-Bit system?
```
Currently, VirtualBox is available for the following [COLOR="Red"]Windows 32-bit[/COLOR] operating systems:
   &#8226; Windows 2000, service pack 3 and higher
   &#8226; Windows XP, all service packs
   &#8226; Windows Server 2003

```

schorsch, I had no problems at all installing either VirtualBox or Ubuntu. I am using 32-bit Vista.
Maybe you are right about Vista support, I don't know. I would say that there have been no error messages of any kind.
I would say though that the article in "PC Answers" magazine (where I got the info from) appears to be using aero type screens in its screenshots.

---

### Post by asmoore82 on 2007-08-25
> **Quackers said:**
> schorsch,** I had no problems** at all installing either VirtualBox or Ubuntu. I am using 32-bit Vista.

:rolleyes: until now :KS

---

### Post by Quackers on 2007-08-25
Can't argue with that, lol. I was just wondering whether I had missed something in the instal or setup.

---

### Post by schorsch on 2007-08-25
Perhaps you can try to create a shared folder under Vista/VirtualBox as described in the FAQ and mount it manually under Ubuntu? After that you should go on as mentioned in the FAQ.
Sorry, that I cannot help any further as I do not have the same environment.

---

### Post by Quackers on 2007-08-25
> **schorsch said:**
> Perhaps you can try to create a shared folder under Vista/VirtualBox as described in the FAQ and mount it manually under Ubuntu? After that you should go on as mentioned in the FAQ.
Sorry, that I cannot help any further as I do not have the same environment.

Ok I can have a look at that. Thanks for your suggestions.

---

### Post by schorsch on 2007-08-25
Another way could be to put the guest additions under Vista on an USB-Drive and mount it under Ubuntu guest after changing the USB settings in VirtualBox. According to the FAQ those are located here:
```
 "On a Windows host, you can find this file in the VirtualBox installation
        directory (usually under C:\Program files\innotek VirtualBox).
```

---

### Post by Quackers on 2007-08-25
> **schorsch said:**
> Another way could be to put the guest additions under Vista on an USB-Drive and mount it under Ubuntu guest after changing the USB settings in VirtualBox. According to the FAQ those are located here:
```
 "On a Windows host, you can find this file in the VirtualBox installation
        directory (usually under C:\Program files\innotek VirtualBox).
```

I have tried with a usb drive and also booting up ubuntu with a cd of that .iso file on it. They just sit there - can't do anything with them, lol. Will keep trying. Cheers.

---

