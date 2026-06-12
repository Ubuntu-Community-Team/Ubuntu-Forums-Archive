---
title: "Gusty Upgrade Root User Issue"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Squid_blk on 2007-10-25
I am a newbie to Linux since May. I had my system running fine under Feisty. I upgraded using Synaptic to Gusty this past Saturday. Looked good but a Java program and a Python program  stopped working. I got the Java one back running but the Python one, Sipie, is still not working yet.  I needed to remove some files but apparently at the moment I do not have permission to do so. What?  How can this be? Under Feisty I was the root and only user of my system. Now the system tells me I do not have permission and has assigned some unknown password and will not let me delete and remove files that I need to remove.  How do I fix this? Or do I need to do the not preferred option and do a clean install? I finally had my system working the way it needed to be except for my extra mouse buttons to work and thought the upgrade would just be a background thing and run some newer software versions. But this is not the case. Need help please. Thanks.

---

### Post by kellemes on 2007-10-25
If you need to move files from terminal the preferred way to get temporary root-privileges is using **sudo**.
```
sudo mv file1 file2
```

If you need to be root from an x-based application, like nautilus (filemanager) you can start it from the terminal like so..
```
gksudo nautilus
```
**or**
```
gksu nautilus
```
You can make a shortcut in your menu for this too, if it's not there already..

This gives you root-privileges.

---

### Post by Squid_blk on 2007-10-25
Did not work. The folders I moved to the trash still keep saying I do not have permission. Did not have these issues before the upgrade. Any other suggestions?

---

### Post by aysiu on 2007-10-25
Can you copy and paste both the command *and* the error message?

Something like ```
sudo mv /path/to/file /path/to/destination
```

---

### Post by taurus on 2007-10-25
What happens when you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```

Are you talking about directories/files in your ~/.Trash?

```
ls -la ~/.Trash
```

---

### Post by Squid_blk on 2007-10-26
I did the "update" and it asked for my password which I typed in.  It spewed out a list of files etc and said was done.  When I did the "upgrade" command it ended with this:

brandon@el-diablo:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

As I indicated before I dragged a folder to the Trash and when I go to delete the folder the error message says:

"/home/brand..._level.txt cannot be deleted because you do not have permissions to modify its parent folder

I opened the Nautilus with the sudo commands but it did nothing different than just dragging the folder around. At this point I am not sure what to do.

---

### Post by taurus on 2007-10-26
Can you at least post the output of my last command from a terminal?

```
ls -la ~/.Trash
```

---

### Post by Squid_blk on 2007-10-26
Sorry forgot that:

brandon@el-diablo:~$ ls -la ~/.Trash
total 12
drwx------  3 brandon brandon 4096 2007-10-25 11:11 .
drwxr-xr-x 61 brandon brandon 4096 2007-10-26 14:43 ..
drwxr-xr-x  4 brandon brandon 4096 2007-10-25 11:08 sipie
brandon@el-diablo:~$ 

I only see the Sipie folder when I open the trash in desktop mode

---

### Post by MegaJim on 2007-10-26
the other two are not really there :P

the single dot is a way of calling the current directory

the double dots is a way of moving up out of the directory

```
sudo rm -ir ~/.Trash/sipie
```

run that and confirm the deletes once you've checked the filename

---

### Post by Squid_blk on 2007-10-26
The sudo rm -ir ~/.Trash/sipie
worked. I hit Y for all the confirmations and it worked.

But how can I remove the bin files? It still says no permission

brandon@el-diablo:~$ locate sipie
/usr/bin/sipie
/usr/bin/sipie.py
/home/brandon/.sipie
/home/brandon/.sipie/history
/home/brandon/.sipie/cookies.txt
/home/brandon/.sipie/config
/home/brandon/.sipie/playlist
/home/brandon/downloads/sipie.patch
/var/crash/_usr_bin_sipie.py.1000.crash
/var/crash/_usr_bin_sipie.1000.crash

Do I need to log in as the root? If so then that might be a problem. To change the password it says the word needs to be at least six characters long. My system password is only 5.  When I first set the computer up I listed myself as the only user but when I checked the root password it had six dots and I do not know what that password is and not sure if anything changed during the upgrade. It is making me think to just wipe everything and start from scratch. I have everything backed up but I only want to do that if I have to.

---

### Post by taurus on 2007-10-26
> **Squid_blk said:**
> The sudo rm -ir ~/.Trash/sipie
worked. I hit Y for all the confirmations and it worked.

But how can I remove the bin files? It still says no permission

brandon@el-diablo:~$ locate sipie
/usr/bin/sipie
/usr/bin/sipie.py
/home/brandon/.sipie
/home/brandon/.sipie/history
/home/brandon/.sipie/cookies.txt
/home/brandon/.sipie/config
/home/brandon/.sipie/playlist
/home/brandon/downloads/sipie.patch
/var/crash/_usr_bin_sipie.py.1000.crash
/var/crash/_usr_bin_sipie.1000.crash

Do I need to log in as the root? If so then that might be a problem. To change the password it says the word needs to be at least six characters long. My system password is only 5.  When I first set the computer up I listed myself as the only user but when I checked the root password it had six dots and I do not know what that password is and not sure if anything changed during the upgrade. It is making me think to just wipe everything and start from scratch. I have everything backed up but I only want to do that if I have to.

```
sudo rm /usr/bin/sipie*
sudo rm "/var/crash/*.crash"
rm -rf ~/.sipie
rm ~/downloads/sipie.patch
```

---

### Post by MegaJim on 2007-10-26
you can do it in much the same way, using the sudo command to assume root status temporarily, without the danger of forgetting you're root and accidentally moving your home to /dev/null :P

```
sudo find / -name sipie -exec rm -ri {} \;
```

[B]be very careful with this!!!

make sure you confirm each file ok, i'm not to blame if you let it delete something it shouldn't :)[/B]

---

### Post by Squid_blk on 2007-10-30
I was able to remove the files in the way Taurus suggested. Thanks Mega Jim I will have to keep that command handy in case of other emergencies.  My work schedule has kept me away this weekend and I will be out most of this week but I will keep you posted on my progress. So far with all your help I am hopefully another step along and my knowledge has certainly been increasing. Thanks.

---

### Post by Squid_blk on 2007-10-31
Apparently there are some sipie files still on my system including one in the /usr/bin folder. It says I cannot delete it because I am not the owner.  I tried a reinstall of the sipie and got it to work until the gusty error comes up but when I went to fix it I still get the permission error.

I am giving up on the sipie thing for now. But I am still perplexed on how I am no longer the owner of my own system. How did this change and how do I restore it?  I was the user and root owner under Feisty and now I am not. This is making me consider wiping my system and starting from scratch but I am reluctant to do that unless completely necessary.  Any suggestions please?

---

### Post by taurus on 2007-10-31
You are the only owner of your own $HOME, not the whole system!  Therefore, if you want to remove something in /usr/bin, you need to include the sudo command first.

```
sudo rm /usr/bin/**filename**
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Squid_blk on 2007-10-31
Then I must be assuming that I have the same access with the terminal as I do when viewing files in gnome.  That makes some sense.  Thanks.

---

