---
title: "Can't remove applications"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by phoenix23 on 2007-05-28
When I go to remove a program through the add/remove under applications, I get a strange error.

In the details section it keeps saying "package python/beryl-settings is not configured yet". How do I configure them?

---

### Post by mahiyar on 2007-05-28
This can usually mean that the packages are half installed, on reboting the machine try to run this from the CLI >> sudo apt-get -f install

---

### Post by phoenix23 on 2007-05-28
I ran that command, and this is what I got:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gtkpod-aac
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
20 not fully installed or removed.
Need to get 0B of archives.
After unpacking 2277kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 112516 files and directories currently installed.)
Removing gtkpod-aac ...

(update-desktop-database:5903): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gtkpod-aac (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 gtkpod-aac
E: Sub-process /usr/bin/dpkg returned an error code (1)
stephen@stephen-desktop:~$ 


---

### Post by Hobo Joe on 2007-05-28
I know this might not be the best place to post this, but I keep on hearing people talk about add/remove programs, but I don't have it.... Am I missing something here?

---

### Post by phoenix23 on 2007-05-28
It should be under the application menu in the top left corner.

---

### Post by Hobo Joe on 2007-05-28
> **phoenix23 said:**
> It should be under the application menu in the top left corner.


I know, but it's not. :/

Oh well, I use synaptic and the termial for that stuff anyway.

---

### Post by techno-mole on 2007-05-28
i dont know if this will work, but i had the same problem in edgy once, the add/remove option vansihed, still dont know why, but i did some research on it and found this command to run in terminal, but i never tested it, so its up to you if you want to try it.

code --> sudo apt-get upgrade gnome-app-install

like i said i dont know if it works, maybe some one will know if you ask about before you try it.
cheers

---

