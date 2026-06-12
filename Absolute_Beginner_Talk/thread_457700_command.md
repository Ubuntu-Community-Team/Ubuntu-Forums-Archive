---
title: "command"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by k33bz on 2007-05-28
how do i remove a directory in the terminal

---

### Post by taurus on 2007-05-28
```
rmdir directory (if it's an empty directory)
```
or
```
rm -rf directory (if it's not emty but be real careful with the -rf options...)
```

---

### Post by mattva01 on 2007-05-28
If it is empty the command is "rmdir <name of directory>" 
Otherwise it is "rm  -rf <name of directory>"
EDIT: Beaten to the punch :)

---

### Post by k33bz on 2007-05-28
rm -rf <name of directory>

whats the warning for this command? why be careful

---

### Post by taurus on 2007-05-28
> **k33bz said:**
> rm -rf <name of directory>

whats the warning for this command? why be careful

If you type in the wrong directory, then the whole thing is bye-bye since it would never ask you for a confirmation.  And you cannot recover it in the trash bin, ~/.Trash, either.

---

### Post by mattva01 on 2007-05-28
Because if you use it in the wrong place you can delete all of your files.

Edit:Again! I should type faster :)

---

### Post by Pobega on 2007-05-28
Because it continues recursing. So if you do "rm -rf /usr" you'll effectively delete everything inside of /usr, including the /usr folder itself. So if you're typing "rm -rf /home/k33bz/images/" and you slip and hit enter on "rm -rf /", you're in a lot of trouble.

---

### Post by k33bz on 2007-05-28
o ok, thanks, cant be in the wrong place, just deleting a user, i already disabled the account, but the home directory for it is still there

---

### Post by k33bz on 2007-05-28
so if i run this command

rm -rf /home/realestate/

it will just delete that user correct?

---

### Post by Pobega on 2007-05-28
No, all that will delete is the user's files, not the user itself. But seeing as you said you already removed the user, feel free to get rid of that account's files.

You may want to do it as sudo, for permission reasons.

---

### Post by mattva01 on 2007-05-28
Couldn't you just run "userdel <user>"?

---

### Post by taurus on 2007-05-28
The best way to do it is

```
cd /home
rm -rf realestate
```

---

### Post by k33bz on 2007-05-28
> **Pobega said:**
> No, all that will delete is the user's files, not the user itself. But seeing as you said you already removed the user, feel free to get rid of that account's files.

You may want to do it as sudo, for permission reasons.


lol, ya i was using sudo to do it, thanks

---

### Post by k33bz on 2007-05-28
> **mattva01 said:**
> Couldn't you just run "userdel <user>"?

mm, i didnt even think of that, i will try that instead

nvm, says it dont exist, might have to do kuz i already got rid of that account as a user

---

### Post by k33bz on 2007-05-28
ok, i took care of it, i gotta run to work now

thanks again

---

### Post by mattva01 on 2007-05-28
Ah I thought you had "disabled" the user by randomizing the password or something.

---

