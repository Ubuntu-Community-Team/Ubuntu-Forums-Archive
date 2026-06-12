---
title: "using older gnu compiler"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by cl3ellio on 2006-05-04
I'm trying to install the CGAL library and it only supports gnu compiler up to 3.4. I have 4.0 and it won't build the library, is there a way to disable a 4.0 and use a previous version? Keep in mind that I'm using their installation scripts.

---

### Post by christhemonkey on 2006-05-04
You can just install gcc3.4 
```
sudo apt-get install gcc-3.4
```

Bear in mind that it will also install cpp3.4 and gcc-3.4-base (which i think are all its dependencies)

---

### Post by cl3ellio on 2006-05-04
I tried installing gcc-3.4 but it tells me that gcc-3.4 is not available and has no installation candidate. Is there another source I can get it from, if so how? Thanks.

---

