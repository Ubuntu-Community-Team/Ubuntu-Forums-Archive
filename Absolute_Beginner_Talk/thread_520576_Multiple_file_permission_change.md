---
title: "Multiple file permission change"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by macosxistheultimate on 2007-08-08
I'm kinda new to the Ubuntu world but i've been messing around with linux since Dec 04. I run Ubuntu at work because its the best Linux distro i've seen that run on the x86 platform also i'm running it because i hate windows. windows sucks  WINE is the way to go. I recently made a new account and transferred a folder containing files from the previous account to the new account to work with. the problem is that all the files belong to the other user. The only way to change the owner is by logging in as root and changing each file one by one. I have about 2500 files to change the permissions on. 
the sudo chown -R username:username /directoryname command is not working please help.

---

### Post by hyper_ch on 2007-08-08
```

sudo chown -R user.user /path/to/dir/*****

```

---

### Post by bodhi.zazen on 2007-08-08
You can change permissions/owner as the owner of the file or root.

sudo chown -R new_user.new_group /dir
sudo chmod -R 770 /dir

---

### Post by macosxistheultimate on 2007-08-08
Ubuntu is unable to find the directory can you give me more details about the chown command which user comes first and does this have to be done in root

---

### Post by bodhi.zazen on 2007-08-08
could you be more specific ?

The file/directory should be in :

/home/<new_user>/<copied_directory_name>

---

### Post by asmoore82 on 2007-08-08
copy and paste the command that you are trying to run.

---

### Post by macosxistheultimate on 2007-08-08
when use the sudo chown -R adamroth.cellanalysis /home/cellanalysis/ Image Analysis it says the directiry does not exist and it cant find it. It says the directory Image Analysis does not exist. I cant even access it through the command line using the cd (change directory) command

---

### Post by bodhi.zazen on 2007-08-08
Looks like you have a space in the file name

Linux does not like this too much.

Use quotes :

```
sudo chown -R adamroth.cellanalysis "/home/cellanalysis/Image Analysis"
```

Or tab completion:

sudo chown -R adamroth.cellanalysis /home/cellanalysis/ Ima<tab>

when you hit the tab key it will auto complete :twisted:

tab completion works for commands, files, and directories

---

