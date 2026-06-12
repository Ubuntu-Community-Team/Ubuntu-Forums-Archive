---
title: "Deleting files and recursivity"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by Roger_Melly on 2007-03-02
:confused: 

Hello good people,
I have been running Ubuntu for several days and am still trying to find my way around it.  I love the fact that it works out of the box, so to speak.  However there were one or two things I am struggling with.  I have worked out how to use my windows NTFS files which now sit on my desktop.  Unfortunately while I was doing this I created two unwanted files on my computer.  I have a book by Keir Thomas which gives an overview of things but when it comes to deleting files he talks about RECURSIVE files and directories.  I have tried searching for a solution but I'm not sure that such a simple question exists!

Directory=Folder

_Q1. How to delete files within directories_
 I would like to delete a directory called Windows.  It sits within /media/Windows.

If I type: [COLOR="SandyBrown"] sudo rm -rf /media/Windows[/COLOR]  will this only delete the Windows file in that directory or will it delete the media directory as well.

Or do I just type: [COLOR="SandyBrown"] sudo rm -rf Windows[/COLOR] because Nautilus will not allow duplicate file names?

_Q2. Is it possible to move the windows folder on my desktop to somewhere less conspicuous?_  
I only use it for music files and so on.

Thankyou for your time.:D

---

### Post by ComplexNumber on 2007-03-02
Q1
what exactly are you trying to do? 
you say "I have worked out how to use my windows NTFS files which now sit on my desktop". don't you mean that the *link* to windows sits on your desktop?

by using those commands that you've stated, its almost as if you're attempting to delete  all your windows stuff in your windows partition. thats not recommended to go about it that way, if thats what you're trying to do.

---

### Post by xyz on 2007-03-02
[of related interest]("http://www.ubuntuforums.org/showthread.php?t=373325")

---

### Post by anaconda on 2007-03-02
Q2. Anything that is mounted to /media will be showing on your desktop. So what you want is to mount it eg. to /mnt. to do that you will have to edit your /etc/fstab file..

eg. first create the new directory where you want windows:.
sudo mkdir /mnt/windows
then open fstab to editor:
sudo nano /etc/fstab

and search the place where it reads "/media/windows" and change it to "/mnt/windows" and save and exit with Ctrl-x 

next time you boot your windows partition will be mounted to /mnt/windows, and it wont be showing on the desktop anymore..

---

### Post by Roger_Melly on 2007-03-02
Guys,
I have mounted my NTFS patition to use my old stored data such as music, photos etc.  Whilst doing this and following several lines of advice i downloaded the NTFS Configuration tool.

Unfortunately for a total noob like myself at the bit where it said name your file I tried entering all sorts of stuff like "/media/Windows" and it kept telling me that I couldn't use certain text i.e. /
What I now know is that it was as easy as typing something like "DAVE" and hey-presto a new folder/Directory is created at /media/DAVE.

I didn't do this I started making directories.  sudo mkdir /media/windows_ntfs, and sudo mkdir /media/Windows.  (please note the text sensitivity)

I gave up on this process and went back to the configuration tool and just typed "windows" and it all did it automatically for me!

So I now have my windows data in a file called "windows" on my desktop and I want to get rid of the other two directories from within my media directory (they are both empty)

As you can see I am a good example of how a little knowledge is a dangerous thing:lolflag:

---

### Post by rjfioravanti on 2007-03-02
In Debian systems, isn't /media the standard location for all secondary memory storage devices? except for the linux partition and the swap partition? (ie cdrom, usb memory sticks, other partitions)

Moving those to /mnt would probably be more confusing for you later, the thing you see on your desktop is just a link, or shortcut, to the /media/Windows location

---

### Post by Roger_Melly on 2007-03-02
See my comments.
Cheers

---

### Post by Roger_Melly on 2007-03-02
Folks,
the advice I had was to mount the NTFS in media, I don't know the ins and outs of why.  I have configured Amarok to it.

I am still in the dark about the deleting thing.

---

### Post by rjfioravanti on 2007-03-02
You confused me with one of your previous posts, and its not really clear if you changed your mind and what stage you are at now

What do you think is currently wrong with your setup, and how do you want it to be

---

### Post by Roger_Melly on 2007-03-02
Hello rjfioravanti,
I am simply trying to delete unwanted empty folders in my computer/filesystem/media directory.

I would also like to hide the windows drive icon that i have on my desktop.
See the screen shot attached.

---

### Post by rjfioravanti on 2007-03-02
ok well your OS is setup to automatically mount your windows ntfs partition. It mounts it by default in /media/windows

if you double click on the windows drive on your desktop, you will see it just opens the directory /media/windows, because it is a shortcut to that location, if you go into a terminal, and do 

cd ~/Desktop
ls

you will notice that windows does not appear, because it is not actually on your desktop. 

Most people are ok with this, if it bothers you, and you don't want to see that windows drive icon on your desktop anymore, you are going to have to mount it in a location other than /media/ directory

To do this you are going to have to follow instructions provided by anaconda above, which explain how to mount it in a different location every time your computer starts up. He recommends /mnt

---

### Post by xyz on 2007-03-02
Can you please do this:
```
th@luser:~$ cd /media/
th@luser:/media$ ls -l

```
and post the output of  ls -l  to see what's in there. Thnx.

---

### Post by konst88 on 2007-03-02
You can delete empty folders using:
rmdir folder_name

---

### Post by Roger_Melly on 2007-03-02
total 28
lrwxrwxrwx 1 root root     6 2007-02-27 19:09 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2007-02-27 19:09 cdrom0
lrwxrwxrwx 1 root root     7 2007-02-27 19:09 floppy -> floppy0
drwxr-xr-x 2 root root  4096 2007-02-27 19:09 floppy0
drwxrwxrwx 1 root root 12288 2007-02-28 16:21 windows
drwxr-xr-x 2 root root  4096 2007-03-01 19:57 Windows
drwxr-xr-x 2 root root  4096 2007-03-01 19:18 windows_ntfs

windows is the one I want to keep.
**W**indows and windows_ntfs I want to delete.

---

### Post by Roger_Melly on 2007-03-02
Bounce):P

---

### Post by rjfioravanti on 2007-03-02
try editting the fstab to remove the mounts you dont want

---

### Post by Roger_Melly on 2007-03-02
These two
drwxr-xr-x 2 root root 4096 2007-03-01 19:57 Windows
drwxr-xr-x 2 root root 4096 2007-03-01 19:18 windows_ntfs
arent actually mounts they are just empty folders........
can i type: rm -rf Windows or do I type rm -rf /media/Windows to delete that empty folder?

---

### Post by Nythain on 2007-03-02
you really only NEED the whole path if you are somewhere else on your system...

in /home you would typ sudo rmdir /media/Windows
in /media sudo rmdir Windows should do the trick

---

### Post by Roger_Melly on 2007-03-02
Nythain thanks,
I thought I was making it clear but also guessed that people might not actually believe I'm this much of a Noob!:lolflag: 

I am _terrified_ of deleting the whole media file.

So I type: sudo rmdir windows_ntfs
OR : sudo rmdir /media/windows_ntfs.

As to the mount Q someone stated that this would have to be done each time I start??? is this right or will that be the end of it?

I'm sure it's just me:) 

P.S. would you mind having a look at my crash post!

---

### Post by Roger_Melly on 2007-03-02
whoops

---

### Post by Nythain on 2007-03-02
whoops?? hope that wasnt a bad whoops

ok, on the mount thing... if you edit your fstab and change the mount point from /media to /mnt changes wont take effect untill you reboot, and it will mount it there everytime you boot

---

