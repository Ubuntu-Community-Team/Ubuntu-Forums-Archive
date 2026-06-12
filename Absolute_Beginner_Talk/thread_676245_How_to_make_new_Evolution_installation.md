---
title: "How to make new Evolution installation?"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by pointyblue on 2008-01-23
Suddenly Evolution email doesn't work. :confused:

When I click the icon it opens the program, then closes it again instantly.

I've tried removing these packages in Synaptic:

[INDENT]Evolution
Evolution common
Evolution exchange
Evolution plugins[/INDENT]

I then reinstalled them, but it seems the computer is still using the old (corrupt?) packages in stead of replacing them with fresh packages from the internet...

The result is that Evolution still isn't working and I can't access my emails and my contacts.

Can anyone tell me how to make Synaptic use fresh packages in stead of the possibly corrupt packages on my computer. Or alternatively: Is there another way to gain access to my emails and my contacts?

(Too bad Ubuntu doesn't have a System Restore option as in MS Windows - that would have fixed this... :(  )

---

### Post by gvartser on 2008-01-23
Try:

1) Make sure you are not running evolution.

2) Rename your old evolution repository, stored in your home folder.
    ```
mv ~/.evolution ~/.evolution.backup
```

3) Start Evolution again.

This will remove all of your saved previous settings in Evolution, but hopefully it will make evolution work again.

Best regz,
/G

---

### Post by Hospadar on 2008-01-23
for general reference, most applications keep their config info in a hidden directory somewhere in your home directory, so you can try looking for something that looks appropriate who's name starts with a dot ('.') and deleting or better, renaming it and seeing if that clears up the issue (if a re-install doesn't work).

---

### Post by gvartser on 2008-01-23
> **Hospadar said:**
> for general reference, most applications keep their config info in a hidden directory somewhere in your home directory, so you can try looking for something that looks appropriate who's name starts with a dot ('.') and deleting or better, renaming it and seeing if that clears up the issue (if a re-install doesn't work).

As i said in the previous post.

The Evolution config folder is called ".evolution" and is placed in the homedir.

/g

---

### Post by pointyblue on 2008-01-24
Thanks for helping out, guys!

When I do
```
v ~/.evolution ~/.evolution.backup
```

It returns
```
bash: v: command not found
```

Can you figure out what's wrong?

---

### Post by FuturePilot on 2008-01-24
Try
```
mv ~/.evolution ~/.evolution.backup
```

---

### Post by pointyblue on 2008-01-28
Thanks, that did it!   ):P

Could you explain what exactly the parameters of that command do? (Trying to learn here.)   ;)

---

### Post by gvartser on 2008-01-28
It renames the folder:
.evolution to .evolution.backup

"mv" is equal to move, so what you are doing is simply renaming the directory by moving it..

Sorry about the typo, sometimes it goes to fast..

/g

---

### Post by pointyblue on 2008-01-28
Ok, thanks!

---

