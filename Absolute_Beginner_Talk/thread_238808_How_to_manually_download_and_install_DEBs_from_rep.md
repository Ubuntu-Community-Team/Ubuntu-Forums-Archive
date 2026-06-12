---
title: "How to manually download and install DEBs from repositories?"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by jamadagni on 2006-08-18
Due to some problem with my net connection, I have never been able to do auto-update or direct repository access from package manager on SUSE and Fedora and now Kubuntu. I have always been downloading the RPMs and installing them using Smart. 

Now I am new to Kubuntu and would like to know where to download the DEBs from and how to install them from the Konsole or Adept or whatever.

Thanks.

---

### Post by Fass on 2006-08-18
You can search the repos and find the debs at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and you can install them either with gdebi (a gui) or by entering ```
sudo dpkg -i name_of_deb_file.deb
``` in a terminal.

---

### Post by red van man on 2006-08-18
In Ubuntu Dapper just double click the .deb files to install the packages, couldn't be simpler!  Don't know if this works for Kubuntu.

---

### Post by alan yeates on 2006-08-18
I made a CD of anything I might want and then added the CD as a repository in Synaptic but watch out for dependancies, though Synaptic will halt if they are absent, so not much to worry about. This is also a good scheme if there is a broadband connection about but you have only dial up. Don't finalise your CD so you can add more stuff as and when.

---

