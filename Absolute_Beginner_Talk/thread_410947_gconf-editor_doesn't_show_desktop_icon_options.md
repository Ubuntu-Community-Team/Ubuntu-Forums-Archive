---
title: "gconf-editor doesn't show desktop icon options"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by ezphilosophy on 2007-04-16
My friend is trying to remove "computer" and "trash" icons from the desktop.  I don't really know how they got there (as they aren't the default as far as I know).  I quickly knew from experience to just run the gconf-editor and go to apps - nautilus - desktop and just check/uncheck as required.  However, when I went there, nothing is listed!  I'm clueless.

I tried reinstalling gconf-editor and nautilus but with the same result.

Any ideas?

---

### Post by Perfect Storm on 2007-04-16
It's set to hide in the panel tabs. If you type alacarte in the terminal you can edit the tabs.
Other than that the command for gconf editor is;

gconf-editor

---

### Post by metnik on 2007-04-16
check/uncheck

/apps/nautilus/desktop/computer_icon_visible
/apps/nautilus/desktop/trash_icon_visible

---

### Post by ezphilosophy on 2007-04-17
A.I. and metnik, I know you are just trying to help (and thank you for that), but it seems that you didn't even read the post before you responded.

A.I. -  as you can see from my post, I already indeed ran the command that you told me to run.

Metnik - you also just told me to do exactly what I said that I already did.


In the configuration editor, under apps/nautilus/desktop/ there is NOTHING there!  There are no "computer_icon_visible" or anything else!  *This* is the reason I'm clueless.  How is it possible that they aren't there?

---

### Post by metnik on 2007-04-17
it seems very strange, try to create a new user and see if that options are listed.. if your user has gconf broken you can reset the profile deleting .gconf/ and .gconfd/

---

### Post by ezphilosophy on 2007-04-17
"Strange" is just not a strong enough word!  :)  You can't imagine how baffled I was upon seeing that.  I was just sitting there thinking... "huh.  this makes no sense at all."

Nevertheless, good advice.  I'll try that the next time.  Thanks for that.

Metnik, just to follow up in advance, what if that doesn't work?

---

### Post by Patrick K on 2007-04-17
I think I'd do a complete removal and reinstall. A complete removal will remove all remnants of it. A regular removal leaves the conf files and the install package. A complete removal will force a new download when you reinstall.

---

### Post by metnik on 2007-04-17
if new_user.has_nautilus_key?
  your_user.reset  ".gconfd" and ."gconf"
else
  apt-get remove nautilus --purge
  apt-get install nautilus
end

check that nautilus is really removed
$ nautilus
bash: nautilus: command not found

---

