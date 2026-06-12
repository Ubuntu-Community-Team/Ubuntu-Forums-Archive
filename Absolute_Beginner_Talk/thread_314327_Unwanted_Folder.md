---
title: "Unwanted Folder"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by tst76 on 2006-12-07
I have successfully installed and partly configured Ubuntu on my desktop computer, but have recently acquired and new and unwanted Icon on my desktop.  It is locked (root only) so I cannot change permissions.  Even in the terminal it tells me the file doesn't exist.  I now realize that the folder is exactly the same size (67.2 Gig) as my desktop.  So, any ideas what I've done and how to undo it?

---

### Post by Tomosaur on 2006-12-07
It may well be nothing more than a link, although this would not explain why it's root only. Please go to Applications > Accessories > Terminal. Once there, type:
```

ls -l ~/Desktop

```

copy and paste the output here please :)

---

### Post by tst76 on 2006-12-07
this is the result :


total 4
drwxr-xr-x 2 root root 4096 2006-12-05 19:41 Desktop

---

### Post by Tomosaur on 2006-12-07
Hmmm, odd, can you paste the output of
```

ls -al ~/Desktop

```

since you seem to have hidden files there also. You can quite easily modify the permissions of that folder, but it shouldn't be root in the first place so it's best to see what's actually happened. Also, please paste the output of:
```

ls -al /root

```

---

### Post by tst76 on 2006-12-07
this is the result of your first request:

total 12
drwxr-xr-x  3 tst  tst  4096 2006-12-07 16:10 .
drwxr-xr-x 53 tst  tst  4096 2006-12-07 17:48 ..
drwxr-xr-x  2 root root 4096 2006-12-05 19:41 Desktop

---

### Post by tst76 on 2006-12-07
this is the response to second request:

total 568
drwxr-xr-x 13 root root   4096 2006-12-07 16:01 .
drwxr-xr-x 22 root root   4096 2006-11-21 17:52 ..
drwx------  2 root root   4096 2006-11-16 16:37 .aptitude
-rw-------  1 root root     25 2006-12-06 19:06 .bash_history
-rw-r--r--  1 root root   2227 2006-06-30 15:03 .bashrc
drwx------  3 root root   4096 2006-12-05 19:38 .config
drwxr-xr-x  2 root root   4096 2006-12-07 16:01 Desktop
-rw-------  1 root root     16 2006-11-19 13:19 .esd_auth
-rw-r--r--  1 root root 494879 2006-11-29 21:30 .fonts.cache-1
drwx------  3 root root   4096 2006-12-07 16:01 .gconf
drwx------  2 root root   4096 2006-12-07 16:10 .gconfd
drwx------  4 root root   4096 2006-12-07 16:01 .gnome2
drwx------  2 root root   4096 2006-11-16 16:54 .gnome2_private
drwx------  2 root root   4096 2006-12-04 18:25 .gnupg
-rw-------  1 root root     33 2006-12-05 19:41 .gtk-bookmarks
-rw-------  1 root root     35 2006-12-06 19:06 .lesshst
drwxr-xr-x  3 root root   4096 2006-12-07 16:01 .nautilus
-rw-r--r--  1 root root    141 2006-06-30 15:03 .profile
-rw-r--r--  1 root root   1323 2006-11-19 23:29 .recently-used.xbel
-rw-r--r--  1 root root      0 2006-12-06 19:03 .sudo_as_admin_successful
drwx------  3 root root   4096 2006-12-07 14:59 .synaptic
drwxr-xr-x  2 root root   4096 2006-11-17 20:18 .wapi

---

### Post by Tomosaur on 2006-12-07
Ok, well it looks to me like the root account has been set up incorrectly. Your root account should not have it's own Desktop folder, and your ordinary desktop folder should neither be root nor so big. You'll need to find it out what the contents of the folder on your own desktop are. My guess is that they're just links to the rest of your filesystem. If the folder on your desktop is called Desktop, then use this command:
```

ls -la ~/Desktop/Desktop

```

If I'm correct, the output should look similar to this:
```

drwxr-xr-x 2 root root 4096 2006-12-05 19:41 bin -> /bin
drwxr-xr-x 2 root root 4096 2006-12-05 19:41 boot -> /boot
drwxr-xr-x 2 root root 4096 2006-12-05 19:41 dev -> /dev

```
 and so on. IF, AND ONLY IF, this little arrows are present, you can delete the contents of the folder using
```

sudo rm ~/Desktop/Desktop/*

```

If you get any error messages, post them up here. Once the folder is empty, type:
```

sudo rmdir ~/Desktop/Desktop

```

Let us know how it goes. Remember, only delete if the little arrows are there. If not, something else is wrong.

---

### Post by tst76 on 2006-12-07
Sorry, no arrows.  This was the result:

total 8
drwxr-xr-x 2 root root 4096 2006-12-05 19:41 .
drwxr-xr-x 3 tst  tst  4096 2006-12-07 16:10 ..

---

### Post by Tomosaur on 2006-12-07
Uhh, use:
```

ls -la

```
since it says you have 8 files, some must be hidden. It doesn't look like anything serious anyway, just a copied file that must have happened while you'd been using sudo. You're probably safe to delete it using
```

sudo rm -rf ~/Desktop/Desktop

```

---

### Post by tst76 on 2006-12-07
Success.  It's gone.  Thanks for your help.  Can you suggest a source to list and explain the terminal commands that I could maybe print out.

Thanks again.

---

### Post by Tomosaur on 2006-12-07
[http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/) is a great page, each command links to an explanation. You can also just use 'man command' where 'command' is someting you're unsure of, for example: 'man rm' or 'man cp'

---

