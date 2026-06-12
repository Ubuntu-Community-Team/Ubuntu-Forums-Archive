---
title: "Trouble booting Ubuntu 6.06 LiveCD(x server error)"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Harkonnen on 2007-03-31
I have been trying to get the Live CD of Ubuntu 6.06 running forever now. Here are some pictures of the X server error I get.

[[COLOR="Blue"]XserverError1[/COLOR]]("http://harkonnen19.googlepages.com/xservererror1.jpg")

[[COLOR="Blue"]XserverError2[/COLOR]]("http://harkonnen19.googlepages.com/xservererror2.jpg")

[[COLOR="Blue"]XserverError3[/COLOR]]("http://harkonnen19.googlepages.com/xservererror3.jpg")

[[COLOR="Blue"]XserverError4[/COLOR]]("http://harkonnen19.googlepages.com/xservererror4.jpg")

My video card is a ATi Radeon 9200se (PCI). I also have a Intel integrated card as well that I believe is causing a conflict. The integrated video **IS** disabled in the BIOS. My monitor is a Samsung 205BW and is hooked up via VGA.

I have tried using Ubuntu 6.10 and even the 7.04 Beta, but when I boot with those discs my CPU fan shuts off! :shock: 

I have tried doing this. But it didn't work. Don't know what I am doing wrong.

[http://www.ubuntuforums.org/showpost.php?p=2353434&postcount=18](http://www.ubuntuforums.org/showpost.php?p=2353434&postcount=18)

This is really starting to get on my nerves. Some help would be greatly appreciated. BTW the 6.06 disc works fine in my Father's laptop, which has an ATi card as well.

---

### Post by Harkonnen on 2007-04-01
.

---

### Post by Harkonnen on 2007-04-01
I could really use some expert help here. I have no idea what to do. I really hope that this issue gets fixed when feisty fawn comes out. It seems to be a common problem.

And the part about my CPU fan shutting off just baffles me.

I just want the Live CDs to work :(

---

### Post by Harkonnen on 2007-04-01
I downloaded the free gnome version of mandriva and it allows me to boot into the live CD fine. So why can't I use ubuntu.

---

### Post by matty_b_1000 on 2007-04-03
I have the exact same problem. I've only tried it with Dapper though, not Edgy or Feisty (I don't have the time to download). I also have an ATI Radeon 9250 and integrated Intel, and NicloeM's method doesn't work. I may try to find out the driver name thru Windows. Watch this space.

---

### Post by matty_b_1000 on 2007-04-03
Nothing doing. I might download some other Linux, see if it works.

---

### Post by jhenager on 2007-04-03
I wouldn't consider this a solution, but as a troubleshooting test, I would re-enable the onboard video and temporarily remove the ATI card to see if that worked. 
You could also try the Alternative CD, to see if you could install using that method.

---

### Post by matty_b_1000 on 2007-04-03
I really don't have time for anything that drastic. But if it helps, I did try to run it before I got my Radeon, with the same result.

---

### Post by matty_b_1000 on 2007-04-03
I have now tried two other distros: openSUSE won't or can't connect thru my wireless adaptor for the web install, and Freespire freezes at the loading screen for the LiveCD and install. I'll stick to Windows for now.

---

### Post by Mmmbopdowedop on 2007-04-04
hey . . this sounds like the exact saem problem i was having

the thing i did to sort it is when ubuntu says that the xserver encountered an error, login as root or w/e and edit your xorg.conf file . . i know you wont have a gui open tho as its not bin recognised, this is done in terminal ;) sooo . . . 

> login as: $$W$%% (your username)
password: (password here)

Then Type:

> sudo nano /etc/X11/xorg.conf

scrol down to wehere you see your graphics card and change the pci to the right value

e.g mine was 1:2:0

> Section "Device"
        Identifier      "ATI"
        Driver          "ati"
        BusID           "PCI:1:2:0"
        VideoRam        102400
        Option          "UseFBDev"              "true"
EndSection


thats what mine looks like now and works great :) 

note: if you changed the identifier, make sure you change it in screen section aswell . . .

> Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI"
        Monitor         "Flatron915FT"


I too have the onboard intel graphics and although they are disabled in bios too they are still in the xorg.conf file, so just overwrite them with the above information :P

---

### Post by matty_b_1000 on 2007-04-04
No, I've tried that. It won't work.
P.S. I tried Edgy LiveCD too, and got the same problem, but this time it wont even give me a command line, after it's tried to configure X the screen just goes blank and I can type but nothing happens.
P.P.S. Is your PC a Dell? Mine is. Does that have anything to do with it?

---

### Post by Mmmbopdowedop on 2007-04-04
nope . . . mine wasnt a Dell . . . i no may seem dumb . . .but u have tried the

> 
sudo dpkg-reconfigure xserver-xorg

just a try :confused: 


mine didnt even boot with some linux', but whichever i did try i always couldnt boot with any till i found that out about my card being 1:2:0

just a note . . i got further with my booting after i swapped the cards pci slot in the comp, so i just moved it down 1 and it worked a whole lot better in various distributions aswell as non ubuntu.

---

### Post by matty_b_1000 on 2007-04-05
I've done it! When you type the driver name in xorg.conf, it's "ati" lowercase, not "ATI".

---

### Post by Mowcius on 2007-04-05
having the same problem  

if you click <no> when it asks you whether you want to view the x server stuff
after a bit of time does it come up with a command prompt bar that looks like:
ubuntu@ubuntu~:

or something like that

if so please put in another post

---

### Post by matty_b_1000 on 2007-04-05
What you do at the command prompt is type "lspci". This will bring up a list of attatched devices. Find your graphics card (the one that says "VGA Compatible Device" or similar) and note the number to the left of it, which will be something like 01:02.0. Then, type "sudo nano /etc/X11/xorg.conf", scroll down to where there is a number similar to the one you just noted. It should also mention the name of your graphics card. Replace the number there with the one you noted, and where it says "driver", make sure it says the maker of your graphics card in **lowercase**. Save it (<ctrl>+O, <enter>), close it (<ctrl>+X) then type "startx". If all is well, you will see another "GDM is disabled" error message, then it will take you to your desktop.

---

### Post by Mowcius on 2007-04-05
I am having the same problems and tried this:
> **matty_b_1000 said:**
> What you do at the command prompt is type "lspci". This will bring up a list of attatched devices. Find your graphics card (the one that says "VGA Compatible Device" or similar) and note the number to the left of it, which will be something like 01:02.0. Then, type "sudo nano /etc/X11/xorg.conf", scroll down to where there is a number similar to the one you just noted. It should also mention the name of your graphics card. Replace the number there with the one you noted, and where it says "driver", make sure it says the maker of your graphics card in **lowercase**. Save it (<ctrl>+O, <enter>), close it (<ctrl>+X) then type "startx". If all is well, you will see another "GDM is disabled" error message, then it will take you to your desktop.

I got a number from my VGA compatible device but when i loaded 'sudo nano /etc/X11/xorg.conf' nothing came up

what can i do?

---

