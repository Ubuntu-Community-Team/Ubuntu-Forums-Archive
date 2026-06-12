---
title: "How do I fix &quot;cannot open shared object file&quot;?"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by dberg on 2007-03-09
I am trying to run a newly installed program and am getting this error:

```

fldigi: error while loading shared libraries: libhamlib.so.2: cannot open shared object file: No such file or directory
```

is there a way I can fix this?

Thanks

---

### Post by Bachstelze on 2007-03-09
```
sudo apt-get install libhamlib2
```

---

### Post by dberg on 2007-03-09
That fixed it! Thanks a lot for the quick reply.

---

### Post by Bachstelze on 2007-03-09
Just so you know, if you have this kind of problem again, the error message said the file that was not found was libhamlib.so.2. So you go to [http://packages.ubuntu.com](http://packages.ubuntu.com) , you search for the file and voilà, it will tell you the package that file is in :)

---

### Post by Luke111 on 2008-03-17
I've been trying to install this same package with no luck. I have done the steps here, but unlike dberg, I still get the error message about libhamlib.so.2 not being installed. I looked in [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and it couldn't find the file either. I see the original message is a year old now, so something could have gotten changed, maybe?

---

