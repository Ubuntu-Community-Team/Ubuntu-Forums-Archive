---
title: "Permissions to write to folder..."
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Navicerts on 2007-03-13
Hello, 

I have just got ubuntu working on an old machine; this is my first time using Linux.

I am interested installing some software that comes in a binary package.  As I understand it, this means there is no installation per say, I just need to put the executable file in the correct location and then run it.

I got the binaries of the two programs i was interested in (PEST and VCE) and put them on my desktop in a common folder.  From a command line I can run the program by typing in the entire path of the executable binary and it runs.  The manual has suggested that I put them in a location where everyone has read access and it is in the search path.  It recommended /usr/local/bin.  I tried to put them in that location via the GUI but i get an error message "Error while copying to "/usr/local/bin" You do not have the permissions to write to this folder".

I'm not sure why i don't have the permissions considering I formatted and hard drive and installed the OS myself.  Also, how do i go about logging on a root user?  I was never prompted to enter a password for root during installation.

Thanks

-Navicerts

---

### Post by dstew on 2007-03-13
You need to get temporary root privleges to write in system directories such as /usr/local/bin. You get these in an Ubuntu system by using the sudo ("soo doo") command. It gives you root privleges for about 5 minutes so you can do such things. You do not need to be logged in as a root user.

sudo cp ~/Desktop/MyProgram /usr/local/bin

---

### Post by Navicerts on 2007-03-13
Thank you, that worked to move the file into usr>local>bin but now i can not run the program instead i get an error message that says "command not found".  when i look at the properties of the file i copied it says "unknown type" before i copied it was "executable"


Any ideas for me?

Thanks

-Navicerts

---

### Post by Navicerts on 2007-03-13
OK, figured that one out.  Changed the owner and group to something i have access to, now it is recognized as an executable.  However, from a command line i still get a command unknown from typing in "vce" and hitting enter, i was expecting the program to run.

---

### Post by taurus on 2007-03-13
Is /usr/local/bin on your path?

```
/usr/local/bin/vce
```

---

### Post by Navicerts on 2007-03-13
Nevermind, it is working OK.  The manual said i could type "vce" alone and it would run.  But i have to type the whole file name (but not the path any longer!), close enough.

Thanks

---

### Post by Navicerts on 2007-03-13
I don't know what that means "on my path", sorry, im new.

---

### Post by taurus on 2007-03-13
Edit ~/.bashrc

```
gedit ~/.bashrc
```
and add these two lines to it.

```
PATH=$PATH:/usr/local/bin
export PATH
```
Save it.  Then, either log out or back in or run this command from a terminal to "read" in the new changes in ~/.bashrc.

```
source ~/.bashrc
```
From now on, you don't have to type the whole path, /usr/local/bin, if you want to run vce since it's in your path now.  This little command should do it.

```
vce
```

---

### Post by Navicerts on 2007-03-13
OK, i think i get it.  I'm glad i could run anything on day 1 :)

Thank you!

-Navicerts

---

