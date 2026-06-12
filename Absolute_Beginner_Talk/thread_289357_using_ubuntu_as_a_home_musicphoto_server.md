---
title: "using ubuntu as a home music/photo server"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by greggfathead on 2006-10-30
Hi:

I just installed Edgy on an old Dell 500SC box I have, and I'd like to turn it into a music/photo server to use at home.  Samba is running, and I can go to System >> Administration >> Shared Folders and make a new folder.  However, when I access the folder on my Mac I cannot write to the folder, I can only pull files down.  Any ideas as to how I can read/write access these folders?  I'd like to be able to access this box from Mac, Ubuntu and Win XP machines.

Any help would be greatly appreciated - thank you!

---

### Post by davmac on 2006-10-31
The first thing I'd check the permissions for the folder you've set up and any files you've created within it. If you open up a terminal and navigate to the parent folder and type "ls -l" you'll get the directory listing that will be prefixed with something like "drwxr--r--".

The "d" denotes that it is a directory. The next three characters show your permissions (read, write and execute), the next three show the permissions for your group. The last three the permissions for everybody.

Try setting the permissions for the folder by typing "chmod a+rw foldername/" to give everyone read/write access and seeing if this sorts the problem out. If it doesn't, you've potentially opened it up when you wouldn't want to. Try "chmod 755 foldername/" to put it back to how it was.

If it's not this then it could be the Samba permissions. Not something I know much about but if you have a look for the smb.conf file (somewhere in /etc) and have a google for Samba configuration you might be able to track it down.

...Come to think of it there's a section covering this in the Unofficial Linux Starter Guide. Have a look at [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server) and see if this helps.

Regards,

Dave Mac

---

### Post by greggfathead on 2006-11-01
So far I've just set up one folder in my home folder for sharing, that one is called "photos" and it's permissions are listed as drwxrwxrwx.  So the permissions look good on this end so far.

I went to edit the samba.conf file, and it tells me I cannot edit the file, that I don't have the correct permissions.  Huh?  I'm the only user set up on this box, so that makes no sense.  

I'd set up my laptop running Dapper to do samba sharing before, so I'm starting to suspect there's something hinkie going on with Edgy here.  Since this is a brand new install of Edgy, I think I might just do a clean install of Dapper real quick and see if I can set up Samba correctly in that, then go back and do a clean install of Edgy again and compare - unless anyone has any other suggestions.  

Thank you for the response Dave, I really appreciate the assistance!

---

### Post by mattskr on 2006-11-01
Use "sudo gedit /etc/samba/smb.conf". It will ask for your root password. Then you will be able to edit the file. Check your share definitions at the bottom and make sure writeable is set to 'yes'

There is also a default share listed there that will enable you to share your home directory. Just uncomment it.

---

### Post by hopstah on 2006-11-01
you need to be in super user mode to edit that file.  type ```
sudo gedit /etc/samba/smb.conf
``` and then enter your password when it prompts for it.  you will then be able to edit the smb.conf file.  down at the bottom is where it shows you what is being shared.  copy and paste that here for us to look at.

---

### Post by greggfathead on 2006-11-04
Thanks to everyone's help in this thread, I finally got my shares up & running!  I have to tell you though, I had to do everything thru the terminal, cause setting up samba and the shares thru the gui didnt work at all.  No matter what I set up it either did not hold when i hit save or just plain did not work.

After I got my shares running, I installed Banshee and the DAAP plugin and now Mac & PC users can see my entire library as a share thru itunes - nice!

For reference: I had to edit my smb.conf file and set up all my users thru the terminal, so for anyone reading this thread and setting up their own music/photo server, don't trust the gui.

---

