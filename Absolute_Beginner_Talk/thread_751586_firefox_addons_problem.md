---
title: "firefox addons problem"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by seamustry on 2008-04-10
i have hardy heron beta  and i didn't like the new firefox because some addons don't work with it. so i uninstalled it using synaptics and installed firefox 2.0.0.13. now i can't install any addons!!!

when i click on addon and say add to firefox, it downloads it and then gives an error that it couldn't be installed (some error 203 or something)...what did i mess up??

thanks for any help that you guys give!        :guitar:

---

### Post by wolfen69 on 2008-04-10
firefox may be using firefox3 config files in your home folder. (hidden files)

---

### Post by seamustry on 2008-04-10
thanks for replying...so how can i check for that?

---

### Post by vasiliymeshko on 2008-04-10
In your home folder there should be a .mozilla/firefox folder. Check 'Show hidden files' in nautilus to see.

---

### Post by manij on 2008-04-12
Same problem here!

if it is using ff3 config files, how do i fix the issue. I rely very heavily on the addons!

Thanks
Mani

---

### Post by dondad on 2008-04-12
> **manij said:**
> Same problem here!

if it is using ff3 config files, how do i fix the issue. I rely very heavily on the addons!

Thanks
Mani

find the mozilla firefox folder in your home directory (it will have a dot in front of the name making it invisible, you can see it by selecting show hidden files in the view tab). Delete that folder to completely remove all of the old Firefox stuff and reinstall Firefox. That should fix the problem. (the install will recreate the folder and a new profile.)

If you have bookmarks or other data, save it somewhere else and restore it after you reload

---

### Post by louieb on 2008-04-12
See post 15. [http://ubuntuforums.org/showthread.php?t=733048](http://ubuntuforums.org/showthread.php?t=733048)

Had the same problem with Add-ons. This fixed it.

Also see post 18. This will work for some extensions in FF3.

---

### Post by philinux on 2008-04-12
The easiest way to resolve this is to back up your bookmarks and delete the .mozilla folder or rename it just in case.

Once FF3 has used the profile FF2 cant read it.

Once you have deleted the folder fire up FF2 and import back you bookmarks.

I'm using FF3 beta5 and the addons I use are working fine.

---

