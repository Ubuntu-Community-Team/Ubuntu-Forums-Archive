---
title: "programming on c for Ubuntu"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by chemicalgr on 2007-11-26
Hey there I'm an Ubuntu feisty user and i want to know what software to download in order to programm in c language
thanks

---

### Post by nick_h on 2007-11-26
Install the build-essential package with:
```
sudo apt-get install build-essential
```
To read manual page for the C compiler type:
```
man gcc
```

---

### Post by chemicalgr on 2007-11-26
sorry but i have to do this by hand,i mean i don't have an internet connection at home(let's say is broken)right now i am on an internet cafe and i have to download it into my flash drive and via this i have to install it to my filesystem.
what you suggest?
thanks for responding

---

### Post by Taboo Mirage on 2007-11-26
Check the package's dependancies (assuming Gutsy):

[http://packages.ubuntu.com/gutsy/devel/build-essential](http://packages.ubuntu.com/gutsy/devel/build-essential)

Download the .deb files, put them all into one folder then install them with:

```
cd folder
sudo dpkg -i *
```

---

### Post by chemicalgr on 2007-11-26
i don't think i can handle this mess(sorry i'm a beginner)
look i found a tar file built essential  and i've download it 
do you think that this tar has all all the files required?

---

### Post by Taboo Mirage on 2007-11-26
Please **DO NOT RUN THE ABOVE COMMAND** posted by user "Fachoman88".  It is malicious.

---

### Post by timbounceback on 2007-11-26


Same person as here: [http://ubuntuforums.org/showthread.php?t=624224](http://ubuntuforums.org/showthread.php?t=624224); _**DO NOT RUN**_

Fixed, post edited to remove malignant code.

---

### Post by chemicalgr on 2007-11-26
sorry but i can't connect to the internet at this time
so apt-get is not an option

---

### Post by nick_h on 2007-11-26
> **chemicalgr said:**
> i don't think i can handle this mess(sorry i'm a beginner)
look i found a tar file built essential  and i've download it 
do you think that this tar has all all the files required?

I doubt it.  You will need to download any dependent packages as well.  The apt-get command normally handles all the dependencies for you.

I have just traced the dependencies for gcc in synaptic and found the following:

cpp
cpp-4.1
gcc-4.1
gcc-4.1-base
gcc-4.2-base
binutils
libgcc1
libc6

---

### Post by chemicalgr on 2007-11-27
so i have to download them one by one and install them in the ascenting order as you've wrote?(reminding you that i don't have an internet connection to use the apt-get function)

---

### Post by chemicalgr on 2007-11-27
Look now i'm on an ubuntu terminal at school.Can i use the apt-get to **only download not install** the built essential package then, saving it in my flash drive,go home and use synaptic to install from the flash drive?
If this possible what shoud i write on terminal?
thanks again

---

### Post by anaconda on 2007-11-27
build-essential 
is also included to ubuntu install cd.. so if you still have it you can add that to your sources (eg. in synaptic) and install from there.. no internet required..

---

### Post by az on 2007-11-27
> **anaconda said:**
> build-essential 
is also included to ubuntu install cd.. so if you still have it you can add that to your sources (eg. in synaptic) and install from there.. no internet required..

Both the live and alternate cds....

---

