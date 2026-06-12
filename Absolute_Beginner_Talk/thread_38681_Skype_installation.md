---
title: "Skype installation"
date: 2005-06-01
forum: Absolute Beginner Talk
---

### Post by landcross on 2005-06-01
I am new to Linux but experienced with Windows.  I have downloaded Skype for Linux but do not know how to install it in Kubantu.
I read a  post to install using command called apt-get but do not know how to complete the parameters after this in the terminal window.

Is there an easier way to do this using the installed package manager Kynaptic. I do not know how to add this to available packages.

Any help appreciated..Thaanks

---

### Post by Bob D. on 2005-06-01
The way to install deb's (xxx.deb files) you download is from the command line. Open a terminal and type (this assumes you downloaded the deb to your home directory):

 ```
sudo dpkg -i /home/<YourUserName>/skype*.deb
``` 

That's it! Using dpkg does cause the application to show in Kynaptic if you ever wish to uninstall it.

Note this doesn't work for all apps you want to install. Installing things this way does not resolve any dependency issues, but works for quite a few including Skype. I just installed Skype this way on Kubuntu and it seems to be working fine.

Bob

---

