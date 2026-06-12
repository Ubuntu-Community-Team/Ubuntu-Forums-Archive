---
title: "Strange Ubuntu problems"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by wat3r on 2006-04-11
I have some very strange (At least I think so) problems with my newly installed Ubuntu. I am a beginner at Linux so I know very little, but I think maybe these problems might not be my fault.

Here's the thing:
I installed Ubuntu 5.10. Installation went fine, but when I was logged in with my user and tried to configure my network card, I was asked to give my root password. I did, and nothing happened. I am 100% positive that I typed in the correct password.
I tried to run the program again ( System -> Admin. -> Network ), but now the mousepointer changes to "working" (Circle spinning thingy) for about ten seconds, and then it goes back to regular mousepointer again, without opening the program.
In a previous post, I was told how to set up my DSL-connection "dialup-style", and was told to type "pppconfig" in terminal to do so. When I do this, it says i have to be root user to run this program. Here is the part I think is strange. I open terminal and type "logout". I am told to type exit. I do this, and terminal closes. Ah well, I log out to the graphic login, and type "root" as user and root password as password. I am told that I cannot log in as root from this point. Well, that's ok by me. I try to log in at terminal at the graphic login screen, but I get the same message. I log in as my "normal" user in terminal, and try to get in to root user from this point, but when I type "logout", I am told to write "exit", and when I do as told, I get sendt back to the graphic login screen. So that got me nowhere, because as I was told earlier, I can't log in as root from here.
I also try to run the "Run as different user" program, but when I do this, nothing happends when I try to start pppconfig.
What is wrong? Is it me or Ubuntu?

Hope you understand what I have written.

---

### Post by jazzmuzik on 2006-04-11
Ubuntu doesn't use a root password. When it asks for one type your user password instead.

---

### Post by wat3r on 2006-04-11
Same thing happens. The program won't start. (System -> Admin. -> Network).

---

### Post by trent dillman on 2006-04-11
boot into recovery mode, then at the root command prompt:

```
visudo
```

go to the bottom and see if there are one of the two following lines:

```
%admin  ALL=(ALL) ALL
%adm  ALL=(ALL) ALL
```

If not, hit the letter I on your keyboard to enter edit mode, and add them
Then hit ESC, then type 

```
:wq
``` and hit enter.

Then, do

```
init 2
```

---

### Post by wat3r on 2006-04-11
Tried to do this, but when I type in "visudo", I get this error message:
visudo: /etc/sudoers: Permission denied

---

### Post by nalmeth on 2006-04-11
sudo is a program that gives "root" permission to regular users with their user password.
If you have permission problems, type sudo before whatever command needs admin priviledges.

---

### Post by wat3r on 2006-04-11
Here is what happens:

eirik@eirik:~$ sudo pppconfig
Password:
eirik@eirik:~$ sudo pppconfig
eirik@eirik:~$

As you can see, the program does not start, and I am not able to start it again. This happens with many different programs when I try to open them with admin access.

---

### Post by Mustard on 2006-04-11
[QUOTE=wat3r]Tried to do this, but when I type in "visudo", I get this error message:
visudo: /etc/sudoers: Permission denied[/QUOTE]

I don't understand how you can get this problem if you followed the instructions given by the previous poster.  The first part of the instructions was to **boot into recovery mode** from the Grub menu.  Recovery mode drops you to a root prompt, and from a root prompt you have access to all files on the system.  I can only assume, at this time, that you have missed that part of the instructions that were given to you.

---

### Post by wat3r on 2006-04-11
Ok, I missed that part. Sorry about that.
I have now booted in recovery mode, and typed "visudo", and at the bottom it says;

root      ALL=(ALL) ALL

Is this how it should be, considering my problem.

---

### Post by Mustard on 2006-04-11
Read over this guide I'm developing on the issue, and see if it makes sense to you. :)


Use the **'Recovery Mode'** from the Grub menu at startup.

Recovery mode will drop you to a root prompt.  If you don't see the GRUB menu at startup then you probably have to press the ESC key to view it, as its sometimes hidden and only revealed when you hit the ESC key.

Once at the root prompt you can use this command to edit the /etc/sudoers file..

```
visudo  #this command does on thing.  It opens the sudoers file for editing
```

My sudoers file looks like this.  Note the last line where I give my user sudo privileges.  This is the line that would need to be added by those who, for whatever reason, don't have sudo privileges.

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
mustard ALL=(ALL) ALL

```

**Method 1. Adding your username directly to sudoers**

You can see my username on the bottom line.  You would need to add your username to the bottom as I have done.

Assuming your user name was "bob'', then the line that would need to be added would be..
```
bob ALL=(ALL) ALL
```

This is just one way of doing it.

**Method 2. Adding a user to the administration group**
Note:If you are going to use this method, please ascertain whether an administration group is already set up.  See instructions below for viewing all the groups on your system.

Some sudoers files are set up with an admin group called 'adm' or sometimes it is called 'admin' (it can be called whatever you like really, but these two are fairly intuitive).  Users are then added to the adm group, and a line in the sudoers file that looks like this below gives members of the 'adm'  group admin access.

```
%adm ALL=(ALL) ALL
```

If your group is called 'admin' then it would look like this

```
%admin ALL=(ALL) ALL
```

You can find out what groups are setup on your system with this command..

```
cat /etc/group
```

If you decided to do it this way you would create the line above at the bottom of your sudoers file, using one of the examples above, save the sudoers file,  then at the root prompt do this command (substituting your username in the appropriate place and whatever your administration group is normally called)..

```
adduser your_username adm
```

or for the case of 'admin' being your administration group..

```
adduser your_username admin
```

---

### Post by bigfatnewbie on 2006-04-11
The totem movie player won't play any of my dvd's.  Everytime I put in a dvd the totem movie player will give me an error message saying:
Totem could not play 'dvd://:
Error invoking "dvdnav_get_next_block":  Error reading NAV packet..
Can somebody help me please!!!!!!!!!!!!!!!!!!:-|

---

### Post by trent dillman on 2006-04-12
You may need libdvdcss. Search the forums for Automatix.

---

### Post by Mustard on 2006-04-12
Instruction for enabling DVD playback are available at this link as well...

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by wat3r on 2006-04-12
Great guide, mustard :) I will try this.

*trying*

The editing of the file went well, now I will try to start the programs that I have had problems starting earlier :)

Ok, the program started fine, but now I have another problem.

I have a DSL-connection, with only a modem, and no router, and have to connect to the internet "dial-up" style.
Any guides on how to get this up and running?
The program I am using is the one located in System -> Admin. -> Network.

edit: Okay, I found an older post on how to do this, and now I am writing this from my computer with Ubuntu installed :) Now I have only one other question. How do I disconnect the connection?

---

### Post by Mustard on 2006-04-12
[QUOTE=wat3r]Great guide, mustard :) I will try this.

*trying*

The editing of the file went well, now I will try to start the programs that I have had problems starting earlier :)

Ok, the program started fine, but now I have another problem.

I have a DSL-connection, with only a modem, and no router, and have to connect to the internet "dial-up" style.
Any guides on how to get this up and running?
The program I am using is the one located in System -> Admin. -> Network.

edit: Okay, I found an older post on how to do this, and now I am writing this from my computer with Ubuntu installed :) Now I have only one other question. How do I disconnect the connection?[/QUOTE]

I would imagine if you connected with the 'pon' command you would disconnect with the 'poff' command.

---

### Post by wat3r on 2006-04-12
Thanks again! You've all been at great help :)

---

### Post by xerxesv5 on 2006-04-12
"Sorry to bump this but...

Instead of rebooting into recovery mode, why couldn't you just pull up a terminal and type:

```
su root
```

... to get you a root console?

:-k I had this problem and that worked for me. The fix works right away. Oh and thanks for the help! I was stuck on this one.

---

### Post by Mustard on 2006-04-12
[QUOTE=xerxesv5]"Sorry to bump this but...

Instead of rebooting into recovery mode, why couldn't you just pull up a terminal and type:

```
su root
```

... to get you a root console?

:-k I had this problem and that worked for me. The fix works right away. Oh and thanks for the help! I was stuck on this one.[/QUOTE]

I'm not exactly sure, but I think for most people the root password in Ubuntu would be disabled and this might preclude them from using this method.  Do you have a root password set up on your system?

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by dvdljns on 2006-04-13
mustard how do I change it to where I can login with root. I either need to be able to login as root or change all my folders to where I own them. This does not even make sense. I cannot write to /usr/src. and it does not give me the option of entering my password. I need to login as root.

---

### Post by xerxesv5 on 2006-04-13
Mustard:
> Do you have a root password set up on your system?

Aha... right. I do, thats why it works for me.

dvdljns:
Can you clarify the problem a bit... you just want to be able to change permissions on some of the directories?

Why not just get root Mustard's way (earlier in this thread)?
> 
Use the 'Recovery Mode' from the Grub menu at startup.

Recovery mode will drop you to a root prompt. 

If you have a root password set however, you can login normally as root, or use "su root" as above. 

You can't login as root from the graphical login screen though, type Ctrl+Alt+F1 or F2 or F3, etc to switch to a text-mode terminal, then if you need to get back to the GUI login, I think its Ctrl+Alt+F6 or F7. 

If not, you should be able to type "passwd" in 'recovery mode' to set one up if you need to login as root any time in future.

Hit me if I haven't read your post right. :)

---

### Post by Mustard on 2006-04-13
[QUOTE=dvdljns]mustard how do I change it to where I can login with root. I either need to be able to login as root or change all my folders to where I own them. This does not even make sense. I cannot write to /usr/src. and it does not give me the option of entering my password. I need to login as root.[/QUOTE]

It's all explained at this link.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

For myself if I want to get a root prompt, I would open a terminal and do this..

```
sudo -i
```

I would put in my user password and voila, I have a root prompt.

If you don't have a user account that is set up with superuser privileges, then that is a different problem altogether, dvdljns. When you installed did you use the expert install option?

Try this command in terminal and show me what output it gives you.

```
sudo whoami
```

---

### Post by crackers on 2006-08-12
ok where can find guide on how to use the recovery mode? had a power outage yesterday not when ubuntu boots itstarts off as normally would and then goes to a text screen.
 file system not clean. 
        starting system log .8211]: 1
 
 is there a place with a set of intructions on how to use recovery mode?

---

