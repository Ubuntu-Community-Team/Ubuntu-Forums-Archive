---
title: "Reading/Writing to Mac partition from Ubuntu"
date: 2011-10-21
forum: Apple Hardware Users
---

### Post by jamiehutber on 2011-10-21
So guys this question has already been asked [here]("http://ubuntuforums.org/showthread.php?t=1760183"). But unfortunately they don't address the right issue.

Currently i have access to all the folders i want as i have in the mac set their permissions to read/write. Yet still i cannot from within ubuntu, this makes me very sad now :( All i want to be able to do is access my /var/www file so i can work between the 2 without any problems. Although in reality i don't think now i have ubuntu working correctly i will ever bother with the pile that is mac '0S'.

I am using Snow Leopard and 11.04, just in case this makes a difference.

Any help will be brilliant :)

---

### Post by jerrycal on 2011-10-22
> **jamiehutber said:**
> So guys this question has already been asked [here]("http://ubuntuforums.org/showthread.php?t=1760183"). But unfortunately they don't address the right issue.

Currently i have access to all the folders i want as i have in the mac set their permissions to read/write. Yet still i cannot from within ubuntu, this makes me very sad now :( All i want to be able to do is access my /var/www file so i can work between the 2 without any problems. Although in reality i don't think now i have ubuntu working correctly i will ever bother with the pile that is mac '0S'.

I am using Snow Leopard and 11.04, just in case this makes a difference.

Any help will be brilliant :)


In order to write to HFS+ partition from Linux you have to turn off Journaling or create separate shared partition in HFS+ format without Journaling.

Next problem you might have is owner rights. Quoting Lifehacker:

> The great thing about OS X and Linux is that they are both UNIX-based  operating systems, so they work pretty well together if you can get  everything set up correctly. When you create a user in either operating  system, it gives you a User ID number. OS X starts these numbers in the  500s, while Linux usually starts in the thousands. This is problematic  because a different "user" owns your home folder in OS X than owns your  home folder in Linux. As such, Linux will deny you access to your OS X  home folder, since you don't have the right permissions to access it.


  There's an easy fix, however—we just need to change our UID in one OS  so that it matches the UID in the other. Unless you have a reason for  choosing otherwise, we're going to change our Linux UID to match our OS X  one, since it's a bit easier. By default, the first user in OS X has a  UID of 501, but you can double check this by going into System  Preferences in OS X, right-clicking on your user, and hitting Advanced  Options. If your User ID is something different from 501, replace 501 with your other UID in the terminal commands below.
 Boot into Linux (we're using Ubuntu in this example) and fire up the  Terminal. First, we're going to add a temporary user, since we don't  want to edit a user that we're currently logged into. So, run the  following commands in the Terminal, hitting Enter after each one:
  sudo useradd -d /home/tempuser -m -s /bin/bash -G admin tempuser  sudo passwd tempuser 
 Type in a new password for the temporary user when prompted. Reboot  and log in as tempuser. Then, open up the Terminal and type in the  following commands, once again hitting enter after each one (and  replacing yourusername with your Linux user's username):
  sudo usermod --uid 501 yourusername  sudo chown -R 501:yourusername /home/yourusername 
 This will change your Linux user's UID to 501 and fix your home  folder permissions so that you still own them. Now, you should be able  to read and write to both your Mac and Linux user's home folder, no  matter what OS you're logged into.
 You may also want to fix your login screen, since by default Ubuntu  won't list users with a UID of less than 1000. To do this, just open a  Terminal and run gksudo gedit /etc/login.defs and search for UID_MIN in the text file. Change that value from 1000 to 501, and when you reboot your user will be listed in the login screen.
 [U]
[/U] Lastly, log back in as your normal user and run sudo userdel -r tempuser to delete the temporary user we created earlier.
 If you like, you can create symlinks in one of your home folders that  point to your main home folder for quick access. For example, since I  use my OS X home folder as my main data dump, my Linux home folder is  mostly empty. So, I created symlinks in my Linux home folder for  Documents, Videos, Pictures, etc. that point to the equivalent folders  on my Mac partition. You can do this by using the following Terminal  command:
  ln -s /path/to/linked/folder /path/to/symlink/ 
 If you're using your Linux home folder as the main one, you can use  this same command to create symlinks that link to your Linux home folder  instead.
 Note that if you're using your Mac partition as the main home folder,  you'll probably also want to automatically mount it in Linux when you  start up. You can do this by adding a line to the end of /etc/fstab. This will vary from person to person, but mine looks like this:
  /dev/sda3 /media/Data auto rw,user,auto 0 0 
 Where /dev/sda3 is the location of the partition containing the home folder and media/Data is the path I want to use to navigate to it.


---

### Post by jamiehutber on 2011-10-24
Cheers dude, 

sure enough disabling Journaling and then i edited my ubntu user id to be the same as my macs user id. Then all i had to do was inside mac change the folders i wanted access to to ´everybody´. Then i was able to do what i liked with the files :)

Cheers, now i need to know how to change this to resolved. i tried advanced edit.

---

### Post by jerrycal on 2011-10-24
> **jamiehutber said:**
> Cheers dude, 

sure enough disabling Journaling and then i edited my ubntu user id to be the same as my macs user id. Then all i had to do was inside mac change the folders i wanted access to to ´everybody´. Then i was able to do what i liked with the files :)

Cheers, now i need to know how to change this to resolved. i tried advanced edit.


Glad it helped. To mark thread as solved, you should be able to go to "Thread Tools" and "Mark thread as solved"

---

