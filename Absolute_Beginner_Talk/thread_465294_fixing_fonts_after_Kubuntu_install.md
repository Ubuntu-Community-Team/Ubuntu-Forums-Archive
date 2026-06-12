---
title: "fixing fonts after Kubuntu install"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by luvinit on 2007-06-05
I decided to try kubuntu. Installing it has buggered up the font rendering in gnome sessions. Some are still sharp, but Firefox, Amarok and Kompozer look truly awful now. Anybody know how to fix this? I restored a backup of my previous setup and it has done nothing to help.
I am using Feisty fawn, nvidia card. Thanks.

---

### Post by luvinit on 2007-06-05
OK as often happens I end up finding the solution.

edit fonts config like this

sudo gedit /home/username/.fonts.conf


delete the top lines

<?xml version='1.0' ?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

Word of advice, don't bother installing kubuntu unless you really want to  use it as your main setup.

---

