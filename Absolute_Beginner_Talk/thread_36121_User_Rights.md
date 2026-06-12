---
title: "User Rights"
date: 2005-05-21
forum: Absolute Beginner Talk
---

### Post by Walker_P on 2005-05-21
I'm new to ubuntu and have came across a problem. ](*,) I can't edit any folder outside of the home folder. I think it has something to do with my user rights. How do I make my self an administrator user, so I can access folders made by other users. ( I'm the only normal user but - you know what I mean). When Installing ubuntu it said to use the sudo command - But How? :?

---

### Post by kassetra on 2005-05-21
[QUOTE=Walker_P]I'm new to ubuntu and have came across a problem.  ](*,) I can't edit any folder outside of the home folder. I think it has something to do with my user rights. How do I make my self an administrator user, so I can access folders made by other users. ( I'm the only normal user but - you know what I mean). When Installing ubuntu it said to use the sudo command - But How?? :???:[/QUOTE]

Ok, there are at least two different answers to your question.  :)  (Other people will most likely tell you more ways to do it)

1. If you just want to edit, say, a text file that you as a regular user do not have permissions to edit - you would open a terminal and type something like this:
```
sudo gedit text.txt
``` and then press return, you will then be asked for your password - that is, the same exact password you use to log into your account... then after you enter your password, gedit (which is a gui text editor) will open the file for editing.

2. If you want to change the permissions for say, the xmaps directory so that you can change default icons, then you need to type in two commands, also using sudo - first though, know the exact path of the directory you want to change, in this case, we'll use /usr/share/pixmaps - and by no means is this the only way, the best way, or even the fastest way - but it works well.  :)
 ```
sudo chown -R root.users /usr/share/pixmaps
sudo chmod -R 775 /usr/share/pixmaps
``` 

The first command changes the ownership (chown) of everything in /usr/share/pixmaps, recursively (that is, through all of the directories nested inside of that directory as well), to root - but also changes the group to users.

The second command changes the permissions of all of the files and directories within /usr/share/pixmaps to user can read/write/execute (7), group can read/write/execute (7) and other users can read/execute (5)...

Since you as a user are not root, but you do belong to the group "users" - you can now edit any of the files in /usr/share/pixmaps

---

### Post by dekoi on 2005-05-22
sudo!

Add "sudo" to anything you wish to do in a terminal. You'll be asked for your user password, then you shouldn't have a prob.

EX: sudo apt-get install WHATEVER

(sudo=super user do) That's what gives you temp. admin. rights.

To anything you don't have the "rights" to do, add "sudo" then your login password (when prompted), and you will be able to do it.

Also, new folders you create in your home folder may be "hidden," in which case "View" and drop to "hidden files" will reveal them.

---

### Post by poofyhairguy on 2005-05-22
Or use a super nautilus:

gksudo nautilus

---

### Post by Walker_P on 2005-05-24
Thanks Eveyone!

---

### Post by Gustav on 2005-05-24
[QUOTE=Walker_P]I'm new to ubuntu and have came across a problem. ](*,) I can't edit any folder outside of the home folder. I think it has something to do with my user rights. How do I make my self an administrator user, so I can access folders made by other users. ( I'm the only normal user but - you know what I mean). When Installing ubuntu it said to use the sudo command - But How? :?[/QUOTE]
 You can add a script in nautilus, do like this:

navigate to ~/.gnome2/nautilus-scripts/

make a file called "Open as root" or something like that

edit the file and write

```
#!/bin/bash 
# 

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; 
       do gnome-sudo "gnome-open $uri" & 
done
```
save the file

Now you can right-click on files in nautilus and click on scripts->Open as root to open the file with root privileges.

---

### Post by Owdy on 2005-09-24
[QUOTE=Gustav]You can add a script in nautilus, do like this:

navigate to ~/.gnome2/nautilus-scripts/

make a file called "Open as root" or something like that

edit the file and write

```
#!/bin/bash 
# 

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; 
       do gnome-sudo "gnome-open $uri" & 
done
```
save the file

Now you can right-click on files in nautilus and click on scripts->Open as root to open the file with root privileges.[/QUOTE]


That wont work in breezy. Any ideas why? There arent 'scripts' part in right click.

---

### Post by adamkane on 2006-11-18
To enable script first place script in nautilus-scripts folder, then make script executable:

```

cp scriptname ~/.gnome2/nautilus-scripts
cd ~/.gnome2/nautilus-scripts
chmod +x *

```

---

