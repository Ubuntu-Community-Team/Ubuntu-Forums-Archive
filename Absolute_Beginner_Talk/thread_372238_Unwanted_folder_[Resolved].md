---
title: "Unwanted folder [Resolved]"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by relambert on 2007-02-27
While I was working in the synaptic package manager, trying to install a newer version of Firefox, I clicked on the "create new folder' button while trying to add the downloaded package to the list, ( which I never quite figured out how to do). After doing this, I now have a folder on the desktop that I cannot send to the trash. It says that I'm not the owner of this folder. Can I change the permissions on just this folder so I can send it to the garbage?
I will address installing downloaded packages in a different post.
Thanks.

---

### Post by timjayko on 2007-02-27
okay go to applications>accessories>terminal 
then type cd ~/Desktop

then type sudo rm nameoffolderyoucreated

---

### Post by timjayko on 2007-02-27
if that doesnt work its sudo rmdir nameoffile

---

### Post by kittyhawk63 on 2007-02-27
> **timjayko said:**
> okay go to applications>accessories>terminal 
then type cd ~/Desktop
then type sudo rm nameoffolderyoucreated

I did like you suggested with terminal and this is its reply:

kittyhawk63@kittyhawk63:~$ Desktop
bash: Desktop: command not found
kittyhawk63@kittyhawk63:~$

 Edit: I forgot the cd ~/        
Sorry.

I can't get it to recognize cd ~/home/kittyhawk63 either. Is **/home/kittyhawk63** the same as **kittyhawk63@kittyhawk63:~$**

---

### Post by aysiu on 2007-02-28
```
Desktop
``` isn't a command
```
cd ~/Desktop
``` *is* a command

I think it's probably easier and safer to do Alt-F2 ```
gksudo nautilus
``` and then go to your desktop from there and delete the folder.

Typing ```
sudo rm
``` can be dangerous.

---

### Post by relambert on 2007-02-28
Ok, tried both of those and these are the results.
bobby@bobby-desktop:~$ cd ~/Desktop
bobby@bobby-desktop:~/Desktop$ sudo rm locked
rm: cannot remove `locked': No such file or directory
bobby@bobby-desktop:~/Desktop$ sudo rmdir locked
rmdir: locked: No such file or directory
bobby@bobby-desktop:~/Desktop$
Did I do something wrong?

---

### Post by Adramelech on 2007-02-28
Linux is case sensitive, its 'Locked' not 'locked'

---

### Post by relambert on 2007-02-28
I did Alt-F2 and typed that. A window came up with the desktop folder, but nothing was in it to remove. See screenshot.
Gotta be something I'm missing.

---

### Post by aysiu on 2007-02-28
> **relambert said:**
> I did Alt-F2 and typed that. A window came up with the desktop folder, but nothing was in it to remove. See screenshot.
Gotta be something I'm missing.
Yes, that command launches the file browser as root.

So you're currently in /root

Just navigate to /home/bobby by pressing Control-L and typing /home/bobby/Desktop and hitting Enter.

---

### Post by relambert on 2007-02-28
That got it, forgot it was a capitol L ! Thanks alot, these forums are really fast! :)

---

### Post by relambert on 2007-02-28
Thanks aysiu. When I did what you said, the contents of my desktop showed up, But the folder was allready gone from when I used sudo rm Locked.

---

### Post by aysiu on 2007-02-28
Well, now you have two methods at your disposal for the future--one point-and-click and one command-line-based.

---

### Post by timjayko on 2007-02-28
way to go.. I am very new at this but a reliable source told me to get to know terminal.. a command line is much better than any GUI

---

### Post by timjayko on 2007-02-28
here is a nice list to start out with for basic commands you can use 

    * cd (directoryname)
      (Changes directories to the one named. In Unix, you change directories one level at a time.)
    * cd ..
      (Changes back up to the previous directory)
    * pwd
      (Prints -- displays to the screen -- the "working" or current directory)
    * ls
      (Lists the contents of the current directory to the screen)
    * ls -l
      (Same as above, but it lists like the DOS DIR command with more information)
    * mkdir
      (Make a directory -- same as DOS "md")
    * rmdir
      (Remove a directory -- same as DOS "rd")
    * cat
      ("Concatenate," or show a files contents to the screen -- same as DOS "type.")
    * cp
      (Copy -- same as DOS "copy")
    * mv
      (Rename [or "move"] a file -- same as DOS "ren")
    * rm
      (Remove [or "delete"] a file -- same as DOS "del")
    * logout
      (Terminates a Unix Shell session)
    * |more
      (When entered at the end of a command such as "cat" or ls -l", this displays a page of text, then stops and waits for you to issue the command to go on) 


p.s. I found that having to repeatedly type sudo before many commands gets annoying.. if you want root privileges without having to keep typing sudo before every command type "sudo su" and then your password 
best of luck and welcome to ubuntu linux :)  its amazing the switch from windows to this OS.. and ubuntu is a great first step into linux with all this assistance in these forums

---

