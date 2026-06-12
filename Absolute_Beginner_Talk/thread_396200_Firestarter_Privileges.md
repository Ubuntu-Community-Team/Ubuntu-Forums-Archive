---
title: "Firestarter Privileges???"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by iClouseau88 on 2007-03-29
Hi,

I am the only one using the computer. Whenever I start the computer, I type in the password for admin/root user to login.  I also set firestarter as one of the startup programs. Now, firestarter says "insufficient privileges" on startup.

I did look at the Firestarter FAQ but have not been able to follow the following:

[QUOTE]
In order for a regular user to be able to launch Firestarter, the user must be given additional privileges. Edit your /etc/sudoers file in your favorite text editor and add the following line at the end:
username ALL= NOPASSWD: /usr/bin/firestarter [unquote]

I opened the terminal and typed "sudo visudo", it gives: 

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#

 If I just type "visudo" (per world_virus' December 11/04 thread entitled " HOWTO: Firestarter Firewall"), it says "visudo: /etc/sudoers: Permission denied" .

I believe I am already root user, but how can I get into /etc/sudoers in order to edit this file???

Thanks in advance for your help.

:confused:

---

### Post by Ecthelion on 2007-03-29
I guess you better make a backup first
```
sudo cp /etc/sudoers /etc/sudoers_back
```

Then I had to type
```
sudo visudo -f /etc/sudoers
```
to get into the file...

Then you can just edit it by moving with the arrows to where you want.
I guess you have to add a line under
> # User privilege specification
root    ALL=(ALL) ALL
Add something like
*username* ALL=(ALL) ALL
(or better if you know which privilige you need, replace <ALL=(ALL) ALL> whith th right privilege.

To save the file just do Ctrl-o

I never did this, but if I would need to do it, I would do it this way...

Btw I was under the impression that the firewall is always up, and that firestarter is just a Graphical User Interface to check its status etc...
So you don't have to start the graphical if you just want to have your firewall to work..

---

### Post by STREETURCHINE on 2007-03-29
system>prefferances>sessions>startup programs
and add

       ```
gksudo firestarter
```

should give you the right permissions.

or to edit /etc/sudoers

        ```
gksudo gedit /etc/sudoers
```

---

### Post by iClouseau88 on 2007-03-29
Ecthelion,

Code:

sudo visudo -f /etc/sudoers 

gives:

"#this file MUST be edited with the "visudo"command as root"

STREETURCHIN,

Code:

gksudo firestarter 

gives the Firestarter user interface.

Code:

gksudo gedit /etc/sudoers 

gives:

"#this file MUST be edited with the "visudo"command as root"

I am still confused!

---

### Post by STREETURCHINE on 2007-03-29
ok i just installed firestarter to see what was going on,

in terminal i typed 

       ```
sudo aptitude install firestarter
```

after it had finished installing in the terminal i typed 

         ```
sudo firestarter
```

it started firestarter

in startup programs i typed 
                 
         ```
gksudo firestarter
```

then i rebooted  and when it started so did firestarter
also i could have edited with 

          ```
gksudo gedit /etc/sudoers
```

but there is no need for that .

so i am confused,what distro are you using,vi should not be needed to edit

---

### Post by iClouseau88 on 2007-03-29
Hi,

I am actually using Feisty these days.  Dapper was wiped off my HD 'cause I had no choice but to re-install Win XP, which I could not boot into because of my naively responding to a false positive by AVG  Antivirus.

---

### Post by compmodder26 on 2007-03-29
You don't need to start firestarter every time you log in.  Firestarter is simply a front end to help you configure ubuntu's underlying firewall, iptables.  Iptables starts automatically for you.  So, the only reason you need to run Firestarter, is to change your firewall policies.

From your first post, you said you logged in as the admin/root user.  Technically this is true, but that user doesn't have admin privileges all the time.  Programs that require admin privileges must be run with "sudo" (from the command line), or "gksudo" from the desktop.  Doing this will result in a prompt for your password.

You tried to start Firestarter without "gksudo" and it failed.  Change your startup line to "gksudo firestarter" and it should work.  But as I said, it is not necessary.

edit: You did the right thing with "sudo visudo".  The text at the top of the file was just a warning to anybody who didn't use visudo to edit the sudoers file.  Add the line it told you to add, and the next time you try to start Firestarter (remember to use "gksudo firestarter"), it should open without asking for you password.

---

### Post by iClouseau88 on 2007-03-29
Hi folks,

I discovered that I did not read the whole file /etc/sudoers, and I should have typed Control V (bottom-of-page instructions) to go to the next page where it says "%admin ALL=(ALL) ALL.  I had thought the page was all I could get.

In the startup command for Firestarter, I typed "gksudo firestarter",albeit unnecessary, and this solved the problem.  On restarting, the computer no longer gives the annoying message about Firestarter privileges.

Thank you all.  I need to learn more and in-depth about Linux!

:popcorn:

---

