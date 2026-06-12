---
title: "Installed vmware 1.03 -- now it won't work ..."
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-07-14
I had vmware-server 1.02 working just fine.  Then I installed vmware-server 1.03 and it won't start now.

I have an entry in menu Applications -> System Tools -> VMware Server Console but when I click on it, it trys to start but just dies.

Any ideas?

Thanks

Carl

---

### Post by anewguy on 2007-07-15
I'm just a rookie, so forgive me if this is obvious.   I had that same problem when I downloaded VMware Server and installed it.  If I remember correctly, it all had to do with permissions.  Try using a terminal window and just putting in "vmware".  If that aborts or does nothing, then try "sudo vmware".  If that works then you have a permissions problem - I think there is a user group of "vmware" you need to be part of - you might want to double check and see if that is set.

Sorry it took so long to get an answer - I assumed people who know a lot more than me would probably answer you.:)

---

### Post by cwmoser on 2007-07-15
Those following this thread, I figured it out.

This is what I did:

Remove any failed installations via:

  sudo  rm  -r  /etc/vmware

  apt-get  remove  --purge  vmware-server


Used the installation procedure at:

[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)


Some points I would like to make:
  1-  don't download the *.rpm file and try to use alien to convert to an *.deb -- it won't work.
  2-  Be sure and don't overlook that you should enter NO when the message "Before running VMware Server for the first time ...".  This is in the installation URL and is easy to overlook.

When done, you can start VMware server via Applications -> System Tools -> VMware Server

Carl

---

### Post by TheExplorer on 2007-07-15
> **cwmoser said:**
> don't download the *.rpm file and try to use alien to convert to an *.deb -- it won't work.
Never do this. Better compile packages with your own hands from the sources or search for .deb files. Red Hat and Ubuntu don't stand so close for the conversion to work :)

---

