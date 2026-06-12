---
title: "How to delete file from terminal?"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-03-31
Hi,

I messed something up on my Ubuntu, and now it wont boot into gnome.
Im pretty sure its because I messed around with the xorg.conf file.

But I took a backup before.

Now im booting my PC from a Knoppix CD, and wanted to delete the xorg.conf, and remame my backup to xorg.conf.

Now my problem is that I dont have permission to do this, I believe I must be logged in as root. So how do I delete the file from the terminal?

Thanks for any help.

---

### Post by Omnios on 2006-03-31
If its a Xorg problem you should be able to boot into recovery mode and log in as root or use sudo basicly you can copy the back_up_file_name to the Xorg_file_name to replace it.

---

### Post by aktiwers on 2006-03-31
Thanks for your quick reply.

Could you give me the exact code to write from there?
Im very new to ubuntu, but when I was in recovery mode before, I didnt know what to type as root.

Actually thats excactly what I wanted to do, to restore the backup.

---

### Post by aysiu on 2006-03-31
If you're in Knoppix, just mount the Ubuntu partition on your desktop and find the button for "File Manager - Super User Mode." Then you'll have root privileges to copy back the backup file.

If you're in Ubuntu, you don't need to boot into Recovery Mode. You can just boot into normal mode. If Gnome doesn't load, you'll be at a black screen with white text. Log in and type ```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
``` This assumes your backup file is called *xorg.conf_backup*.

---

### Post by johnnymac on 2006-03-31
If you jacked your xorg up and didn't make a backup of it....oops.  You can reset xorg.conf by this

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

Once that's done...done jack with your xorg.conf file before making a backup like the above post indicates.

GL

---

### Post by Omnios on 2006-03-31
To copy a file using a terminal, use 

cp


For example: 

cp template.html course-schedule.html


This makes a new file that contains the same information as the first file with the name indicated. In the example above, cp takes the contents of template.html and makes a file called course-schedule.html that contains all the information in template.html. 

cp can also be used to copy a file from one directory to another. For example:

cp /home/tmp/mbl.color.logo.jpg /home/mwaring/images/MBL.jpg


This command will take MBL.color.logo.jpg in /home/tmp and copy it to /home/mwaring/images. It names the copy MBL.jpg. If a name is not specified for the file, a copy with the same name as the original is made. For example:

cp /home/tmp/mbl.color.logo.jpg /home/mwaring/images


To copy an entire directory, use the -R flag.

cp -R dir-to-copy/ new-dir/ 

For example:

cp -R /home/tmp/images/ /home/mwaring/temp-images 
copies the directory in /home/tmp called images into the temp-images directory in /home/mwaring. Note: on some computers, cp -R does not copy dot-files (files that start with '.', for example .bashrc). 

You may run into trouble copying files from or to directories which you do not have permission to read or execute. 

 -R means recursive which includes files in a directory. 

 First off recovery mode is a boot option when grub starts. After it boots in you can log into in text mode and if I remember properly xorg.conf is in /etc/X11/xorg.conf so the command will be cp /etc/X11/xorg.conf.(what you names the backup) /etc/X11/xorg.conf  cp is copy the first file name is the one you are copying which is your backup file and the second is where it is being copied and it will overwrite the exzisting xorg file. You can also cd /etc/X11/ then use ls to see the files in that directory to check on the backup name if not shure though it should be what you chosse as a back up filename.

---

### Post by aktiwers on 2006-03-31
Great, just took a shower and came back to all these nice responces!

Im gonna try it! I will report back :)

Thanks!

---

### Post by aktiwers on 2006-03-31
[QUOTE=johnnymac]If you jacked your xorg up and didn't make a backup of it....oops.  You can reset xorg.conf by this

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

Once that's done...done jack with your xorg.conf file before making a backup like the above post indicates.

GL[/QUOTE]

Thanks, this one worked! Im now logged in on Ubuntu again :-D 
Thanks for the support guys! :)

---

### Post by iansane on 2007-10-01
I know this was an old topic but I had to look else where to find the answer to the question asked in the original post so this is for anyone who comes here looking for the answer.

from a sudo terminal or with the sudo command, "rm -r  [name of directory]" will delete a file  or directory from terminal. As in the replies above from Omnios, the -r is for an entire directory (folder). Use "rm" for a single file.

I did not see this by typing help. Seems like this would be an important one to include in the basic "help" listing but I guess that's a matter of opinion. :)

---

### Post by Celegorm on 2007-10-01
Careful with that -r. It deletes recursively, meaning 'rm -r a_folder' will delete a_folder and all of its contents, and the contents of its subdirectories, and their subdirectories.... It's very dangerous if you aren't careful what you type. It's better to use -ri which makes it interactive so you don't delete something by accident. To remove an (empty) directory it's much safer to use 'rmdir a_folder'

---

### Post by iansane on 2007-10-06
good to know Celegorm, maybe it's good that it was not easy to find. thanks :)

---

