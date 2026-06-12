---
title: "[SOLVED] GUI install from kubuntu/ubuntu cd for Ubuntu Server 7.04"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by avionion on 2007-10-16
hi all, i have 2 questions:
1. is it possible to install gnome desktop from ubuntu 7.04 cd on ubuntu server 7.04 machine? if it is possible then how?
2. if i had to install gnome or kde desktop on ubuntu server 7.04 on a machine which can not be connected to internet because of certain reasons, what all packages i will have to download? can i download all dependencies and required packages in a single zip or tar file? 
regards.

---

### Post by overdrank on 2007-10-16
> **avionion said:**
> hi all, i have 2 questions:
1. is it possible to install gnome desktop from ubuntu 7.04 cd on ubuntu server 7.04 machine? if it is possible then how?
2. if i had to install gnome or kde desktop on ubuntu server 7.04 on a machine which can not be connected to internet because of certain reasons, what all packages i will have to download? can i download all dependencies and required packages in a single zip or tar file? 
regards.

Hi if you are looking to install a GUI without the internet I would recommend either install with the desktop version
 [http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/)
Or you can look into APTon CD
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)
Good luck! :KS

---

### Post by anubhavrocks on 2007-10-16
1.Yes.
```
sudo apt-cache add cdrom
sudo apt-get install ubuntu-desktop
```
2.Refer step 1.

---

### Post by avionion on 2007-10-17
i tried to run sudo apt-cache add cdrom after mounting cdrom but it gives following message:
E: Unimplemented
i double checked the cdrom directory listing with ls command and cdrom is working fine with all files being read without any problem.
and then running sudo apt-get install ubuntu-desktop says the following:
E: Package ubuntu-desktop has no installation candidate
Package ubuntu-desktop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source.
where things  went wrong?

---

### Post by anubhavrocks on 2007-10-17
okay, try using synaptic```

sudo synaptic
```
In synaptic 
1.> Edit->Add Cdrom 
2.> Edit->Reload Package Information
3.Now search for > Ubuntu-Desktop and install it.

---

### Post by avionion on 2007-10-21
there is no synaptic in server. so what i did was i installed ubuntu 7.04 then from synaptic i added ubuntu server 7.04 cd and installed the LAMP and DNS server from the synaptic interface. i guess if u have both the server and ubuntu Cds, this is the easiest way to install a server with GUI. thanks for all the help. 
it can be marked as solved.

---

### Post by anubhavrocks on 2007-10-23
Right,please mark the thread as solved.

---

### Post by overdrank on 2007-10-23
> **anubhavrocks said:**
> Right,please mark the thread as solved.

You can do that with the link in my signature. Good luck! :KS

---

