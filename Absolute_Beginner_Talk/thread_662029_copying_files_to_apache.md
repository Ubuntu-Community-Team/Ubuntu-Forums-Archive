---
title: "copying files to apache"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by zaphodbeeblebrox on 2008-01-08
How do I copy files to apache2-default directory? I used to be able to use gftp on other distributions and login as root then copy the files over and do permission modifications later. So with all this sudo crap do I actually have to copy them to a user directory on the server then ssh over and sudo and then copy files from a command line? I thought this ubuntu idea was to make things easier. 

All I want to do is copy the files directly from one ubuntu machine to another into apache2-default directory using gftp with sftp option. Any assistance would be nice. At first I liked the sudo idea but now.....I feel like an old noob-dog. Now I'm going to have to change my screen name to Noob-dog.

Please help.

---

### Post by p_quarles on 2008-01-08
To get a root shell, you can always use:
```
sudo -i
```
Same thing as simply "su" or "su root" on other distros. 

You could also just create a password for the owner of the apache2 directory, and use that to login via sftp:
```
sudo passwd www-data
```

---

