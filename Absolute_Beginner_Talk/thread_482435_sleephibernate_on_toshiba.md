---
title: "sleep/hibernate on toshiba"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by whauser on 2007-06-23
hello all, this is my first post.  I've got ubuntu up and running on my toshiba a135-s2386, I've got the sound working and have installed a gysynaptics touchpad controller.  I've been following the how to on this page:

[http://arbitraryusefulinfo.wordpress.com/2007/06/12/configuring-ubuntu-on-a-toshiba-a135-s2356/](http://arbitraryusefulinfo.wordpress.com/2007/06/12/configuring-ubuntu-on-a-toshiba-a135-s2356/)

I can't get the sleep/hibernate mode to function correctly though.  The machine will now sleep but I can't get it restarted afterwards.  I've completed the steps listed on the page with the exception of the last line of code:
echo "/sbin/s2ram-install -f" > /sbin/s2ram; chmod 755 /sbin/s2ram;

I get this error message:
bash: /sbin/s2ram: Permission denied
chmod: cannot access `/sbin/s2ram': No such file or directory

I've looked at the s2ram home page and they have a few recommendations but I am concerned that I've been moving and renaming things and I don't want to screw up the pmi coding (package installer?).

So, can I undo what I've done and try a different approach to the sleep/hibernate issue?  Or can I complete the process I started and get it working?

Thanks

---

### Post by sparc1998 on 2007-06-24
Hi,

I'm the author of [http://arbitraryusefulinfo.wordpress.com](http://arbitraryusefulinfo.wordpress.com).  In order to run ```
echo "/sbin/s2ram-install -f" > /sbin/s2ram; chmod 755 /sbin/s2ram;
``` you need root privileges.  Probably the easiest way to accomplish that is to run the following two commands instead of the one you originally tried to run.  ```
sudo echo "/sbin/s2ram-install -f" > /sbin/s2ram
``` ```
sudo chmod 755 /sbin/s2ram
```

Since this is the beginner's forum I wanted to briefly explain the change.  The original command is really two commands.  Multiple commands on the same line are separated by semicolons.  So, the first thing I did was split the command into two separate commands.  The second thing I did was prepend each of those commands with sudo.  By putting sudo in front of a command, you are instructing the OS to turn you into root while the command is executed, giving you the required root privileges.

---

### Post by whauser on 2007-06-24
Thanks,
I did some searching on the sudo command and found it helpful.  I'm still running into some problems running those last two commands though.  
The first half gives me the "permission denied" message and the second half then says the file or directory doesn't exist (presumably because the first command did not successfully execute).  Here's the exact code I entered into the terminal, I re-ran it from the beginning:

will@will-laptop:~$ sudo dpkg-divert --rename --divert /usr/sbin/pmi-disabled /usr/sbin/pmi
Leaving `local diversion of /usr/sbin/pmi to /usr/sbin/pmi-disabled'
will@will-laptop:~$ sudo dpkg-divert --rename --divert /sbin/s2ram-install /sbin/s2ram
Leaving `local diversion of /sbin/s2ram to /sbin/s2ram-install'
will@will-laptop:~$ sudo echo "/sbin/s2ram-install -f" > /sbin/s2ram
bash: /sbin/s2ram: Permission denied
will@will-laptop:~$ sudo chmod 755 /sbin/s2ram
chmod: cannot access `/sbin/s2ram': No such file or directory


You can see that the first two lines of code ran successfully - the diversions in place are left alone.  However, the echo command fails and I'm not sure why.

Thanks for your help.  I have to say, this open source community is full of helpful and intelligent people.  I'm liking Ubuntu better and better, it's definitely not a memory hog like Vista.  The open office applications are also far better than I expected - perhaps even better than MS ;)

---

### Post by sparc1998 on 2007-06-24
As you suggested, the second command failed because the first command failed.  Just so you know, the first command is supposed to create the file /sbin/s2ram, and the second command changes the permissions of /sbin/s2ram.

On a side note, whenever you're not sure how to use a command or don't know what it does, you can type "man" followed by the name of the command, e.g., "man sudo."  That will start up a manpage, an informational page on the command.  You can scroll through it with the up and down arrows and the spacebar.  When you want to exit the manpage, simply hit "q."  If you want to search through the manpage, hit "/" and then type the word for which you want to search, followed by return.

Back to your problem.  Instead of the command ```
sudo echo "/sbin/s2ram-install -f" > /sbin/s2ram
``` try ```
sudo vi /bin/s2ram
```  That will open a text editor called vi.  The first thing you need to do when the text editor starts is hit "i," which will put vi into insert mode where you can freely type.  At that point, type ```
/sbin/s2ram-install -f
``` followed by hitting escape.  After that, type ":wq" and hit return.  That should create the file /sbin/s2ram.  Then you can execute ```
sudo chmod 755 /sbin/s2ram
```

If for some reason the above does not work, can you type the following 3 commands and post the results.  ```
ls -ld /
``` ```
ls -ld /sbin
``` ```
ls -l /sbin/s2ram
```

---

### Post by whauser on 2007-06-25
sorry, still no dice.  I checked the bin folder and there is a text file named "s2ram" that contains the text I inserted in the VIM editor - "/sbin/s2ram-install -f"

When I look in the sbin folder I see the s2ram-install file; it is an executable file.

I see in the code that the chmod is referencing the s2ram file in the sbin folder but this file does not exist -  only the s2ram-install file is present.  If I reference that file instead the command executes without an error message but nothing seems to happen as a result.  

Here are the results of the other bits of syntax you asked me to run:

will@will-laptop:~$ ls -ld /
drwxr-xr-x 21 root root 4096 2007-06-23 09:24 /
will@will-laptop:~$ ls -ld /sbin
drwxr-xr-x 2 root root 4096 2007-06-23 19:19 /sbin
will@will-laptop:~$ ls -l /sbin/s2ram
ls: /sbin/s2ram: No such file or directory
will@will-laptop:~$ 

the "/" on the second line and the "/sbin" on the 4th are highlighted in blue.

On a side note, how do you delete swp files?  After closing a terminal window without saving I now have one present.  As far as I can tell it is essentially a log file from which I can recover my work - being that I am only cutting and pasting a single line into the VIM editor I have no need to recover anything.  Nonetheless, VIM gives me this warning every time I access the /bin/s2ram.  I can't delete the file from the file folders because, evidently, it is prepended with the "." so it doesn't show up.  There are lots of sites that suggest deleting the recovery files if you don't need them but not one indicates how exactly I should do so.

Thanks again

edit:  I see now that the "." simply makes the file hidden and that, as in windows, the hidden/system files can be made viewable.  However, ubuntu still has this user security system where no users have root privileges, thus I cannot delete the files from the viewer because I can't log in as root.  So, I guess what I have to do is delete the file from the terminal but I'm not sure what the correct command would be.

---

### Post by dresnu on 2007-06-30
I see you are having problems with root privileges.
I must say that the easiest way to gain them imho is to type ```
sudo bash
```and then type your user password. This will make you root and you can change anything ;-)

---

