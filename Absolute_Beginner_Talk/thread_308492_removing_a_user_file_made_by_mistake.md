---
title: "removing a user file made by mistake"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by matt_tee on 2006-11-28
i have tried to do this in gui (users and groups) without success.

I have a folder called 'ded' which is in my 'home' folder.

I have tried to delete it but there is no option to move to deleted items folder.

If i right click this folder and click permissions tab, i cannot access it.:confused: 

how do i delete this folder?

please help.

thanks.

---

### Post by Kurt` on 2006-11-28
sudo rm -r ~/ded/

---

### Post by Bachstelze on 2006-11-28
```
sudo rm -rf /path/to/folder
```

---

### Post by matt_tee on 2006-11-28
did as you said

root@matt-laptop:/home# sudo rm -r ~/ded/
rm: cannot remove `/root/ded/': No such file or directory
root@matt-laptop:/home#

with the above results, what am i doing wrong?

---

### Post by Bachstelze on 2006-11-28
Do note use ~. Use the full path to the dir.

---

### Post by mitch.c on 2006-11-28
> **matt_tee said:**
> did as you said

root@matt-laptop:/home# sudo rm -r ~/ded/
rm: cannot remove `/root/ded/': No such file or directory
root@matt-laptop:/home#
What is the output from:
```
$ ls -ld ~/ded
```

---

### Post by Kieranties on 2006-11-28
> **matt_tee said:**
> did as you said

root@matt-laptop:/home# sudo rm -r ~/ded/
rm: cannot remove `/root/ded/': No such file or directory
root@matt-laptop:/home#

with the above results, what am i doing wrong?

from the above it seems you are logged in as root.  In *nix systems the tilde "~" denotes your home directory.  So
```
sudo rm -r ~/ded/
``` translates to ```
sudo rm -r /root/ded/
```
also as you are logged in as root, you  do not need to use sudo.  You know it would be much safer if you logged in as a normal user.  Then use sudo when you need to perform an operation which requires root privaleges

---

### Post by kerry_s on 2006-11-28
You don't need sudo if you switched to root. You can also open nautilus as root and delete it-> alt+F2> gksu nautilus /home/matt-laptop

---

### Post by matt_tee on 2006-11-28
sorry, i've done as you have said, but got this result :

root@matt-laptop:~# rm -r ~/ded/
rm: cannot remove `/root/ded/': No such file or directory

?

---

### Post by matt_tee on 2006-11-28
also entered this:

root@matt-laptop:~# $ ls -ld ~/ded
bash: $: command not found
root@matt-laptop:~# 


?

---

### Post by Bachstelze on 2006-11-28
I repeat it for the third time : use the full path to the dir and not ~ !

---

### Post by steve.horsley on 2006-11-28
What is the full path to the directory you want to remove? Is it /home/ded? Or is it /home/matt/ded?

Anyway, if you are running as root (which you appear to be judging by your posts), simply **rm -rf /home/ded** or **rm -rf /home/matt/ded**.

---

### Post by Kurt` on 2006-11-28
> **HymnToLife said:**
> Do note use ~. Use the full path to the dir.

~ = /home/currentuser/

And for the original poster:

When you are logged in as root, ~ is /root, when you are logged in as your normal user, ~ = /home/yourusername/

So sudo "rm -r ~/ded/" is equivalent to running "rm -r /home/yourusername/ded/" as the root user.

The reason you have to use sudo is because the directory you are trying to delete is not writable by your user. The root user can remove any file though, regardless of who owns it.

---

### Post by Bachstelze on 2006-11-28
I'm pretty well aware of what ~ is, thanks, I was using *nix perhaps before you were born. And as he is logged in as root, ~/ded will be /root/ded and not /home/*/ded.

---

### Post by Kurt` on 2006-11-28
> **HymnToLife said:**
> I'm pretty well aware of what ~ is, thanks, I was using *nix perhaps before you were born. And as he is logged in as root, ~/ded will be /root/ded and not /home/*/ded.

He shouldn't be logged in as root when running sudo commands, and you can leave the assumptions and condescending attitude at the door. Thanks.

---

### Post by Bachstelze on 2006-11-28
You're the condescending one here I think...

And I agree he should not been logged in as root but the fact is that he is, and he can very well use sudo if he wants to, though that will be pretty useless.

---

### Post by anaconda on 2006-11-28
If the folder is empty you can write:
rmdir /home/matt/ded
or go to the folder /home/matt and type
rmdir ded

And if the folder is not empty then you have to use 
rm -R ded
(when you are already in the folder /home/matt)
I am not sure if rm -R removes an empty directory? propably yes.. have to try sometime.

And finally. If it complains that file or directory doesn't exist... are you sure you are sure it really exists?

can you see it if you type:
ls -la |more 
in your home directory?

---

### Post by anaconda on 2006-11-28
yes rm -R ded 
removes also an empty directory..

Are you sure that the name of the directory isn't Ded ?
In linux big and small characters are completely different.

if You still cant remove the directory, which is unbeliavable. can you copy/paste the line where that directory shows in
ls -la
so that we can see which owner owns that directory, is it just a symlink, or is it spelled differently than "ded"

---

### Post by hotbrainz on 2006-11-28
This may seem a bit crude compared to the elegant methods suggested before but it will work i guess. You have to become root user in graphical mode then just delete it ( select -> right click )>delete) To go in graphical mode as root user, the commands are - 

gksudo nautilus        

This is for gnome desktop which is default. As soon as you type this command a window will pop up with the file system. In this you have root privileges. But friend...careful you have the power to delete anything. So just delete the particular file and close the window and return to being a normal user.

---

