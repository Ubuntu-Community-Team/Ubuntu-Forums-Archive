---
title: "nVidia GFX Installation / Resolutions Issues"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by The Pinny Parlour on 2006-01-06
Hi Guys,

Have just made a ubuntu box and have accidently pressed escape during the setup where it asked me for the resolution settings.  Now I can't change the resolution to anything higher than 1024x768.  

How do I,

a, Install the nVidia GeForce MX440 SE vid card drivers?
b, change the resolution?


I have searched but nothing has really been successful and I'm scared of stuffing something up.  Total newbie here.  BTW I love ubuntu linux.  :cool: 

Thank you,
Ian



UPDATE:  Have worked out how to install drivers via synaptic package manager.  I installed the nvidia.glx.

---

### Post by Perfect Storm on 2006-01-06
Resolution: [http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution](http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution)


3D card: [http://doc.gwos.org/index.php/3D_Graphic_Cards](http://doc.gwos.org/index.php/3D_Graphic_Cards)

---

### Post by The Pinny Parlour on 2006-01-06
[QUOTE=Artificial Intelligence]Resolution: [http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution](http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution)
][/QUOTE]

 Is there anything easier than cutting and pasting endless code?  I just want to change resolutions.:confused:

---

### Post by Perfect Storm on 2006-01-06
You could do:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by The Pinny Parlour on 2006-01-06
[QUOTE=Artificial Intelligence]You could do:

```
sudo dpkg-reconfigure xserver-xorg
```[/QUOTE]


Is it safe?

---

### Post by Gustav on 2006-01-06
But that might not work as good (you might not get the maximum resolution that your monitor supports)

---

### Post by The Pinny Parlour on 2006-01-06
I don't know about all this code stuff/changing it.  I think I will just reinstall ubuntu and not make the initial mistake I made.  No one has yet to show me a way of doing a simple task of resolution changing that is user-friendly and easy.

---

### Post by Gustav on 2006-01-06
[QUOTE=The Pinny Parlour]Is it safe?[/QUOTE]
Pretty safe but if you want to be on the safe side you can backup the file /etc/X11/xorg.conf

---

### Post by The Pinny Parlour on 2006-01-06
[QUOTE=Gustav]But that might not work as good (you might not get the maximum resolution that your monitor supports)[/QUOTE]

  arrghhhhhhhh    why isn't this EASY??  :confused:    It's just changing the resolution for goodness sake.

---

### Post by handy on 2006-01-06
You can certainly trust AI  :KS 

You might find Automatix helpful, great for noobs like us.  :D 

[http://www.ubuntuforums.org/showthread.php?t=80295](http://www.ubuntuforums.org/showthread.php?t=80295)

Cheers,

handy

---

### Post by Gustav on 2006-01-06
[QUOTE=The Pinny Parlour]arrghhhhhhhh    why isn't this EASY??  :confused:    It's just changing the resolution for goodness sake.[/QUOTE]
Just changing the resolution is done via the resolution tool (system->settings->resolution) and it's easy.

This is about recognising your monitor in the best way possible.

---

### Post by Gustav on 2006-01-06
And the sudo dpkg-reconfigure xserver-xorg way isn't that hard either

---

### Post by The Pinny Parlour on 2006-01-06
[QUOTE=Gustav]Just changing the resolution is done via the resolution tool (system->settings->resolution) and it's easy.

This is about recognising your monitor in the best way possible.[/QUOTE]


Yes, that is correct, but, It only list 3 resolutions. It is currently set at 1024x768.  I would like 1280x1024.  But alas, no option to do that.   Hence my aarrrrggghhhhh

---

### Post by The Pinny Parlour on 2006-01-06
[QUOTE=Gustav]And the sudo dpkg-reconfigure xserver-xorg way isn't that hard either[/QUOTE]
I don't even know what that means or is

---

### Post by Gustav on 2006-01-06
in the terminal (program->accessorys->terminal) type:
```
sudo dpkg-reconfigure xserver-xorg
```
and follow the instructions.

---

### Post by The Pinny Parlour on 2006-01-06
Here one for the seasoned veterans:

&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
               &#9474; Please enter the video card's bus identifier.  &#9474;
               &#9474;                                                &#9474;
               &#9474; PCI:1:0:0_____________________________________ &#9474;
               &#9474;             


What the heck does this mean? and what goes here?

---

### Post by Gustav on 2006-01-06
just press enter on the questions that you don't know the answer to, the default is usually correct.

---

### Post by The Pinny Parlour on 2006-01-06
[QUOTE=Gustav]just press enter on the questions that you don't know the answer to, the default is usually correct.[/QUOTE]

Thank You for your help  :)

---

### Post by The Pinny Parlour on 2006-01-06
I have done all you said Gustav but it didn't work.  I went through a long drawn out QandA session and then I rebooted, but alas still 1024x768    grrrrrrrrrrrr:mad: :confused:

---

### Post by The Pinny Parlour on 2006-01-06
Ok. I seem to have done it.  Thank you all who helped.   **Just one more question though, how do I change the refresh rate?**

---

### Post by Perfect Storm on 2006-01-06
Get your monitor manual or make a google on your monitor specs.

Then:

```

sudo gedit /etc/X11/xorg.conf

```

scroll down to **Section "Monitor"**
There you'll see **HorizSync** and **VertRefresh**, change them to the right number you have in your monitor manual.


save & reboot.

---

### Post by Gustav on 2006-01-06
[QUOTE=The Pinny Parlour]Ok. I seem to have done it.  Thank you all who helped.   **Just one more question though, how do I change the refresh rate?**[/QUOTE]
It's the same thing there. You change it via system->settings->resolution.

The way to change which is the highest possible refresh rate its the same method as with the resolution. (So you've probably already done it)

---

