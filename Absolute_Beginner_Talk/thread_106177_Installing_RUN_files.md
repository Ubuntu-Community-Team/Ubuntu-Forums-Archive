---
title: "Installing RUN files"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by Sambie on 2005-12-20
I have no idea what im doing. I'm 100% a newbie! I've downloaded and installed Kubuntu 5.10 Breezy  onto my machine. I've downloaded a game called Wolfenstein ET ( et-linux-2.60.x86.run ) but i have no way of knowing how to install the darn thing! The file is a .run file. 

Can anybody help me out here? I'm very new so please explain so i can understand :)

---

### Post by Sutekh on 2005-12-20
To install this you will need to do some terminal commands.
It should be pretty easy to follow, but if not, just sing out.

The terminal will be found in Applications -> Accessories -> Terminal
You should get something like this
```
user@ubuntu:~$

```
You are currently in your user's home (or base) directory.

First change to the directory you downloaded the file to.  I'll assume it's on the Desktop, as Firefox defaults it there.
```
user@ubuntu:~$ cd Desktop
user@ubuntu:~/Desktop$
```
Note: Case is important

Next you have to set the file to be executable
```
chmod +x et-linux-2.60.x86.run
```
Then execute it using
```

./et-linux-2.60.x86
```
I don't know what's going to happen after that, but those commands will execute the .run file.

Hope that gets it working for you.  Again, if it doesn't make sense, just ask.

Here is a great link for understanding the terminal;
[http://www.ubuntuforums.org/showthread.php?t=73885]("http://www.ubuntuforums.org/showthread.php?t=73885")

---

### Post by Sambie on 2005-12-20
thanks however this is what i did..

brittany@ubuntu:~$ cd Desktop

brittany@ubuntu:~/Desktop$ chmod +x et-linux-2.60.x86.run

brittany@ubuntu:~/Desktop$ ./et-linux-2.60.x86

bash: ./et-linux-2.60.x86: No such file or directory

brittany@ubuntu:~/Desktop$

I've even placed the files onto my desktop... It's showing that it's not there. What can I do?

---

### Post by plcdfa on 2005-12-20
Try this way: 
sudo bash ./et-linux-2.60.x86.run

(You can omit sudo if you're installing in your home directory.)

---

### Post by Sambie on 2005-12-20
Thank you for the help... 

After installing it... it gave me the option of where to put it... in /usr/local/games/enemy-territory 

After accepting it.... I've recieved an error

**Failed permissions**
**No write permissions**

How can I fix this?

---

### Post by plcdfa on 2005-12-20
I suppose you didn't use the "sudo" command in the command line. Either use it, or change the installation directory to /home/yourusername/et
If you use sudo then you must type your password in the commandline before the install program starts.

---

### Post by plcdfa on 2005-12-20
And almost forget... ;) if you're not using sudo then you should also disable any "install symlink to /usr/bin" like option in the installer.

---

