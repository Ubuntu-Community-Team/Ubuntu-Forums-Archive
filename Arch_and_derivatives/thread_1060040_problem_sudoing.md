---
title: "problem sudoing"
date: 2009-02-04
forum: Arch and derivatives
---

### Post by stonecoldjha on 2009-02-04
hi,i installed sudo.i logged in as a non-root user,and then in the terminal,i typed:
sudo pacman -S vlc
I was prompted for password.I keyed in my root password.But,it said,"sorry,try again".

How do i fix this?

---

### Post by Nepherte on 2009-02-04
I you added the user to the /etc/sudoers file, you should provide the user password when using sudo. See the wiki for more information: [http://wiki.archlinux.org/index.php/Sudo#Enabling_sudo_for_Users](http://wiki.archlinux.org/index.php/Sudo#Enabling_sudo_for_Users)

---

### Post by SkonesMickLoud on 2009-02-04
Sudo uses your user password, not roots password.

---

