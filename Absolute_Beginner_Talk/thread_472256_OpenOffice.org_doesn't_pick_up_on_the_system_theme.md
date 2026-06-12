---
title: "OpenOffice.org doesn't pick up on the system theme"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by James Bennett on 2007-06-12
I've been using AbiWord for a good long while, but wanted to add OpenOffice as a possible replacement, particularly as there are lots of powerpoint presentations in my classes right now. 

However, I noticed that OpenOffice doesn't seem to obey the themes that I install, instead showing an ugly, flat appearance to things like the scrollbars. Attached is a screengrab of each.

I've searched the forums, but my search-fu might not be strong enough to find what I'm looking for, unfortunately. 

Thank you in advance for any help with this matter.

---

### Post by starcraft.man on 2007-06-12
Oh, right, I think I know what is wrong here.

Ok open up any terminal real quick and paste this command into it.

```
sudo cp -r ~/.themes /root
```

Then restart OO. That should do it I believe. If you change the theme ever again, reapply the command.

---

### Post by qamelian on 2007-06-12
> **starcraft.man said:**
> Oh, right, I think I know what is wrong here.

Ok open up any terminal real quick and paste this command into it.

```
sudo cp -r ~/.themes /root
```Then restart OO. That should do it I believe. If you change the theme ever again, reapply the command.

No, this only applies to apps that you run with admin privileges, like synaptic. It looks like what is missing are the packages to provide gnome/gtk support. You need to install openoffice.org-gnome and openoffice.org-gtk.

---

### Post by starcraft.man on 2007-06-12
> **qamelian said:**
> No, this only applies to apps that you run with admin privileges, like synaptic. It looks like what is missing are the packages to provide gnome/gtk support. You need to install openoffice.org-gnome and openoffice.org-gtk.

Oh, my bad... how could you have installed OO without those packages though? Kinda an odd thing...

How did you install your copy of OO James? Was it the default? An RPM? Updated from repo?

---

### Post by qamelian on 2007-06-12
> **starcraft.man said:**
> Oh, my bad... how could you have installed OO without those packages though? Kinda an odd thing...

Checking OOo's dependencies through apt-cache shows openoffice.org-gnome to only be a suggestion, not a required dependency, and openoffice.org-gtk is a dependency of openoffice.org-gnome. So it is quite possible to install OOo without these to packages.

---

### Post by starcraft.man on 2007-06-12
> **qamelian said:**
> Checking OOo's dependencies through apt-cache shows openoffice.org-gnome to only be a suggestion, not a required dependency, and openoffice.org-gtk is a dependency of openoffice.org-gnome. So it is quite possible to install OOo without these to packages.

Right. I see, I did a quick check myself just now. I've always used the latest builds and thus usually just alien the RPMs, they always have the GNOME and KDE integration packages in them, thus I've never been without the gtk/GNOME support.

Oh well, learn something every day. Thanks for pointing that out, I'll remember :).

---

### Post by James Bennett on 2007-06-13
> **starcraft.man said:**
> Oh, my bad... how could you have installed OO without those packages though? Kinda an odd thing...

How did you install your copy of OO James? Was it the default? An RPM? Updated from repo?

I installed from the Ubuntu repositories. 

I installed openoffice.org-gnome and all works now. 

Thanks a lot, guys!

:D

---

### Post by starcraft.man on 2007-06-13
> **James Bennett said:**
> I installed from the Ubuntu repositories. 

I installed openoffice.org-gnome and all works now. 

Thanks a lot, guys!

:D

Hehe. Your welcome. Oh and ya should still run my command up there if ya want all the root/system apps to look like your user theme.

Oh and one more thing, OO 2.2.1 just got released if you like being on top you'll have to install it yourself manually I think, the repos might take a while getting to it... just a note for your info.

Off I go now, other people to help.

---

