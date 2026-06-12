---
title: "Truecrypt Using Command"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by saj0577 on 2008-03-27
Right I have a problem here with using truecrypt and the terminal. What i have is a command to mount a truecrypt volume. 

When I use JUST a keyfile i can mount the drive without it asking for any confirmaion using the command:

```
truecrypt truecrypt/tester /media/truecrypt1  --keyfiles="Song name.mp3"
```

All works fine.

But when i try to use a password by itself or with a keyfile as well it will ask me for my password again. For example:
```

truecrypt truecrypt/tester /media/truecrypt1  --password="password"

truecrypt truecrypt/tester /media/truecrypt1  - p "password"
```

None of these work when they should according to 
```
truecrypt - h
```

They still ask me for the password even though it is stated above. Pleas do not comment on the HUGE security hole in this method. Does anyone know how to get it to read the password variable?

Saj

---

### Post by TheWizzard on 2008-03-27
try without the double quote (") signs.

---

### Post by TheWizzard on 2008-03-27
> **saj0577 said:**
> 
They still ask me for the password even though it is stated above. Pleas do not comment on the HUGE security hole in this method. Does anyone know how to get it to read the password variable?

Saj

why on earth do you want to apply this method? 
this is like a very secure lock and then leaving the key in...

---

### Post by saj0577 on 2008-03-27
Well my scenario, is I have a script but i want on the end of the script to save a file into the secure volume, then disconnect the volume and shut down my pc. The script is not very automated when you have to type in a password. 
Any alternatives? (not bothered about using truecrypt in particular)

Saj

---

### Post by TheWizzard on 2008-03-28
it's no use encrypting anything when you have tha password in a script. 
why bother?!?

---

### Post by saj0577 on 2008-03-28
Yeah ive changed it so it asks the user for the password at the start. Less automated but more secure.

Saj

---

