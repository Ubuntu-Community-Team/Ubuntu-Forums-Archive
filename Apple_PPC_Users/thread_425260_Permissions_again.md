---
title: "Permissions again"
date: 2007-04-27
forum: Apple PPC Users
---

### Post by tomos on 2007-04-27
Alright, I am not getting this.  I copied a folder(bigfolder) to my home folder from a cd made on my powerbook consisting mostly of tex and pdf files.  I used

sudo chmod a+rw bigfolder
sudo chown username bigfolder

to hopefully be allowed to copy, move, delete, edit, etc, but I always get a message saying I don't have permission to do what I want to do.  I tried the chmod and chown commands on some individual subfolders and files with the same outcome.  I noticed email attachments have no problems with permissions.  I can do whatever I want with them.


TIA

---

### Post by amaroKer on 2007-04-27
I am unsure exactly what you are trying to ask, but I think this may help.  Permissions are divided up like this:

There are 3 types of users in the system
1) Owners
2) Groups
3) Others

Each of these users can have permission to do 3 things.
1) Read
2) Write
3) Execute

When dealing with permissions you need to find out who the owners are, and what permissions they already have.  There are 2 ways to do this (that I care to use).

1) Graphical
Right click on the file, go to "Properties" and go to the "Permssions" tab.
It will display a) the owner and the permissions he/she has, b) the group and the permissions they have, and what permissions all others have.

2) Text-mode (terminal)
Type: ```
sudo ls -l */directory/name*
```
where **ls** lists files in the directory specified, and **-l** shows permissions of files.

I'll show you mine for the home folder:
```
logan@ubuntu-desktop:~$ sudo ls -l /home/logan
Password:
total 3080
drwxr--r-- 2 logan logan    4096 2007-04-27 02:27 Desktop
drwxrw---- 7 logan logan    4096 2007-04-27 02:27 Documents
drwxrw---- 6 logan logan    4096 2007-04-27 02:27 Graphics
-rwxrw---- 1 logan logan    2917 2007-04-27 02:27 Notes, Quotes, and Musings.abw
-rw-r--r-- 1 logan logan 3146240 2007-04-27 02:27 smamp.smc
```

The first d (or lack thereof) specifies that that entry is a directory.
The next 3 letters show the permissions of the owner. (r=read; w=write; x=execute)
The 3 after that show permissions of the group.
The last 3 are the permissions of all others.

After that, the number listed is the number of contained files (always 1 for entries not tagged with **d** (directory)).

Finally, the 2 names associated with the entry are 1) the owner, and 2) the group.

If you don't have read or write permissions for something in your home folder, first check it's owner (use ```
sudo chown -R *user*:*group* */directory/name*
``` to change, if needed), and then give yourself the appropriate permissions (use ```
sudo chmod -R *(permission arguments here)* /directory/name
``` if needed).  

NOTE: the -R option makes the command work recursively, that is, on all contained files and sub-folders.

I will go through this if you ask.  Don't change your permissions for /home/user from their defaults, or you will run into problems (worry slightly less about subfolders, though).

Hope this helps.  It helped me just explaining it in plain english, which is something that many posters can/will not do.

Logan W

---

### Post by amaroKer on 2007-04-27
This site is quite helpful too.

[http://catcode.com/teachmod/try_1.html]("http://catcode.com/teachmod/try_1.html")

---

### Post by marcus2004 on 2007-04-27
AmaroKer, thank you, that was a great explaination. I know it helped me.

---

### Post by tomos on 2007-04-27
Thanks, Logan.  You explain things well.  The link [http://catcode.com/teachmod/try_1.html](http://catcode.com/teachmod/try_1.html) is also very good.  Among the things I was unable to do was to open a tex file and edit it.  In other words with foul permissions I could not create any new tex documents from old ones. 

That closes this question for me.

Thanks again.

---

### Post by defenestratos on 2007-04-29
sudo chmod -R (permission arguments here) /directory/name

What are the permission arguments?
Hugo

---

### Post by amaroKer on 2007-04-29
The permission arguments are as follows

WHO:
owner = u
group = g
others = o
all = a

PERMISSIONS:
read = r
write = w
execute = x

EXAMPLES:

The permission arguments work as follows.  (BTW, you can try these non-destructively at the first link I posted)

To enable read for owner (adds permissions to those already there AKA append):
```
sudo chmod -R u+r /directory/name
```

to set permissions to exactly read for owner (changes all permissions to only read for owner AKA replace)
```
sudo chmod -R u=r /directory/name
```

to enable read and write for owner and group (appends):
```
sudo chmod -R ug+rw /directory/name
```

to disable writing and executing for others (appends):
```
sudo chmod -R o-wx /directory/name
```

I think those examples are sufficient.  Try the link to see how it works.

Logan Woolf

---

