---
title: "how to share folders"
date: 2005-07-19
forum: Absolute Beginner Talk
---

### Post by signtist on 2005-07-19
Hi,

I have two ubuntu accounts on my computer and I'd like to set up a folder which is shared by both accounts.

I created an account /home/shared and gave access to both accounts, unfortunatly whenever I write an file into the ordner the new file is read only for the other account. How can I create a folder in which every file new or old is automaticly read and write for both accounts?

Many thx in adv

---

### Post by frodon on 2005-07-19
Create a group in which your 2 users are member (system>Administratio>User and Group) and specify your users to use this group, and give your folder the group permission, I think a chmod 775 do the job, then make some tests. It's just an instant idea, I'm not in front of my computer  :smile:

---

### Post by signtist on 2005-07-19
that's what I have done. But this only allows everyone in the group to save files into the folder, but the these new file are then only read only for the other group members (unless of course you give access  manually ).
What I need is a real shared folder where every new file created is automatically read and write for everyone who has access to this folder.
Know what I mean?

thx

---

### Post by frodon on 2005-07-19
look at the permissions of the created files, maybe the defaut mask for a created file is wrong for your use, if you want to change the default mask add these lines in the .bashrc file in the /home directory of the user : ```
# other setting
umask 002       # set rwxrwxr-x (775) for all created files
```also verify the group permissions (but I think you already do it  :wink: )

---

### Post by signtist on 2005-07-20
oh,
that sounds better! but will this be for every file newly created on the computer or only for this folder?  (I only want it for the folder)

thx

---

### Post by frodon on 2005-07-20
[QUOTE=signtist]but will this be for every file newly created on the computer or only for this folder?[/QUOTE] It's for every newly created file but i think it always respect the permissions of the directory , so i think your shared folder will be the only one writable by both users (because it's the only one with group permissions). 
Make some tests to confirm that.

Does it work ?

---

### Post by signtist on 2005-07-21
[QUOTE=frodon]look at the permissions of the created files, maybe the defaut mask for a created file is wrong for your use, if you want to change the default mask add these lines in the .bashrc file in the /home directory of the user : ```
# other setting
umask 002       # set rwxrwxr-x (775) for all created files
```also verify the group permissions (but I think you already do it  :wink: )[/QUOTE]
 Hi,

I cannot find .bashrc file. 

thx

---

### Post by frodon on 2005-07-21
.bashrc file is in your /home/user_name directory, all the files which start with "." are hidden files, if you want to see them use ls -a command or type Ctrl + H in nautilus (file browser). The easiest way to find a file even if you have just a part of the name is to type : ```
sudo updatedb
locate the_file_name
```updatedb allow you to create a database containing all the paths and locate command allow you to search a name in this database (you need often to run updatedb command in order to have an up to date database, if you're interested ask me and i will explain you how to do that automaticaly using [crontab](http://www.adminschoice.com/docs/crontab.htm) )

---

### Post by signtist on 2005-07-21
ok, I found the file. thx. I don't however understand what to do next.
I added  what you said at the end of the file but nothing has changed so far. the permissions for new files are still the same. 

I found the following in the .bash_profile file:
[I]
# ~/.bash_profile: executed by bash(1) for login shells.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

[B]# the default umask is set in /etc/login.defs
#umask 022[/B]

# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi[/I]


Could it be, that I have to change here?


thx

---

### Post by frodon on 2005-07-21
[QUOTE=signtist]Could it be, that I have to change here?[/QUOTE]I don't think so because these lines :   
# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
. ~/.bashrc
fi
specify to take care of your .bashrc file which will normally overwrite the default umask if you specify one in your .bashrc .
I need more information to understand what's happen.
Please, could you give me the result of "ls -lg" command in your shared directory  with a created file (using the umask i gave you in .bashrc file) ?
For information : each time you modify .bashrc file you need to run a "source .bashrc" command in order to take care of the latest modifications, or just close your terminal and open a new one

---

### Post by signtist on 2005-07-21
[QUOTE=frodon]
For information : each time you modify .bashrc file you need to run a "source .bashrc" command in order to take care of the latest modifications, or just close your terminal and open a new one[/QUOTE]

oK, i didn't do that. 
now I did. pls see:

torsten@ubuntu:~/Shared$ ls -lg
insgesamt 32
drwxrwxr-x  17 benutzer 4096 2005-07-23 16:42 Fotos
-rw-rw-r--   1 torsten     5 2005-07-21 14:12 test
-rw-r--r--   1 torsten  5187 2005-07-21 14:14 test2.sxw
-rw-r--r--   1 torsten  5193 2005-07-21 09:52 TEST.sxw
-rw-r--r--   1 torsten  6680 2005-07-21 14:17 testtest

I have created all the test files after I have added unmask .. 
It work for the file test, which is created with gedit, but not with open office files or gimp. further, the editing of the bashrc changes the permission mask for my whole personall directory and not only for the shared one.

thx

---

