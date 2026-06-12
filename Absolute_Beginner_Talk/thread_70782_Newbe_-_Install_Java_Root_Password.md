---
title: "Newbe - Install Java? Root Password"
date: 2005-10-01
forum: Absolute Beginner Talk
---

### Post by tr6scott on 2005-10-01
Ok, about 10 hours into Ubantu & Linux, taking baby steps...
I was trying my ISP speed test, and it uses java, and it was not installed. Went to the sun website, downloaded the non rpm version and I need to use the terminal and use the command "SU" which asks for the root password. 
What is the root password? I did not see the install ask me for one, so is there a default one when you set ubantu up? 
And with a this mocha stuff how can there be no java? :)

---

### Post by jrib on 2005-10-01
Use sudo instead to run the command.  For example, if you wanted to copy file1 to file2, you would do:
```
$sudo cp file1 file2
```
That will prompt you for your own password on the account you are currently on. 

I don't think Ubuntu has a root password enabled by default.  It is supposedly  more secure this way.

---

### Post by nitricacid on 2005-10-01
I will have to refer you to this thread [http://ubuntuforums.org/showthread.php?t=70017&page=2](http://ubuntuforums.org/showthread.php?t=70017&page=2)

I had the same problem trying to install Java and after going over each step on the java site 5 times over it still did not let me install it the way it said.

there is no root password.
The root password is your password that you login with and use for everything else.
aslo you do not use 'SU' for root rites you use 'Sudo'.

---

### Post by tr6scott on 2005-10-01
From the link posted, these were the commands. 
sudo apt-get install fakeroot java-package
fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin
sudo dpkg -i *.deb
I have the jre-1_5_0_04-linux-i586.bin on the desktop, when I run the first command, I get this error. 
```
scott@ubuntu:~$ sudo apt-get install fakeroot java-package
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package
```

---

### Post by nitricacid on 2005-10-01
Might try placeing it into the home file.

The way i Installed mine was from the synaptic package manager (search java) and then use the sudo apt-get install fakeroot java-package and everything installed fine.

You have to have the java installed on the machine first and then use the code (above) to implament them into the browser (from what i understand).

---

### Post by tr6scott on 2005-10-01
Moved file from Desktop to Home, 
Same results... :(

---

### Post by blastus on 2005-10-01
I believe the java-package package is in the multiverse. If you're running Hoary then make sure this line

```
deb http://archive.ubuntu.com/ubuntu/ hoary multiverse
```

is in your /etc/apt/sources.list file. To edit the file you would type

```
sudo gedit /etc/apt/sources.list
```

then, after you have edited and saved the file, type

```
sudo apt-get update
```

to update your repository cache. Now 

```
sudo apt-get install fakeroot java-package
```

should work.

---

