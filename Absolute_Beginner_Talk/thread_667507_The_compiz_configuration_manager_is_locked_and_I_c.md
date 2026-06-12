---
title: "The compiz configuration manager is locked and I can not configure it"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-01-14
Hi
Thank you for reading my post
I have made some configuration which I read in other forums:
[http://forum.compiz-fusion.org/showthread.php?t=5901&highlight=wallpaper+gnome](http://forum.compiz-fusion.org/showthread.php?t=5901&highlight=wallpaper+gnome)
[http://ubuntuforums.org/showthread.php?p=3816927#post3816927](http://ubuntuforums.org/showthread.php?p=3816927#post3816927)
in order to configure my workspace and compiz in a good way, now when I open ccsm (compiz configuration setting manager) It does not allows me to change any options, can some one please let me know what to do?

I attached an image shows ccsm, 

Thanks

---

### Post by PeterJS on 2008-01-14
Did the permissions on your compiz settings get changed? Looks like the settings might be read only for your user.

---

### Post by wolfen69 on 2008-01-14
try running as superuser.
```
sudo compizconfig-settings-manager
```

---

### Post by thelatinist on 2008-01-14
I think I had this same problem, and somehow I had managed to get my .compiz folder owned by root.   Have you checked to make sure you own /home/your_user_name/.compiz?

---

### Post by legolas_w on 2008-01-14
Thank you for reply.
I tried to change the permission using gksudo nautilus by using gui based permission management of nautilus, problem is that it does not apply the permissions and also it does not return any error.

Can you please let me know what is shell command  to change the permission of .compiz and compiz folders, I want to give all permission  of those two folders and what ever is inside them to a user named legolas.


Thanks.

---

### Post by PeterJS on 2008-01-14
To change the owner ship on a file:
```

sudo chown username:groupname file -R

```
In ubuntu there is also a group created for each user so unless you have some specific plans in to share it, just putting your username twice should be plenty. Being a unix derivative files and directories can be used pretty much interchangeably with the basic tools except in cases that make no sense, like trying to open a directory in a text editor.

To change the permission after you've gotten the ownership changed see the man page for chmod, there are a couple ways to go about accomplishing what you want, and the explaination's a bit long but makes sense after you read it.

---

### Post by nikoPSK on 2008-01-14
> **legolas_w said:**
> Hi
Thank you for reading my post
I have made some configuration which I read in other forums:
[http://forum.compiz-fusion.org/showthread.php?t=5901&highlight=wallpaper+gnome](http://forum.compiz-fusion.org/showthread.php?t=5901&highlight=wallpaper+gnome)
[http://ubuntuforums.org/showthread.php?p=3816927#post3816927](http://ubuntuforums.org/showthread.php?p=3816927#post3816927)
in order to configure my workspace and compiz in a good way, now when I open ccsm (compiz configuration setting manager) It does not allows me to change any options, can some one please let me know what to do?

I attached an image shows ccsm, 

Thanks

:shock: As peter suggested, probably folder got root only access or read only...

nikoPSK

---

### Post by legolas_w on 2008-01-15
Hi
Thank you all for your suggestions and help.
I used chown and it executed without any problem on both .copiz and compiz folders in my own home directory. but the problem still is in place.

Any other place that I should check?

thanks.

---

### Post by legolas_w on 2008-01-15
Any suggestion? 
what could be that wrong which do not allows me to perform the configuration?
I gave all permissions to my own user with no luck, it does not allows me to edit the configuration.
I removed the CCSM and install it again with no luck.
thanks

---

### Post by PeterJS on 2008-01-15
You could try recursively chowning all of the hidden directories in you home directory:
```

sudo chown user:user .[.^]* -R

```

---

### Post by legolas_w on 2008-01-15
I used the command you gave me and it bring me no luck,
Is there any way that I could use sudo to configure my own user compiz?

Thanks

---

### Post by nikoPSK on 2008-01-15
> **legolas_w said:**
> I used the command you gave me and it bring me no luck,
Is there any way that I could use sudo to configure my own user compiz?

Thanks

Unfortunately not that I know of, you could try reinstalling compiz. :)

nikoPSK

---

### Post by legolas_w on 2008-01-16
Thank you all for your comments, it looks like that this is not going to answer to our solutions and 
it really made me crazy, I will reinstall the Ubuntu.

Thanks.

---

### Post by ronmarley1 on 2008-01-16
> **legolas_w said:**
> Thank you all for your comments, it looks like that this is not going to answer to our solutions and 
it really made me crazy, I will reinstall the Ubuntu.

Thanks.

Wait!  I hope you have not tried a full system reinstall.  Try this first: go into CCSM and click the Preferences button.  Go to the Plugin List tab and see if "Automatic plugin sorting" is checked.  I bet it is not.  Tick the box, and you should now be able to change the preferences.  Sorry I did not see this sooner!

---

### Post by legolas_w on 2008-01-16
Thanks, It was the mistake that i have made.
Now it is fine.

---

### Post by ronmarley1 on 2008-01-16
Cool.  I was hoping I caught you before a reinstall of the whole OS.

---

