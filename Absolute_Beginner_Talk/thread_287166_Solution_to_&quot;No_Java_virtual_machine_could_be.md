---
title: "Solution to &quot;No Java virtual machine could be found from your PATH&quot;"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by Contrast on 2006-10-28
Just thought I'd share this as it might save someone else the few hours I've spent trying to get past it. I didn't see any other threads that listed what I had to do to get this to work.

If you're trying to install a program that runs in a Java environment, and you're a noob like myself, chances are you've come across this problem. The first thing you need to do, obviously, is install Java. I won't go into the details of that process as it's been thoroughly covered elsewhere. This post is dealing more with situations where you see the message in the thread title after you've installed Java.

(For all of the following commands, you'll obviously need to replace "/home/mike" with the actual directory that jre1.5.0_09 resides in, as well as changing mike:mike to yourusername:yourgroupname.)
After installing Java, you should have a folder named jre1.5.0_09. Now you need to make sure that directory and its relevant subfolder are in your path. Enter these commands in the terminal:> PATH=$PATH:/home/mike/jre1.5.0_09
PATH=$PATH:/home/mike/jre1.5.0_09/bin You can go ahead and try running the installation file for whatever you're trying to install now; in my situation, it kept coming back with the same error message about the virtual machine not being installed. This seems to be a rare case, but I had to change permissions and ownership of the folder before the installer would recognize it.

[It's possible that you only need to do one of the following (I went ahead and did both before trying to run the installer, and I'm not going to bother messing with it at this point), so after changing the ownership, try running the installer again to see if you actually need to change the permissions. If jre1.5.0_09 is located in a system-critical folder, such as /usr, I do not recommend performing either of the following steps prior to [moving the folder to a different location]("http://www.ss64.com/bash/index.html"). I've done this in the past and experienced major problems, e.g., My desktop environment wouldn't load at all.]

To change the ownership so that "mike" is the owner and the group, enter> sudo chown mike:mike /home/mike/jre1.5.0_09 Now let's change the permissions.> sudo chmod 777 /home/mike/jre1.5.0_09Like I said, actually having to do all of this seems to be a rare case, as the problem is usually solved by just including the relevant folders in your path (judging by the couple dozen threads and troubleshooting guides I went through).

---

### Post by DaveBorealis on 2006-10-28
Another option is to install the jre as root (using sudo) and have it placed somewhere in the default path for all users.  It should work without having to change any permissions or ownerships.

If you do need to add a directory to your path, assuming that you use BASH, you can add it to /home/<user>/.bash_profile and it'll be permanent:
export PATH=$PATH:/some/new/directory:
 
Best regards,
Dave

---

