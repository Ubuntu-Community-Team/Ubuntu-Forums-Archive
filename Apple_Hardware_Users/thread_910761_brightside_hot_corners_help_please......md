---
title: "brightside hot corners help please....."
date: 2008-09-04
forum: Apple Hardware Users
---

### Post by rogkmyers on 2008-09-04
Hi 

I use a mac at work and like the expose hot corners functionality. I have installed "brightside" and it works fine, but it lacks some functionality and I was wondering if it is just me not understanding the setup menus or that the functionality does not exist.

I can get the "show desktop" function to work, but how do I get the hot corners to show me "All windows"

Thanks for taking the time to read this.

Regards

Roger

---

### Post by cyberdork33 on 2008-09-04
> **rogkmyers said:**
> Hi 

I use a mac at work and like the expose hot corners functionality. I have installed "brightside" and it works fine, but it lacks some functionality and I was wondering if it is just me not understanding the setup menus or that the functionality does not exist.

I can get the "show desktop" function to work, but how do I get the hot corners to show me "All windows"

Thanks for taking the time to read this.

Regards

Roger
If you are looking for a function similar to expose on OSX, then you probably need to setup compiz to have a certain trigger for an action that is similar, then set the corner to perform that trigger as well.

---

### Post by rogkmyers on 2008-09-08
does Brightside have a website? or Howto page or instruction manual?

---

### Post by cyberdork33 on 2008-09-08
> **rogkmyers said:**
> does Brightside have a website? or Howto page or instruction manual?

It looks like the Debian devs were the original developers of the app, which means there is probably not a 'webpage' per se. If you download the source package, there is probably a README and maybe some other information:
[http://packages.ubuntu.com/source/hardy/brightside](http://packages.ubuntu.com/source/hardy/brightside)

This is more or less the approach I would start on, but is likely not the only solution:
What you will want to do is mess with your compiz settings to get the function you want performed to occur via keystroke or something (there might even be 'hot corners'-like ability in compiz already), then you will have to write a script or figure out how to trigger this function from the commandline (dbus, echo commands, whatever). Finally, you setup brightside to have a corner trigger a "Custom Action" (You set this in the brightside properties window.), and run the command or script that you have created (and undo that too if needed).

Overall, what you are trying to do is really beyond the scope of the brightside application (as I was trying to explain previously). All it does is trigger an event from the corners, the acual actions performed are handled by other things. The reason it can perform the "Show Desktop" action is because it is built into Gnome. The "Show All Windows" function is not so you will have to integrate that some other way.

Additionally, this is really beyond the scope of this forum. We are really focused on helping users install Ubuntu on your Mac and troubleshoot hardware problems. Since you seem to have a working install and are dealing with customization/tailoring of software, you will likely find more technical help / information in other areas. (Programming Talk possibly, or desktop effects on working with Compiz via script / commandline)

---

