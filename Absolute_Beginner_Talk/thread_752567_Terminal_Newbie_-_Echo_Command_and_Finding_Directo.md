---
title: "Terminal Newbie - Echo Command and Finding Directories"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by DanseNoir on 2008-04-11
I'm a complete newbie.  I've only been using Ubuntu for a few days and while I'm having a lot of success quickly learning most of the other aspects of Ubuntu, I'm still having tons of trouble using Terminal.  I'm trying to set up my wireless and the problem is that every tutorial has a ton of command lines with little explanation as to what I'm actually doing.  

Following [this tutorial]("http://ubuntuforums.org/showthread.php?t=112526") on how to set up my wireless, I'm on Step #4.  The author suggests using this command line:

> echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

When I enter it, I get this result:

> blacklist bcm43xx

The author goes on to say:

> The bcm43xx driver is a linux proprietary driver that will make some wireless cards with a Broadcom chipset work, but it is only "okay", and it may conflict with your wireless hardware and prevent your wireless from working with ndiswrapper.

Despite its mere OKness, I'm perfectly content to use this driver.  So my question is, how do I discover its directory in order to continue with the tutorial?  Was the echo command suppose to do this for me or do I have to manually search for the directory?  I'm confused.  


Hope this question wasn't too stupid.  Methinks I need to discover a very thorough primer on Terminal at some point in the near future.  :)

I did find a few things on this forum, but they didn't help unravel the meaning of "echo" for me.

Also, would this be the appropriate forum for posting this or is there a more terminal-centric forum I should post this in?

---

### Post by andrewc6l on 2008-04-11
What the command does is append the text 'blacklist bcm43xx' to the file /etc/modprobe.d/blacklist, and also print it out to the console. (The echo command does the printing, and the tee -a command does the appending.)

If you want to remove that, you'll need to edit /etc/modprobe.d/blacklist using your favourite text editor as the root user (sudoedit should do that).

Here's some useful info about the shell:
[http://partmaps.org/era/unix/shell.html](http://partmaps.org/era/unix/shell.html)

---

### Post by spiderbatdad on 2008-04-11
It's directory is /etc/modprobe.d   the file is 'blacklist'
You can navigate to it Places>>Computer>>File System>>etc>>modprobe.d>>blacklist
But in this mode, you will not have permission to edit the file...only to view it.
If you enter ```
gksu nautilus
``` 
in the terminal...then password...you can navigate to the file again, with write permission...be careful in this 'super user' mode.

---

### Post by handydan918 on 2008-04-11
> **DanseNoir said:**
> I'm a complete newbie.  I've only been using Ubuntu for a few days and while I'm having a lot of success quickly learning most of the other aspects of Ubuntu, I'm still having tons of trouble using Terminal.  I'm trying to set up my wireless and the problem is that every tutorial has a ton of command lines with little explanation as to what I'm actually doing.  

Following [this tutorial]("http://ubuntuforums.org/showthread.php?t=112526") on how to set up my wireless, I'm on Step #4.  The author suggests using this command line:



When I enter it, I get this result:



The author goes on to say:



Despite its mere OKness, I'm perfectly content to use this driver.  So my question is, how do I discover its directory in order to continue with the tutorial?  Was the echo command suppose to do this for me or do I have to manually search for the directory?  I'm confused.  

No, that command is supposed to send the output of the 'echo' command to the target file (/etc/modprobe.d/blacklist), in other words, it adds that module to the "don't load this module"list. 

> 

Hope this question wasn't too stupid.  Methinks I need to discover a very thorough primer on Terminal at some point in the near future.  :)

I did find a few things on this forum, but they didn't help unravel the meaning of "echo" for me.

Also, would this be the appropriate forum for posting this or is there a more terminal-centric forum I should post this in?

I like your attitude. You'll do well. 
Try the manual pages. They are a bit cryptic, but the raw info is there if you want to learn. 
From a terminal, do ```
man echo
```
and you'll get a manual page about the echo command. You can find a man page on almost anything in the linux world by doing ```
man <command>
```


You can even do ```
man man
```

or ```
man bash
```

---

### Post by DanseNoir on 2008-04-11
Ahhh ... thank you so much to all of you!  I understand now :)

---

### Post by JoshuaRL on 2008-04-11
> **DanseNoir said:**
> Ahhh ... thank you so much to all of you!  I understand now :)

For help with the terminal, try the "Learn the Terminal" link in my sig.  It's a great site and helped me out a lot.

---

