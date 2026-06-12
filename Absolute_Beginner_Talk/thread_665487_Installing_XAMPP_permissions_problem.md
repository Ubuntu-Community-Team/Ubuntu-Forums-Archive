---
title: "Installing XAMPP permissions problem"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by goMON on 2008-01-12
To install XAMPP, the XAMPP Tutorial told me to copy the LAMPP folder to opt, i tried to do so, but it says 'You do not have permissions to write to this folder.'
How do i change my permissions to copy the folder?

EDIT - I have now changed my Permissions to full control of everything..

---

### Post by goMON on 2008-01-12
Any help?

---

### Post by LinuxIsInnovation on 2008-01-12
> **goMON said:**
> Any help?

 Open terminal and type: 

```
$sudo nautilus
``` 
Try from there..

---

### Post by goMON on 2008-01-12
That puts me in my user area, but, i have to put it in Opt? :confused:

---

### Post by goMON on 2008-01-12
I've just copied the LAMPP folder to /home/richard/opt/lampp, and tried to run this in the Terminal:
```
/home/richard/opt/lampp/lampp start
```
But it says 'You have to start XAMPP in root!'..

So all thats left really, is to either somehow get logged in as root..
Or, change my permissions on this account i am using now..

Any help please?

---

### Post by Nepherte on 2008-01-12
You have to copy it to the /opt directory with the sudo command:

```
sudo cp <initial lampp directory> /opt
```

to start the lampp server you place sudo in front of the command again.

---

### Post by goMON on 2008-01-12
Thank you, it now asks me for '[sudo] password', is this my User Password? Plus, i tried typing it, but nothing shows up.

---

### Post by goMON on 2008-01-12
Hello?

---

### Post by Nepherte on 2008-01-12
Yes this is your user password. It is absolutely normal you don't 'see' the password you type, not even **. Just type the user password when asked for and hit the enter key.

---

### Post by Dr Small on 2008-01-12
Try this (taken from the XAMPP page):
```
sudo tar xvfz xampp-linux-1.6.5a.tar.gz -C /opt
```

---

### Post by Nepherte on 2008-01-12
A comprehensive guide has been written in the tutorial section of this forum:
[http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

---

### Post by goMON on 2008-01-12
Thank you for your replies, and I'm sorry for my rudeness..

I tried:
```
sudo tar xvfz xampp-linux-1.6.5a.tar.gz -C /opt
```
But it returned the following after typing my password:
```
tar: xampp-linux-1.6.5a.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
```

I then tried the code with the location of the .tar.gz file:
```
sudo tar xvfz /Desktop/xampp-linux-1.6.51.tar.gz -C /opt
```
But that then gave me the same response.

Anymore ideas? :lolflag:

---

### Post by goMON on 2008-01-12
Sorry, i didn't see Nepherte's post until after my last post, i am reading that article now, thank you :)

EDIT - Because i do not have much knowledge of the Terminal, in fact basically none, i have no idea how to do this...
It says:
> Extract the archive to /opt using sudo: (make sure you are in the directory that you downloaded the archive to)
```
sudo tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt
```

But, how do i get into the Desktop Directory? (Yes, the Desktop Directory is where i have the tar.gz file).
I have tried typing in:
```
dir Desktop
```
And then typing in:
```
sudo tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt
```

I have also tried doing that but hitting Enter after both:
```
dir Desktop
```
and
```
sudo tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt
```

But, all i get in return is:
```
tar: xampp-linux-1.5.3a.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
```

Could anyone help me please?

---

### Post by Dr Small on 2008-01-12
Try this, which will change directory to your Desktop,
```
cd /home/`whoami`/Desktop/
```

And then run the untar command:
```
sudo tar xvfz xampp-linux-1.6.5a.tar.gz -C /opt
```

Dr Small

---

### Post by goMON on 2008-01-12
Holy Shmoley, it's working!

Thank you to everyone who replied!!

---

### Post by goMON on 2008-01-12
MySQL does not Execute :confused:
I have Stopped ProFTPD thinking it was that, but it still doesn't work, i click Execute over and over again, but nothing..

---

### Post by Dr Small on 2008-01-12
Where are you clicking this??
To start XAMPP, run:
```
sudo /opt/lampp/lampp start
```

To only start MySQL, run:
```
sudo /opt/lampp/lampp startmysql
```

---

### Post by goMON on 2008-01-12
In Terminal i put:
```
gedit ~/.local/share/applications/xampp-control-panel.desktop
```
Then in the note file i put:
```
[Desktop Entry]
Comment=Start/Stop XAMPP
Name=XAMPP Control Panel
Exec=gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"
Icon[en_CA]=/usr/share/icons/Tango/scalable/devices/network-wired.svg
Encoding=UTF-8
Terminal=false
Name[en_CA]=XAMPP Control Panel
Comment[en_CA]=Start/Stop XAMPP
Type=Application
Icon=/usr/share/icons/Tango/scalable/devices/network-wired.svg
```
And saved that.
That then adds a Control Panel kind of thing to my Applications Menu.
Thats where i was clicking it..

When i put in that command you gave me, i get:
```
XAMPP: Another MySQL daemon is already running.
```

---

### Post by Dr Small on 2008-01-12
Are you sure that MySQL is not running then?
Have you tried going to:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin) ?

Dr Small

---

### Post by goMON on 2008-01-12
When i go to that link i get:
> #2002 - The server is not responding (or the local MySQL server's socket is not correctly configured).

In the control panel i have, it doesn't say its running, but in that error it doesn't say its not running...

---

### Post by Dr Small on 2008-01-12
Hmm. I don't know what to do about that.
Have you previously installed MySQL before ?

---

### Post by goMON on 2008-01-12
Not on Ubuntu.
Thank you for your help anyway, you've been a great help so far :D

---

### Post by dustman on 2008-01-13
i am also using XAMPP, but i had no trouble with it. Followed these instructions to get it working: [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html) . You have to copy XAMPP to /opt , and always have to run as root. That error message ```
XAMPP: Another MySQL daemon is already running.
``` could be from the fact that a program uses the port typically used by MySQL. I know i had trouble with Eclipse & Tomcat & Internet Browser. Tomcat was set to run on port 8080, but Firefox was already running and i got all sorts of errors, till i set Tomcat to run on 8081. And make sure you don't have MySQL previously installed :) . 

Cheers!

Radu

---

### Post by goMON on 2008-01-13
Thank you, i followed those instructions from the start, i just don't know much about the Terminal, and so i tried manually copying the files to /opt, and obviously it doesn't work because of permissions.

I will try the MySQL now, and shut down programs as i go if it doesn't work!

Thanks for the help guys!!

---

### Post by goMON on 2008-01-13
Does the Movie Player use a port? :lolflag:
I don't know hardly anything about Ubuntu.

I have nothing running, except the Movie Player, but I doubt it uses a port so left it running, and still that same error message:
```
XAMPP: Another MySQL daemon is already running.
```

---

### Post by dustman on 2008-01-13
you can see the running processes by again, opening a terminal, and entering: ```
ps -e
``` or for a detailed version:```
ps aux
``` You'll see a big list of running processes. Look in that list for MySQL process. You can do this by inputing: ```
ps -e | grep mysql
``` . The first column in the list that appears contains the PID's (process ID's). Let's suppose that the MySQL process that is already running has the PID: 1234. You can kill this process by inputing in a terminal: ```
kill -9 1234
``` if this returns and says something like "you don't have permissions bla bla" , input : ```
sudo kill -9 1234
```. Then start XAMPP, and MySQL should start fine.

---

### Post by goMON on 2008-01-13
Ah, MySQL was running on port 8076, thank you :D
You've all been a great help!!

---

### Post by dustman on 2008-01-13
glad to help :)

---

### Post by martin_n_c on 2008-01-14
> **goMON said:**
> To install XAMPP, the XAMPP Tutorial told me to copy the LAMPP folder to opt, i tried to do so, but it says 'You do not have permissions to write to this folder.'
How do i change my permissions to copy the folder?

EDIT - I have now changed my Permissions to full control of everything..

I'm new to Ubuntu and I've got a similar (I think) problem as goMON in the original post. I installed Xampp okay and set up the symbolic link to htdocs, but I get a 403 error (Permission denied) when I try to get at htdocs. How do I change the permissions? I've tried logging in as root and going:

$ chmod u+rw htdocs

but that doesn't help :(

---

### Post by dustman on 2008-01-15
> **martin_n_c said:**
> I'm new to Ubuntu and I've got a similar (I think) problem as goMON in the original post. I installed Xampp okay and set up the symbolic link to htdocs, but I get a 403 error (Permission denied) when I try to get at htdocs. How do I change the permissions? I've tried logging in as root and going:

$ chmod u+rw htdocs

but that doesn't help :(

Have you tried to "chmod" with "sudo" in front? ```
sudo chmod 777 htdocs
``` . And you do know that if you issue that command, the permissions of the files in that folder remain the same. To change the permissions you have to also input: ```
sudo chmod 777 htdocs/*
``` !note the "/*" after "htdocs" ;) .

Hope i'm right with this :).

Cheers!

Radu

---

### Post by martin_n_c on 2008-01-15
Radu: thanks for the reply! I got it partly working by changing the httpd.conf file, though I don't know if that was the right approach. I changed:
```
User nobody
```
to:
```
User myusername
```
I could get at my files but I couldn't get at the Xampp splashscreen because I didn't have permission!

So I changed the httpd.conf back to its original state and tried:
```
sudo chmod 777 htdocs/*
```
and:
```
sudo chmod 777 lampp/htdocs/*
```
I've got my Xampp splashscreen back but now I can't get at my files because I don't have permission :confused:

---

### Post by martin_n_c on 2008-01-17
Okay, I *think* I've got to the bottom of it now. I was importing files from my Windows partition and that was causing permission problems. I've got it working by following these steps (no need to change config files or default file permissions on Xampp or Ubuntu files!):

1) Installed Xampp by following this tutorial:
[http://ubuntuforums.org/showthread.php?t=223410]("http://ubuntuforums.org/showthread.php?t=223410")
I copied in the Python script to give me the Xampp console, but I wanted to simplify things so I didn't make a symbolic link to my home directory.

2) Made a new directory in /opt/lampp/htdocs. Let's call it 'test':
```
sudo mkdir /opt/lampp/htdocs/test
```

3) Changed directory to /opt/lampp/htdocs (cd /opt/lampp/htdocs) and gave myself permission on 'test':
```
sudo chmod 777 test
```

4) Now I can copy what files I like into 'test' using Nautilus, so I copied my .html files from the Windows partition into 'test'. (All right, so I could have done this in the terminal, but I'm new to Linux so that was less familiar.)

5) I don't have permission to view the files via localhost yet, so I give myself permission.  I've got subdirectories in 'test' so I make the permission change recursive and applying to all files:
```
sudo chmod -R 777 test/*
```
Note: this will generate an error if there are no files in the 'test' directory.

6) Now I make sure I've got Apache running and go to [http://localhost/test/myfile.html](http://localhost/test/myfile.html), and there we are! The only thing to remember is that if I import more files from the Windows partition I have to reset the permissions:
```
sudo chmod -R 777 test/*
```

That was what was confusing me. I'd set permissions, view a file and think 'Great! It's working' then paste in another file and Apache says I don't have permission to view it! Very perplexing for a newbie like me.

Sorry for this long explanation - I wanted to get it clear in my own head what I'd done! Any suggestions for improvements gratefully received!

---

### Post by dustman on 2008-01-18
well, yeah...the thing with the permissions is kinda tricky at the beginning. I usually use the terminal to copy stuff around, and i got used with the "chmod" :). Anyways, this permission thing gives linux the advantage of being so secure. There are almost no permission restrictions in windows, and we all know how secure windows is :lolflag:

---

### Post by martin_n_c on 2008-01-21
Yeah, I think I'm getting the hang of it - the permissions make sense, as you say. And if it's a choice between permissions or the Norton/McAfee route, give me the permissions any day :)

---

### Post by loveunit on 2008-05-10
that is the magic answer - perfect... just finally dumped MS from my computer, but all my files still remember.. now they have correct permissions and all is running smoothly - thanks a million.

---

