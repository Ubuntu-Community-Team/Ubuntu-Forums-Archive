---
title: "[SOLVED] I can't delete some .rar files in my home folder?"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2008-01-19
These are a bunch of pdf files of some short stories that I extracted to my home directory. I went to organise them into a single folder but I can't move them because I apparently don't have the rights to do so. I can't even delete them because that entailes moving them to the trash folder. How do I give myself the right to move them?

---

### Post by Pevichaey5 on 2008-01-19
hey

type this in terminal

sudo nautilus
(then your sudo password)

it will give you the file manager but with root privledges

---

### Post by kellemes on 2008-01-19
> **thexero said:**
> hey

type this in terminal

sudo nautilus
(then your sudo password)

it will give you the file manager but with root privledges


Works fine.. still gksudo would be better.
Read the following.. [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by boriquajake on 2008-01-19
> **thexero said:**
> hey

type this in terminal

sudo nautilus
(then your sudo password)

it will give you the file manager but with root privledges

That did just what you said it would but once I am the file manager as root things look different. How do I find my home directory?

---

### Post by kellemes on 2008-01-19
> **boriquajake said:**
> That did just what you said it would but once I am the file manager as root things look different. How do I find my home directory?


Browse to /home/yourusername

---

### Post by Pevichaey5 on 2008-01-19
change the address to

/home/your_username

---

### Post by boriquajake on 2008-01-19
This is a screenshot of the error I am getting.

---

### Post by drs305 on 2008-01-19
To permanently change ownership of files:

```
sudo chown <username> <location>/.<filetype-extension> 
```
Example: sudo chown jake /home/jake/*.rar

This will change the owner of the files to you and then you should be able to do what you want to the files in your home directory.   If the files are on your Desktop, the address would be /home/jake/Desktop/*.rar  or whatever filetype...

To change all the files in a directory and subdirectories, add a -R switch:
```
sudo chown -R <username> <location>/*.<filetype-extension> 
```
Example:  sudo chown -R jake /home/jake/*.rar  will change ownership to jake for all rar files in jake's home directory and all its subdirectories.

If you want to change group permissions at the same time, replace jake with jake:<groupname>   e.g.  sudo chown -R jake:jakesgroup /home/jake/*.rar

Substitute .rar  or any other extension to change only that type of file. To change all file types in the driectory, just leave off the "/*.rar"  e.g. sudo chown -R jake /home/jake

---

### Post by boriquajake on 2008-01-19
> **drs305 said:**
> To permanently change ownership of files:

```
sudo chown <username> <location> <filetype> 
```

This will change the owner of the files to you and then you should be able to do what you want to the files in your home directory. Example for user drs:  sudo chown jake /home/jake/*.pdf  If the files are on your Desktop, the address would be /home/jake/Desktop/*.rar  or whatever filetype...

To change all the files in a directory and subdirectories, add a -R switch:
```
sudo chown -R <username> <location> <filetype> 
```


Substitute .rar  or any other extension to change only that type of file.

Thank you. That was very helpful.

---

