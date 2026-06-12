---
title: "find out version number of program from terminal"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by larrybrazos on 2007-03-15
i might have an issue with an outdated version of ntfs3g.

i am in an ssh session and want to find out what version i have from the terminal . . .

what is a command i can use to find out what version of a particular program i have installed?

---

### Post by Belyel on 2007-03-15
a lot of programs will print their version number if you type "*nameofprogram* -v"

---

### Post by kpkeerthi on 2007-03-15
```

aptitude show ntfs3g

```

---

### Post by 23meg on 2007-03-15
```
apt-cache show ntfs3g | grep Version
```

---

### Post by overdrank on 2007-03-15
> **23meg said:**
> ```
apt-cache show ntfs3g | grep Version
```

Thanks for that input!:)

---

