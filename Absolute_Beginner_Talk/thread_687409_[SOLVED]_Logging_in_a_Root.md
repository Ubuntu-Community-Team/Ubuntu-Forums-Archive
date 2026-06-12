---
title: "[SOLVED] Logging in a Root"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Ohioan on 2008-02-04
I'm an absolute beginner to Linux and Ubuntu.  I just installed last night.  I did not have enough RAM on my computer to run Ubuntu (integrated graphics card stealing too much RAM.)  But, I loaded up Xubuntu from the CD, partitioned my drive with a Windows Drive, a 1g swap drive and a Ext2 drive.  I was then able to load and install Ubuntu onto my Toshiba Laptop.

Now, I'm trying to install Novel, but when I go to move a file to /usr/lib/ it says I don't have permission to write to that folder.  So, I log out and attempt to login as Root.  

The root username does not accept the only password I could've entered.  Is there a default root password I'm not aware of?   

Any suggestions? thanks!

---

### Post by LowSky on 2008-02-04
ubuntu disables loggin in as root... if you need root permision for moving files use the sudo command.

---

### Post by jaytek13 on 2008-02-04
Meaning preface any command you need root priviledges for with sudo, so in your case

```

sudo mv file /usr/lib/

```

---

### Post by beercz on 2008-02-04
try inserting sudo before your command in the terminal window, e.g.

> sudo mv <<myfile>>  /usr/lib/ where <<myfile>> is the file you are trying to move.

When you are prompted for a password, simply type your login password.

See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you ***must*** enable the root account type:

> sudo passwd rootUntil you have more experience and knowledge of linux ***I strongly recommend you do not run that last command***.

---

### Post by Arwen on 2008-02-04
You don't have to login as root to move that file,you can do it in the terminal,I think is sth like "sudo mv /dir1/file  /usr/lib/"..






OK,some people are faster typers than me :-P

---

### Post by dward526 on 2008-02-04
NOTE:  Your SUDO password is your account password.

EDIT:  Apologies to beercz, did not notice you note to this affect already

---

### Post by beercz on 2008-02-04
> **dward526 said:**
> EDIT:  Apologies to beercz, did not notice you note to this affect already
No problem!! :-)

---

### Post by Ohioan on 2008-02-04
Hmmmm.. i wanted to move it via the file manager because when I type that command into terminal I get an error that says "mv: cannot stat 'libstdc++-libc6.1-1.so.2': no such file or directory" 

I see the file right on my desktop...

---

### Post by Ohioan on 2008-02-04
in place of file is the correct file name of course

---

### Post by jken146 on 2008-02-04
You're supposed to replace the word 'file' with the path to that file.  If the file is on your Desktop and is called fooBar, you would type ```
sudo mv Desktop/fooBar /usr/lib/
```


Anyways, if you want to use Thunar (Xubuntu's file manager) as the super user, press Alt+F2 then type in ```
gksu thunar
```

---

### Post by p_quarles on 2008-02-04
Just open the file manager with root permissions. You can do that by typing this in the terminal:
```
gksudo nautilus
```You can use the same command to create a desktop/menu launcher for the root file manager.

EDIT: Didn't notice you were using Xubuntu. jken146's version (i.e., thunar) is correct.

---

### Post by jken146 on 2008-02-04
> **Ohioan said:**
> in place of file is the correct file name of course

OK, saw your edit.  You need the correct **path** to the file, not just its name.  The absolute path would be **/home/someUserName/Desktop/someFile**

---

### Post by jbalazs on 2008-02-04
sudo -s -H

---

### Post by Ohioan on 2008-02-04
I just tried the command 
"sudo mv Desktop/libstdc++-lib6.1-1.so.2 /usr/lib"
and it came back
"mv: cannot stat 'Desktop/libstdc++-lib6.1-1.so.2': No such file or directory"

---

### Post by Ohioan on 2008-02-04
p_quarles: Thanks! that works! very simple.  

I'm not using Xubuntu.  I'm using regular Ubuntu, I just used X to partition my HD with a Swap so I'd have enough available memory to run Ubuntu.

---

### Post by jken146 on 2008-02-04
If that doesn't work (it's a relative path and will only be correct if you're currently in your /home/yourUser, type **pwd** to find out what your **p**resent **w**orking **d**irectory is) try using the absolute path to the file, i.e. **/home/yourUser/Desktop/fileName**.  


By the way, you can replace /home/yourUserName/ with ~/

---

