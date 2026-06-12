---
title: "Desktop effects do?"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by pardesi on 2007-06-12
would desktop effects work on my computer .
my specs
are 1GB RAM
160 GB SATA
dual boot XP -Fiesty Fawn
Compaq Presario
i tried once but got a white screen for about 10-15 secs then pressed escape..or was it normal

---

### Post by Kosimo on 2007-06-12
> **pardesi said:**
> would desktop effects work on my computer .
my specs
are 1GB RAM
160 GB SATA
dual boot XP -Fiesty Fawn
Compaq Presario
i tried once but got a white screen for about 10-15 secs then pressed escape..or was it normal

What grafics card do you have?

---

### Post by pardesi on 2007-06-12
how do i know that i am prsently typing from XP ....

---

### Post by pardesi on 2007-06-12
is there any way by which i can know what graphics card i have

---

### Post by george29 on 2007-06-12
> **pardesi said:**
> is there any way by which i can know what graphics card i have

From windows 

Start > Control Panel > System > Hardware tab > device manager 

and look for display adaptor - that should tell you what graphics card you have.

---

### Post by pardesi on 2007-06-12
so i have ATI RADEON EXPRESS 200 Series ...so will desktop effects do

---

### Post by viciouslime on 2007-06-12
I *think* this card is supported by the open source ati driver and so works fantastically with desktop effects, just press the button et voilà.

---

### Post by brennydoogles on 2007-06-12
> **pardesi said:**
> so i have ATI RADEON EXPRESS 200 Series ...so will desktop effects do

What version of Ubuntu are you using?? If you are using Feisty Fawn you can go to System ->Administration -> Restricted Drivers Manager    and enable the best driver for your card (it should be the only one that pops up). If you are using Edgy Eft, I would recommend reading the sticky threads on ATI video cards in Absolute Beginner Talk, and if it sounds too complicated, you may be better off upgrading to Feisty through the download manager (it can take a while, but it is usually very reliable and easy). Hope this helps, and have a great day!!

---

### Post by pardesi on 2007-06-12
yes i run on fiesty fawn thanks :p:p

---

### Post by pardesi on 2007-06-12
i went to enable desktop effects and enabled it but then a white screen came for about 15 secs and i had no patience and i pressed escape...is it normal or is something wrong

---

### Post by terabite on 2007-06-12
Your graphics havent been detected properly...
Try running liveCD in **normal graphics** mode. Not safe graphics. See if u can enable desktop effects there.

Also, tell me the current output of:

```
glxinfo | head
```

---

### Post by pardesi on 2007-06-13
here is it

```
pardesi@pardesi-desktop:~$ glxinfo | head
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer

```

---

### Post by terabite on 2007-06-13
ok... mostly an issue with drivers... did u try what i said?

---

### Post by pardesi on 2007-06-13
problem is i don't have fiesty live cd with me i have distributed it among my friends:(

---

### Post by kittyhawk63 on 2007-06-13
> **pardesi said:**
> i went to enable desktop effects and enabled it but then a white screen came for about 15 secs and i had no patience and i pressed escape...is it normal or is something wrong

I had this same problem. I resolved it by starting Linux in "Recovery Mode."
This I typed at the ~$ prompt:
sudo dpkg-reconfigure xserver-xorg 
Now I went through the GUI and set up my video card. Take your time and read all the instructions. Stick with the default settings if you don't know the correct inputs. Voila, is right. It worked for me. Then reboot and go into Linux.
kh
Edit: Sorry that I missed typing the x in front of "org". Happy_Man caught the error. It is now correct.

---

### Post by Happy_Man on 2007-06-13
he means ```
sudo dpkg-reconfigure xserver-xorg
```.... (kitty hawk forgot an x)

---

### Post by kittyhawk63 on 2007-06-13
> **Happy_Man said:**
> he means ```
sudo dpkg-reconfigure xserver-xorg
```.... (kitty hawk forgot an x)

Thanks Happy_Man. Typos make a difference.
Where did you get that great avatar?
kh

---

### Post by terabite on 2007-06-13
As far as i can see... It definitely a display driver problem....
Run with LiveCD as ive told u... And tell me the results...

---

