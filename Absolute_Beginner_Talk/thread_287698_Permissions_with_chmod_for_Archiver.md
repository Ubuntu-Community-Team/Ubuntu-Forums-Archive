---
title: "Permissions with chmod for Archiver"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-29
Hello, I was wondering if I could change the settings for my Archiver (that is where the /tmp/ files that need to be extracted go, right?) and the rest of my file system by changing the permissions to [mode]=700 by using a sudo chmod command since I am the only user/owner of my computer (and have no groups or other users).

I would like to have a chmod command with the[mode]700 or -read, write, exec. for me only, no group, no others. And I would like the correct [options] to go with that command like these Common options," -i (interactive, it asks you to confirm every action), -r or is it -R (Recurses into directories, means it basically grabs everything in there. Needed for copying directories), -v (Verbose, tells you everything its doing),"

I would need full details and step by step directions on this process if anyone can help me open up my permissions for what files it's safe to do that with. I figure if I have the -i [option] to double check if I want to go through with the terminal command, the -r [option] to include everything in the file (if that is correct), and the -v [option] to let me know what I have just performed using terminal, kind of like a receipt.

Thank you and if you know of a link to a good tutorial about it, then please link me, thanks,
-c.

also, is 700 for root only, would I actually want 770, or 750 as the "user" or sudo superuser, I'm still very new so sorry for the confusion.

---

### Post by kerry_s on 2006-10-29
It would be better to just start xarchiver as root instead of trying to mess with permissions.

Press alt + F2
type->
gksudo xarchiver

That will give you xarchiver with root permission.

---

### Post by crimesaucer on 2006-10-29
cool, thank you, "gksudo xarchiver" will work for xubuntu also, right, and what does the "gk" part mean?

I'm still interested in learning if there is a safe and permanent way to set the file permissions for my file system with certain options like -i to have a check to make sure I don't do something by accident.

Thanks.

---

### Post by kerry_s on 2006-10-29
> **crimesaucer said:**
> cool, thank you, "gksudo xarchiver" will work for xubuntu also, right, and what does the "gk" part mean?

I'm still interested in learning if there is a safe and permanent way to set the file permissions for my file system with certain options like -i to have a check to make sure I don't do something by accident.

Thanks.

"gksudo" is for launching graphical applications, while "sudo" is more for commands.

"will work for xubuntu also"

It should work with any system, in kde it would be "kdesu". I'm using edgy server install+xfce4 build up, but it should be mostly the same as xubuntu, i just don't have all the applications and settings. If you need root file system access you can use launch thunar with "gksudo thunar", but changing permissions on the root side can quickly break the system. There should be no need to modify permissions.

---

### Post by crimesaucer on 2006-10-29
Yeh, that's why I'm asking about it, I don't want to break anything. But I also would like to learn how to use linux the proper way, the fastest way.

Struggling with permissions for basic things like beginner downloads and extracting files to move and open has been a little frustrating for a beginner. Why even have something download to a tmp file that you don't have permission to execute from if you are the only owner/user. Opening up gksudo xarchiver to open up an archiver that opens up automatically seems like an extra few steps for a downloading and extracting and moving a simple tar.gz file.

Should I have my download manager in Firefox set to something different than desktop. 

I have been reading some tutorials about chown and chmod root permissions, and it seems safe if you know what files need which permissions/options, and which files not to use chmod on. 

I am the only one on my computer so "I'm not scared about some one else ruining my system" so working as a superuser I understand is a precaution for only me, but wouldn't it be easier to set the common folders that I will always be using (archive extractor and tmp) to a root chmod with an -i option to double check myself before actually completing a command.

I mean if I know I want to click on to a link for a download, then click again for it to extract and then go through opening it in gksudo and finishing the operation, wouldn't it be easier to have the setting set as su, properly with an -i option to make it faster and easier. 

I probably have this wrong, but I am under the impression that having terminal in an OS is faster than say, using windows as an administrator. But using gksudo to open the archiver (which I did and worked, thank you) seems like the slow and improper way to use linux, rather than setting a chmod permission properly once, to be faster than windows by being able to use the gui of the archiver as fast as a windows gui for extract "AND" being able to perform (exec) the same extract in terminal as fast or faster. I was reading this in a unix tutorial but I don't think it applies to ubuntu: [http://users.tkk.fi/~thyle/unix_opas.html](http://users.tkk.fi/~thyle/unix_opas.html)

for example this part:     

    *  Create tar file and add all txt files from current directory
      tar cvf example.tar *.txt
    * Create tar file and add all content recursively from dirname
      tar cvf example.tar dirname
    * Extract files from tar
      tar xvf example.tar
    * View contents of tar file
      tar tvf example.tar


I wish I could find tutorials for ubuntu/xubuntu like this.

---

### Post by kerry_s on 2006-10-31
There should not be permission problems, everything you do should be in your user account. There should be no reason for you to leave the home folder for what you want to do.

> Should I have my download manager in Firefox set to something different than desktop. 

I would, i usally create a tmp folder and firefox is set to download there.

> I have been reading some tutorials about chown and chmod root permissions, and it seems safe if you know what files need which permissions/options, and which files not to use chmod on.

For what your doing you don't need permissions.


> I mean if I know I want to click on to a link for a download, then click again for it to extract and then go through opening it in gksudo and finishing the operation, wouldn't it be easier to have the setting set as su, properly with an -i option to make it faster and easier.


You download> right click> extract here,now click>view>show hidden files and middle click .icons or .themes folder(which ever your installing) this will open a second thunar, now drag the extracted folder from tmp to the other thunar, done. There is NO need to do gksudo, you do not need to leave your home folder. If you don't have permissions in your home folder for a folder or file that means you created it as root, then you can> gksudo thunar /home/(you) < and delete the folder/file and create it again as a normal user(aka: no red bar).


Xubuntu is dirt simple to use, i'm sure you'll get it in time. Don't concern your self with the command line just learn to use the gui stuff first and be able to find your way around a linux file system, once you get that down the command line stuff will be easy because you'll know where everythings at.

---

