---
title: "Samba sharing"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by quarkhirad on 2008-01-14
i clicked on the share folders in system and then administration share a folder called buffer which is located in / . I have gave browse permissions also. However when i try and access the folder from   comp d (my friends comp) it shows me the folder and i can see all the data inside however i am unable to create files or folders. That is my friend cannot write to my shared folder how do i do it.

---

### Post by njparton on 2008-01-14
Permissions.

Change the permissions of the folder you're sharing using chmod to allow him to fully use that folder.

Search for chmod if you've never used that before.

Also, to avoid this issue in future, edit your smb.conf file so that the directory and create masks are 0777 not 0700.  However, this will allow everyone with access to see, open and modify everything shared.  Then restart samba or reboot.

Search the net for "samba" as there are many good guides on how to configure it out there.

---

### Post by quarkhirad on 2008-01-14
Thanks njparton. 

Yes i am familiar with chmod  and the smb.conf file. However i am not familiar as how to change the mask in the file to 0777 can u please tell me how to do that

---

### Post by quarkhirad on 2008-01-14
Thanks njparton. 

Yes i am familiar with chmod  and the smb.conf file. However i am not familiar as how to change the mask in the file to 0777 can u please tell me how to do that.

---

### Post by quarkhirad on 2008-01-14
Ahh just one more thing . I now tried accessing my folder for a windows machine and it pops up a dialogue box asking for a user name and password . I dont remember setting up a username and password. what do i have to enter. In linux it does not ask for anything its only windows that asks for user name and password.

---

### Post by njparton on 2008-01-14
You'll need to first create yourself a samba password:

```

sudo smbpasswd -a *username*

```

where *username* is your username.

Repeat for all other users.  They'll also have to have linux accounts too.

then edit the following file:

/etc/samba/smb.conf

and search for the lines in the global section that refer to directory and create mask.  Change them to 0777, but note my earlier word of warning about access.

Then restart samba:

```

sudo /etc/init.d/samba restart

```

Please search the web or this forum for samba how to's - they will guide you through the whole process.

---

### Post by njparton on 2008-01-14
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by quarkhirad on 2008-01-16
dear njparton

Thanks for the links however, I enterred the following code in the terminal

all@webbi:~$ sudo useradd -s /bin/true autocad
all@webbi:~$ sudo smbpasswd -L -a -n autocad
Added user autocad.
all@webbi:~$ sudo smbpasswd -L -e -n autocad
Enabled user autocad.
all@webbi:~$ sudo /etc/init.d/samba restart
 * Stopping Samba daemons...                                             [ ok ]
 * Starting Samba daemons...                                             [ ok ]
all@webbi:~$ 


I then went to my windows machine and tried to access my samba. It gave my the dialogue box in which i enterred the username as autocad and left the password blank and clicked ok. The dialogue box reappeared with the username as WEBBI\autocad and password field was blank. I again left the username as it is clicked ok it still just pops the dialogue box up again as though my password was wrong. Please help

---

### Post by RudolfMDLT on 2008-01-16
Sorry to jump in like this,

But if you want to you can turn off the security all together. If you are working on your own private lan then I'm sure it won't be a problem.

In the smb.conf file, under Authentication, there is a line which reads "Security = user" change that to "security = share".

You should now not be pestered with login dialogs.

---

### Post by quarkhirad on 2008-01-16
Yes yes yes yes.:guitar::guitar: It worked. :guitar:Thanks a lot RudolfMDLT. Thanks :guitar:

Oh and its not at all a problem if you jump in its ok 

Hey there is just one thing. I am setting up this samba server in my college so that students can use it so that they come to the lab work on there stuff and then put it on the server and then tell the faculty that its there and then the faculty sees there work. One more thing is if a facult has some notes he/she can put it on my samba server and then all students can come to the lab and access it . Now the problem is the share folder ( This folder is called buffer ) has permissions of 0777. Now the prob is that after the faculty put the notes up in the buffer folder the  students cut and paste the files into there system.Hence deleting the files from the buffer folder. Hence i would like to create a shared folder ( say FACULTY NOTES ) such that only the faculty are allowed to add and delete their notes and the students can just access them copy it to their system but not delete it from the share folder. Is this possible if so then tell me how? Just as info i am using ubuntu 6.06 LTS and my network is a totally private network . Hence as you said i have disabled the security feature. :lolflag:

---

### Post by RudolfMDLT on 2008-01-16
I have tried to do something along the same lines but setting up user permissions with samba is a pain. If anybody here know how to user based permissions in samba please post any ideas! :)

Give me a couple of minutes and I'll see what I can do.

Can your faculty people work SSH, SCP or Rsync... or are they windows people? :)

EDIT:

You are going to need to re-enable security.

Now I don't know how to do this in text but here is the basic idea and it should work.

In post 8 you added the user "autocad". As far as I know, samba users also need to exist as system users. That is, you need to create a user called autocad, and autocad must be able to log into the pc and have a home folder ect... Then only when you add them to the samba user list will the login's work.

So, create a group called 'students", these are basic desktop users, and create a group called "faculty"/ or you don't have to. Create a user "student" that belongs to the group "students" and a user "Professor" that then belongs to the 'admin" or the faculty group that have admin rights.

Now using (i think) the chmod command, set the folder to be owned by Professor, Read and Writable by Professor, Read and Writable by the group, but only readable and executable by everybody else.

details are here: [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#access1](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#access1)

Now when somebody logs in, the system security profile is applied and they can then either read or read and write?

Sounds good in principle anyway! :)

Goodluck!

Let me now whether it works!

PS: I dont't know whether when files are pasted in the folder, they retain their permision. You might need to administer the system via ssh and just run a recursive chmod on the folder so that all the files stay secure.

---

### Post by quarkhirad on 2008-01-16
Dear   RudolfMDLT 

Thanks.  Yeah they are windows users :( . Thats so horrible. 

Hey i tried this 


Created a user called faculty and created a share folder /faculty_test changed ownership through chown so that faculty owns the folder. Then set permissions to 0777. 

I then put back the security. 
 
Then restarted samba 


Now i have the same problem as before ( see same post but no 8 post ) even when i tried to log on as faculty it denied. 

Any suggestions.

---

### Post by RudolfMDLT on 2008-01-16
> File Permissions

File Permissions define the explicit rights a computer or user has to a particular directory, file, or set of files. Such permissions may be defined by editing the /etc/samba/smb.conf file and specifying the explicit permissions of a defined file share. For example, if you have defined a SAMBA share called sourcedocs and wish to give read-only permissions to the group of users known as planning, but wanted to allow writing to the share by the group called authors and the user named richard, then you could edit the /etc/samba/smb.conf file, and add the following entries under the [sourcedocs] entry:

read list = @planning

write list = @authors, richard

Save the /etc/samba/smb.conf for the changes to take effect.

Another possible permission is to declare administrative permissions to a particular shared resource. Users having administrative permissions may read, write, or modify any information contained in the resource the user has been given explicit administrative permissions to. For example, if you wanted to give the user melissa administrative permissions to the example sourcedocs share, you would edit the /etc/samba/smb.conf file, and add the following line under the [sourcedocs] entry:

admin users = melissa

Save the /etc/samba/smb.conf for the changes to take effect. 

The above is exactly what you want to do I believe.

You can find more on the topic here:
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/windows-networking.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/windows-networking.html)

But lets first make sure that you can log into your samba box.

Create a user "autocad".

> useradd autocad
now follow the steps and create a new password, for now 123 or something simple.

next, do exactly:
> sudo smbpasswd -a autocad
sudo smbpasswd -e autocad

also make the password here 123 or the same as above.

Now reboot your system and verify that you can login as a user on the box as autocad.
Next logout, and try and access the box from windows using the user name and password.

I think the problem is that you added users with null passwords and either samba config doesn't allow it or it confuses the windows box.

Edit: If you still have troubles, please paste your entire smb.conf file under quotes. Also the output of this command : "ls /home -al"

---

