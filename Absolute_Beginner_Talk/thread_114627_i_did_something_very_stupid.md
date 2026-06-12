---
title: "i did something very stupid"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by djlilyazi on 2006-01-08
Hello,

everytime i start my computer i get an error that says this :

"your $home/.dmrc files has incorrect permissions and is being ignored"

how to i fix this error ?

thanks

DJ LIL YAZI

---

### Post by shadesfox on 2006-01-08
chmod 600 ~/.dmrc

That will put the right permissions on the file.

---

### Post by djlilyazi on 2006-01-09
[QUOTE=shadesfox]chmod 600 ~/.dmrc

That will put the right permissions on the file.[/QUOTE]

wow thanks i willl do that and restart to see if it comes up again..

thank uuuuuuuu

---

### Post by djlilyazi on 2006-01-09
[QUOTE=shadesfox]chmod 600 ~/.dmrc

That will put the right permissions on the file.[/QUOTE]

that did not work...

ok the exact error is :

" your $HOME/.dmrc files has inccorect permission and is being ignored.  This prevents the default session and language from being saved. File should be owned by user and have 644 permissions."

sooo........what do i do now to solve this ?

---

### Post by lyly on 2006-01-09
[QUOTE=djlilyazi]
" your $HOME/.dmrc files has inccorect permission and is being ignored.  This prevents the default session and language from being saved. File should be owned by user and have 644 permissions."
[/QUOTE]

```

$chmod 644 ~/.dmrc
$chown yourusername ~/.dmrc
```

chmod change the permission, and your error recommend 644 permission. chown change the owner of the file...

---

### Post by shadesfox on 2006-01-09
One thing you could try is 
sudo rm -f ~/.dmrc

This will remove your old .dmrc and next time you log in a new default one will be made.

---

### Post by lyly on 2006-01-09
[QUOTE=lyly]```

$chmod 644 ~/.dmrc
$chown yourusername ~/.dmrc
```

chmod change the permission, and your error recommend 644 permission. chown change the owner of the file...[/QUOTE]

Oups I forget to precise you must be root to do this:
```

$sudo chmod 644 ~/.dmrc
$sudo chown yourusername ~/.dmrc
```

---

