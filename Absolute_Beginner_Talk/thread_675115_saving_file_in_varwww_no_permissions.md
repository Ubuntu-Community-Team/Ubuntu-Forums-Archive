---
title: "saving file in /var/www no permissions"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by ben22 on 2008-01-22
tried to save a file in /var/www/ - but it says that it does not have correct permissions.

now i tried **chmod 755 /var/www** - but problem persists.

What do I have to do to save files in the www folder so that they can be accessed via [http://localhost?](http://localhost?)

---

### Post by philc on 2008-01-22
Change ownership permissions on this directory.

In a Terminal window type:

sudo chown yourusername /var/www
sudo chgrp yourusername /var/www

Enter your password when requested.

This should fix it, although someone else may know a better way.

---

### Post by PeterJS on 2008-01-22
Who is the owner and group of /var/www/? 755 means that the owner can read, write and execute, the group can read and execute, and everyone else can read and execute.

---

### Post by ben22 on 2008-01-22
I am the only one using the machine. I want to store my php files and see the effects

---

### Post by PeterJS on 2008-01-22
Just because there is only one human user on the machine does not mean that there is only one user account that can own files. Phillc suggested a solution, and I offered a roundabout explaination of what's going on.

---

### Post by p_quarles on 2008-01-22
Leave it the way it is currently, and move files to the Apache document root using root privileges. Either:
```
gksudo nautilus
```
for a root graphical file manager, or
```
sudo cp file.php /var/www
```

---

### Post by ben22 on 2008-01-22
@philc

your hint worked, thanks, dude

[B]Change ownership permissions on this directory.

In a Terminal window type:

sudo chown yourusername /var/www
sudo chgrp yourusername /var/www

Enter your password when requested.[/B]

[I also have a problem with phpmyadmin]("http://ubuntuforums.org/showthread.php?t=675117") - I linked to the thread

---

### Post by philc on 2008-01-22
Just keep in mind that you are now the owner of this directory. It might cause issues later.

It may be the case that your Apache user (probably www-data) needs to be the owner of this directory and files within it for some applications.

If this is the case, change owner (chown) and group (chgrp) on the directory again using the commands you already know.

Then follow p_quarles advice on how to save files in the directory. These files will then be owned by root user. So you will need to change the ownership permissions (chown and chgrp) on the specific files to www-data.

---

### Post by jd65pl on 2008-01-22
I think you should leave the permissions as they are and make a symbolic link to the directory you want served. So I have my website in a folder called public_html in my home directory and I want it served as a web page so I link to this folder and it works.

```
sudo ln -s /var/www/myweb /home/user/public_html
```

---

### Post by rosegarden78 on 2008-01-22
You should consider using a GUI to solve the problem.  From a terminal or by pressing Alt-F2 type either command:

gksudo nautilus
kdesu konqueror

This will launch a file browser in root mode or superuser.  Navigate to the file in question.  Right-click Properties and look for permissions.  You should see a drop-down menu with  a list of possible owners.  Or type in the box your login name.  You can also do this to a folder and it's sub-directories last time I checked.  You can even save these commands as launchers or icons on your desktop.  I had the same issue using Apache for the first time.  Good news is:  All computers running Apache on your wireless or home network can communicate with each other by typing the ip address.  ie.  192.168.#.#  That's one way to have wireless file sharing.

---

### Post by proxpero on 2008-01-22
> **philc said:**
> Just keep in mind that you are now the owner of this directory. It might cause issues later.

It may be the case that your Apache user (probably www-data) needs to be the owner of this directory and files within it for some applications.


How can I find out for sure whether 'www-data' is the Apache user? (In case I need to restore ownership)  Thanks in advance.

---

### Post by PeterJS on 2008-01-22
> **proxpero said:**
> How can I find out for sure whether 'www-data' is the Apache user? (In case I need to restore ownership)  Thanks in advance.
Try:
```

ps aux | grep apache

```
The far left column is the username.

---

### Post by jd65pl on 2008-01-22
These 'GUI' methods people are providing are not good. You should follow the solution I provided and use a directory in your home folder or somewhere where you do naturally have permissions.

You will still be able to use the folder through nautilus or what ever interface you require, you will only need to create a symlink to the folder, you will spend alot less time on CLI with my method also it is much safer.

---

### Post by p_quarles on 2008-01-22
> **jd65pl said:**
> These 'GUI' methods people are providing are not good. You should follow the solution I provided and use a directory in your home folder or somewhere where you do naturally have permissions.

You will still be able to use the folder through nautilus or what ever interface you require, you will only need to create a symlink to the folder, you will spend alot less time on CLI with my method also it is much safer.
Evidence? 

First off, symbolic links don't have separate permissions from the target, so if that method is working for you, it's because your user has write permissions to /var/www. Second, there is no reason to believe that using a root graphical file manager is any less "secure" than any other method of managing that folder.

---

### Post by jd65pl on 2008-01-22
1. The owner of /var/www is root 
2. The owner of the ln -s is root
3. The permissions of ln -s do not need to be the same as the target
4. I start using nautilus as root, then forget I am using it as root and accidently delete things I don't understand or accidently delete something.

Edit.
Its also much easier to develop your site with it located in a convenient place such as ~ no copying and pasting files over, or starting gksudo nautilus every time you want to make a change.

---

### Post by p_quarles on 2008-01-22
The permissions on a symlink are essentially meaningless. Root may be the owner of /var/www/, but I'm guessing the permissions are set to 777, which would allow any user to write to it. If I'm wrong about the permissions, let me know.

As for point 4, that could easily be solved by not deleting things unless you're sure what they are.

---

### Post by jd65pl on 2008-01-22
Permissions of:

755 /var/
755 /var/www/


Both with the owner root. Try yourself it works and as I see it a much more convenient and a practical solution rather than a work around.

IMHO, everyone is can have their own idea of the best way to solve the problem i guess :)

I think my main point here is, if you have a multi user system with each user wanting to serve a site then adding a symlink to the users public_html is the better solution to providing all access to /var/www where they can mess up other peoples sites.

---

### Post by philc on 2008-01-22
> **jd65pl said:**
> 
I think my main point here is, if you have a multi user system with each user wanting to serve a site then adding a symlink to the users public_html is the better solution to providing all access to /var/www where they can mess up other peoples sites.

I have used this method myself in the past and it works quite well, but I also found that when using symbolic links I need to edit the file /etc/apache2/sites-available/default with something like the following:

<Directory /www/sitename>
  Options FollowSymLinks
</Directory>

---

### Post by ben22 on 2008-01-22
> **jd65pl said:**
> I think you should leave the permissions as they are and make a symbolic link to the directory you want served. So I have my website in a folder called public_html in my home directory and I want it served as a web page so I link to this folder and it works.

```
sudo ln -s /var/www/myweb /home/user/public_html
```

This sounds like a great idea - but I cannot create any folder in the www folder.

Can you please post exact steps what I have to do? I am a total rookie ;)

1. I created a directory in home folder and also called it public_html
2. cannot create a folder in www - change permissions???

---

### Post by sitmex on 2008-01-22
> **jd65pl said:**
> I think you should leave the permissions as they are and make a symbolic link to the directory you want served. So I have my website in a folder called public_html in my home directory and I want it served as a web page so I link to this folder and it works.

```
sudo ln -s /var/www/myweb /home/user/public_html
```

Thanks, for this one, I consider to be the "safer" solution to the problem, I also the only user in this box, so I've decided to go with this one. Thanks again.

Cheers, Oscar

---

### Post by ben22 on 2008-01-22
I cannot create a folder in /www 

What are the exact steps? 

I did:

1) create public_html folder in /home

2) ??? how do I create the folder in /www - what do I have to consider permission wise??

---

### Post by jd65pl on 2008-01-23
[LIST]
[*]Make a folder in your home folder called public_html
[*]Now go to the terminal and do the following exchanging USER for your user name and MYWEB for whatever you want your web to be called[/LIST]```
sudo ln -s /home/USER/public_html /var/www/MYWEB
```[LIST]
[*]Now go to your public_html file and create a file called index.html
[*]In the file put a line that says "Just to check it works!" or something
[*]Open your web browser and navigate to localhost
[*]You should see a folder with the name of your web click on it
[*]The browser should show the page we made earlier if it doesn't post back![/LIST]J

---

### Post by ben22 on 2008-01-23
I followed your instructrions, but it's not working. 

[LIST]
[*]the public_html folder it shows the link to myweb, but it says it is broken

[*]var/www does not contain the myweb folder

[*]when I create the myweb folder manually, it's not working either
[/LIST]

[B]ls --lcontext /var/www produces:
total 12
drwxr-xr-x 2 root root 4096 2008-01-22 19:20 apache2-default
drwxr-xr-x 2 ben2 ben2 4096 2008-01-23 11:59 myweb
lrwxrwxrwx 1 root root   21 2008-01-22 23:58 phpmyadmin -> /usr/share/phpmyadmin
-rw-r--r-- 1 ben2 ben2   68 2008-01-22 20:03 test.php
[/B]

---

### Post by jd65pl on 2008-01-23
Can you remove the folder you created, it should be a link not a folder:

```
sudo rm /var/www/myweb
```Then recreate the link

```
sudo ln -s /home/USER/public_html  /var/www/myweb/
```

---

### Post by ben22 on 2008-01-23
> **jd65pl said:**
> Can you remove the folder you created, it should be a link not a folder:

```
sudo rm /var/www/myweb
```



it worked with ```
sudo rmdir /var/www/myweb
```


Then recreate the link

```
sudo ln -s /home/USER/public_html  /var/www/myweb/
```

it worked wit ```
sudo ln -s /home/USER/public_html  /var/www/myweb
``` no **/** at the end

---

### Post by ben22 on 2008-01-23
Problem solved. Thx to everybody

---

### Post by az on 2008-01-23
> **philc said:**
> 
It may be the case that your Apache user (probably www-data) needs to be the owner of this directory and files within it for some applications.


Apache should not own, nor be able to write to the files it is serving.  When you use Php with apache (or any other scripting language) to run scripts, you introduce a vulnerability of allowing a remote user to run scripts on your computer.  Keeping the directory as locked-down as you can (for example, only allowing apache to write to very specific files/directories) is best-practice.

---

### Post by razordead on 2008-02-09
Wouldn't it be better to use Apache's built-in user directory support? Just make symlinks in /etc/apache2/mods-enabled to ../mods-available/userdir.load & ../mods-available/userdir.conf .
Then restart Apache & /home/username/public_html will be accessible as [http://localhost/~username/](http://localhost/~username/) .

---

### Post by jd65pl on 2008-02-10
It would but at least what was provided gave the poster a place to start if you read through the thread there was alot of conflicting advice given and I wanted to keep mine simple

;)

J

---

### Post by UberKnight on 2008-03-08
Razordead, would you please explain this in more detail?

> Wouldn't it be better to use Apache's built-in user directory support? Just make symlinks in /etc/apache2/mods-enabled to ../mods-available/userdir.load & ../mods-available/userdir.conf .
Then restart Apache & /home/username/public_html will be accessible as [http://localhost/~username/](http://localhost/~username/)

Thanks!

---

