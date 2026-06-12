---
title: "A Few Questions"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by mkw87 on 2006-07-25
Ok, I'm fairly new to Ubuntu (and linux in general), but I am fairly intelligent and can root out problems generally if I am given some background information (and I've read so much but I still have some questions).  I am running the latest 64 bit kernel with a fairly new install, the latest nvidia graphic drivers are installed and working, and I even got dual monitors working.

I tried to install OpenFOAM so I can learn it this summer as I may possibly need to use it or Fluent this year for school, and the installation did not go so well.  

1) What should the output of "echo $PATH" be by default?  Mine contains several references to OpenFOAM directories now, and I would like to get rid of them and try the OpenFOAM installation from scratch, so is it necessary to re-export what $PATH should be?  (Or is this controlled by what I did in question 2) below?)

2) The installation of OpenFOAM requires you to edit ~/.bashrc and add a line, which worked for me, but now when I open a terminal it echo's 3 lines stating that the bashrc's of OpenFOAM in various directories are loaded, is there a way to hide this output because it happens every time I open a terminal?

3) Somehow I messed up GCC, the error stating it cannot make executables, and the config log having the line gcc <dev/null &> or something to that effect for the version.  I think this can be solved by reinstalling build-essential and/or one of its depencies that I likely screwed up when trying to install this or messing with compiz/xgl, but I'm at work and have not had time to test this as I gave up at midnight or so last night.


For Reference for anyone trying to help:
The OpenFOAM wiki I used to install is [here](http://www.cdlact.unileoben.ac.at/non_cdl/OpenFOAMWiki/index.php).
The page with install instructions to OpenFOAM is [here](http://www.opencfd.co.uk/openfoam/linuxAMD64.html).
The readme file with further installation instructions is [here](http://foam.sourceforge.net/README).

I had issues with OpenFOAM saying I had conflicting installations with my java and gcc, but resolved them by editing various installation files to point to the correct directories.  This worked and I had it installed properly *I think*, but it would not launch due to an internal error that I think is related to me setting it up improperly, so I want to start again from scratch and see if I can fix it, and since all files related to it are kept in ~/OpenFOAM, I just need to reset my $PATH *I think*.

Thanks in advance for any help.

---

### Post by mlind on 2006-07-25
> **mkw87 said:**
> 
1) What should the output of "echo $PATH" be by default?  Mine contains several references to OpenFOAM directories now, and I would like to get rid of them and try the OpenFOAM installation from scratch, so is it necessary to re-export what $PATH should be?  (Or is this controlled by what I did in question 2) below?)


Default $PATH is setup on /etc/environment (*cat /etc/environment*). If you have additional entries on your path, those are probably from ~/.bashrc or from script that's sourced on ~/.bashrc or ~/.bash_profile.


> **mkw87 said:**
> 
2) The installation of OpenFOAM requires you to edit ~/.bashrc and add a line, which worked for me, but now when I open a terminal it echo's 3 lines stating that the bashrc's of OpenFOAM in various directories are loaded, is there a way to hide this output because it happens every time I open a terminal?


What did you add to ~/.bashrc? Nothing should echo out, if you're not explicitly echoing it (or there's not errors while sourcing the file).

> **mkw87 said:**
> 
3) Somehow I messed up GCC, the error stating it cannot make executables, and the config log having the line gcc <dev/null &> or something to that effect for the version.  I think this can be solved by reinstalling build-essential and/or one of its depencies that I likely screwed up when trying to install this or messing with compiz/xgl, but I'm at work and have not had time to test this as I gave up at midnight or so last night.


try invoking *sudo aptitude reinstall build-essential*

---

### Post by mkw87 on 2006-07-25
> **mlind said:**
> Default $PATH is setup on /etc/environment (*cat /etc/environment*). If you have additional entries on your path, those are probably from ~/.bashrc or from script that's sourced on ~/.bashrc or ~/.bash_profile.
Ok, then I just have to fix the bashrc and that should clear that up.

[quote=mlind]What did you add to ~/.bashrc? Nothing should echo out, if you're not explicitly echoing it (or there's not errors while sourcing the file).[/quote]
I added
```
. ~/OpenFOAM/OpenFOAM-1.3/.bashrc &
```
Or something to that effect that points to .bashrc files within in the OpenFOAM installation folder.  What is in those bashrc files I do not remember, but I'm guessing it points to various paths so that programs can be executed by their name w/o browsing to the appropriate folder.

[quote=mlind]try invoking *sudo aptitude reinstall build-essential*[/QUOTE]
I will try that as soon as I get home and report back, thanks.

---

### Post by mlind on 2006-07-25
> **mkw87 said:**
> Ok, then I just have to fix the bashrc and that should clear that up.


I added
```
. ~/OpenFOAM/OpenFOAM-1.3/.bashrc &
```
Or something to that effect that points to .bashrc files within in the OpenFOAM installation folder.  What is in those bashrc files I do not remember, but I'm guessing it points to various paths so that programs can be executed by their name w/o browsing to the appropriate folder.


I will try that as soon as I get home and report back, thanks.

That command sources ~/OpenFOAM/OpenFOAM-1.3/.bashrc file. Which means that  all environment settings set on that file are applied to your current shell.
If something is echoing out, it probably happens on that file. Edit it and remove all **echo** words.

---

### Post by mkw87 on 2006-07-25
Ok, that fixed my issue compiling, thank you.

However, I have another problem not related to OpenFOAM, but to other things I've tried to compile from source.  I have had several packages ask for aclocal-1.6, but I only have 1.4, 1.7, 1.8, and 1.9.  Should I (is there a reason to) find and install 1.6?  Why shouldnt newer versions be compatible instead, and if they are is there a symlink or something I need to fix?

Also, I'm thinking it might be a good idea to make /home a separate partition as it seems ubuntu is going to stay on my comp, would the best way to do that simply make another partition and mount it in fstab as /home?  

Again, thanks for the help.

---

### Post by mlind on 2006-07-25
> **mkw87 said:**
> Ok, that fixed my issue compiling, thank you.

However, I have another problem not related to OpenFOAM, but to other things I've tried to compile from source.  I have had several packages ask for aclocal-1.6, but I only have 1.4, 1.7, 1.8, and 1.9.  Should I (is there a reason to) find and install 1.6?  Why shouldnt newer versions be compatible instead, and if they are is there a symlink or something I need to fix?

Again, thanks for the help.

automake1.4 is deprecated and been unmaintained code for some time. When you install automake package, automake1.4 is automatically installed :(

Install automake1.9 or 1.7 and if you still have problems compiling, create symlink, aclocal-1.6 that points to aclocal-1.9.

```

sudo aptitude purge automake 
sudo aptitude install automake1.9

```


> **mkw87 said:**
> 
Also, I'm thinking it might be a good idea to make /home a separate partition as it seems ubuntu is going to stay on my comp, would the best way to do that simply make another partition and mount it in fstab as /home?  


Use parted or gparted to create a new (ext3) partition, mount your new partition to temporary mount point, move your stuff from old /home to new partition so that file permissions are preserved, mount new partition as /home and add it to /etc/fstab.

---

