---
title: "Mounting shares for different users"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by lazyart on 2008-01-12
I have multiple users on a ubuntu machine and would like to mount different network shares depending on the user logging in.  How do I do this?  I want them to mount automatically on log in.  Any ideas?

---

### Post by Rocket2DMn on 2008-01-12
You should be able to add commands under System->Preferences->Sessions and add a startup program (or a script that mounts the shares you want).

---

### Post by Rocket2DMn on 2008-01-13
I've been looking around for a method of specifying for different users without having to login to their names with X, but I couldn't find anything GNOME specific.  I did find this for X which uses a file called .xinitrc in the $HOME directory.  If you use this, don't forget to "chown" the files to the specific users in their home directories.

---

### Post by lazyart on 2008-01-13
Oops... forgot to mention this is without a gui.  Doing it on a server and don't really want to implore X.

---

### Post by Rocket2DMn on 2008-01-13
Yeah, that's an important piece of information.  If this is for people logging into the server, then they are getting to bash shell when they log in.  You should be able to add the mount lines to ~/.bashrc
This script is executing when a user logs into a shell.  It can be modified even when a user is logged in and reloaded with the changes using
```
source ~/.bashrc
```

---

