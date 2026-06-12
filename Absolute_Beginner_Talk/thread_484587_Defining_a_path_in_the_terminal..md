---
title: "Defining a path in the terminal."
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by kevCast on 2007-06-26
Hello. I was wondering, how would I go about defining a path in the terminal? I need to move a file to a shared folder, and I can sudo bash it there, but I forgot how to define the path of the file and how to move it to the /usr/share folder.

All help is appreciated, thank you.

---

### Post by Gigzaholic on 2007-06-26
I don't know how to define the path but to move files do this:

```
sudo mv (path of file) /usr/share folder
```

---

### Post by kevCast on 2007-06-26
> **Gigzaholic said:**
> I don't know how to define the path but to move files do this:

```
sudo mv (path of file) /usr/share folder
```

Thank you.

:)

Now if anyone would be so kind as to post how to define a path, I'd be on my way.

*Edit: Nevermind, I got it.*

---

### Post by Bluecircle on 2007-06-26
> **kevCast said:**
> Thank you.

:)

Now if anyone would be so kind as to post how to define a path, I'd be on my way.

What do you mean? Like 

change directory
```

$ cd /path/

```

move a file
```

$ mv /source/ /destination/

```


cd from home folder to my desktop, then move folder "datarec" from my desktop to my home folder:
```

$ cd Desktop/ && mv datarec /home/brian/

```


???

---

### Post by kspn on 2007-06-26
From memory the command to update the path is
```
export PATH=$PATH:{NewPath}
```
But I think that this needs to be run each time you reboot.

You could put it into the **$HOME/.bash_profile** File and then it would be set on each login for that user.

---

### Post by alan_daniel on 2007-06-26
> **kspn said:**
> From memory the command to update the path is
```
export PATH=$PATH:{NewPath}
```
But I think that this needs to be run each time you reboot.

You could put it into the **$HOME/.bash_profile** File and then it would be set on each login for that user.

Isn't the traditional place for path additions the .bashrc?

---

### Post by kspn on 2007-06-26
> **alan_daniel said:**
> Isn't the traditional place for path additions the .bashrc?

If it is a task you want to run when the Terminal gets opened, every time.

I believe that profile is the location for tasks that are applied globally to your login (so the path would also be valid from within the GUI, whereas I don't believe that it would be if it was in bash_rc)

If I am wrong then I need to know but I believe that is the difference between  the two files.

---

