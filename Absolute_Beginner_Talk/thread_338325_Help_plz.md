---
title: "Help plz"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by dragonmine on 2007-01-14
How can i install a .run file , ex/ enemy territory game.

et-linux-2.55.x86.run    cant figure out how to install this dont know many commands would be thankfull if somone can help.

---

### Post by taurus on 2007-01-14
Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 et-linux-2.55.x86.run
./et-linux-2.55.x86.run
```

---

### Post by dragonmine on 2007-01-14
what does this mean?

It is recommended to install as the super user
Please enter the root password or hit enter to continue as is
Password: 
su: Authentication failure
Sorry.
/home/bras/.setup10856: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1

See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting

---

