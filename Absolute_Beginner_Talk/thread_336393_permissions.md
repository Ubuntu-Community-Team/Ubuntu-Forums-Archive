---
title: "permissions"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by oscar78 on 2007-01-11
I'm a bit confused about permissions, specifically their default values.  I'm running this tcl script that basically takes one of my files and unpacks it into a number of other files.  These new files that arise, however, have specific permissions attached to them.  My question is, what decides these respective permissions?  the script itself?  the permissions of the folder to which they are downloaded?  

This isn't really a life or death issue, I am just curious.

---

### Post by bodhi.zazen on 2007-01-11
Short answer is archive programs (tar) preserve permissions.

cp (copy) does not without the -p or -a flags.

---

### Post by steve.horsley on 2007-01-11
As bodhi says, tar and other unix based archive programs will store permissions along with the file, and restore them. In fact, if root unpacks a tar file, then tar also sets the ownership of the file.

When you create files, a default permissions is applied. This default is controlled by the command **umode**.

---

