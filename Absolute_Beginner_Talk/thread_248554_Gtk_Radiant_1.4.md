---
title: "Gtk Radiant 1.4"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Qwerty_ on 2006-09-01
Hey i am in need of assistance with installing Gtk Radiant i get the following error when trying to install

Do you need to issue an xhost + command to let root access X11?
The setup program seems to have failed on x86/glibc-2.1

I have googled around about xhost and disabled tested and renabled without any luck.

Any suggestions would be great.

---

### Post by TFX360 on 2006-09-01
> **Qwerty_ said:**
> Hey i am in need of assistance with installing Gtk Radiant i get the following error when trying to install

Do you need to issue an xhost + command to let root access X11?
The setup program seems to have failed on x86/glibc-2.1

I have googled around about xhost and disabled tested and renabled without any luck.

Any suggestions would be great.

What is the command you use to install...

---

### Post by Qwerty_ on 2006-09-01
I tried a couple all with no no luck

bash linux-radiant-1.4.0.run
sudo sh linux-radiant-1.4.0.run

---

### Post by TFX360 on 2006-09-01
> **Qwerty_ said:**
> I tried a couple all with no no luck

bash linux-radiant-1.4.0.run
sudo sh linux-radiant-1.4.0.run

Not sure but this worked for me with an install:


you probably need:

```
sudo aptitude update 
```
```
sudo aptitude install module-assistant build-essential
``` 
```
sudo aptitude install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
```


```
sudo chmod +x linux-radiant-1.4.0.run
```
```
./linux-radiant-1.4.0.deb --buildpkg Ubuntu/dapper
```

```
sudo dpkg -i thecreated.deb
```

If this doesn't work you can always remove the extra installed apps. I would keep build-essentials though.

---

### Post by Qwerty_ on 2006-09-01
thanks i will try those now and see how it goes.

---

### Post by TFX360 on 2006-09-01
> **Qwerty_ said:**
> thanks i will try those now and see how it goes.

Success!

---

### Post by Qwerty_ on 2006-09-02
Ok i tried that but i am stuck here either it happens really fast or nothing actually happened.


```
 sudo chmod +x linux-radiant-1.4.0.run 
```

What i did was 

```

mike@123456:~$ sudo chmod +x linux-radiant-1.4.0.run
mike@123456:~$ ./linux-radiant-1.4.0.deb --buildpkg Ubuntu/dapper
bash: ./linux-radiant-1.4.0.deb: No such file or directory

``` 

Is there something that i have done incorrectly?

---

### Post by TFX360 on 2006-09-02
> **Qwerty_ said:**
> Ok i tried that but i am stuck here either it happens really fast or nothing actually happened.


```
 sudo chmod +x linux-radiant-1.4.0.run 
```

What i did was 

```

mike@123456:~$ sudo chmod +x linux-radiant-1.4.0.run
mike@123456:~$ ./linux-radiant-1.4.0.deb --buildpkg Ubuntu/dapper
bash: ./linux-radiant-1.4.0.deb: No such file or directory

``` 

Is there something that i have done incorrectly?

./linux-radiant-1.4.0.deb --buildpkg Ubuntu/dapper

Maybe this created a package with a different name. Look for a .deb file.

---

### Post by henriquemaia on 2006-11-13
> **TFX360 said:**
> ./linux-radiant-1.4.0.deb --buildpkg Ubuntu/dapper

Maybe this created a package with a different name. Look for a .deb file.

You have not issued a command to create the deb file. What's the command for it?

---

