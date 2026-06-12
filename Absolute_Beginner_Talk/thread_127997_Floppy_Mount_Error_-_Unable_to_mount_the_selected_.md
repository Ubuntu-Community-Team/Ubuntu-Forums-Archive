---
title: "Floppy Mount Error - Unable to mount the selected volume"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-10
Hello everybody,

I have a simple question:

I tried to access a Floppy Disk in Ubuntu & I got the following Error Window:

Window Name:      Mount Error
Window Contents: Unable to mount the selected volume

This floppy was formatted in Windows in FAT32.

Why can't I see the contents, copy or write to it?

From what I know, Linux can read/write to FAT32 drives.

Please help...

---

### Post by Klaidas on 2006-02-10
Hmm. Don't know how much it would help, but try doing this:
[http://www.linux.org/lessons/beginner/l13/lesson13c.html](http://www.linux.org/lessons/beginner/l13/lesson13c.html) and [http://www.linux.org/lessons/beginner/l13/lesson13d.html](http://www.linux.org/lessons/beginner/l13/lesson13d.html) :)

---

### Post by Pragmatist on 2006-02-10
What exactly did you type to mount the floppy?

---

### Post by george_apan on 2006-02-10
Have a look at this:
[http://ubuntuforums.org/showthread.php?t=104259](http://ubuntuforums.org/showthread.php?t=104259)

---

### Post by dvarsam on 2006-02-10
I managed to find a solution, which I will post for all the Newcomers, like Me.

**File systems in Linux:**
That is to say, the way data is stored and managed in Linux.

MS-Windows, from Windows 95 on up uses a File System called 'vfat'.
Linux uses a different System called 'ext2'.

You may have chosen to have both Windows & Linux installed in your computer.
At one point, you might have to access files in the Windows partition of your hard drive.
You would use a command called 'mount' to do that.

You would also have to indicate as an option in that command that the File System you want to access or "mount" is a Windows 'vfat' File System. 

_Assumption_:
Your Floppy is already Formatted.
For this, read:
[http://www.linux.org/lessons/beginner/l13/lesson13c.html](http://www.linux.org/lessons/beginner/l13/lesson13c.html)

**Mounting file systems (e.g. Accessing Floppy):**
We'll learn how to use the commands mount & umount.

In Linux the Floppy Drive or other device MUST be "mounted".

That means basically, incorporating it temporarily into your Linux File System or, in other words, telling Linux that it is a file to be written to or copied from. 

Before you access a Floppy disk, make sure that in your root directory, you HAVE a directory called floppy.

Before you start, open the "Terminal" window, that is from Menu, select:

Applications\Accessories\Terminal

In the command prompt, type:

            sudo -i

The above command helps you start a root shell (i.e. a command window where you can run root commands).

When asked to type your password, type:

	"Your password"

The above password, is the one you typed during the installation of Ubuntu, when you first created your account. If you only have one account on your computer, it is that same password you use every time you startup your computer.

To verify that you are Logged-in as a root user:

user_name@ubuntu:~$		   sudo -i
Password:		                	******
root@ubuntu:~#

The word "root" above verifies that you are logged-in as a root user (superuser).

To access your root directory & check if you have a floppy directory, on the command prompt type:

		cd /

Now you are in the root directory.

Use the command "ls -l", to check whether the floppy directory exists.

Note:
In Ubuntu, the root directory does NOT have a floppy directory.
You MUST create one.

To do this, in the command prompt, type:

		mkdir floppy

Now you are ready to access the Floppy disk.

To access a Windows Floppy disk from the command line of our shell, we would use the command "mount" and type the following: (remember: you need to be working as 'root' to do this):


mount -t vfat /dev/fd0 /floppy	( < - You type this as long as floppy directory EXISTS)

To access a Linux Floppy, you would ONLY change "vfat" to "ext2".

Note:
By performing the above command, a Floppy icon should show on the Desktop.

Let's explain what we've just done here. When we typed: mount -t vfat /dev/fd0 /floppy we told Linux that our floppy disk is now part of our Linux File System ("/dev/fd0") & that any files we would like to store on that disk will be copied to "/floppy", as if it were just another directory on our Linux system.

To view the contents of the Windows Floppy, at the command prompt, type:

	cd /floppy

Then, type the command:

	  ls -l

All the floppy's contents should print on a list.


To copy a file from the Desktop to the Floppy, you MUST use the "Terminal", if you have NOT booted as the root user.

To move to the Desktop folder, in the "Terminal" window, type:

	cd /home/user_name/Desktop

To perform the move, type:

	mv filename /home/user_name/Desktop

_SOS_:
Make sure you do NOT type "mv filename /Desktop", cause this command MOVES the filename to the root directory & ALSO renames the file to a name called "Desktop".
One of the first things you learn in a Unix class, for this exact reason, is to NEVER use the "mv" command, except to rename things.
It is MUCH safer to use the "cp" (copy) & then "rm" (remove) to the filename, than use the  "mv" command.

You can go now & check whether the Floppy includes the filename you just added.

**Umount command:**
Mounting file systems that aren't part of the standard Linux system is considered a temporary condition in Linux. Now that we know how to mount these outside file systems in Linux, the important thing now is to learn how to unmount it when we're finished using it. 

In the early days of Linux, you could do serious damage to your System if you didn't unmount manually after you were finished.

Nowadays if you have mounted a System & you shut down the computer without unmounting, the chances are pretty slim that you're going to trash a File System.

Slim, however, isn't good enough for me. I'd rather not take a chance.

The command for this is:

              umount /floppy

Note:
You can also do this from the Desktop.
Right-click on the Floppy icon & select "Unmount Volume".
You are 'unmounting' but the command is _u_mount (that is, without the N of un).

Good Luck,

Dimitris.

---

### Post by Pragmatist on 2006-02-10
First, let me say that I think its great that you took the trouble to research and write such a thorough explanation for the benefit of others like yourself.

There are some statements I think are wrong, however. 

> In Ubuntu, the root directory does NOT have a floppy directory.  You MUST create one. 

I've used over a dozen different distributions of Linux and none of them had **/floppy**  and I haven't had to make a **/floppy** directory.  In Linux, the floppy directory is in one of two places.  Classically, all mount directories are located in:  ** /mnt**  Since the advent of ***udev*** you find your mount point directories in **/media**  If you look there you will find the floppy directory.
> To copy a file from the Desktop to the Floppy, you MUST use the "Terminal", if you have NOT booted as the root user.Yes and no.  Take a look at your **/etc/fstab** file there are entries like this:
> /dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

In the section **rw,user,noauto**  Here, **user** allows any user to mount floppy.  Note: to mount this you'd type:
```
mount /dev/fd0 /media/floppy0
```  Since there is a line in fstab, however, you can just type: ```
mount /media/floppy0
```  or ```
mount /dev/fd0
```  For more details on how to configure your **/etc/fstab** file to allow users other than root to mount drives, check out: 
```
man fstab
```

---

### Post by dvarsam on 2006-02-10
As you said:
...Take a look at your "/etc/fstab" file there are entries like this...

I tried to open the file with "gedit fstab" (from the Terminal as root user), and I cound not open the file.

The Output I got was:
(gedit:11023): Gtk-WARNING **: cannot open display:
root@ubuntu:/etc#

Please keep in mind that I am a beginner in Linux, so I might be doing something wrong...

How did YOU open the file?

---

### Post by Pragmatist on 2006-02-10
I opened it with ```
vi
```  which is a CLI (Command Line Interface) editor.  The message you got has nothing to do with /etc/fstab  It is some other problem which you should probably post as a separate issue.  What is probably happening is that gedit isn't gettting access to the display and therefore can't open to edit /etc/fstab.

Just to show you that, try this:```
cat /etc/fstab
```  This will output the file (it is only a few lines) to the screen but you won't be able to edit it.  To edit it with ```
vi
``` type ```
vi
```  once in the editor you can move around with the arrow keys and when you get to where you want to edit just press ```
i
```  This puts you in edit mode and you can modify the text.  When you are done type: ESC to get back into command mode and the type  ```
:wq
```  If you don't want to save the changes or just want to exit type ESC to get into command mode and then type ```
:q!
```  You probably want to make a copy of the file in case you make a mistake.  Also, to make changes to this file you'll need to be root.

---

### Post by Pragmatist on 2006-02-10
btw, I'm assuming you were in the **/etc** directory when you typed ```
gedit fstab
```  If not, you should try: ```
gedit /etc/fstab
``` just to make sure that that wasn't the problem.

---

