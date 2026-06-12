---
title: "How to run 3D Studio 7"
date: 2012-02-12
forum: Art &amp; Design
---

### Post by dc_wmj2 on 2012-02-12
I used crossover to install 3DSMax 7 in ubuntu. Unlike other versions, this one is known to run with wine (and crossover). Even though the software indeed is starting and running, I'm facing trouble with directx and my ATI-graphics-card now: The viewports just don't refresh (see screenshot below). Changing to OpenGL causes ubuntu to freeze. Software-rendering doesn't work either. Are there any tricks I could try to get directx to work somehow? I of course installed the newest version (directx 9.0) in crossover already.

[This website]("http://wiki.winehq.org/UsefulRegistryKeys") is showing a lot of registry-tweaks to adjust the graphics-settings in wine. However, I just don't know where to begin - the list is really long. Which component could cause the graphics-issues? Should I better try some settings in the catalyst-driver instead? Someone please help.


[[IMG]http://s7.postimage.org/vmtwc78uf/3dsmax7_screenshot.jpg[/IMG]]("http://postimage.org/image/vmtwc78uf/")

---

### Post by kayosiii on 2012-02-15
I would imagine you are more likely to find info at the WineHQ site. 

I have to admit 3dsmax 7 seems a little old to me to be much use in any studio, The studio I work at was using max 8 when I got there 4 years ago and we usually trail 1-2 years behind the current version. (Without the compatibility I can't think of a good reason to be using it vs one of the many fine 3D packages that work natively on Linux; I think max, lightwave and cinema4D are the only ones that don't have native linux versions).

I think virtualbox has 3d drivers and it is not the only virtual pc software to do so. I have used Max in this way but it is quite slow.

Currently at work I am using RDP to remotely control a spare windows pc that is mostly used for rendering but has a copy of Max on it. This Is just a little bit slower than above solution but very easy to set up. One of my tasks is to automate tasks in 3dsmax using maxscript I don't need great performance.

If you are using a Desktop see if you can't borrow a nVidia card for testing, of all the drivers for the Linux desktop the nVidia binary drivers are the only ones I trust to be production ready for 3d content creation.

---

### Post by dc_wmj2 on 2012-02-24
I posted on winehq already - however, they are not very friendly there. In my opinion 3D studio is completely usable since version 5 already. All important basics are included and required resources are low. Beginners like me don't miss anything. All basic modelling-techniques are possible - the software is running smooth and without errors. I see no reason slowing down my machine with a newer version - even if it was possible. I can't even reach the limits of the old version. So - old or new - I always will just produce poor rendering-results. 

According to my problem: It seems openGL is not running in wine. I'm using Ubuntu 10.10 with Trinity Desktop Environment on a 64-bit-AMD and ATI-graphics. With googleing around, I found out that Wine always need 32-Bit-versions of several libraries to run OpenGL.

Unfortunately no website is actually telling how to install these required 32-bit-libraries for ATI-cards and ubuntu64. ia32-libs are already present but don't seem to be enough. 

I would be glad for help.

---

### Post by dc_wmj2 on 2012-02-24
Maybe I should be more precise: This is the error-message from wine:

> err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems

[This]("http://wine.1045685.n5.nabble.com/Counter-Strike-1-6-quot-Choose-Pixel-Format-Failed-quot-td3393009.html") guy here says: "You forgot to install 32-bit OpenGL libraries (Nvidia installer asks you to install them or not)." 

I don't have nvidia, I have ATI and the newest catalyst-driver didn't ask for something like that. So what should I do?

---

### Post by dc_wmj2 on 2012-02-24
I found out: after upgrading wine, it is neccesary to also reinstall the catalyst-drivers. I didn't mention that I indeed did update wine from 1.2.2 to to 1.2.3. 

So after reinstalling catalyst a 2nd time, the opengl-error-message is gone - 32bit-libs seem to be installed. Also all error-messages in 3d studio are gone now. The problem with the broken viewports however, is back again. I'm sure it's just some tweak to make opengl finally work in wine. Somebody has an idea?

Edit:

Oh no, this doesn't look good for me: [Bug in X-driver]("http://bugs.winehq.org/show_bug.cgi?id=12911")

---

### Post by dc_wmj2 on 2012-02-25
The linked bug-report is about 4 years old. I can't believe the issue isn't fixed in current ATI-catalyst-drivers. Also, the "missing" GL_EXT_framebuffer_object extension *is* listed by glxinfo on my machine. 

This is the output on the console when running 3dsmax. Can anyone see some sense in it? I guess the last two lines are opengl-related.

> 3dsmax.exe
err:ole:CoGetClassObject class {d27cdb6e-ae6d-11cf-96b8-444553540000} not registered
err:ole:CoGetClassObject no class object {d27cdb6e-ae6d-11cf-96b8-444553540000} could be created for context 0x1
---------------------------
 Havok - Build (0)
 Base system initialized.
----------------------------
---------------------------
 Havok - Build (0)
 Base system initialized.
----------------------------
---------------------------
 Havok - Build (0)
 Base system initialized.
----------------------------
---------------------------
 Havok - Build (0)
 Base system initialized.
----------------------------
---------------------------
 Havok - Build (0)
 Base system initialized.
----------------------------
---------------------------
 Havok - Build (0)
 Base system initialized.
----------------------------
---------------------------
 Havok - Build (0)
 Base system initialized.
----------------------------
fixme:win:EnumDisplayDevicesW ((null),0,0x32d56c,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats


---

