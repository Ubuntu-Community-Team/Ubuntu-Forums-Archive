---
title: "Intel Mainboard"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by robodan on 2007-09-06
I have Intel 965SS mainboard & would like to know what drivers I will need to download from the intel site please?

Ubuntu is not listed only redhat, Suse, Mandriva

---

### Post by svalding on 2007-09-06
Is there a source or debian package? Either of those should work. You can also download the rpm package, and and use the following:

```

apt-get install alien 
```

This is an RPM to deb converter

then 

```


cd <directory of rpm file>
alien *packagename*.rpm packagename.deb 
```

If you type alien --help in a command window it will show the switches you use to install it (I think it's -i, but I'm not positive.)

---

### Post by robodan on 2007-09-06
there is debian, thanks mate. getting them now.

something tells me i'm in for a long night!!!

---

