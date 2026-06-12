---
title: "Whoo Noobishness kicks in."
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Hartxenon on 2007-11-03
Alrite heres the deal, i switched over to ubuntu yesterday and well im trying to install some of my favorite programs but the linux version. the first program i tried to install was xpad, a program that installs the drivers for a USB xbox controller. But the thing is I dont know what im doing when it comes to installing. i mean i downloaded the file and then i extracted the files from it and the one that installs called "install.sh¨ is there i dont know what i am doing. I get to this point and my brain shuts off. how do i install this what process would i use? i am not very experienced when it comes to linux, ubuntu, shell programs,  I mean im 17years old and have spent about 18 of those years using nothing but windows so a easy simple answer on how to install programs will be very appreciated. Please keep the hard tech talk to a mininum.

---

### Post by linuxlizard on 2007-11-03
I'm not familiar with that particular script, but usually one like that would be executed in your terminal by typing:

./ install.sh
sh install.sh

or you may need to put a sudo in front of one of the above:
sudo : ./ install.sh
sudo: sh install.sh

---

### Post by jpietari on 2007-11-03
1. Right-click the "install.sh" and Properties->Permissions->Enable "Execute".  
2. Open Terminal (Applications->Accessories->terminal)
3. Navigate to the file by using cd <path>
4. type command sudo ./install.sh
5. Enter root password

You are good to go

---

### Post by SOULRiDER on 2007-11-03
You should allways look for DEB packages.

Please, its important that you read this guide and understand how installing software works in Linux. [https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

Good luck, and ask any questions here!

---

### Post by jpietari on 2007-11-03
Random Points:
- .sh = Shell script
- Shell scripts must be set to be executed
- sudo = Command used to execute a command with Super User privileges.  This is needed to ensure that the script has full access to your PC.

---

### Post by jpietari on 2007-11-03
SOULRIDER - Say I installed a DEB package that is outside any repository I have.  How would I uninstall it?

---

### Post by jpietari on 2007-11-03
My real question is:

Say I installed monodevelop from the Ubuntu repositories.  I then install the latest version of monodevelop from a website.  How do I uninstall monodevelop?  Would I uninstall monodevelop by using "Add/Remove..." (the Ubuntu version) and then execute the command "dpkg -r packagename" (website version) .

---

### Post by SOULRiDER on 2007-11-03
Just do an
```
apt-get remove monodevelop
```
or you could do (its actually better in some cases
```
aptitude remove monodevelop
```

Its the same as if you had installed it from the repos.

---

### Post by Maestro23 on 2007-11-03
> **jpietari said:**
> My real question is:

Say I installed monodevelop from the Ubuntu repositories.  I then install the latest version of monodevelop from a website.  How do I uninstall monodevelop?  Would I uninstall monodevelop by using "Add/Remove..." (the Ubuntu version) and then execute the command "dpkg -r packagename" (website version) .

1. Uninstall the Repo version 1st.  Either thur Synaptic or command line: sudo apt-get remove...

2. Install your .deb: sudo dpkg -i packagname

---

### Post by jpietari on 2007-11-03
That is great.  Thanks

---

### Post by SOULRiDER on 2007-11-03
> **Maestro23 said:**
> 1. Uninstall the Repo version 1st.  Either thur Synaptic or command line: sudo apt-get remove...

2. Install your .deb: sudo dpkg -i packagname

The version installed should get upgraded when the newer deb package is installed.

---

