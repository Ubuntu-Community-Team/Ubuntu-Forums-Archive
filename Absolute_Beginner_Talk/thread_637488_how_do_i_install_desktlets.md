---
title: "how do i install desktlets?"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by antisocialist on 2007-12-11
[http://www.gnome-look.org/content/show.php/Sidebar+Screenlet+%28Vista%27ish+look%29?content=63172](http://www.gnome-look.org/content/show.php/Sidebar+Screenlet+%28Vista%27ish+look%29?content=63172)
the app there is what i want, how do i install it?

---

### Post by PeterJS on 2007-12-11
> **antisocialist said:**
> [http://www.gnome-look.org/content/show.php/Sidebar+Screenlet+%28Vista%27ish+look%29?content=63172](http://www.gnome-look.org/content/show.php/Sidebar+Screenlet+%28Vista%27ish+look%29?content=63172)
the app there is what i want, how do i install it?

First install Screenlets:
[http://www.screenlets.org/index.php/FAQ#Installation_instructions_for_Ubuntu_users_.28Edgy_Eft.2FFeisty_Fawn.2FGutsy_Gibbon.29](http://www.screenlets.org/index.php/FAQ#Installation_instructions_for_Ubuntu_users_.28Edgy_Eft.2FFeisty_Fawn.2FGutsy_Gibbon.29)

Then extract the app you want to ~/.screenlets

And last run:
```

screenlets-manager

```And off you go.

---

### Post by antisocialist on 2007-12-11
i dont have a ~/screenlets directory... and yes, i installed screenlets

it said:
Invalid archive. Archive must contain a directory with the screenlet's name.
when i tried to install it

---

### Post by jryprt on 2007-12-11
> **antisocialist said:**
> i dont have a ~/screenlets directory... and yes, i installed screenlets

it said:
Invalid archive. Archive must contain a directory with the screenlet's name.
when i tried to install it

Here is a link [http://ubuntuforums.org/showthread.php?t=614031](http://ubuntuforums.org/showthread.php?t=614031) 
you need to make a  .screenlets folder

---

### Post by stchman on 2007-12-11
> **antisocialist said:**
> [http://www.gnome-look.org/content/show.php/Sidebar+Screenlet+%28Vista%27ish+look%29?content=63172](http://www.gnome-look.org/content/show.php/Sidebar+Screenlet+%28Vista%27ish+look%29?content=63172)
the app there is what i want, how do i install it?

sudo apt-get -y install gdesklets

Once that is done then you will have a menu item and you can install the desklets.

Once you have your desklets you will need to add the gdesklets-daemon to your sessions for startup.

---

