---
title: "change login screen resolution"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by UberNewber on 2007-04-08
Edgy...

Yeah, I've searched. Yup, I've seen some "fixes" suggested and that apparently have worked for "the other guy". What I haven't been able to do is fix ***my*** login screen resolution!

This is absurd to me that it's so difficult. I mean, going into xorg.conf and changing *anything* means I lose all ability to do anything graphical. And, what is the deal with doing sudo dpkg-reconfigure xserver-xorg when it refuses to give you the correct options for your hardware; the very options that it *was* able to detect upon initial install??? Weird! No matter how many times I try, the right options do not appear. If I go through the -phigh way and pick the "better" options of the lot, I can get into graphical mode again, but nasty and annoying graphics to say the least.

Also, why in the world are there no refresh rates listed in my X11/xorg.conf file? Shouldn't there be? When I go back to my backup of the file (i.e., the file created at original install) I have the correct options for res and refresh through the normal screen resolution setting interface, although the refresh rates are not themselves in the file. Again, weird! I'm wondering just where the "transparency" of Linux is in this particular endeavor.

Anyway, I'd mostly just like to know how I may get my login screen resolution fixed. Any other insights about my ramblins' may be very helpful as well. My monitor and onboard Intel graphics are correctly identified, by the way, so no problems there.

I'm sorry if some of the terminology, files, commands I noted above aren't quite correct (I hope you understand what I mean), but I don't have an internet connection from my Ubuntu partition yet and therefore can't exactly verify them. I have a USB ISDN modem from my provider and understand that isn't ideal, and haven't messed with it yet.

End long-winded first post... and despite my frustration with the login screen issue, I think I *likey* Ubuntu... :)

---

### Post by dreadlord_chris on 2007-04-08
You need to be more specific. Stating "What I haven't been able to do is fix my login screen resolution!" doesn't give enough information.

Some useful info would be: 
1. What Intel Graphics chipset
2. Monitor model

And while you're at it, why don't you post your xorg.conf

---

### Post by vanadium on 2007-04-17
I was also looking for a way to change my login-screen resolution and refresh rate, and according to a more recent port, it would be as simple as setting the screen resolution in System - Preferences and checking "make default for this computer (only)

See [http://ubuntuforums.org/showthread.php?t=409888&highlight=login+resolution](http://ubuntuforums.org/showthread.php?t=409888&highlight=login+resolution)

I'll check it out and post back (after one week Edgy on my laptop for work, I am currently upgrading my operating system on my home desktop).

---

### Post by victor_c26 on 2007-05-16
I have this same problem. For some reason, setting a custom resolution in xorg.conf, and changing the resolution in Ubuntu only changes the resolution for the Gnome user session. and it leaves the login screen at the default 1024x768 resolution.

It isn't a problem with xorg.conf, it's just that the login screen seems to stay at 1024x768. This is especially annoying when trying to use this comp on my HDTV, since 1024x768@85 isn't supported by this HDTV. So I get a "Resolution not supported" black screen at the login screen. I have to literally type blindly hoping I don't mistype my username and password.

---

