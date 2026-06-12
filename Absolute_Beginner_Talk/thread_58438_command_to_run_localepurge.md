---
title: "command to run localepurge?"
date: 2005-08-20
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-08-20
How do I run localepurge? I ran it once a while ago and I can't remember the command line to do it again? :(

---

### Post by az on 2005-08-20
sudo remove-language-locales?

---

### Post by gammyhand on 2005-08-20
[QUOTE=azz]sudo remove-language-locales?[/QUOTE]
 Thanks but I want the command to open the GUI.

---

### Post by twowheeler on 2005-08-20
If it's installed and configured, 'sudo localepurge' should do it.  If it is installed and nothing happens, it is probably not configured right.  Read the 'man localepurge' page for details.  I would note that after the first run, it will be run automatically after each apt-get so you should not have to do it again, according to the docs.

Also there are rather dire warnings about using it at all on the synaptic description page.  Might want to think about that.

---

### Post by gammyhand on 2005-08-20
[QUOTE=twowheeler]If it's installed and configured, 'sudo localepurge' should do it.  If it is installed and nothing happens, it is probably not configured right.  Read the 'man localepurge' page for details.  I would note that after the first run, it will be run automatically after each apt-get so you should not have to do it again, according to the docs.

Also there are rather dire warnings about using it at all on the synaptic description page.  Might want to think about that.[/QUOTE]
 Thanks :)

---

