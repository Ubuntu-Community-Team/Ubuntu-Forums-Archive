---
title: "cant install from synaptic"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by dragnazz5.0 on 2006-08-22
well everytime i try to download from synaptic it wont let me.  i get an error message about the file not being supported or other files need to be downloaded but cant be installed.  what do i do now


i also dont have any sound with flashplayer.  ive installed it and reinstalled it twice to no avail

---

### Post by b_martinez on 2006-08-22
1> which programs are you trying to install?
2> which repositories do you have ? check by opening synaptic, open 'settings' open 'repositories' and see which have a check mark by them.
3> to get an exact listing of the errors, open a terminal and 'sudo synaptic'. while synaptic is running, the terminal will output all messages, including any errors. This will help to trouble shoot hte problem.
Bill

---

### Post by edopizza on 2006-08-22
Does synaptic work? Do you see the main window? 
If so, try to select "Edit > Fix Broken Packages" on the top menu bar of synaptic. 

If synaptic doesn't work, type
```

sudo apt-get -f install

```
to fix the problem.

---

### Post by dragnazz5.0 on 2006-08-22
ive got the universe and multiverse repositories.  just about anything, i tried the flashplayer package and firestarter and it wouldnt work.


this is what i get when i try to download firestarter

firestarter:
 Depends: libgnutls11 (>=1.0.16) but it is not installable

---

### Post by edopizza on 2006-09-01
> **dragnazz5.0 said:**
> 
this is what i get when i try to download firestarter

firestarter:
 Depends: libgnutls11 (>=1.0.16) but it is not installable

According to the ubuntu packages pages for dapper, firestarter doesn't depend on libgnutls11: 

[http://packages.ubuntu.com/dapper/admin/firestarter](http://packages.ubuntu.com/dapper/admin/firestarter)

Are you running the correct repositories for your ubuntu version (dapper/breezy/hoary...)? :confused:  Check in your "System" menu what version are you running, recheck your repositories for the correct version. All the urls should look something like that: 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) **mycorrectversion** main restricted universe multiverse

If everithing is fine and still wont work, try to install libgnutls11 alone before firestarter: 

```

sudo apt-get install libgnutls11

```

---

