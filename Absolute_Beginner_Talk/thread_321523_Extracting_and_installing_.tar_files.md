---
title: "Extracting and installing .tar files"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by Nhatz on 2006-12-19
how can i extract and install tar files... thanks... :mrgreen:

---

### Post by xyz on 2006-12-19
This is a good place to strat with:
[How to install ANYTHING in Ubuntu!]("http://monkeyblog.org/ubuntu/installing/")
Good luck; let us know how it goes.

---

### Post by macogw on 2006-12-19
Double click on the .tar to open the Archive Manager.  Tell it to extract to a folder in your home drive.  I think most people call it src for source. So that'd be ~/src.  Then, look in there and read the install directions.  Normally, you go to the terminal and type
```

cd ~/src/folderOfYourProgram
./configure
make
make install
make clean

```
but it can vary with some programs.  If ./configure spits an error at you, you just need to read it and see what the dependency is.  Look in Synaptic to find the missing dependency (probably a library) and install it, then do ./configure again until it stops telling you to download more stuff and simply works.

---

### Post by boralyl on 2006-12-19
```
sudo apt-get install tar
tar -xvf thefile.tar

```
If it's gunzipped too, aka file.tar.gz include -z as well
```

tar -xvzf thefile.tar.gz

```

---

