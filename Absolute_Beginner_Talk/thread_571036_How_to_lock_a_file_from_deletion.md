---
title: "How to lock a file from deletion?"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by infurnus on 2007-10-08
I use a Citrix program and i have created a shortcut to launch the program automatically with the ICAClient. It works perfect except when i close out of the application the file i have on the desktop is gone and its not in the trash.

I've tried changing permissions with the file and have it read-only or execute only I've played around with those settings a lot and to no avail it hasn't worked. I also tried creating a soft link to the file and it will delete the soft link but keeps the original file in a different directory intact and as well have played with permissions and owner of the file.

The only solution i can come up with now is to create a folder with about 20 or so short cuts and run them each day and copy more when i get low. I hope their is a far more sophisticated method than my archaic ideas of how to get this working. 

SO my question, Is their a way to "lock" a file from deletion or modification to another program?

EDIT: i have searched google and found an option 
```

lockfile-create CitrixFile.ica

```
however this does not work correctly it gives an error " Error in configuration file: "/home/infurnus/Desktop/CitrixFile.ica.lock" Cannot find section "ApplicationServers". "

---

### Post by llamakc on 2007-10-08
Make it immutable.

[http://linuxhelp.blogspot.com/2005/11/make-your-files-immutable-which-even.html](http://linuxhelp.blogspot.com/2005/11/make-your-files-immutable-which-even.html)

---

### Post by infurnus on 2007-10-08
DUDE! you rock thanks for the very quick reply. Better news it works perfect. Thanks again

---

