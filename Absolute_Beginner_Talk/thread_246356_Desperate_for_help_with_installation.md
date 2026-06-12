---
title: "Desperate for help with installation"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by cinderella on 2006-08-29
[I would like to attach a pdf to this msg but it is too big so if anyone who is really interested in helping me pls could u give me your e-mail address and i will mail it too you.]

Hi I am absolutely new to Linux and Ubuntu and I desperately need help. 

This is gonna sound like a dumb qusetion but pls could u help me.

I'm currently working with a fingerprint board which requires me to develop code in linux hence I chose ubuntu. The fingerprint board(called sm01) comes with a cd that contains some compilers that need to be installed, however I simply cannot install these files from my live cd (the cd that came with my fingerprint kit) to the pc. 

I simply want to install the compiler from the cd onto my pc, but I simply cannot do it. 

The manual for the fingerprint board, SM01,states the following:

[I]2.2.1 Installation 

The cross compiler environment and the SM01 SDK can be installed by running the install_sm01 shell script from the CD ROM provided on the Linux development PC.
This installation script is designed for use with sh, ksh or bash shells, for both the
installation and development phase. If the shell is not sh, ksh or bash, this script should
not be used—configuration through the install_sm01 command must be done manually
according to your shell syntax. We do not recommend executing this script as root, but
rather under your login. The root password will be requested during installation. From
the CD ROM directory (usually /mnt/cdrom), type:
[PC_DEV]> ./install_sm01 sdk_dir

sdk_dir is the path relative to your home path under which the SDK will be installed.
Therefore, once installation is completed, you can access the SDK tree of files under
~/sdk_dir.
The installation script:
•	 Installs the cross compiler under /usr/local
•	 Copies the SDK files (these include various files, a 
         library file, example files, kernel
•	 sources and image files)
•	 Sets environment variables, such as SDK_DIR and 
         EMB_LIB_ARM
•	 Adds the cross compiler path to the PATH environment
         variable.
•	 Creates two working directories: /nfsshare and /mnt/ramdisk [/I]

SO THIS IS WHAT I DID!!!
Since the manual states that the cd rom is usually found in the /mnt/cdrom directory. So this is the procedure that I followed. Please tell me if you know what I'm doing wrong.

In the terminal I typed: cd /
and then I type : ls (to list the directories)

In this list both "media" directory and "mnt" directory show
When I list the files in these directories once i put the cd in the drive (Ubuntu apparently mounts the cd automatically), the " mnt " directory does not list any files ( I dont understand this because Ubuntu supposed to automatically mount the cd) but the "media" directory shows me 2 sub directories namely, "cdrom" and "cdrom0".

I then listed the files in the "cdrom directory (/media/cdrom)" and I found the files that were in my cd that I inserted in the drive.


This is how I went about installing the file from the cdrom:
I typed: cd /media/cdrom
Then in this directory I typed: ./install_sm01 sdk_dir (as instructed from the manual where install_sm01 is the file to be installed and sdk_dir is the destination path)


but it then gives me the following error
bash: ./install_sm01: /bin/bash:bad interpreter : permission denied
 :mad: 

I tried to mount the cd so that it appears in the mnt directory but I was unseuccesful because when I listed the files in mnt once I mounted the cd manually no files were shown

I then typed : sudo -i
and gave my password
and then went into the media directory again and tried to install my program but still said :
bash:./install_sm01: /bin/bash:bad interpreter : permission denied
 

](*,) 
Please if u have any idea let me know.

Thanks for trying to help me out. 

Sincerely,
cinderella

---

### Post by Jussi Kukkonen on 2006-08-29
Try 
```
./install_sm01 ~/sdk_dir
```


It could of course be that the installer is broken. If it is a script file (human readable, that is) and the license allows it, please paste the installer here (or if it's a long script, use [http://paste.ubuntu-nl.org/](http://paste.ubuntu-nl.org/), and post a link here).

Then again, I wonder if it could just be a permission-problem... What does *ls -l /media/cdrom/install_sm01* say?

---

### Post by steve.horsley on 2006-08-29
You're getting close. But there are problems. The script installs things in directories that are outside of your home directory. This is not allowed to normal users - you have to prefix the word **sudo** to your command. This will ask you for your password again, and then will have the extra rights that you need. So the command probably needs to be:> 
cd /media/cdrom
sudo ./install_sm01 ~/sdk_dir

---

### Post by cinderella on 2006-08-29
Thanks I will try this out tonite!! I pray to God it works!!!!

---

### Post by Jussi Kukkonen on 2006-08-29
Steve is probably at least partially right. The instructions said this:
> We do not recommend executing this script as root, but
rather under your login. The root password will be requested during installation.
What they suggest is not possible with default ubuntu installation. Running the installer under sudo might work, but there are probably complications -- e.g. the files that end up under your home dir might be owned by root...

The reason I didn't mention this first was that you received an error before you were asked for a root password -- I would have thought that the problems related to root permissions would only appear after that... 

There is yet another option to handling this: enabling root account so that the installer can be run as it was meant to be run...

---

