---
title: "How to enable root?"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by rdav@usa.com on 2006-02-08
I get the following error when I enter "sudo passwd root":

">>> sudoers file: syntax error, line 23 <<<"
"sudo: parse error in /etc/sudoers near line 23"


Since I can't get read/write privileges, I not only can't change the file, I can't even read it -- so I have no idea what to do.

Can I fix this, or do I have to completely reinstall ubuntu?

tia

Robert
Mill Valley, CA

---

### Post by dickohead on 2006-02-08
sudo passwd
your password
root password
root password

that works for me.

---

### Post by donkle on 2006-02-08
[QUOTE=rdav@usa.com]I get the following error when I enter "sudo passwd root":

">>> sudoers file: syntax error, line 23 <<<"
"sudo: parse error in /etc/sudoers near line 23"


Since I can't get read/write privileges, I not only can't change the file, I can't even read it -- so I have no idea what to do.

Can I fix this, or do I have to completely reinstall ubuntu?

tia

Robert
Mill Valley, CA[/QUOTE]
Just type 'sudo su' (without the quotes) in the terminal.  You will then be asked for your password, enter it and you will be the root user *** long as you remain in the terminal.

---

### Post by rdav@usa.com on 2006-02-09
No, when I type "sudo su" the response is:

">>> sudoers file: syntax error, line 23 <<<"
"sudo: parse error in /etc/sudoers near line 23"


As I indicated, there appears to be a typo which prevents me from going into root mode, which prevents me from reading the file with the typo and from fixing it.

Is there any other way to get into root mode?

---

### Post by jbinc1 on 2006-02-09
From command line try

```
sudo -H -s
```

---

### Post by bartbes on 2006-02-09
in the recovery console you can fix the sudoers file
you can start recovery console from the grub boot menu

---

### Post by rdav@usa.com on 2006-02-09
How do I run the recovery console?

---

### Post by newuser111 on 2006-02-09
at the grub menu

also always use visudo to edit the sudoers file, there is a good reason, because it easily becomes broken by improper edits if you dont use the right syntax

---

### Post by rdav@usa.com on 2006-02-09
Where is the grub menu?

---

### Post by Pragmatist on 2006-02-09
You can switch to root by typing ```
su
``` and make sure to type ```
exit
``` when your done.  You don't want to spend more time than necessary working as root.  That is the advantage of using "sudo".  It executes the command as root and thats it, your root only for that command.

To fix your sudo command you need to be root, so use the "su" command above to become root. You have a sample file on your system here: 
/usr/share/ubuntu-docs/generic/faqguide/en_AU/sample/sudoers_allowmoresudoers

Here is my /etc/sudoers

# sudoers file.
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets

# User privilege specification
root    ALL=(ALL) ALL

# Added by Ubuntu installer
mnaus   ALL=(ALL) ALL

Note, the only entries I have take up 3 lines.(unlike the sample file which has more entries) the first line is standard, the second is also standard and is for root user and the last is my regular user.

I'm not sure how/why yours got screwed up.  I've never actually had to edit mine.  However NOTE: YOU CAN'T EDIT DIRECTLY!!!
you use a program called ```
visudo
```  This utility also checks the file for syntax errors.

So, you do the following:
```
su
``````
visudo
```

You might want to read, or at least look over, the man pages for sudo and visudo.

Let us know how it all works out.

---

### Post by rdav@usa.com on 2006-02-09
When I type su it asks me for a password...

What should I respond with?

---

### Post by rdav@usa.com on 2006-02-09
When I type su it asks me for a password.  If I type my user password or if I type "root" it replies "su: Authentication failure    Sorry."

---

### Post by newuser111 on 2006-02-09
to reboot in recovery mode, hit the esc key when prompted to see the grub menu - then choose the recovery mode option

---

### Post by rdav@usa.com on 2006-02-09
Nothing happens when I hit the esc key.   I am in console mode and don't know how to get to the grub menu...

---

### Post by Pragmatist on 2006-02-09
Did you create a root password when you installed Ubuntu?  When you type ```
su
``` and it prompts you for your password, you give it your root password.  su stands for switch user and by default it assumes you want to switch to root user.  So give it your root password.

---

### Post by rdav@usa.com on 2006-02-09
When I installed the system, I only gave it a user id and a password.  When I start the system, it asks me for the user id and password, and they both work fine.  In the console, it displays "myuserid@Master:~k$" on the console.

But when I type "su", it asks me for a password and when I type my user password, it responds "su Authentication failure   Sorry.".

I get the same response if I type "root".:cry:

---

### Post by Pragmatist on 2006-02-09
Ok, my advice assumed you actually had a root account.  I think the people who were suggesting you use recovery mode better understood your situation.

---

### Post by Pragmatist on 2006-02-09
I think they are saying that to get to recovery mode you Reboot the computer. Then, when you see the ubuntu screen, hit ESC.  This should put you in recovery mode.

---

### Post by rdav@usa.com on 2006-02-09
I don't have a clue as to how to get into recovery mode.  Does anyone here know how to do it?:cry:

---

### Post by Pragmatist on 2006-02-09
Have you tried rebooting your computer yet??

---

### Post by john_spiral on 2006-02-09
The grub menu is normally the first thing you see when you start up your computer.

---

### Post by rdav@usa.com on 2006-02-09
When I first boot, there is a menu that allows me to select various ubuntu versions (including two that are indicated to be recovery) and then the option to run windowsXP is last.

I selected the first recovery option, and somehow managed to get the system running and I am apparently in root mode (the terminal prompt is: "root@Master: /home/myusername".

I entered "visudo" at the prompt and am now in a very primitive editor with the sudoers file being edited.  I added the line "myusername ALL=(ALL) ALL" and wrote the file.

Although I am in root mode, I still cannot get permission to edit the file I want to change ( /boot/grub/menu.lst).

How can I edit this file?

---

### Post by Pragmatist on 2006-02-09
Great!  So you now have a root account?  Can you login like you used to (as a regular user) and then use sudo or su ???  Do you have the problem of editing /boot/grub/menu.lst in recovery mode or when you login regularly??

---

### Post by The Mekon on 2006-02-09
Why not go System->Administration->Users and Groups enter your normal password to bring up the Users and Groups window.  

Select the Groups tab, look for root and select it. Next click on Properties and you should be able to change the Password manually.

---

### Post by kurt on 2006-02-15
can not log in as root user even have tryed every tip given in this thread.
trying to edit /etc/network/interfaces but get only in reply 'permission denied' every f** time. maby its time to admit that a server with a graphical setup is a better choice for me. othervice, thanks to those who try to help us greenies.

---

