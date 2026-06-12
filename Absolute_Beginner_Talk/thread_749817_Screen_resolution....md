---
title: "Screen resolution..."
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Nile1037 on 2008-04-08
Since this is *absolute* beginner talk, I figure that this is the perfect place for this.

How do I change the resolution. I have a widescreen screen and there's a big black bar on the left right now, because Kubuntu wants to be a square. It's also cutting a bit off at the bottom.

Thanks.:)

---

### Post by Joeb454 on 2008-04-08
You could try running the following from a terminal: ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` It should allow you to reconfigure your graphics drivers etc. :)

---

### Post by overdrank on 2008-04-08
> **Nile1037 said:**
> Since this is *absolute* beginner talk, I figure that this is the perfect place for this.

How do I change the resolution. I have a widescreen screen and there's a big black bar on the left right now, because Kubuntu wants to be a square. It's also cutting a bit off at the bottom.

Thanks.:)
Hi and to add to Joeb454, what is the model of the graphics card and have you installed the drivers?

---

### Post by Nile1037 on 2008-04-08
Terminal? I don't know what that means. :confused:

---

### Post by overdrank on 2008-04-08
> **Nile1037 said:**
> Terminal? I don't know what that means. :confused:

The terminal is located under applications, accessories. This link may help also [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by Joeb454 on 2008-04-08
Sorry my mistake, I should've clarified that!

Click Applications>Accessories>Terminal.

Don't be too scared of it :) Just copy and paste the code I posted above, and it won't be *too* scary, I promise :)

---

### Post by Nile1037 on 2008-04-08
> **overdrank said:**
> Hi and to add to Joeb454, what is the model of the graphics card and have you installed the drivers?

I don't know if off by heart, and have no idea how to check it out in Kubuntu. When I boot back into Windows I'll check, but I know it's on board graphics. 

Right now I'm only using the Live CD to see if I like it.

> **overdrank said:**
> The terminal is located under applications, accessories. This link may help also [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Honestly, I have no idea how to use the terminal thing. I copied and pasted the code in there and it said:


xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080409015554

:confused:

---

### Post by overdrank on 2008-04-08
> **Nile1037 said:**
> I don't know if off by heart, and have no idea how to check it out in Kubuntu. When I boot back into Windows I'll check, but I know it's on board graphics. 

Right now I'm only using the Live CD to see if I like it.



Honestly, I have no idea how to use the terminal thing. I copied and pasted the code in there and it said:


xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080409015554

:confused:

Ok you are using the live cd so the resolutions may be limited until the install. You can find your graphics card by using the command ```
lspci 
``` in the terminal and look for VGA

---

### Post by Nile1037 on 2008-04-08
> **overdrank said:**
> Ok you are using the live cd so the resolutions may be limited until the install. You can find your graphics card by using the command ```
lspci 
``` in the terminal and look for VGA

I'm back in Vista now.

[IMG]http://i25.tinypic.com/2n9mb6p.jpg[/IMG]

Also, while in Kubuntu I found where I could change my resolution, and it was already at 1440 x 900, but the black bar was still there. I think it's just the Live CD.

---

