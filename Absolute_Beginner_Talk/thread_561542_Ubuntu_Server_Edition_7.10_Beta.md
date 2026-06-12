---
title: "Ubuntu Server Edition 7.10 Beta"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by stevezygote on 2007-09-27
I am SO used to GUI. Is this edition not GUI? If it is, how do I activate it? I have installed it in a virtual machine using VMWare Workstation 6. I get a prompt line but no GUI, which I'd dearly love to have! Very visual this nub!

---

### Post by overdrank on 2007-09-27
> **stevezygote said:**
> I am SO used to GUI. Is this edition not GUI? If it is, how do I activate it? I have installed it in a virtual machine using VMWare Workstation 6. I get a prompt line but no GUI, which I'd dearly love to have! Very visual this nub!

Hi and all server version have no GUI. You will need to install the desktop.```
sudo apt-get install ubuntu-desktop or
sudo apt-get install xubuntu-desktop
or 
sudo apt-get install kubuntu-desktop
```

---

### Post by Jimmyfj on 2007-09-27
I'm not sure but try this:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by stevezygote on 2007-09-27
I tried that command. My gosh. Talk about a lot of activity. And then I got the following error message. And it kept repeating and repeating, even though the ISO I'd downloaded and burned was in my CD drive. 

Please insert the disc labeled 
Ubuntu-Server 7.10 _Gutsy Gibbon_ Beta i386 (20070925)

Now I don't know where to go from here. :(

---

### Post by overdrank on 2007-09-27
> **stevezygote said:**
> I tried that command. My gosh. Talk about a lot of activity. And then I got the following error message. And it kept repeating and repeating, even though the ISO I'd downloaded and burned was in my CD drive. 

Please insert the disc labeled 
Ubuntu-Server 7.10 _Gutsy Gibbon_ Beta i386 (20070925)

Now I don't know where to go from here. :(

If you are installing on virtual machine using VMWare you might want to just download the destop version.

---

### Post by jimrz on 2007-09-27
> **stevezygote said:**
> I tried that command. My gosh. Talk about a lot of activity. And then I got the following error message. And it kept repeating and repeating, even though the ISO I'd downloaded and burned was in my CD drive. 

Please insert the disc labeled 
Ubuntu-Server 7.10 _Gutsy Gibbon_ Beta i386 (20070925)

Now I don't know where to go from here. :(  that's just apt looking for the CD as a source. 
Go to /etc/apt/sources.list and comment out the line referencing the CD and that will get rid of the error. OR you could just pop the CD in the drive.

---

### Post by stevezygote on 2007-10-01
I hate to have to admit it but I'm a total NEWB when it comes to Linux. How do I edit the file in question from the command line? Nothing I seem to do works. In addition, I tried putting the CD into the drive as you suggested. It STILL keeps asking me for the drive. It's like it doesn't recognize the drive.

---

