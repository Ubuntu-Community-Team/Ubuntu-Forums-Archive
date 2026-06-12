---
title: "Add a password to a folder?"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-03-12
How do I add a password to a folder?

---

### Post by markjensen on 2008-03-12
Password to what folder?  Inside your home?

I would use account separation to create a "passworded" access, I guess.   Under my account, I trust me.   My screensaver locks and requires a password.  My kids aren't going to get in and mess with my settings, or get access to anything.

Would creating an account, maybe called "locked" even removing login priveleges by removing the shell field work for your situation?   You could "su locked" to gain acess to data stored there.

---

### Post by Tom--d on 2008-03-12
Yes, its under home.

---

### Post by wednesday allfather on 2008-03-12
Tricky wording...

If you want to restrict access to a certain area with a password, I would use the chown or chmod commands.

Decide what folder you want to protect and change the ownership to "root"

```
sudo chown -R root:root /path/to/your/folder
```

Now only a user that has access to the root password (well, sudo password to be correct) can open that folder.  If someone gains root access to your comp, you will have bigger fish to fry anyway.  

If you want more info on this topic, try searching for encryption software (if you are very paranoid about this folder) or google CHOWN or CHMOD.  

There are many ways to go about doing what I can only assume you want to do.  

Hopefully, that answers your question.

---

### Post by markjensen on 2008-03-12
I don't know of any tools to password protect something that you already had to enter your user credentials to get access to.  In essense hiding it from yourself.

Can you move it to another special-purpose user, and use the built-in unix user permissions to deny access without password?  Sort of like connecting to a network share with a password - just locally.

If not, then maybe someone here knows of tools to lock you out of your own directories...

---

### Post by Tom--d on 2008-03-12
If I give the folder root access.. could I change things in that folder.. eg.. add stuff and delete/move things?

---

### Post by Tom--d on 2008-03-12
> **markjensen said:**
> I don't know of any tools to password protect something that you already had to enter your user credentials to get access to.  In essense hiding it from yourself.

Can you move it to another special-purpose user, and use the built-in unix user permissions to deny access without password?  Sort of like connecting to a network share with a password - just locally.

If not, then maybe someone here knows of tools to lock you out of your own directories...

Yeah.. I can move the folder any where... 

All i want is, when you click on it.. it says password needed to enter. something like that

---

### Post by scramasax on 2008-03-12
> **Tom--d said:**
> Yes, its under home.

If this is just about protecting a folder from other users on the machine, you'd use permissions.  See my response in the earlier thread "Any user can access my home folder... why?" on this page:

[http://ubuntuforums.org/showthread.php?t=722081](http://ubuntuforums.org/showthread.php?t=722081)

Set permissions on the folder in question to 700.

If this is about securing some more cast-iron level of protection, then you really need to encrypt the folder.  I suppose you could use GNUPG or something like TrueCrypt.

---

### Post by Golem XIV on 2008-03-12
You can try [TrueCrypt]("http://www.truecrypt.org/").  it lets you create an encrypted "file" which is in fact a container for files/folders that you want to keep away from prying eyes.

---

### Post by Tom--d on 2008-03-12
> **wednesday allfather said:**
> Tricky wording...

If you want to restrict access to a certain area with a password, I would use the chown or chmod commands.

Decide what folder you want to protect and change the ownership to "root"

```
sudo chown -R root:root /path/to/your/folder
```

Now only a user that has access to the root password (well, sudo password to be correct) can open that folder.  If someone gains root access to your comp, you will have bigger fish to fry anyway.  

If you want more info on this topic, try searching for encryption software (if you are very paranoid about this folder) or google CHOWN or CHMOD.  

There are many ways to go about doing what I can only assume you want to do.  

Hopefully, that answers your question.

```
sudo chown -R root:root /path/to/your/folder
```

Never work. I can still open the folder without a password needed to enter it. 


What about encrypt the folder? Is that possible? and I need it to prompt me the password even if I'm logged in.

---

### Post by Martje_001 on 2008-03-12
Then you have to install TrueCrypt as mentioned above. It will create an encrypted file on your hard-disk, which you can mount.

---

### Post by scramasax on 2008-03-12
> **Martje_001 said:**
> Then you have to install TrueCrypt as mentioned above. It will create an encrypted file on your hard-disk, which you can mount.

Although GNUPG (or GPG for short) is already included in the standard distribution.  Most often, of course, it's used for public/private key email signing/encryption, but you can also encrypt files with it.

I haven't done it, but apparently the command is gpg --clearsign.

[http://blogs.techrepublic.com.com/opensource/?p=165](http://blogs.techrepublic.com.com/opensource/?p=165)

---

### Post by wednesday allfather on 2008-03-12
I didn't realize you were wanting to protect it during your session.  Building a reactor, are ya?  :)

Sorry to misinform.  I'd check out Truecrypt.  Good luck and happy Linuxing.

---

### Post by scorp123 on 2008-03-12
> **Tom--d said:**
>  ```
sudo chown -R root:root /path/to/your/folder
```
Never work. I can still open the folder without a password needed to enter it.  Of course. Changing the owner alone without changing the permissions won't help.

> **Tom--d said:**
>  and I need it to prompt me the password even if I'm logged in.  What is it that you want to achieve?? Can you please explain in more details?

There are various things you could do.

1. It's your computer, right? So make sure everybody has their own account.

2. Restrict the permissions on the folder. Please read here first:
[http://en.wikipedia.org/wiki/File_system_permissions#Notation_of_traditional_Unix_permissions](http://en.wikipedia.org/wiki/File_system_permissions#Notation_of_traditional_Unix_permissions)

So a folder with permissions "rwx r-x r-x" is writable only by you, but it can be accessed and its contents can be read from by everyone else too. To change that:
```
chmod 700 /path/to/folder/in/question
``` ... Now the permissions should read "rwx --- ---" which means everybody else not being you is locked out and gets a "Permission denied" message if they try to access the folder.

So as long as nobody else has your username + password and for as long as nobody else has "root" access (e.g. via sudo?) you are the only one who can go into this folder.

For a 'normal' home user or a corporate environment this should be enough. HOWEVER: This does not protect your data in anyway ... Anyone with physical access to the computer could still easily make their way to the files in that folder if they know how.

It all really depends on what you want.


3. If restricting file permissions on that folder is not enough you can try something else, e.g. encrypting the folder. Somebody further up already mentioned TrueCrypt ... that's good stuff. You can try that. Or I myself use **encfs** .... A tutorial can be found here:
[http://ubuntuforums.org/showthread.php?t=148600](http://ubuntuforums.org/showthread.php?t=148600)

---

### Post by Tom--d on 2008-03-12
mm...

Its not that important.. I could just hide the folder. I think that might do the trick!

---

### Post by scorp123 on 2008-03-12
> **Tom--d said:**
>  I could just hide the folder. I think that might do the trick! "hide" the folder? How? By putting a dot in front of its name? Forget that. That doesn't stop anything or anyone from accessing the content. What you need here are proper file permissions. You can do this in the file manager too if the shell command above was a bit too intimidating for you, e.g. open Nautilus via **Places > Home Folder** ... and then right-click on the folder in question and select **Properties** ... A new pop-up window should have opened. Go to the **Permissions** tab ... And here you make sure that it says **"Owner -- create and delete files"** and that for the the following two categories (**Group + Other**) it says **"None"**. Voila. Nobody can get into the folder anymore unless he's logged in as you (which would require them to know your username and your password).

---

### Post by kevdog on 2008-03-14
Have you read this article, this kind of sums up the available encryption methods that Iknow about.
[http://www.movingtofreedom.org/2007/02/21/howto-encfs-encrypted-file-system-in-ubuntu-and-fedora-gnu-linux/](http://www.movingtofreedom.org/2007/02/21/howto-encfs-encrypted-file-system-in-ubuntu-and-fedora-gnu-linux/)

---

### Post by Psyphre on 2008-03-18
Guys i think its obvious what he wants.

For example:
He has a folder full of ummm.. "private" material... which he doesnt want people to see. (e.g adult movies). He basically wants it password protected so when you click on the folder in the file browser it requires a password to enter. So if he's logged in as his account and a friend walks in and asks to borrow the pc for a while, he can leave without being paranoid that guy mite try and open his secret folder. 

No fancy multiple user permissions, no mounting encryptions, he just wants a put a password on a folder.

---

### Post by scorp123 on 2008-03-18
> **Psyphre said:**
>  He has a folder full of ummm.. "private" material... which he doesnt want people to see. (e.g adult movies).  We are not stupid. :)  ... That's why I suggested **encfs** .... It's dman (yes, I know) easy to use and it just works ... and keeps all those curious eyeballs away. 

Sometimes it's not necessary to state the obvious. The obvious speaks for itself ;)

---

### Post by Martje_001 on 2008-03-18
> **Psyphre said:**
> No fancy multiple user permissions, no mounting encryptions, he just wants a put a password on a folder.
Without encryption this CANNOT be done. You will alway be able to read it from the live-cd.

Hardy will support this however. It will make encrypted virtual folders, which you can (thanks to the new gnome-filesystem), open and close with nautilus.

---

### Post by Psyphre on 2008-03-19
> **scorp123 said:**
> We are not stupid. :)  ... That's why I suggested **encfs** .... It's dman (yes, I know) easy to use and it just works ... and keeps all those curious eyeballs away. 

Sometimes it's not necessary to state the obvious. The obvious speaks for itself ;)

> **Martje_001 said:**
> Without encryption this CANNOT be done. You will alway be able to read it from the live-cd.

Hardy will support this however. It will make encrypted virtual folders, which you can (thanks to the new gnome-filesystem), open and close with nautilus.

Lol yes true it was obvious. But wat i was trying to make clear was not wat he was hiding, rather how he wanted to hide it. I remember when i used to use windows there was an app i downloaded that could add a pasword to a folder. So everytime you wanted to access it, it prompted you for a password.

In my experience (and correct me if im wrong) when ive tried using encryption methods, you have to mount/unmount which is alot of hassle. Even if you dont have to mount/unmount it only asks for your password once (to decrypt), and never asks again until you encrypt it again.

The new hardy feature sounds really interesting. Cant wait for hardy's many new features :D

---

