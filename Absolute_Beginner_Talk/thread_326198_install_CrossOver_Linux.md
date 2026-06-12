---
title: "install CrossOver Linux"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by lucky_chouhan on 2006-12-27
Hi i want to know where to download and how to install CrossOver Linux on my ubuntu 6.10.

---

### Post by taurus on 2006-12-27
[http://www.codeweavers.com/](http://www.codeweavers.com/)

---

### Post by Perfect Storm on 2006-12-27
If you are indoubt which package to download from Codeweavers - go for .deb, double click the package and it will install.

---

### Post by lucky_chouhan on 2006-12-27
i am download this link this file extention is .sh. when i double click i get -

The file
fileL//home/xxx/install-crossover-standard-prerelease-6.0.0beta3a.sh is a binary , saving it will result in a corrupt file.:(

---

### Post by taurus on 2006-12-27
Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 install-crossover-standard-prerelease-6.0.0beta3a.sh
sudo ./install-crossover-standard-prerelease-6.0.0beta3a.sh
```

---

### Post by lucky_chouhan on 2006-12-27
Now i get this -

xxxxxx@xxxxx-desktop:~/Desktop$ chmod 755 install-crossover-standard-prerelease-6.0.0beta3a.sh
xxxxxx@xxxxxx-desktop:~/Desktop$ sudo ./install-crossover-standard-prerelease-6.0.0beta3a.sh
Password:
Verifying archive integrity...OK
Uncompressing CrossOver Linux
........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
The '/home/xxxxxx' directory does not belong to you.
Point $HOME to your home directory and try again.:(

---

### Post by taurus on 2006-12-27
Or maybe don't put the sudo in front of it so it would install in your own $HOME directory...

```
./install-crossover-standard-prerelease-6.0.0beta3a.sh
```

---

### Post by lucky_chouhan on 2006-12-27
what that mean i mean i am unable to copy the file in my home folder.

---

### Post by taurus on 2006-12-27
It means that root is not the ower of your $HOME directory.  However, root can delete and modify everything in your $HOME and I guess the program is checking to make sure you are the real owner since I assume you may have to modify something and if root is the owner, then you can't do anything without using the sudo command.  Therefore, try to install it without the sudo in front...

---

### Post by lucky_chouhan on 2006-12-27
so what i do (help with command not message):(

---

### Post by taurus on 2006-12-27
Look at post #7!!!

---

### Post by Literatka on 2006-12-27
> **taurus said:**
> Or maybe don't put the sudo in front of it so it would install in your own $HOME directory...

```
./install-crossover-standard-prerelease-6.0.0beta3a.sh
```

Yeah that doesn't work either.

---

### Post by ibc on 2006-12-27
Did you try:

```
_**sh**_ ./install-crossover-standard-prerelease-6.0.0beta3a.sh
```

Like the instructions on codeweavers.com said?

---

### Post by Literatka on 2006-12-27
> **ibc said:**
> Did you try:

```
_**sh**_ ./install-crossover-standard-prerelease-6.0.0beta3a.sh
```

Like the instructions on codeweavers.com said?

Nope it doesn't work with the .sh code for some reason I can't use Loki installer. I'm running Drake.

---

### Post by ibc on 2006-12-28
> **Literatka said:**
> Nope it doesn't work with the .sh code for some reason I can't use Loki installer. I'm running Drake.
Well, since it's a commercial product, you're only going to be able to install it if you can figure out your shell issues.  What's it tell you when you try to run the shell script?  What's Drake?  An Ubuntu release?  That shouldn't matter...

---

### Post by Jussi01 on 2006-12-28
> **ibc said:**
> What's Drake?  

Drake as in Ubuntu 6.06 Dapper Drake...??

---

### Post by ibc on 2006-12-28
> **Jussi01 said:**
> Drake as in Ubuntu 6.06 Dapper Drake...??

Ah, sorry.  New to the whole Ubuntu naming convention.  Like I said earlier, if the guy can't write to his home directory, and has no 'sh' on his path, I think he's got bigger issues than which distro release he's installed...  :)

Is Literatka the same poster as "lucky_chouhan"?  Or are these two separate issues?

---

### Post by Jussi01 on 2006-12-28
> **lucky_chouhan said:**
> Now i get this -

xxxxxx@xxxxx-desktop:~/Desktop$ chmod 755 install-crossover-standard-prerelease-6.0.0beta3a.sh
xxxxxx@xxxxxx-desktop:~/Desktop$ sudo ./install-crossover-standard-prerelease-6.0.0beta3a.sh
Password:
Verifying archive integrity...OK
Uncompressing CrossOver Linux
........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
The '/home/xxxxxx' directory does not belong to you.
Point $HOME to your home directory and try again.:(

I had the same error, How i fixed it was by going to root, 

```
sudo su root
```

Enter password

 then 
 
```
sh ./install-crossover-standard-prerelease-6.0.0beta3a.sh
```

this worked form me, so maybe it will work for you?

---

