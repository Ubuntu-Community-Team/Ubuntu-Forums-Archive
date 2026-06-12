---
title: "Uninstalling a .deb file"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by Michiba on 2006-05-21
Hi again,

If i install a *.deb file using "sudo dpkg -1 *.deb"

Is there a simple way to cleanly and completly uninstall it.

Sorry 2 posts 2 problems, 1 day

Michiba

---

### Post by mostwanted on 2006-05-21
Search for it Synaptic, mark for removal, apply.

---

### Post by Klaidas on 2006-05-21
Or, you can usin the same dpkg:
```
dpkg -r your_installed_file
```
Note that you give only the 'your_installed_file' for --remove, while --install requires the entire .deb filename. :)
For removing configuration files, use --purge
it will permanently delete every last file associated with the your_installed_file package.

---

