---
title: "Removing a file-folder directory at the path: /home"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by annda on 2007-04-16
```
sudo cd /home
sudo rm -rfi stuff
```

this will ask you about all the files - the -i option. it is safer than without asking: (use this if you are sure you have entered everything right)

```
sudo cd /home
sudo rm -rf stuff
```

---

### Post by Kisil on 2007-04-16
If you know how what the command does and you're sure you entered it correctly, you don't need to use interactive mode.  -i would allow you to delete some files and not others, but if you're using -r on a directory it means you want the whole thing gone.  

As a sidenote, you don't need "sudo" for "cd /home" - "sudo" runs the command with root, super user, permissions, but you don't need special permission to change into the home directory.

---

