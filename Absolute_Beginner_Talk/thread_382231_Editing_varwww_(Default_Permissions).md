---
title: "Editing /var/www/ (Default Permissions)"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by atraeyu on 2007-03-11
I installed edgy desktop, then installed the apache2, php, & mysql modules.  The default directory for apache documents directory is /var/www/.  The default permissions for this directory restrict the changing of documents to root.  

What's the preferred method of creating documents/folders in the /var/www/ directory?     Use "sudo" from the terminal everytime?  Change the default permission of the /var/www/ directory to include my user?  Something else?

Lemme know, thanks!

---

### Post by po0f on 2007-03-11
atraeyu,

I usually add users I would like to be able to write to this folder to the '**www-data**' group (I believe that's apache's default group), then change the group owning /var/www to www-data and include write permission for the group:

```
$ sudo gpasswd -a <user> www-data
$ sudo chgrp -R www-data /var/www
$ sudo chmod -R g+w /var/www
```

The first command adds <user> to the www-data group.  The second command recursively changes group ownership of /var/www to www-data.  And the third command recursively adds group write permission to /var/www.

Note that if any users you added to www-data were logged in when you added them, they will have to log out and re-login for their membership to take effect.

HTH

---

### Post by atraeyu on 2007-03-11
Interesting.  I went to System->Administration->Users and Groups.  This brings up the "User Settings" window - from there I clicked on the "Manage Groups" button.  This brings up the "Groups Settings" window.  In this - I don't see a group named "www-data" ... 

So then I navigated in gnome to the /var/www/ directory, right clicked it, and selected properties the owner is "root" and the group is "root."  

Not sure what to do ... :)

---

### Post by po0f on 2007-03-11
atraeyu,

Just enter the commands I posted in a terminal (Applications->Accessories->Terminal).  The dollar sign represents your terminal prompt (usually "user@host:directory$") and is *not* part of the command.

---

### Post by harrisupstate on 2007-03-11
Hi,

I was in the exact same situation as you, wondering the same thing....  one Ubuntu guide (I think it might've been ubuntuguide.org, which is excellent) was talking about changing a particular settings file that specified "Document Root" as being /var/www.  I think I tried that, and it didn't work, so I kept searching for an answer.

I found one site that suggested doing a "chown" on that directory to change the owner to my particular userID.  That worked, and now I'm happily editing PHP files directly in that location.

I'm not aware of any downsides to this technique, so if anyone knows of any, I'd love to hear about 'em.  Just wanted to share that this has worked well for me.

Harris

---

### Post by po0f on 2007-03-11
harrisupstate,

Your solution works for one user (yourself).  My solution works for whoever is in the www-data group.  ;)

---

### Post by Gerard Barberi on 2007-03-11
> **atraeyu said:**
> Interesting.  I went to System->Administration->Users and Groups.  This brings up the "User Settings" window - from there I clicked on the "Manage Groups" button.  This brings up the "Groups Settings" window.  In this - I don't see a group named "www-data" ... 

So then I navigated in gnome to the /var/www/ directory, right clicked it, and selected properties the owner is "root" and the group is "root."  

Not sure what to do ... :)

I can't remember where right now, but there is a selection "to view all groups" and "all users".  

did you select that?

---

### Post by atraeyu on 2007-03-11
> **Gerard Barberi said:**
> I can't remember where right now, but there is a selection "to view all groups" and "all users".  

did you select that?

I looked for this, but I don't see it anywhere ...

---

### Post by po0f on 2007-03-11
atraeyu,

Is there any reason you aren't running those commands from the command line instead?  You could have been done with this an hour ago.  ;)

---

### Post by atraeyu on 2007-03-11
> **po0f said:**
> atraeyu,

Is there any reason you aren't running those commands from the command line instead?  You could have been done with this an hour ago.  ;)

Yeah, sorry.  I read your instructions first - and they make sense.  

However ... the www-data group either doesn't exist or isn't being displayed by the Users & Groups tool.  If it's just not being displayed, I'd like to display it and so that I know it's the right group.  If it doesn't exist, then I could create it and set myself to the group and set the /var/www/ directory to have read/write privileges by the www-data group ...

But - then I read the second set of instructions that said to simply said to change ownership from root to my account, which was easier.  I did that and it worked, but obviously it won't work if I want to setup more users with their own directories for access.  But it's easy to undo, so I'm going to stick with it right now, until I understand a few more things.

Do the permissions need to be set a certain way for the server applications to function correctly?  If I used "www-group" instead of "www-data" would it matter?  If so, what applications rely on permissions and for what purposes?

---

### Post by po0f on 2007-03-11
atraeyu,

Run `**grep www-data /etc/group**` from a terminal to see if the group is available.  It should be; I don't have a web server installed at the moment, but this group is available on my system.  Something like the following should appear in the terminal:

```
$ **grep www-data /etc/group**
www-data:x:33:
$

```

If you want to use "www-group" as a group name, you'll have to create a new group for it.  That's why I suggested just adding users to the already existing www-data instead.

[EDIT]

Added sample output.

---

### Post by atraeyu on 2007-03-11
Interesting: I did a more /etc/group and I see all the different entries here.  So I did the grep www-data /etc/group and it found: "www-data:x:33:" ... looks like it is present ... what is the significance of the "x" and the "33"?

And ... I don't see www-data has permission to the /var/www/ folder.  Is there a way to check that?

---

### Post by atraeyu on 2007-03-11
Ooops, just reread your first post.  I see that I need to set the permissions.

---

### Post by DaveyG on 2007-03-11
> **po0f said:**
> atraeyu,

I usually add users I would like to be able to write to this folder to the '**www-data**' group (I believe that's apache's default group), then change the group owning /var/www to www-data and include write permission for the group:

```
$ sudo gpasswd -a <user> www-data
$ sudo chgrp -R www-data /var/www
$ sudo chmod -R g+w /var/www
```

The first command adds <user> to the www-data group.  The second command recursively changes group ownership of /var/www to www-data.  And the third command recursively adds group write permission to /var/www.

Note that if any users you added to www-data were logged in when you added them, they will have to log out and re-login for their membership to take effect.

HTH

Id just like to say a thank you for posting this.. iv been going on all night about it, you`v saved me from smashing the crap out of my server.. :lolflag:

---

### Post by po0f on 2007-03-11
atraeyu,

From `**man group**`:

> There is one entry per line, and each line has the format:

              group_name:passwd:GID:user_list

The '**x**' is the password for the group.  Well, actually, it means the password is encrypted.  This is so someone won't be able to just look at the file and get all your passwords.  The '**33**' is the GID, or Group ID, number.

To check the permissions for /var/www, run this from the terminal:

```
$ **ls -ld /var/www**
drwxr-xr-x 16 root **[color=red]root[/color]** 4.0K 2007-03-06 21:22 /var/www

```

The bold, red field is the group that owns the folder.

---

### Post by po0f on 2007-03-11
Davey Goudou,

Glad I could help you.  :)

---

### Post by atraeyu on 2007-03-11
Awesome, thank you so much man.  You got me all sorted out. :)

---

### Post by atraeyu on 2007-03-12
Ugh, sorry - another question.

If you check [www.webdroid.net](www.webdroid.net) you'll see a 403 Forbidden Error for the index.html file.

I created the file in gnome.  The default permissions were set as:
Owner: atraeyu
Group: atraeyu
Others: none

I manually set them to:
Owner: atraeyu
Group: www-data
Others: read only

But I still have the same problem.  Any ideas?  Thanks.

---

### Post by atraeyu on 2007-03-12
Sorry, my bad.  I hadn't set the www-data group to have read access.
Is there a way to change the default permissions of files in the /var/www/ directory ... so that when I create them they will be correct?

---

### Post by Penguin Power on 2007-03-12
I'd say the simplest solution is to simply "chown" the /var/www directory.

This will change the owership of the file, rather than altering permissions.

open a terminal and type:

$ sudo chown -R sean:sean /var/www

that should do the trick afaik - but don't go chowning any old directory you feel like from now on, it can break your system - in my younger days (like... a month ago) i chowned /var/ and had to do a reinstall ;)

edit: and from there you can right click on /var/www in nautilus and alter the permissions of the file, and note that the "-R" part of that chown command will apply the settings recursively, to all files and folders within /var/www

---

### Post by po0f on 2007-03-12
atraeyu,

Is root the owner and www-data the group for /var/www?  Just double-check; look at the output of the following command (example output shown):

```
$ ls -ld /var/www
drwxr-xr-x 16 **root www-data** 4.0K 2007-03-06 21:22 /var/www
```

If you notice, group doesn't have write permission (hypothetically; this directory doesn't exist on my box, I made the example up).  That was the reason for the **chmod** command I posted.  Just to be sure, execute the following after making sure that www-data is the group associated with /var/www:

```
$ sudo chmod 775 /var/www
```

This command will make sure that the "user" and "group" has full permissions (read, write, and execute) permission for /var/www , and "other" has read and execute permission.  I don't suggest arbitrarily giving all the files execute permission as well, so just recreate any files that are already in /var/www.

---

### Post by az on 2007-03-12
From what I gather, it is desirable for the webserver to only have read priviledges to what it needs to read and only have write privs for what it would need to write.

If you are hosting several different sites on the same server, and someone made a script to compromise the web server (or php) then the dammage would be less if apache was not able to write to much of the filesystem, including /var/www, where it could compromise the other websites hosted there.

The fact that apache runs as www-data and the /var/www directory is owned by root is inconvenient, but is more secure than granting rights willy-nilly.

---

### Post by cje on 2007-03-17
I found this thread very interesting as I have the same case. 
On the other side I really see the concerns of az. 

My case is linked to this error message: 
Alert: Cannot create file config.inc.php!
The webserver needs the permission to write the file config.inc.php .....

What is the easiest way for me to assign writing privileges to the web server for this specific file or folder?

---

### Post by az on 2007-03-17
> **cje said:**
> 
What is the easiest way for me to assign writing privileges to the web server for this specific file or folder?

Use whatever filemanager you want to temporarily change the permissions of the file.

(sudo nautilus)

It's the same when you use a hosting provider.  You upload your website contents via FTP and it may ask you to temporarily allow it to write to a settings file during the install process.  You then change the permissions back so that your site is not left insecure.

Your web application documentation should specify exactly what it needs to be able to write to.  Usually, it only needs to be able to write to a single folder to hold uploaded documents, for example.

---

### Post by cje on 2007-03-18
actually, i've already done that; given root (and www-data) writing privileges for this particular file with the gksudo nautilus command - but it didn't change the error message ....

---

### Post by az on 2007-03-18
Do you have the right directory?  Is the directory writeable?

---

### Post by PhillyB on 2007-03-18
> **po0f said:**
> atraeyu,

I usually add users I would like to be able to write to this folder to the '**www-data**' group (I believe that's apache's default group), then change the group owning /var/www to www-data and include write permission for the group:

```
$ sudo gpasswd -a <user> www-data
$ sudo chgrp -R www-data /var/www
$ sudo chmod -R g+w /var/www
```


HTH


Total newb here, so the <user> is a substitute for my username?  

If I wanted to post up links to files on the website can I put a folder in the var/www folder with windows files that people can download?

This allows for apache to read write what it wants?  I dont want people changing anything just being able to write to the database and post to the chatbox, etc.  I am trying to run something similar to this software 

[https://www.nerdclub.net/alp/test/index.php](https://www.nerdclub.net/alp/test/index.php)

on my server.  I got it running on that other OS but I am loving this Ubuntu stuff!

---

### Post by cje on 2007-03-19
> **az said:**
> Do you have the right directory?  Is the directory writeable?

I think so, I've assigned write permission for the whole directory tree under the www folder (not to var and www).

---

### Post by cje on 2007-03-19
> **az said:**
> Do you have the right directory?  Is the directory writeable?

Sorry, I thought all directories was writeable - but they weren't. Now they are - and everything works fine. Thanks for your help.

---

