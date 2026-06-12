---
title: "Graphics Card Config"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by cperalta1 on 2008-01-27
Hello all.

*First Post!*

Maybe you guys could help me.  I just installed Gutsy on a Thinkpad T40 with a ATI Radeon Mobility 7500 graphics card (everything is working fine).  

When I go to System >Administration >Screens and Graphics it brings up this...

[IMG]http://i169.photobucket.com/albums/u230/cperalta1/Screenshot-ScreenandGraphicsPrefere.png[/IMG]

Please take note at what the driver is set at.  There is an option for "radeon - ATI Radeon cards, including Radeon Mobility and FireGL"  However, when I select it as the new driver and click on "Test" the screen gets all wacked out with an "X" as the curser and and it asks me if I want to keep the current configuration.  I click cancel, then it gives me a test failed message and goes back to normal.

What do you guys make of this?

Should I not try to configure it with the (what I believe to be) the correct driver?  Or is the driver it's currently configured with the right one?

Please help.

Chris

---

### Post by emarkd on 2008-01-27
See if you have a restricted driver available using System > Administration > Restricted Driver Manager

---

### Post by wolfen69 on 2008-01-27
if everything is working, i would just stay with the current driver.

---

### Post by cperalta1 on 2008-01-27
No drivers available.

My only fear is that if I go ahead and switch the driver and my screen stays all jacked up it, that I won't be able to access the driver settings or even the terminal to reverse it.

---

### Post by the_bengine on 2008-02-01
Hi Cperalta.

I'm in the same boat as you, i've just installed Ubuntu and can't get my dell inspiron 5100 with ATi radeon mobility 7500 to work. It just defaults to generic 'vesa' drivers.

I've dropped myself in the deep end a bit and have spent the past few evenings scanning forums on how to reconfigure xorg with different drivers.

If you mess with your video drivers and ubuntu refuses to boot (like mine does everytime i try anything other than 'vesa' :( ) you can press escape as ubuntu begins to boot and start up in safe mode. from here you can re-configure your sound card so all is not lost.

at the command prompt in safe mode (ubuntu's pretty windows interface (the Xserver) wont load), type:

sudo dpkg-reconfigure xserver-xorg

and you'll be taken through a serious of question about your graphics setup.

After doing a bit of forum searching myself, it would seem that Ati cards, especially these mobility ones, are an absolute nightmare. something to do with Ati not releasing the something or other....

---

