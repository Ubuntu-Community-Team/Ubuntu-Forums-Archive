---
title: "Tar Comparison"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by leetcharmer on 2008-03-24
I have a bunch of shell scripts inside of a bzip2 package I made.  I have the package stored in a different directory on the drive than the original files, but I want to compare the archive with the original -- this is what I get:
```
$ tar --compare --file=pkg.bz2 /home/simbala/Scripts/
tar: /home/simbala/Scripts: Not found in archive
```
Do you know how I can get it to compare with the contents inside the "Scripts" folder without trying to check if the "Scripts folder exists?"  If I change it to:
```
$ tar --compare --file=pkg.bz2 /home/simbala/Scripts/*
```
I get even more issues:
```
tar: /home/simbala/Scripts/script.sh: Not found in archive
tar: /home/simbala/Scripts/starttun.sh: Not found in archive
tar: /home/simbala/Scripts/startvboxnetwork.sh: Not found in archive
tar: /home/simbala/Scripts/stoptun.sh: Not found in archive
tar: /home/simbala/Scripts/stopvboxnetwork.sh: Not found in archive
tar: Error exit delayed from previous errors
```

Any ideas how to get a successful compare going on without having to put the file in the same directory?

---

### Post by erginemr on 2008-03-24
I think you are getting "Not found in archive" error because tar is looking for "/home/simbala/Scripts/script.sh" together with the path (as if considering the whole path as the file name), not just the file "script.sh". So, it depends on the folder tree of the *.sh files inside your tar archive. 

Again, depending on the folder tree, I suggest you to first "cd" into the "/home/simbala/Scripts" folder and then make the comparison.

---

### Post by leetcharmer on 2008-03-24
if I wanted to run the command with another script from another directory -- how would I have it cd for me?

---

### Post by erginemr on 2008-03-24
Something like this should do:
```
cd /home/simbala/Scripts/ && tar --compare --file=pkg.bz2 * 
```
Here, the expression <command-1> && <command-2> means execute the first commmand, and if it is successful, execute the second.

---

