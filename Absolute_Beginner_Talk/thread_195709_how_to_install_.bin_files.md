---
title: "how to install .bin files"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by abdalla_salama on 2006-06-13
how to install .bin files

---

### Post by halfvolle melk on 2006-06-13
What are you trying to install?

---

### Post by oly on 2006-06-13
usually just make sure they are executable in the file permissions then type ./filaname.bin at leats that works for realplayer 10

---

### Post by u.b.u.n.t.u on 2006-06-13
[QUOTE=abdalla_salama]how to install .bin files[/QUOTE]

If it is a movie, use VLC and treat it as you would an avi. It worked for me just the other day.

---

### Post by soonindallas on 2006-06-13
.bin files are executable.  often installers are .bin files, though you *run* the installer, you don't *install* it.

example: you want to install Googleearth, now available for Linux.

get the file GoogleEarthLinux.bin here [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html) and select "save to disk"

assuming you saved in to your Desktop, type:

```
cd ~/Desktop
chmod 755 GoogleEarthLinux.bin
```

to make it executable, then

```
./GoogleEarthLinux.bin
```

to run it.  Installation subsequently occurs.

---

### Post by mitchellthegreat on 2008-03-18
Whenever I did a ./<whatever it is>.<whatever>, I would always get an error message.
 
Why? Does Ubuntu just hate me?

---

### Post by halitech on 2008-03-18
what is the error it gives you? might be a case that it wants to install somewhere other then your home folder in which case you would need to run it as sudo

---

### Post by SOULRiDER on 2008-03-18
I believe its important that you read:
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)
before trying to install anything.

---

### Post by mitchellthegreat on 2008-03-18
To be honest, I got this error so many times I just ignored it from then on and just quit what I was doing.

---

### Post by gecko113 on 2008-03-18
I have a similar problem i have a .bin file on my desktop and i want to install it how would i go about it in code in the terminal like the dirctory is /home/dj/Desktop and the file is jre-6u5-linux-i586.bin how would i just install that file

---

### Post by thomas7.10 on 2008-03-18
maybe you should try

```
sh ./GoogleEarthLinux.bin
```

---

### Post by SOULRiDER on 2008-03-19
> **gecko113 said:**
> I have a similar problem i have a .bin file on my desktop and i want to install it how would i go about it in code in the terminal like the dirctory is /home/dj/Desktop and the file is jre-6u5-linux-i586.bin how would i just install that file

THIS IS A MUST READ,
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

To install java just type
```
sudo aptitude install sun-java6-jre sun-java6-plugin
```
What that command does is all explained in 
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

---

