---
title: "Webserver Permissions"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by gomisute on 2008-02-07
What is the best way to set up my web server permissions?
I am running php scripts that need to run the mkdir() function all the time.

I keep getting an error of permission denied.

I have done CHOWN, CHMOD, etc...and have reached my limits

I have searched and read all the resulting pages on this forum and tried every solution I could think of.

I am also, not the greatest when it comes to command line syntax and permission, yet I don't use the GUI part of Linux at all since I find the command line much more powerful and easier to use.

So please help since I am sick of getting permission denied messages from the server.

Note: I can use the command line to make dirs, the problem is how do I give the "all mighty" permissions to my web server!

Please help.
THANK YOU> :confused:
PS
here is a ls -la result:

```
doraemon@kuru:~$ ls -al /var/www/
total 12
drwxrwxrwx  3 www-data www-data 4096 2008-02-05 20:06 .
drwxr-xr-x 17 root     root     4096 2008-01-30 15:33 ..
drwxrwxrwx  9 www-data www-data 4096 2008-02-07 00:29 apache2-default
doraemon@kuru:~$ 


```

---

### Post by whazooo on 2008-02-07
The problem is that a php script is usualy ran from a browser.
And the browser has the permission distinction of being "other"
in the permission scheme, 
user group other

If your script is writing to a directory on the web server it would have to have the permissions to do so.

chown www-data:www-data yourscript.php

This way your script can write to a directory owned by www-data

---

### Post by gomisute on 2008-02-07
OK.
That makes sense and thank you.
---
But here is what the permissions for the script look like:
Is this suitable?
```

doraemon@kuru:~$ ls -al /var/www/apache2-default/v1dev/database/logo.inc.php 
-rwxrwxrwx 1 www-data www-data 1816 2008-02-06 15:55 /var/www/apache2-default/v1dev/database/logo.inc.php
doraemon@kuru:~$ 

```

Oh, and this still doesn't work!
The same error appears.
Any more help, Please?!
:(

---

### Post by whazooo on 2008-02-07
Without knowing what the script is doing, Its kinda hard to say what you need to do.
But in general;

If the script is creating a file in some directory, Giving the directory 0777 permissions
ought to do the trick.

If however the script is manipulating a file in said directory, The file would need to have the 0777 permissions.

If the script were creating directorys the script would need the same permissions as the owner of the parent directory.

Now with all that said, Opening a directory with 0777 permissions is a security risk
as is giving the script ownership of the directory or web server. If this is a production box open to requests from the internet you will want to use these permissions sparingly.

Let us know what the script does and to what and people here should be able to get you going pretty quick.

---

### Post by whazooo on 2008-02-07
Heres the thing..
In your first post you said you could create directorys from the command line with no problem. but who are you when you do it? you? root?
if you create a directory like so.
/var/www/gomisute
and this directory is owned by you.
And you want the script to create directories under the directory /var/www/gomisute/script_made_directory/

And If the script is owned by gomisute:gomisute,
Then all you have to do is chmod 777 /var/www/gomisute

The script should be able to crank out directories no problem.

---

