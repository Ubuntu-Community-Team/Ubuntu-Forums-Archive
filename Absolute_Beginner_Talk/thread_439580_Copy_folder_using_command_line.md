---
title: "Copy folder using command line"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Michaelt74 on 2007-05-10
How do I copy a folder on my desktop to another folder using the command line. i.e I want to copy the folder 'Aqua' on my desktop to /usr/share/amsn/skins. What is the command using the terminal? 

Thanks!

---

### Post by Bachstelze on 2007-05-10
```
sudo cp -R ~/Desktop/Aqua /usr/share/amsn/skins
```

You basically do the same thing you would do if Aqua was a file, you just add the -R switch.

---

### Post by Foxmike on 2007-05-10
```
sudo cp -R ~/Desktop/Aqua /usr/share/amsn/skins/
```

Sudo is because you need root privileges to write something outside your home directory.

~ Stands to be a shortcut to your home direcory.  You can use it as it is.

cp is the "Copy" command.  -R is the "recursive" option which means "copy the folder and it's content".

Hope it helps!:)

Good luck!:)

Regards,

-FM

---

### Post by fakie_flip on 2007-05-10
```
man cp
```

---

### Post by Foxmike on 2007-05-10
> **HymnToLife said:**
> ```
sudo cp -R ~/Desktop/Aqua /usr/share/amsn/skins
```

You basically do the same thing you would do if Aqua was a file, you just add the -R switch.

You are a fast typer!:)

-FM

---

### Post by Michaelt74 on 2007-05-10
Thanks for the amazingly quick response!

---

