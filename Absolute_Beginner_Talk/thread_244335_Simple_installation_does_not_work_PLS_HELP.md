---
title: "Simple installation does not work_PLS HELP"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by cinderella on 2006-08-26
hello! I have a simple problem with installing a compiler that I require from my live cd. 

Thanks to ubuntu the cd mounts automatically however when I go to the mnt directory and list the files/sub directories then nothing shows. I find it strange that this happens since Ubuntu automatically mounts the cd so I expected to see the cdrom sub-directory with the cd contents but when I type: 
cd /mnt/cdrom the error says no such file or directory because the mnt directory does not have any subdirectories or files

I then typed: cd /media/cdrom 
once I was in the /media/cdrom directory I then tried to install my compiler by typing:
./install_sm01 sdk_dir

where install_sm01 is the name of the file and sdk_dir is the destiniation path.

The following error was shown:
bash: ./install_sm01: /bin/bash: bad interpreter: Permission denied 
PLEASE HELP ME!!!!

---

### Post by lynxus on 2006-08-26
try sudo ./install_sm01

---

### Post by cinderella on 2006-08-26
Thanks! but it didnt work. I tried it in /media/cdrom directory and also in the main directory and both dont work. it still says permission denied. 

Thanks though;)

---

### Post by steve.horsley on 2006-08-26
It's possible, I suppose, that it's trying to create some temporary files in the current directory. This will of course fail if the current directory is on a CD. Try changing to your home directory and doing:
> sudo /media/cdrom/install_sm01 sdk_dir

---

### Post by cinderella on 2006-08-28
I typed sudo /media/cdrom/install_sm01 sdk_dir and this is the error it showed:
sudo: unable to execute /media/cdrom/install_sm01 : Permission denied

---

### Post by deltoya on 2006-08-28
It seems you have the cd mounted with the noexec option, which prevents it from running. You could either copy the data into the hard disk, and execute from there, or trying to remount it without that option.

try:
mount | grep cdrom

if you see 'noexec' in the line, then that's your problem. I'm not sure, but maybe 'sudo mount -o remount,exec /mnt/cdrom' would do the trick.

---

