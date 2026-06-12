---
title: "make command in Kubuntu"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-06-08
I decided i wanted to test this app on my Kubuntu box cause that has apache nd php and mysql installed but when i run the make command it errors

john@Kubuntu:~/Desktop/gnump3d-2.9.8$ sudo make install
sudo: make: command not found

So what is the correct command for Kubuntu??
i thought it would be the same as ubuntu or do i need to install a package to allow this command to work?

---

### Post by taurus on 2006-06-08
You probably need to install it first before you can use it...
```

sudo apt-get install build-essential

```

---

### Post by lime4x4 on 2006-06-08
yeap that was it..It was driving me crazy cause i was able to install it in ubuntu but then after u posted that it hit me.. I had to install that same package for vmware server

---

