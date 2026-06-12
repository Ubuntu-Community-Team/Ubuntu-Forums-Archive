---
title: "Installed Ubuntu 7.10, installed ATI Drivers with Envy...CANNOT enable Desktop Effect"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by Nurly on 2008-02-28
I just installed Ubuntu 7.10 on my desktop and I had some problems with the ATI Restricted drivers after I enabled them and got a black screen on startup. :(  So I reinstalled and then I downloaded Envy and I manually installed the ATI Driver 8.42 with the program and then I downloaded all updates needed for Ubuntu then finally I enabled the Restricted drivers (just to be safe with all the updates) so I would not get the black screen after booting up again.

Now that I have my resolution to where it needs to be and no more black screens after booting up, I am trying to enable desktop effects.  I know my computer and graphics card is more than capable of running them.  

I followed this tutorial (thinking maybe it was the packages that i needed) :confused:, here is the link just so you can track what i did: [http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200](http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200) 

I did all that and still I cannot enable desktop effects.
[U]
Here are my specs:[/U]

[B]Dell Dimension E521
Windows Vista/Ubuntu 7.10 DUAL BOOT
AMD Athlon 64 2.2GHz
3 GB of RAM
ATI Radeon X1650 Pro 512MB 
HDD 1 (Vista Partition): 65 GB
HDD 2 (Ubuntu Partition): 10 GB
HDD 3 (Storage): 160 GB
HDD 4 (Storage): 160 GB[/B]

Any help at all would be greatly appreciated and thanks a bunch! :)

---

### Post by Rafadagaffer on 2008-02-28
The ATI drivers are known for not installing correctly, so to check

What is the result of both of these commands?

```
glxinfo | grep render
```

```
fglrxinfo
```

---

### Post by justleen on 2008-02-28
I've only managed to get ATi working with compiz user the binary driver..

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by jan quark on 2008-02-28
I had to install this package
```

sudo apt-get install xserver-xgl
```

and then change the session during login to xclient to enable the effects

---

### Post by Nurly on 2008-02-28
> **Rafadagaffer said:**
> The ATI drivers are known for not installing correctly, so to check

What is the result of both of these commands?

```
glxinfo | grep render
```

```
fglrxinfo
```

```
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: Radeon X1650 Series
```

and

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.0.6747 (8.40.4)
```

---

### Post by miciurin on 2008-02-28
Your driver version 8.40 does not support AIGLX, so you have to install XGL (xsever-xgl). Then try the command *compiz --replace*. If nothing happends you can try *compiz --replace -v* in a terminal window. That would report any errors encountered. Post the errors or just google for the same error. Odds are that somebody already had the same problem.

---

### Post by bumanie on 2008-02-28
This site may  help [http://forlong.blogage.de/article/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710](http://forlong.blogage.de/article/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710)
It is often sited as a good guide re enabling compiz-fusion.

---

