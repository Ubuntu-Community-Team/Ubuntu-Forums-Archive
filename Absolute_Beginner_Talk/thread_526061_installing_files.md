---
title: "installing files"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by satnampenaich on 2007-08-15
/home/satnam/Desktop/NVIDIA-Linux-x86-100.14.11-pkg1.run 
I just downloaded this file but how do I install this file. It opens up in the text editor. how should I open this up. Thanks

---

### Post by Rocket2DMn on 2007-08-15
Open a terminal and type these commands.  The // is me telling you what each command is doing, don't include them in the terminal:
```
//change directory to the Desktop under your username
cd ~/Desktop
//set the file with executable permissions
chmod +x NVIDIA-Linux-x86-100.14.11-pkg1.run
//run the file
./NVIDIA-Linux-x86-100.14.11-pkg1.run
```

The restricted drivers for NVIDIA are also available in the repositories, you don't need to install them manually.  Check this guide out: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by logos34 on 2007-08-15
> **satnampenaich said:**
> /home/satnam/Desktop/NVIDIA-Linux-x86-100.14.11-pkg1.run 
I just downloaded this file but how do I install this file. It opens up in the text editor. how should I open this up. Thanks

Unless you have a burning desire for the bleeding edge nvidia proprietary driver, I'd recommend using the  nvidia-glx-new or nvidia-glx driver as described in the link Rocket2Dmn posted above.  

If you still want the latest driver, then use this [howto]("http://doc.gwos.org/index.php/Latest_nvidia_feisty") (**Method 2**) to install the 100.14.11 you downloaded (there are versions for edgy and dapper if you're running those).  Remember, you can't  run './NVIDIA-Linux-x86-100.14.11-pkg1.run' from the desktop -- you have to drop to the console and shutdown the display manager:

ctrl+alt+F1

login and enter pwd

sudo /etc/init.d/gdm stop

cd Desktop

sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run 

etc etc,

Follow tseliot's howto

---

