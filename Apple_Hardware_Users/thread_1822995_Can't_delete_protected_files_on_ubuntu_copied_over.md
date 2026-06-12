---
title: "Can't delete protected files on ubuntu copied over from OS"
date: 2011-08-11
forum: Apple Hardware Users
---

### Post by libdev on 2011-08-11
Hi all, I'm new to Ubuntu (as you will shortly see) and have been trying to move my music files from OS to Ubuntu. I was able to copy my OS music folder to my Ubuntu partition, but folder/files were all protected/access denied. In addition, the partition got filled up while making the transfer. 

I had to restart the macbook for an unrelated reason, and when I tried to log in to Ubuntu, I was unable and given a GNOME power manager configuration error (sorry I dont have the exact msg in front of me ATM). I browsed forums and found that this error was likely being caused by not enough disk space being available. So I opened Ubuntu in recovery mode and tried to a) delete the directory using rm -rf and b) move the folder from ubuntu back to OS. I got permission denied errors for both.

Anyone have any suggestions to clear up space/add space to the partition just so at the very least I can get back on Ubuntu? Or freeing up permissions of the folders? Any help would be appreciated. Thanks!

---

### Post by ~!geek!~ on 2011-08-11
If you are able to login ubuntu (in normal or recovery mode), use:
> sudo chown <your username> <directory name with appropriate path> -R 
to make yourself owner of the director-y(-ies) within the above mentioned directory. 
If you don't care about the permissions already set and want the files and directories within the mentioned directory to be accessible to anyone using the system 
you may use:
> sudo chmod 777 <directory name with appropriate path> -R 
It will make all the files n directories inside the directory accessible to everyone using the system (having access to directory in which original directory was present)
Although I suggest you use the chown command because changing the owner of the directory doesn't change the permissions set for the files n directories. The original permissions are retained as it is. 

If you are tired and fed up not being able to login, just use a live ubuntu cd or usb and delete the files you want to, to free up some space. Now, login and try one of the above instructions.

---

### Post by jerrrys on 2011-08-11
sudo apt-get clean

sudo apt-get autoclean

sudo apt-get autoremove

see if that gives you some room

---

### Post by phuongdt3 on 2011-08-13
> **libdev said:**
> Hi all, I'm new to Ubuntu (as you will shortly see) and have been trying to move my music files from OS to Ubuntu. I was able to copy my OS music folder to my Ubuntu partition, but folder/files were all protected/access denied. In addition, the partition got filled up while making the transfer. 

I had to restart the macbook for an unrelated reason, and when I tried to log in to Ubuntu, I was unable and given a GNOME power manager configuration error (sorry I dont have the exact msg in front of me ATM). I browsed forums and found that this error was likely being caused by not enough disk space being available. So I opened Ubuntu in recovery mode and tried to a) delete the directory using rm -rf and b) move the folder from ubuntu back to OS. I got permission denied errors for both.

Anyone have any suggestions to clear up space/add space to the partition just so at the very least I can get back on Ubuntu? Or freeing up permissions of the folders? Any help would be appreciated. Thanks!

yes,i'm having semilar problem,thanks for thread

---

