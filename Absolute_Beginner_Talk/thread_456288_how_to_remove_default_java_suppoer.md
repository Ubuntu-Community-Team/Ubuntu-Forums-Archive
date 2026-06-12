---
title: "how to remove default java suppoer"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2007-05-27
ubuntu provides opensource implementation  of java by default, i want to use sun java for java softwares. please let me know how can i remove opensource implementation? actually i don't know the names of the packages installed.

---

### Post by taurus on 2007-05-27
Just install Sun version and it's all good.  No need to remove anything.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install sun-java-6-bin sun-java6-plugin sun-java6-font
java -version
```

---

### Post by u04f061 on 2007-05-27
> **taurus said:**
> Just install Sun version and it's all good.  No need to remove anything.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install sun-java-6-bin sun-java6-plugin sun-java6-font
java -version
```

i had java6.bin package and i installed it in /home directory and then added it to my path.
i really need to remove that bcoz i am running out of space

---

### Post by taurus on 2007-05-27
You want to remove the version that you installed by hand to /home!  What's the name of that directory in /home?  _Assuming_ it's called /home/**java1.6.0**, run

```
sudo rm -rf /home/**java1.6.0**
```

---

### Post by u04f061 on 2007-05-27
i donot want to remove sun java. i want to remove gnu java support! i mean gij

---

### Post by taurus on 2007-05-27
If you install Sun java, it will be your default java.  If you install it by hand, then you need to configure it.

```
sudo update-alternatives --config java
```

---

### Post by u04f061 on 2007-05-27
the result of executing above command is > There is only 1 program which provides java
(/usr/bin/gij-wrapper-4.1). Nothing to configure.


---

### Post by taurus on 2007-05-27
So you installed the latest version from Sun in /home.  Normally, people would install stuff to /opt instead of /home since /home should be where the user accounts located.  

What's the output of this command from a terminal then?

```
ls -la /home
```
Otherwise, you can always remove it and install the one from the repos.  Then, it will automatically configure it for you as a default version.

---

### Post by u04f061 on 2007-05-27
ejaz@ejaz-desktop:~/koctave-0.65$ ls -la /home
total 12
drwxr-xr-x  3 root root 4096 2007-05-08 15:47 .
drwxr-xr-x 21 root root 4096 2007-05-08 15:56 ..
lrwxrwxrwx  1 root root   44 2007-05-08 15:16 .directory -> /etc/kubuntu-default-settings/directory-home
drwxr-xr-x 73 ejaz ejaz 4096 2007-05-29 06:58 ejaz
ejaz@ejaz-desktop:~/koctave-0.65$

---

### Post by taurus on 2007-05-27
Where did you say you installed that java again?

---

### Post by u04f061 on 2007-05-27
in /home/ejaz directory
> ls /home/ejaz
ello2
hello.cir
hello.dpl
hello.pro
hello.sch
hxsetup
islam
jre1.5.0_09


---

### Post by taurus on 2007-05-27
> **u04f061 said:**
> in /home/ejaz directory

I thought you said /home.  I think you meant $HOME which is /home/ejaz or ~.

Now, do you want to remove it to free up some space since you mentioned doing that earlier in this thread?

---

### Post by u04f061 on 2007-05-28
i donot want to remove java in my $HOME  because it is sun java. i want to use it as my java for running applets etc.
currently gij is my default java. it can't run efficiently. i want to remove opensource java and configure sun java as my default java

---

