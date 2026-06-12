---
title: "[SOLVED] add /usr/local/mercury-0.13.1/bin to my PATH"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by rmx on 2008-01-28
Hello,

How can I add /usr/local/mercury-0.13.1/bin to my PATH permanently?

thanks

rmx

---

### Post by emarkd on 2008-01-28
Add it into your .bashrc file.  From the terminal in your home directory:

```
gedit .bashrc
```

When your editor comes up, look for path setting already there.  There may already be a line for that where you can add yours. If not, add a line like this:

export PATH=$PATH:/usr/local/mercury-0.13.1/bin

and save it.  You'll have to log out and back in to see the changes.  Of course, this change only effects your login.

---

### Post by infurnus on 2008-01-28
You should probably either softlink or copy the binaries to /usr/bin. If you still want to, edit .bashrc and use export below on a new line. First echo your path and copy the settings down just in case ^_^.

```

$ echo $PATH

```

```

$ cd ~
$ nano .bashrc
# including mercury bin folder
export PATH=${PATH}:usr/local/mercury-0.13.1/bin

```

This should take care of it so you don't have to reboot.
```

$ export PATH=${PATH}:/usr/local/mercury-0.13.1/bin

```

---

