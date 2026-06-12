---
title: "[SOLVED] Silly question - What is the &amp;quot;#&amp;quot; for?"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by snteran on 2008-03-07
I am in the process of reinstalling Nagios.  And I am using two different install procedures.  I am basically verify one with the other.  I'm hoping to get this install done correctly.  I do notice that sometimes they have the same request but one has the "#" in front of the command.
i.e.: 
# tar -xvf nagios-2.6.tar.gz 
or
tar xzf nagios-3.0rc3.tar.gz

I can see that one is in reference to different versions of nagios that you might download and install.  But first I see a "#" and then there is a "-" in from of the xvf.

I know this might be simple, but I have looked in my Linux Bible text book and in this forum and found no information.

Thanks,

---

### Post by Snakob808 on 2008-03-07
# is a comment.  It does not execute.

---

### Post by uberlube on 2008-03-07
# usually means 'comment out'/ so in a script, that line would be bypassed.

---

### Post by maybeway36 on 2008-03-07
Sometimes the # means you should do it as root. Don't actually type it in. (Notice how the prompt ends with $ as a user and # as root)

---

### Post by steveneddy on 2008-03-07
> **maybeway36 said:**
> Sometimes the # means you should do it as root. Don't actually type it in. (Notice how the prompt ends with $ as a user and # as root)

+1

---

### Post by PeterJS on 2008-03-07
And as for the dash in the tar command, newer versions of tar do not require the dash, but in older versions have stricter adherence to the idea that all flags should start with a dash. Some people include it, others don't, you can tell the old school curmudgeons from the newer users, as the old school types still include the dash even though it's not required.

---

### Post by akiratheoni on 2008-03-07
> **snteran said:**
> I am in the process of reinstalling Nagios.  And I am using two different install procedures.  I am basically verify one with the other.  I'm hoping to get this install done correctly.  I do notice that sometimes they have the same request but one has the "#" in front of the command.
i.e.: 
# tar -xvf nagios-2.6.tar.gz 
or
tar xzf nagios-3.0rc3.tar.gz

I can see that one is in reference to different versions of nagios that you might download and install.  But first I see a "#" and then there is a "-" in from of the xvf.

I know this might be simple, but I have looked in my Linux Bible text book and in this forum and found no information.

Thanks,

It depends. A # in a text file means that the line is commented and will be ignored.

However in your case, I believe it is referring to root. Normally the command would look like this if it were as a normal user:

$ tar -xvf nagios-2.6.tar.gz 

The # means you need to log in as root. But don't do that... instead, do this:

$ sudo tar -xvf nagios-2.6.tar.gz 

The $ and # just designate which user level you are supposed to be in to execute that command (regular user and root, respectively).

---

### Post by snteran on 2008-03-07
Thank you for all the replies.  I thought it was for a comment, but it did not make sense why the instructions would include that in the code to type.  But if it is to denote that the command is to be done as root, then that helps me understand.  

Thanks again!

---

