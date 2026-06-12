---
title: "Clean uninstall of apache"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by rgb on 2007-12-04
I was trying to configure my apache server to set up mediawiki. I seem to have messed it up, and I may have forgotten to back up some default file, because returning to the backed up ones is not working. So, I am trying to do a fresh install of apache, hoping that I will get the default configuration files back that way, and can follow the usual instructions. 

However, when I go to synaptic search for apache, and choose to completely remove all files with names containing apache, the /etc/apache2 directory is not removed. Hence I do not get the default configuration files. Could anyone help me understand how I can go about it?


Thanks

---

### Post by vikramsharma on 2007-12-04
apt-get autoremove gets rid of the dependencies as well.  You can do man apt-get to get more idea.

---

### Post by rgb on 2007-12-04
Thanks, so I tried that, but it did not remove the apache2 directory or its contents. Is it safe to delete the directory?

---

### Post by vikramsharma on 2007-12-04
I would advice against deleting the directory, you can use apt-get to install apache use apt-get clean install apache (name of the package you want to install).  Hope that helps you out.

---

### Post by rgb on 2007-12-05
You mean apt-get clean and apt-get install apache ? This does not solve the problem.

---

