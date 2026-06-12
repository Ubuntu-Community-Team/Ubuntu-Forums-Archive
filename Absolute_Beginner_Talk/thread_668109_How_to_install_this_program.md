---
title: "How to install this program?"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by ExBuM on 2008-01-15
I downloaded something called The PSP Manager ([http://sourceforge.net/projects/qpspmanager/](http://sourceforge.net/projects/qpspmanager/)) which was in a tar.gz file. I extracted it and I'm not sure how to install it since inside the src folder there's no configure or makefile or anything. There's only a lot of files ending with .h, .cpp, .ui, and .qrc. I've never installed anything like that before :O

---

### Post by kostkon on 2008-01-15
> **ExBuM said:**
> I downloaded something called The PSP Manager ([http://sourceforge.net/projects/qpspmanager/](http://sourceforge.net/projects/qpspmanager/)) which was in a tar.gz file. I extracted it and I'm not sure how to install it since inside the src folder there's no configure or makefile or anything. There's only a lot of files ending with .h, .cpp, .ui, and .qrc. I've never installed anything like that before :O

You have to compile the program by yourself.

Thus, go to *Synaptic* and install the package called *build-essential*. Then open a terminal, go to the folder in which you extracted the files and do
```
./configure && make && make install
```

After this the application should be installed in your system. Check your *Applications* menu if an entry for the program has been added. 

If not, try to run the program from the terminal, like for example
```
qpspmanager
```
Then you can add your own menu entry for the program.

---

### Post by ExBuM on 2008-01-15
I had build-essential installed. I did the 

```
./configure && make && make install 
```

but i got this message

```
bash: ./configure: No such file or directory
```

---

### Post by xc3RnbFO8P on 2008-01-15
Look at this:

[http://ubuntuforums.org/archive/index.php/t-403899.html]("http://ubuntuforums.org/archive/index.php/t-403899.html")

[http://www.mirrorservice.org/sites/download.sourceforge.net/pub/sourceforge/q/qp/qpspmanager/]("http://www.mirrorservice.org/sites/download.sourceforge.net/pub/sourceforge/q/qp/qpspmanager/")

---

### Post by Sef on 2008-01-15
Check out [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

