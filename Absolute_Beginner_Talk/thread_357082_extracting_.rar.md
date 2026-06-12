---
title: "extracting .rar"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by kayratorvi on 2007-02-09
How can I extract .rar files? Archive manager isn't able to at the moment....

---

### Post by arochester on 2007-02-09
Try unrar

---

### Post by hyper_ch on 2007-02-09
Go into the command line interface
Enter
```

sudo apt-get install unrar

```
and then I think it's just

```

unrar archive.rar

```

Don't have a linux box here right now... maybe a parameter is required... if the above command doesn't work have a look at the syntax
```

unrar --help

```

That should tell you the correct syntax for unraring.

---

### Post by sh4d3z on 2007-02-09
cd to the dir where the rar is and do a unrar e file.rar (yes without a hyphen)

---

### Post by ckaya on 2007-02-09
This is exactly what you are looking for: [https://help.ubuntu.com/community/FileCompression#head-32ba956d13d49934f65bf67dd40646653a7a6140](https://help.ubuntu.com/community/FileCompression#head-32ba956d13d49934f65bf67dd40646653a7a6140)

For further reading: [https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

---

