---
title: "curiosity: can I use Ubuntu repos in Debian Etch?"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by icceric on 2008-01-29
Hi, I have been enjoying a tremendous amount of stability using Debian 4.0r2 (for other enjoyment purposes I flip back and forth between Ubuntu and Kubuntu as well).

Obviously the Ubuntu repos have a lot more to offer... especially in non-free software, such as Xara and Firefox... I know and understand that Iceweasel is rebranded Firefox, but for use with Eclipse (as a built-in html previewer) I must have a fully installed (package managed) Firefox.  Eclipse doesn't recognize Iceweasel and when I install Firefox according to Mozilla's instructions, it installs and runs great, but because it is basically an unarchived folder in my home drive and not really integrated into Debian (like Iceweasel is), Eclipse won't recognize it.  Anyway, I am trying to stick with Stable packages for the Debian install and hope I can add some Ubuntu repos to my sources list.  

And if I can, for using Etch (4.0r2), which repos would I use?   I assume not the Gutsy ones??

Thanks for your help, it is greatly appreciated.

Eric

---

### Post by shad0w_walker on 2008-01-29
I believe in THEORY you could setup things to access the Ubuntu repos however you are likely to encounter a million and one dependencies or package conflicts that won't easily be sorted out.

---

### Post by p_quarles on 2008-01-29
The link below discusses how to mix Debian repositories (e.g., Etch and Lenny) without breaking things. The same *should* apply to mixing the Etch repos with a set of Ubuntu repos:
[http://forums.debian.net/viewtopic.php?t=15612](http://forums.debian.net/viewtopic.php?t=15612)

If Firefox is the main problem here, though, I would recommend putting that into your user's local executable path. That way it would be easy to create a desktop/panel launcher for it.

---

### Post by icceric on 2008-01-29
> If Firefox is the main problem here, though, I would recommend putting that into your user's local executable path. That way it would be easy to create a desktop/panel launcher for it.

That *is the main* concern.  But I am not exactly following, where would that path be located and is a drag and drop of the already unarchived firefox folder be good enough?  Or uninstall and unarchive to the path in question?

As for the other info, I will look into it now.  Thank You both!

Regards,
Eric

---

### Post by icceric on 2008-01-29
Well, I tried to add a few Ubuntu repos, commenting out Debian ones because it would just try to install Iceweasel, but a ton of dependencies showed up and even some that wanted to remove some installed software to replace with different versions.  I'm thinking of making a dummy install to mess around with to see what would happen.  Thank You.

Regards,
Eric

---

