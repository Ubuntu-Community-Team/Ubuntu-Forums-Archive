---
title: "Deleting a write protected directory"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by destromofia on 2006-09-13
Hello everyone, I am a bran-spanking-new Linux user and I am using ubuntu as my Distro.

My question is this:

I recently downloaded a directory to my desktop that I now want to delete, but I cant because it is write protected. 
Now when I ripped my cd's to my hd, they were all write protected too, but I was able to right click on them to change the permissions, this directory wont let me do that, it says that I am not the owner of the file.

I have looked around for commands to type in the terminal to solve this, but nothing I try seems to work, I am always getting an error either saying that it cant delete because I dont have permission, or that it cant delete because the directory isn't empty.

I know I am just missing somthing simple, and Im sorry for the noobishness, but I am really getting fed up.

Any help would be appreciated.

---

### Post by meng on 2006-09-13
sudo rm -rf (name of directory)
Enter your user password when asked. The password will not echo to screen.

---

### Post by Timothy Butwinick on 2006-09-13
To get permission:
"sudo rm YOUR_FILE"

To remove a folder containing files:
"rm -R YOUR_FOLDER"

---

### Post by destromofia on 2006-09-13
ok I tried both of those commnads, this is what I get in terminal.

david@DVR:~$ sudo rm scorched3d-40
Password:
rm: cannot remove `scorched3d-40': Is a directory
david@DVR:~$ rm -R scorched3d-40/
rm: descend into write-protected directory `scorched3d-40/'? y
rm: descend into write-protected directory `scorched3d-40//usr'? y
rm: descend into write-protected directory `scorched3d-40//usr/bin'? y
rm: remove write-protected regular file `scorched3d-40//usr/bin/scorched3d'? y
rm: cannot remove `scorched3d-40//usr/bin/scorched3d': Permission denied

Any Ideas?

---

### Post by meng on 2006-09-13
sudo rm -R scorched3d-40

---

### Post by aysiu on 2006-09-13
How about Alt-F2 ```
gksudo nautilus
``` This will launch a file browser as root. You can then go to the folder and delete it.

The command-line is powerful, but it's sometimes a little *too* powerful. You could be meaning to type ```
sudo rm -rf /usr/bin/scorched3d
``` and you hit the *Enter* key too soon... and lose your entire OS!

---

### Post by destromofia on 2006-09-13
The sudo rm -R scorched3d-40 command worked, thanks a lot for all the help.

I am glad I didnt have to mess with any commands that would potentialy destroy my OS, my wife would kill me if I lost all of our music. \\:D/

---

### Post by meng on 2006-09-13
Two words:
Backup. Often.

---

### Post by gigi1234 on 2006-09-13
I have never figured out how to delete a directory that is full of files. But if you cd into the directory and remove all the files first then you should be able to delete the directory. (You will still have to sudo the commands).

This is a lame work-around. But it works.

---

### Post by Timothy Butwinick on 2006-09-13
What if it's full of folders full of folders full of folders and so on? In the end, this is the easiest way.

---

### Post by gigi1234 on 2006-09-13
Yeah that is the trouble! This was just the only noob-headed way I could figure out how to do this. 

I would rather have an easier way. 

So you just use the -R append?

---

### Post by gigi1234 on 2006-09-13
I have used the sudo nautilus approach most often these days.

You can even create a custom launcher to launch nautilus as root from the desktop or taskbar. Probably a lot safer in the end.

---

### Post by aysiu on 2006-09-13
Hopefully your custom launcher will have the command *gksudo nautilus* instead of *sudo nautilus*.

---

### Post by gigi1234 on 2006-09-13
Explain the difference? I just used sudo nautilus...

---

### Post by aysiu on 2006-09-13
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by gigi1234 on 2006-09-13
Great! Thanks!

---

