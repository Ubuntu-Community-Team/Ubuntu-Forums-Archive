---
title: "Superuser?"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by Kem Rixen on 2006-01-04
I was trying to install the package that lets you use mp3 files in the terminal, I put in this.
```

sudo apt-get install gstreamer0.8-mad
```

It asked for my password, I gave it and then it said.

```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct this problem.
```

So I type in what is in the paranthesis and it told me.
```

dpkg: requested operation requires superuser privilage
```

I'm stuck now, I don't know what superuser privilage is, any help would be nice.

---

### Post by linuxted on 2006-01-04
[QUOTE=Kem Rixen]I was trying to install the package that lets you use mp3 files in the terminal, I put in this.
```

sudo apt-get install gstreamer0.8-mad
```

It asked for my password, I gave it and then it said.

```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct this problem.
```

So I type in what is in the paranthesis and it told me.
```

dpkg: requested operation requires superuser privilage
```

I'm stuck now, I don't know what superuser privilage is, any help would be nice.[/QUOTE]

You can try "sudo passwd"  to set root password

Then try the dpkg command

---

### Post by piedamaro on 2006-01-04
Put sudo at the beginning again:
sudo dpkg --configure -a

---

