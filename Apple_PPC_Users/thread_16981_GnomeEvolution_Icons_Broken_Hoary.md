---
title: "Gnome/Evolution Icons Broken? Hoary"
date: 2005-02-25
forum: Apple PPC Users
---

### Post by seed on 2005-02-25
installed hoary for ppc. It works pretty well except there are missing images. First it seemed just the evolution and gnome-help icons but all of the icons within evolution are missing or not looking in the right place. Also, the lower left "Click here to hide all windows and desktop" icon is missing as well. All are replaced with a red X. Any ideas?

Thanks,

-Christian

---

### Post by nubeiro on 2005-02-25
I'm on hoary ppc and have the same problem.
Curiously enough, gnome complains about not finding the icons, but i can see they are there. 
I get the red X for missing icons on panels, and the default gnome icon for everything in nautilus  :confused:

---

### Post by gwilkes on 2005-02-25
I have this same issue, I saw this talked about in the hoary development forum and it seems this is a PPC issue.  However, this is why hoary is not released yet, there is definately bugs.  The only way I know to get this icons completely back is to go back to warty for now.  I'm sure they will figure this bug out eventually though.

---

### Post by val1984 on 2005-02-27
I had the same kind of problem with debian/sid.

It was solved with this command :
```
sudo rm -f /usr/share/icons/*/icon-theme.cache
```

---

### Post by seed on 2005-03-01
Worked! Thanks a lot! Now I habe a working ubuntu with an atheros wireless card. Very happy.

-Christian

---

### Post by khc on 2005-03-01
Thanks, do you know the bugzilla # btw?

---

