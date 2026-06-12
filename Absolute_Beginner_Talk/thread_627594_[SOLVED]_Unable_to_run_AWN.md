---
title: "[SOLVED] Unable to run AWN"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by dinuop on 2007-11-30
what this error means
how to sort it out
see the screenshot.png

no avant window navigator doc at bottom

ubuntu7.10 gusty i386

---

### Post by Pumalite on 2007-11-30
You need your restricted driver and compiz-fusion working first.

---

### Post by dinuop on 2007-11-30
how can i do :(

---

### Post by atlfalcons866 on 2007-11-30
System>adminstiration>restricted drivers manager

---

### Post by dinuop on 2007-11-30
ok let me tr n get bak to you

---

### Post by PmDematagoda on 2007-11-30
The Restricted Drivers Manager can be found in System>Administration>Restricted Drivers Manager, once you open it, just enable the drivers for your VGA card and allow it to install the drivers.

To activate Compiz-fusion right-click on the desktop, click Change Desktop Background and then go to the Visual Effects tab and put it to the Normal or Extra option, this should start Compiz-Fusion.

---

### Post by dinuop on 2007-11-30
i installed 
compiz-core_0.6.0+git20071008-0ubuntu1.1_i386.deb
compiz-fusion-plugins-extra_0.5.2+git20070928-0ubuntu1_i386.deb

and this is tha error now showing

its not showing my vga on restricted drivers

i m using SiS M760GX vga with 128mb shared memory

---

### Post by dinuop on 2007-11-30
sory hear it is screenshot

---

### Post by PmDematagoda on 2007-11-30
I do not think that an SiS card has drivers for itself on Linux other than vesa which may be the one you are using now. And I also have my doubts whether your VGA card can support desktop effects such as Compiz-Fusion.

---

### Post by Pumalite on 2007-11-30
+1

---

### Post by LowSky on 2007-11-30
what happens if you use the command

```
compiz --replace
```

---

### Post by dinuop on 2007-11-30
finally i decided to not to go for AWN & ubuntu !!!!!1
cuz it wont support SiS M760GX Display card

i m unabelto enable desktop-effects from none to normal 
i think it wont suppot my display card

anybody have solution for this 
is their any other program which make ubuntu looks like leopard

or should i say gudbye to UBUNTU!!!! :(

---

### Post by PmDematagoda on 2007-11-30
Would [Mac4Lin]("http://sourceforge.net/project/platformdownload.php?group_id=204373") be any good?

---

### Post by dinuop on 2007-11-30
how it can without dock effect?

---

### Post by LowSky on 2007-11-30
why do you want it too look like a Mac? Sure it looks cool, but why is this one thing going to stop you from using ubuntu or linux in general?

---

### Post by dinuop on 2007-12-01
i like effects of mac4lin so i m trying to install AWN

its my bad luck i have SiS graphics card
i think it wont support AWN

---

### Post by derred on 2007-12-01
Simdock is what I use.

It's a bit tricky to find but the result is worth it. You can get the .deb file [here]("http://www.getdeb.net/search.php?search_distro_id=5&keywords=simdock") but that's for feisty only.
I found [http://ubuntuforums.org/showthread.php?t=536461]("http://ubuntuforums.org/showthread.php?t=536461")
 thank's to[ oasick]("http://ubuntuforums.org/member.php?u=202240") for>  Post  Re: Installing SimDock
Hi everybody !!! I compiled wxwidgets_2.8.5 and simdock-1.2 for Ubuntu Gutsy

You can download the files here:
[URL="http://www.box.net/shared/91x5r27zyg"]
wxwidgets_2.8.5[/URL]
[URL="http://www.box.net/shared/ht4abfyf46"]simdock-1.2
[/URL]
First you most install wxwidgets_2.8.5.deb

If you have any problem with background (sometimes appears a message at start session) you most do 2 things:

1. Scale the wallpaper image to your screen resolution. For example, if your screen resolution in 1024x768 your wallpaper image most have the same resolution.

2. To start simdock you most indicate where is your wallpaper image like this:

simdock /here/is/my/wallpaper/thisis.jpg

Don't forget that simdock is a very earlier application... but this version works very fine in my ubuntu gutsy

I hope that this halp you. Reggards and.. Good save Ubuntu  

That's what I did and it's been rock stable

Compiling it form [source]("http://sourceforge.net/projects/simdock/") is said to be a bit of a pain. but you could try that

---

### Post by dinuop on 2007-12-01
Finally i belive  SiS Graphics card can't support 3D Compiz Awant-Window-Navigator and 3D desktop 

Thanks to all

---

### Post by wheredidrealitygo on 2007-12-01
[http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac_p3](http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac_p3)

The walkthrough for the Mac4Lin project specifically states you can use AWN, _or_ Simdock, a dock that requires no compositing (and therefore doesn't need Compiz).

So you can still use a dock, and it will be functional, it just won't be as highly decorative as AWN.

This is the first page of the [walkthrough]("http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac"), which will provide you with step-by-step instructions, just skip the part about compiz and go to the part on Simdock, at the bottom of page 3.

---

### Post by derred on 2007-12-01
> **dinuop said:**
> i like effects of mac4lin so i m trying to install AWN

its my bad luck i have SiS graphics card
i think it wont support AWN

I have a similar card and 3D acceleration is out (except for mesa stuff and that's waaaaay too slow). AWN requires composition and a compositing manager in order to work (aiglx or xgl) but since none of those work on SiS cards... we're out of luck.

---

### Post by dinuop on 2007-12-01
again let me try using [http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac](http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac)

and i wil get bak

should i remove compiz ?

---

### Post by wheredidrealitygo on 2007-12-01
If your graphics card can't support it then it wouldn't hurt anything, as right now it's just taking up space.

---

### Post by dinuop on 2007-12-02
i happened 
i m able to install AWN in SiS Graphic card

thaks a lot to web support

now i m going to remove (#@!*) Windows

---

### Post by PmDematagoda on 2007-12-02
Congratulations:):lolflag:, you stuck with the idea that you can solve the problem and you finally solved to a good degree after some effort. Personally, I feel that you have a good attitude since you did not just give up like some people do when they first use Linux.

---

### Post by dinuop on 2007-12-02
you know even i got internet connection on my great ubuntu after a week effort through 
3G HSDPA Option GTMAX e PCMCIA card and 
compare to win its fast and now i lov to work on 

now onwords let me try to get into this and learn as much as i can and let me help other

-din

---

