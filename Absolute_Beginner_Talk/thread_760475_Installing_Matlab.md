---
title: "Installing Matlab"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by satyavan on 2008-04-20
I have the .iso image disk of Matlab (ver.7 R14) and as absolute Linux beginner I have no idea where to begin with. The disk does not do anything alone when restarting. Clicking on the installation icon doesn't do nothing either. The readme.txt tells to "run the installer", what exactly does that mean? Many thanks to anyone who can help.

---

### Post by daengbo on 2008-04-20
You will probably need to install via command line. I don't know Matlab, so I'm going to guess a little. Things may not be exactly as I describe. Don't worry.

Open a terminal and change to the CDROM directory
> cd /media/cdrom0
Next, check the contents.
> ls
There should be a file named "install.sh" or something similar. It will probably end in ".sh"
> sudo ./install.sh
type in your password and you will be prompted to install. The installer may ask you questions. If you're confused, come back to ask. You are running as root and have the power to really mess up your system if you do something wrong.

Good luck.

---

### Post by iSplicer on 2008-04-20
Are you sure you have the Linux version of MATLAB?

---

### Post by satyavan on 2008-04-20
There is an "install" file without .sh extension. Anyhow it answers "Setup aborted.. The installer can not be run when your current directory is on the cd. Change to the target MATLAB installation directory and rerun the installer". Which is the "target directory"?

---

### Post by satyavan on 2008-04-20
Hmmm... possibly... The label of the zipped file was "Matlab.7.R14.for.MacOSX-Unix-Linux.zip".

---

### Post by DBrocks on 2008-04-20
Okay, try this
Make a folder for Matlab to be installed to:
```
sudo mkdir /matlab
```Change to the mablab installation folder:
```
cd /matlab
```execute the installer
```
sh /media/cdrom0/.install
```


If the above fails, just try copying the contents of /media/cdrom0 to /matlab and execute the installer from /matlab

---

### Post by iSplicer on 2008-04-20
Hm.. Im sure there should be a readme or instruction file in the CD.. there usually is

---

### Post by satyavan on 2008-04-20
DBrocks: The first does not work, while the second tells that it can't open mapname.sh.

ISplicer: of course there is a readme.txt. It writes that one should "launch the installer"....:confused:

---

### Post by RudolfMDLT on 2008-04-20
Hi,

I have have matlab installed and running happily on my Ubuntu machine. 

If you downloaded a pirate copy of matlab, just be careful that it's not a dud - the mathworks people are getting REALLY pedantic about copy protection. Anyway:

[http://ubuntuforums.org/showthread.php?t=74708](http://ubuntuforums.org/showthread.php?t=74708)

These instructions should help you out! :)

Post back of you have any troubles

EDIT: It's a very old matlab release - see if you can get your hands on a R2007a release - works awesome on linux.

---

