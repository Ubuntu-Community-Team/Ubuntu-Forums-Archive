---
title: "lamp permissions"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by fatnjazzy@gmail.com on 2006-10-24
hi there,
i just installed lamp with your kind help.
i want to create a php file in my /var/www folder, but i see in the properties of this folder that im not the owner so i cant add or delete files in there.
can you explain please how can i add files to this folder and still remain in highest level of security.
thanks again.

---

### Post by CupofDice on 2006-10-24
```

[COLOR="Red"]cd to the directory[/COLOR]
sudo touch file [COLOR="Red"](this should create the file)[/COLOR]
sudo rm file [COLOR="Red"](to delete the file)[/COLOR]

```

---

### Post by fatnjazzy@gmail.com on 2006-10-24
im sorry but i dont understand that (and it didnt do anything).
in windows, Right click and than change the permittions.
as far as i understand, i must be the owner of this folder.
so i went to user profile but nothing there about ownership.
can you explain what should i do?
thanks.

---

### Post by CupofDice on 2006-10-24
"cd" moves you into that folder.
"sudo" gives you the permission to create/delete/edit files in that folder.
"touch" will create the the file.

```

[COLOR="Red"]Open up the terminal[/COLOR]
cd /var/www/
sudo touch fileyouwanttocreate

```

---

### Post by fatnjazzy@gmail.com on 2006-10-24
ok, i see what you saying, but.
when programming if i have to do that, the work will be very very slow.
i want to creat, edit, delete the files form the editor and   not from the shell.
i want to do, file->save as, and save the file to the www dir.
thanks

---

### Post by mssever on 2006-10-24
> **fatnjazzy@gmail.com said:**
> ok, i see what you saying, but.
when programming if i have to do that, the work will be very very slow.
i want to creat, edit, delete the files form the editor and   not from the shell.
i want to do, file->save as, and save the file to the www dir.
thanks

Make yourself the owner of /var/www and all files/subdirectories in it: ```
sudo chown yourusername /var/www && sudo chown -R yourusername /var/www/*
```

---

