---
title: "Using the cp command"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Mitchlb on 2007-12-31
I'm trying to figure out how to use the terminal. The cp command is giving me some trouble. At one point, to copy files, all i needed to do was 

cp filename PlaceToMoveFile

now when i try that (let's say i want to move a directory otherstuff into a directory stuff)

cp otherstuff stuff


It gives me an error message

cp: omitting directory 'otherstuff'


This is really aggravating for a simple drag and drop scenario using a graphical interface. How does one properly use the cp interface in ubuntu?

---

### Post by taurus on 2007-12-31
Are there other directories under otherstuff?  

```
cp -R otherstuff stuff
```

---

### Post by eternicode on 2007-12-31
> **Mitchlb said:**
> I'm trying to figure out how to use the terminal. The cp command is giving me some trouble. At one point, to copy files, all i needed to do was 

cp filename PlaceToMoveFile

now when i try that (let's say i want to move a directory otherstuff into a directory stuff)

cp otherstuff stuff


It gives me an error message

cp: omitting directory 'otherstuff'


This is really aggravating for a simple drag and drop scenario using a graphical interface. How does one properly use the cp interface in ubuntu?

"man cp" should give you some good reading material :)

To copy directories, you want to use the -r or -R switch, for "recursive".  Also, make sure directory "otherstuff" exists, and use a forward slash at the end of the directory you're mocing to.

---

### Post by wh0rd on 2007-12-31
If you're trying to move things like cute & paste. You should use the **mv** command.

---

### Post by Mitchlb on 2007-12-31
Can you give me an example?

---

### Post by eternicode on 2007-12-31
> **Mitchlb said:**
> Can you give me an example?

Copy everything in "this" directory, including subfolders, to "that" directory

```
cp -r this/* that/
```

Make a copy if "this" directory inside "that" directory

```
cpr -r this that/
```

---

### Post by nick_h on 2007-12-31
> let's say i want to move a directory otherstuff into a directory stuff
Use:
```
mv otherstuff stuff
```

---

### Post by logos34 on 2007-12-31
delete
(I was thinking of files)

---

### Post by nick_h on 2007-12-31
> no, that renames the directory 'otherstuff' as 'stuff'
Not if stuff is a directory.
Try the following:
```
mkdir test1
mkdir test2
mv test1 test2
```

---

### Post by Mitchlb on 2008-01-02
Ok. This is starting to make a lot more sence. I think i have it. Thanks.

---

