---
title: "Change boot splash screen on G4"
date: 2009-12-28
forum: Apple Hardware Users
---

### Post by .:exLainMaile:. on 2009-12-28
I've read some guide on how to change the splash screen (usplash?) and those says install startup-manager. I did, but when i start startup manager i get "Performing pre-configuration tasks" and then it just closes down. Maybe becouse Ubuntu on PPC doesn't use GRUB? :confused:

Anyway, somebody that knows how to either get startup-manager to work or how i can change the splash screen and gdm theme in another way?

---

### Post by edog76 on 2009-12-28
You can change the gdm screen through the System>>Admin>>Login Window menu. Yaboot will allow you to change the colors, but I think that's as complex as it gets. Manual page is here:
[http://hermes.ppckernel.org/cgi-bin/man/man2html?5+yaboot.conf](http://hermes.ppckernel.org/cgi-bin/man/man2html?5+yaboot.conf)

I think you have to run a command after making changes to the .conf file ```
ybin
``` but I'd check on that with a google search.

---

### Post by .:exLainMaile:. on 2009-12-28
Thx for the GDM change. I'll check it out.
The splash screen i'm talking about is the UBUNTU text and loading bar that appears between yaboot and GDM.

---

### Post by edog76 on 2009-12-28
Oh, right, that is separate. I found this terminal version. So, I think you can follow whatever tutorial you have up to the point of creation of the splash and then go with this:
[http://ubuntuforums.org/showthread.php?t=334428](http://ubuntuforums.org/showthread.php?t=334428)

---

