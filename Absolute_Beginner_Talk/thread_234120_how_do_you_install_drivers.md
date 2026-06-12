---
title: "how do you install drivers?"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by L_o_N_e_R on 2006-08-11
i have the drivers in tar.gz format


how do i install them?

heres a link

[http://downloadfinder.intel.com/scripts-df-external/Filter_Results.aspx?strOSs=39&strTypes=all&ProductID=669&OSFullName=Linux*&lang=eng&sType=prev](http://downloadfinder.intel.com/scripts-df-external/Filter_Results.aspx?strOSs=39&strTypes=all&ProductID=669&OSFullName=Linux*&lang=eng&sType=prev)

---

### Post by GuitarHero on 2006-08-11
tar.gz is a compressed format.  Right click it and hit extract here.  Inside should be a readme or install file.  Look in that for instructions.

---

### Post by L_o_N_e_R on 2006-08-11
heres how to install in the readme

1.  Install Linux

2.  Log in as root or as a superuser

3.  Install kernel headers

    	a.  For Red Hat versions, this is normally on CD2:
	    /RedHat/RPMS/kernel-source-2.4.18-3.i386.rpm

    	b.  Alternately, load your kernel config file, 
	    save the config, and run &#8220;make dep&#8221; 

4.  Extract the downloaded files:
        
	a.  tar &#8211;zxvf 20030106-i386-Linux.tar.gz

5.  Ensure X Windows is not running

6.  cd dripkg

7.  ./install.sh

8.  Follow the prompts; most users should be able to press
    &#8220;Enter&#8221; at each prompt


how do i isntall kernel headers?

and how do i exit x windows?

---

### Post by GuitarHero on 2006-08-11
Go to the synaptic package manager and search for kernel headers.  Install the one for your kernel.  Not sure about the X windows part, I guess just close everything before you do this.  Then it wants you to go to the directory in the terminal with cd, if the folder is on the desktop type cd Desktop/dripkg.  Then run the script with the next command.

---

### Post by bukwirm on 2006-08-11
Ctrl + Alt + Backspace kills X windows.

---

### Post by L_o_N_e_R on 2006-08-11
how do i know which kernel to use

---

### Post by L_o_N_e_R on 2006-08-11
will any kernel header do?

---

### Post by L_o_N_e_R on 2006-08-11
ctrl+alt+backspace takes me back to the login screen


wtf? am i doing something wrong?

---

### Post by L_o_N_e_R on 2006-08-11
bump help

---

### Post by christhemonkey on 2006-08-11
Type Ctrl+Alt+F1 to get to a virtual terminal.

Log in with your user name and password.

Then type:
```
sudo /etc/init.d/gdm stop

```

This will stop X11 from running.

Then type:
```
uname -r 
```
This will return what kernel version you are running.

Then type
```
sudo apt-get install linux-headers 2.6.your-kernel-version

```
Obviously replacing 2.6.your-kernel-version with your actual kernel.

Then you need to get on with extracting and installing your drivers.
I'll let you do this bit first, let us know if you have any problems.

---

### Post by L_o_N_e_R on 2006-08-11
> **christhemonkey said:**
> Type Ctrl+Alt+F1 to get to a virtual terminal.

Log in with your user name and password.

Then type:
```
sudo /etc/init.d/gdm stop

```

This will stop X11 from running.

Then type:
```
uname -r 
```
This will return what kernel version you are running.

Then type
```
sudo apt-get install linux-headers 2.6.your-kernel-version

```
Obviously replacing 2.6.your-kernel-version with your actual kernel.

Then you need to get on with extracting and installing your drivers.
I'll let you do this bit first, let us know if you have any problems.




i already updated my kernels now what?

---

### Post by christhemonkey on 2006-08-11
You have your kernel headers?

Well, then you proceed from step 6.
(presuming you extracted the .tar.gz before, if not do step four)

---

### Post by L_o_N_e_R on 2006-08-11
noob question how do i run install.sh?

---

### Post by christhemonkey on 2006-08-11
probably will have to type:
```
sudo sh ./install.sh 
```
into a terminal.

---

### Post by L_o_N_e_R on 2006-08-11
ok thnx im going to try and install

---

### Post by L_o_N_e_R on 2006-08-11
it says that it cant compile....


now what?

---

### Post by christhemonkey on 2006-08-12
What is the exact error message it gives?

You probably will need build-essential:
```
sudo apt-get install build-essential 
```

---

