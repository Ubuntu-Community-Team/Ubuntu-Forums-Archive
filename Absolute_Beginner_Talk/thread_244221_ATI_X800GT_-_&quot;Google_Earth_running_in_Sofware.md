---
title: "ATI X800GT - &quot;Google Earth running in Sofware Emulation mode - update drivers&quot;"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by McBainUK on 2006-08-26
I have an ATI X800GT graphics card

When I launch Google Earth I get the message "Google Earth running in Sofware Emulation mode - update drivers"

Where do I start? I found [this]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27"), but looks really complicated 8-[

---

### Post by Paul133 on 2006-08-26
It's probably a problem with your graphics card drivers, not that I have any idea what to do, as I just have integrated graphics. But look around for howto's for your card. Do other things that require powerful graphics work?

---

### Post by Frank Golden on 2006-08-26
> **McBainUK said:**
> I have an ATI X800GT graphics card

When I launch Google Earth I get the message "Google Earth running in Sofware Emulation mode - update drivers"

Where do I start? I found [this]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27"), but looks really complicated 8-[Did you just lately install Google Earth?
Is this a new Ubuntu install? Have you installed any ATi
restricted drivers?

To see what drivers are being used
in the terminal type [sudo fglrxinfo] without brackets and post the output. I bet you are using the mesa drivers. This is the software emulation refered to by the message.


[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

The above tutorial is a good place to start for ATi drivers.
It covers installing proprietary drivers for x series cards
including yours. Read and understand all directions before using. Use method 2 for latest drivers.
Make sure your machine is up to date especially the kernel.
Make sure your restricted and universe repositories are available
as recomended in tutorial. This part is important as you won't
be able to D/L the stuff needed as you proceed.
Follow the directions exactly using cut and paste where possible
to avoid typing errors. Take your time and watch for error messages. If you encounter errors stop and post here. The directions are clear and well written and should setup you video card for 3D operation (hardware). What you are doing is compiling a graphic module using the proprietary ATi drivers and your kernel. This will enable hardware acceleration and install a bare bones GUI configuration applet for your card. That should fix Google Earth. You need to reboot to see change. Remember
if you later update kernels you will need to do the above again.
I have done this several times with no problems. Again take your
time.

---

