---
title: "Something Bad happend. how to fix it?"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by Solidad on 2006-05-24
i can't access some of my admins previlages. like the Disk and Symphatic. they just load and nothing happend. even thou i entered my password for accessing.

and evreytime i use the "sudo" command it doesn't respond. anymore. 

it mst have been the packages i tried to install. mostly are modem packages. 

is theres a way to revert the changes i made. something like restore the files changed or reintall the packages. something like that?

---

### Post by Steggy on 2006-05-24
[QUOTE=Solidad]i can't access some of my admins previlages. like the Disk and Symphatic. they just load and nothing happend. even thou i entered my password for accessing.

and evreytime i use the "sudo" command it doesn't respond. anymore. 
[/QUOTE]
This kind of sounds like the user you're logged in as doesn't have sudo priveledges. Is that possible? Is this a new user or did you just install Ubuntu and used the "expert" installer (in which case you would have a root account but your user account wouldn't be able to use sudo)?

If neither of those are the case, however, I don't have any idea what your problem is.

---

### Post by nalmeth on 2006-05-24
Can you open a terminal and post what happen's when you type:

sudo -i

?

---

### Post by Solidad on 2006-05-24
there is only one user for now. that the user i typed, during the setup.

i'll try pls wait.

---

### Post by Solidad on 2006-05-24
i get this. actualy nothing happends.

[IMG]http://i21.photobucket.com/albums/b289/Solidad2x/u23.jpg[/IMG]

argh. wrong image anyway 

when i type

sudo hsfconfig

i dont get a response. that the same thing on typing 

sudo -i

no response.

---

### Post by nalmeth on 2006-05-24
sudo -i 
will make you root for 15 minutes, or some similar time frame.

I don't know what to make of what you posted, I don't think you can make uninstall but I may be wrong. Likely the case :)

Unrelated to your current problem, you should use checkinstall, that way you can uninstall the application safely.

Try it now, we'll test sudo again, post what you get from:

sudo apt-get update
sudo apt-get install checkinstall

---

### Post by nanotube on 2006-05-25
it seems that your user has no sudo privileges. reboot into "recovery mode" (one of the items on the list in the grub menu). that should spit you out into a root shell. once there, look and see what the contents of your /etc/sudoers file are, and what the contents of your /etc/group file are.
specifically, for sudoers, you should see a line that looks like 
```
%admin ALL=(ALL) ALL
```
and in /etc/group, you should make sure that your username is listed under group "admin", so you should see a line that looks like:
```
admin:x:106:yourusernamehere
```
do that, and report here whether these things are present.

 (if not, you should either add that %admin line to /etc/sudoers, by editing that file with command "visudo", or by adding your name to the admin line in /etc/group, by editing that file with command "nano /etc/group")

---

### Post by Solidad on 2006-05-25
well when i enter

/etc/group or /etc/sudoers it get this msg

bash:/etc/group: permission denied 
bash:/etc/sudoers/: permission denied

right now. when i enter ubuntu. it hangs. w/c defineitly something is worng now.

can i reinstall?

---

### Post by nanotube on 2006-05-25
dont just enter those files. enter the commands as i gave you. those files are just text files, not executable, so you have to edit them. "visudo" command edits the sudoers file, and "nano /etc/group" edits the /etc/group file. (assuming you are running as root, which you should be if you reboot into recovery mode, like i said you should in my previous post :) ).

---

### Post by Solidad on 2006-05-25
well i added my username in admin:x but when i did that. well ubuntu hanged. so  i feel like its better to format the linux partitions and start anew. ubuntu OS.

---

### Post by nanotube on 2006-05-25
[QUOTE=Solidad]well i added my username in admin:x but when i did that. well ubuntu hanged. so  i feel like its better to format the linux partitions and start anew. ubuntu OS.[/QUOTE]
hmm, interesting... maybe you made some kind of typo in /etc/group...? post your /etc/group file here.
or, of course, you can just reinstall :)

---

### Post by Solidad on 2006-05-26
yeah i already did that.

is it safe to put my username on the root group?

---

