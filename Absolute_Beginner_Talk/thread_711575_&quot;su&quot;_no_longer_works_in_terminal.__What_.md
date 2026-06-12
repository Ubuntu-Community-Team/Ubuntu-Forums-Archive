---
title: "&quot;su&quot; no longer works in terminal.  What happened?"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Motorhead Kaze on 2008-02-29
The title pretty much sums it up.  I was trying to install something from the terminal, used ```
su
``` to get root power and it was fine.  But soon after, su stopped working and I get ```
kaze@kaze:~$ su
Password: 
su: Authentication failure
Sorry.

```  I have not changed passwords, and my password works for everything else.

---

### Post by taurus on 2008-02-29
Which password did you use?  Su requires the actual root password, not your password, the one that you use to log in with.  Did you create a password for root?

---

### Post by falkaholic on 2008-02-29
try 

```

sudo su -

```

there is also some terminal packages that start as root.

---

### Post by Nythain on 2008-02-29
and remember... sudo, gksu, kdesu are all your friends, su is not :P

---

### Post by aysiu on 2008-02-29
What do you mean by *no longer works*? Are you saying you were able to *su* to root before? In other words, you've already activated the root account and given it a password?

If not, then use *sudo*.

What are you trying to install? I've never heard of any software installation that requires you to log in as root.

---

### Post by Motorhead Kaze on 2008-03-01
Hello and thank you all for the responses.

I see our "Guardian against root attacks" is on the job, and thank you Aysiu.  I appreciate the comments you have made about being careful using root power.

To answer the question, I was having a Java issue.  Sorry to add lots of details, but:
Somehow I ended up with Java 1.7, something related to a program called "Iced Tea"? That was covering up or otherwise in the way of Java 1.6.  I did not know this was the case at first, so I went chasing wild geese.   I needed 1.6 to run a Japanese to English translation tool.  Fully understanding that most people say, "If it ain't in synaptic, you don't need it" I decided to follow Java's instructions on how to get 1.6 from them.

Linux download and installation instructions for the Java Runtime Environment (JRE)
To install the Linux (self-extracting) file
Follow these instructions:
   1. At the terminal: Type:       su
   2. Enter the root password.
   3. Change to the directory in which you want to install. Type:
      cd <directory path name>
      For example, to install the software in the /usr/java/ directory, Type:
      cd /usr/java/
Note about root access: To install the JRE in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the JRE in your home directory or a subdirectory for which you have write permissions.
   4. Change the permission of the file you downloaded to be executable. Type:
      chmod a+x jre-6u<version>-linux-i586.bin
   5. Verify that you have permission to execute the file. Type:
      ls -l
Start the installation process.Type:
./jre-6u<version>-linux-i586.bin
6. This displays a binary license agreement. Read through the agreement. Press the spacebar to display the next page. At the end, enter yes to proceed with the installation

and so on.  At first when I did this, su did work, and I got all the way to DONE.  But I was still told that I was running 1.7.  And now we are back to the point where I remembered I could go to Synaptic and search for this 1.7.  A bit backwards in process, but oh well.  Nothing was broken, and I will remember this for the future.  It is all about learning isn't it.

Now, as to why, since I am the only user, and installed Ubuntu with one password, use the same password in synaptic, and for sudo nautilus, etc. and why that isn't the same as the root password, I will have to assume this is a noob proof security measure, so one doesn't just go and destroy their system.  Not a real hassle to go and make a root password I suppose. 

BUT, typing in su did work at first, with my login password.  So I have to assume that this IS the root password, and which is why I posted this comment in the first place.  If it had never worked, I would have written a post about that instead.  So, what, is my system just a freak or what?

On a related topic, trying to install this translation software, a friend said if it isn't in synaptic you can't trust it.  That is ridiculous.  A free, Japanese language translation tool for Linux has got to be one of the least common programs I could ever try to get.  There is no way that will ever find its way into Synaptic.  So I shouldn't use it?  How stupid.  Part of the reason I came to Linux is because I like the adventure.  Sheesh.

Now if you are still wondering why I would want to install the translation software as root, I quote the guy who wrote this software:
If you execute the installer as root (su):
* The program is installed in a folder accessible to all users 
* An icon is added to GNOME and KDE menus
* The command to launch the program (swordfish) is automatically added
to system path 

I hope this seems like good sense. And if not, you are certainly welcome to comment.  Especially if you know why su worked first but stopped working.  Also, if you would like to tell me where I should go to make a root password, that would be cool too.

 I still haven't got the software up and running. 

Cheers.

---

