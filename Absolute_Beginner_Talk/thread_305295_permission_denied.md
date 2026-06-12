---
title: "permission denied"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by tribeone on 2006-11-23
Why am I getting permission denied with this command 

(/usr/share/doc/libdvdread3/README.Debian)? I am the systems admin.

---

### Post by adwait on 2006-11-23
This isn't a command, its a file. If you try to execute a file which is not executable, it will give you a permission denied error even if you are the admin. If you want to make the file executable, use
```
chmod +x <filename>
```

---

### Post by hotbrainz on 2006-11-23
are you logged in as root?

You might wanna add "sudo" before you type any command. On entering the password..you will get the required root privileges.

---

### Post by cantormath on 2006-11-23
> **hotbrainz said:**
> are you logged in as root?

You might wanna add "sudo" before you type any command. On entering the password..you will get the required root privileges.

instead of logging in as root try

```
sudo gedit whateveryouwanttoread.txt
```

then use your password.

---

### Post by junglepeanut on 2006-11-23
Everything has basically been answered, but I just thought to add, if you are not interested in changing a file you can often "see" what is inside with out  being "root".

i.e.

```
gedit thefile
```

would work just as well. This way if it is an important file you do not accidentally make a change (years of windows make me save all the time) then save it to something that should not be changed just yet, or maybe is the original file that you need to move somewhere else and change, it is always nice to have the original. So you can make backups to if you want to make changes or just open every time with the possibility of making changes.

---

### Post by tribeone on 2006-11-23
thanks guy's helped a lot.

---

