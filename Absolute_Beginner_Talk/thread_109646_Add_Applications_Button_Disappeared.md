---
title: "Add Applications Button Disappeared?"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by rizzyc on 2005-12-29
I used to have that add apps button under Applications, not it just disappeared?? I dont know where it went?
Do You?

---

### Post by Sutekh on 2005-12-31
Go to the Menu Editor; Applications -> System Tools -> Application Menu Editor
and see if there is an entry under 'Applications' for the 'Add Applications' Program, it might be greyed/unchecked.

If it's not there at all, you can add it by clicking the 'New Entry' button and entering these details;

```

Name : Add Applications
Comment : Install and remove applications
Command : /usr/bin/gksudo /usr/bin/gnome-app-install

```

The command line is important, the others are up to you, but that's what my entry has.

The icon that I have is /usr/share/pixmaps/update-notifier.png

---

### Post by ncappel1 on 2006-01-27
I got very excited when I found this post, I have the same problem and I thought that it would be solved. Alas, after following the directions and clicking on the new icon I get an error message that says:

> Failed to run /usr/bin/gnome-app-install as user root:
 Child terminated with 1 status

Oh no!

---

### Post by Sutekh on 2006-01-28
[QUOTE=ncappel1]I got very excited when I found this post, I have the same problem and I thought that it would be solved. Alas, after following the directions and clicking on the new icon I get an error message that says:



Oh no![/QUOTE]
Do you get this error before or after you are prompted for your password?

Can you open other applications such as SYnaptic, or anything in the System -> Administration menu?  (things that require a password)

---

### Post by hen3rz on 2006-01-28
> I used to have that add apps button under Applications, not it just disappeared?? I dont know where it went?
Do You?

To re add it to your menu click **Applications > Systems Tools > Applications Menu Editor**. Then you will see two windows. In the right window tick the Add Applications Box. The Add Applications buttun should now be on the menu.

This button can also be found in **System > Administration > Add Applications**

---

### Post by ncappel1 on 2006-01-29
Suteckh, I do have to enter in my password, it is after I press enter that the window comes up. I can still open the package manager from the System-->Administration-->synaptic package manager drop down.

---

### Post by ncappel1 on 2006-02-24
I finally realized my problem. I did a compkete removal of firefox (1.07) to install 1.5 and it seems that removing that I uninstalled the package, gnome-app-install, which is somehow tied to it.

if reinputing the command line doesn't work, try searching for "gnone-app-install" in synaptic and see if it is installed.

---

