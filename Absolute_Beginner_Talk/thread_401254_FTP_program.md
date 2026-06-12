---
title: "FTP program ?"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Winterdream on 2007-04-04
I need an FTP program.  I went to Applications - Add/Remove Applications and searched for FTP.  It showed "gFTP" but when I clicked the checkbox, a message pops up that says:
> 'gftp-gtk' is not available in any software channel.  
The application might not support your system architecture

It's the only FTP program that showed up.  Could someone please tell me if there's a way to get this program or is there another FTP program?  I'm hoping to find something like WS_FTP.

Thanks for any advice!

---

### Post by Maestro23 on 2007-04-04
Check here: [http://linuxappfinder.com/internetandnetworking/ftpclients](http://linuxappfinder.com/internetandnetworking/ftpclients)

Then see what is available in the Ubuntu Repositories.

Good luck.

---

### Post by Bachstelze on 2007-04-04
Forget the "Add-Remove"-thing, open a terminal and do :

```
sudo apt-get install gftp
```

---

### Post by StifflerNewb on 2007-04-04
is gui really important for you? if not I'd say pftp is a really good client.

---

### Post by Winterdream on 2007-04-04
Thank you for the reply!  :) 

> **HymnToLife said:**
> Forget the "Add-Remove"-thing, open a terminal and do :

```
sudo apt-get install gftp
```

That results in:
> E: Couldn't find package gftp


I suspect I'm missing something important here, did I skip a step?  :confused:

---

### Post by Bachstelze on 2007-04-04
You need the Universe repo enabled :

```
sudo nano /etc/apt/sources.list
```

You'll have two lines beginning with '#deb' and ending with 'universe', for example :

```
#deb http://archive.ubuntu.com/ubuntu edgy universe
#deb-src http://archive.ubuntu.com/ubuntu edgy universe
```

Just remove the # on both lines, save the file (Ctrl+O, Enter to confirm), exit nano (Ctrl+X) and do

```
sudo apt-get update
sudo apt-get install gftp
```

---

### Post by Winterdream on 2007-04-04
Thank you!

> **Maestro23 said:**
> Check here: [http://linuxappfinder.com/internetandnetworking/ftpclients](http://linuxappfinder.com/internetandnetworking/ftpclients)

Then see what is available in the Ubuntu Repositories.

Good luck.

I don't know how to use the Repositories!  I think that's what I need to learn now.  :)

---

### Post by Kobalt on 2007-04-04
Here is a good place to start learning : [https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

---

### Post by Winterdream on 2007-04-04
> **HymnToLife said:**
> You need the Universe repo enabled :


I followed every step successfully until this:

```
sudo apt-get install gftp
```

That resulted in this:
> 
 sudo apt-get install gftp
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gftp: Depends: gftp-gtk (= 2.0.18-11ubuntu1) but it is not installable
        Depends: gftp-text (= 2.0.18-11ubuntu1) but it is not going to be installed
E: Broken packages

So I guess I should I look for another FTP program?

Also, is there someplace where I could get a listing of the commands and their functions for the terminal?  I need a "cheatsheet"!  ;) 

Many thanks!

---

### Post by jhenager on 2007-04-04
> **Winterdream said:**
> I followed every step successfully until this:

```
sudo apt-get install gftp
```

That resulted in this:


So I guess I should I look for another FTP program?

Also, is there someplace where I could get a listing of the commands and their functions for the terminal?  I need a "cheatsheet"!  ;) 

Many thanks!

[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

Also, ftp is available from the command line.
ftp *server*
Ftp another machine. (There is also ncftp which adds extra features and gftp for GUI .) Ftp is good for copying files to/from a remote machine. Try user "anonymous" if you don't have an account on the remote server. After connection, use "?" to see the list of available ftp commands.  The essential ftp command are: ls (see the files on the remote system), ASCII, binary (set the file transfer mode to either text or binary, important that you select the proper one ), get (copy a file from the remote system to the local system), mget (get many files at once), put (copy a file from the local system to the remote system), mput (put many files at once), bye (disconnect). For automation in a script, you may want to use ncftpput and ncftpget, for example:
ncftpput -u my_user_name -p my_password -a remote.host.domain remote_dir *local.html

---

### Post by JayTheHun on 2007-04-04
I used the Firefox add-on called "FireFTP."  Works great.  Once installed and you restart the browser, it shows up under your Firefox Tools menu.

---

### Post by mcduck on 2007-04-04
Gnome also has it's built-in FTP support. Just go to Places/Connect to Server to create your connection and you'll get icon for it on your desktop. Then you can navigate FTP just like local directories using Nautilus :)

I love being able to just drag&drop files to icon on my desktop to upload them to my web site ;)

---

### Post by Irony on 2007-04-04
Here's my /etc/apt/sources.list for Dapper gftp and dependencies must be in there somewhere;

[PHP]deb http://gb.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse[/PHP]

Although I have gftp I prefer to use Nautilus's inbuilt connect to server system - simply open up nautilus then go to File > Connect to Server. I find Nautilus handles batches of files better than gftp.

Connect to server doesn't work in Edgy.

---

### Post by Winterdream on 2007-04-04
> **mcduck said:**
> Gnome also has it's built-in FTP support. Just go to Places/Connect to Server to create your connection and you'll get icon for it on your desktop. Then you can navigate FTP just like local directories using Nautilus :)

I love being able to just drag&drop files to icon on my desktop to upload them to my web site ;)

Thank you, that works !!  :) 

One question - when I close the File Browser window, does that end the connection to the server?  Or is there something else I have to do to close that connection?  I don't want to leave it open if I'm not using it.

This is wonderful !  :)

---

### Post by gh0st on 2007-04-04
You could install gftp and loads of other things besides pretty painlessly with Automatix you know. That may be overkill just to install an FTP client and Automatix isn't popular in some quarters because of the way it works but I have always found it very useful. Especially as a new user I found it made switching to Ubuntu much less painful.

Check it out here: [http://www.getautomatix.com/](http://www.getautomatix.com/)

It may not be the answer for you but I just thought it was worth a mention. 

Good luck :)

EDIT: I was pretty slow typing my reply and when I finished you'd posted saying the problem was sorted. I guess you can probably ignore me :)

---

### Post by Winterdream on 2007-04-04
> **gh0st said:**
> You could install gftp and loads of other things besides pretty painlessly with Automatix you know. That may be overkill just to install an FTP client and Automatix isn't popular in some quarters because of the way it works but I have always found it very useful. Especially as a new user I found it made switching to Ubuntu much less painful.

Check it out here: [http://www.getautomatix.com/](http://www.getautomatix.com/)


Thank you!  I was just wondering if there wasn't some way to use the Windows programs that I really depend on.  Automatix seems to have a lot of them covered.  It's bookmarked for later.
:)

---

### Post by Gina on 2007-04-04
Just Installed FireFTP - will look at it shortly.

Was writing to say it wouldn't install - but I've just checked the extensions and it's there - must have been so fast I didn't see it :lol:  So I've edited the post.

---

### Post by mcduck on 2007-04-06
> **Winterdream said:**
> Thank you, that works !!  :) 

One question - when I close the File Browser window, does that end the connection to the server?  Or is there something else I have to do to close that connection?  I don't want to leave it open if I'm not using it.

This is wonderful !  :)
I think the connection is kept open for some time after being used in case you'd use it again, and then after some idle time it's closed automatically.

---

### Post by Cariboo1938 on 2007-04-11
Hi all,
I need to use a FTP client to transfer a large file (>1GB) for error detection. I found this interesting thread and I read through it and I pretty much know what I would have to do to install it....except one issue which seems not to be covered here. 
**[COLOR="Magenta"]Does gFTP run on [/COLOR]**an Ubuntu **[COLOR="Magenta"]6.10_amd64 [/COLOR]**installation?

---

### Post by Bachstelze on 2007-04-11
Yep, it does.

---

