---
title: "Terminal Help"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by ChrisC098 on 2006-08-11
Hi Everyone,

I have a WUSB54GS, a USB network adaptor and am having trouble getting it to work. I found this: [http://www.ubuntuforums.org/showthread.php?t=225206](http://www.ubuntuforums.org/showthread.php?t=225206)

It's pretty comprehensive and I'm sure it will work except for the fact that I have no idea how to use the terminal. I have a dual boot setup with Ubuntu and Windows XP if that is need to know information. Any help would be appreciated.

---

### Post by wpshooter on 2006-08-11
Well basically there should be a terminal program on one of your drop down menus at the top of the screen.  Open the terminal, maximize it, then reduce it to the task bar, then go back to the instructions on the thread and then copy and paste the commands that are given on the tread, one at a time, hitting the enter key after each command to execute it at the terminal.

---

### Post by ChrisC098 on 2006-08-11
I understand that part, what I am having trouble in is that, the instructions tell me to go into a certain folder and I am not sure how to do that. I'm sorry for not elaborating.

---

### Post by ciscosurfer on 2006-08-11
To use the **Terminal**, click on the **Applications** menu in the upper-left of your screen.  Then go to **Accessories** and then select **Terminal**.  A terminal window will open up and you can then begin to type commands.  Enter commands into the Terminal (also refered to as command line input) as you see them in thread you mentioned in your original post.

Here is an example of what you can enter into a terminal (simply copy and paste)```
echo "Hi $USER, you're in a terminal and are in the $PWD directory."
```Here's an example to update your repositories```
sudo aptitude update
```And here's a more advanced command to let you see all TCP connections that are present on your computer```
 netstat -plant | grep "tcp"
```If you have any additional questions, please don't hesitate to ask anyone here...we will be glad to help you out! :grin:

---

### Post by ciscosurfer on 2006-08-11
To change to a specific folder, for example, the /etc/apt directory, you would enter into a terminal```
cd /etc/apt
```The cd command stands for "change directory".

---

### Post by Iowan on 2006-08-11
> **ChrisC098 said:**
> I'm sorry for not elaborating.Elaboration might be a good thing... **cd /the/folder/you/want** *should*
work - but probably isn't the entire solution.

(I gotta learn to type faster...)

---

### Post by ciscosurfer on 2006-08-11
Here is an [*excellent *post]("http://www.ubuntuforums.org/showpost.php?p=812448") that describes how to get around your system!

---

### Post by r4ik on 2006-08-11
Here's another link worth reading,

[http://ubuntuforums.org/showthread.php?p=990636](http://ubuntuforums.org/showthread.php?p=990636)

---

### Post by ChrisC098 on 2006-08-11
Ok the folder i need to get to is ndiswrapper-files and it is on my desktop. Do I have to type this?:

cd/desktop/ndiswrapper-files

Becuase it says the folder doesnt exist.

---

### Post by ciscosurfer on 2006-08-11
You must space it out just a bit.  You need to add a space between the command 'cd' and the folder you want to get to.  For example, type or copy/paste this```
cd ~/Desktop/<folder you want to get to>
```The '**~**' character basically stands for "your home directory".  And your Desktop is located in your home directory.

It's helpful also to use your 'tab' key.  For example, enter into a terminal **cd ~/** then hit your Tab key once...this will change the output to reflect your actual home directory...then hit the Tab key *twice in succession*, like Tab-Tab and you'll be able to see what's in your /home/your_name directory....you can then add the directory "Desktop" to the line```
cd /home/<*your_username*>/Desktop/<*the_directory_you_want_to_open*>
```

---

### Post by Third Thoughts on 2006-08-11
Your desktop is located in your home folder so what you want to type is 
```

cd /home/your username/Desktop/ndiswrapper-files

```

Also worth knowing is that the terminal has tab compliation. This means if you type cd /ho, and then hit tab it will finish the word home. This makes getting around alot easier.

~Andrew S.

---

