---
title: "Absolute Linux Newb"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by malnacido on 2006-09-29
God I do not know where to even begin. I have been a windows user forever and am just now discovering the wonder that is ubuntu and linux in general. I guess my problem is that I have been spoiled by GUIs my whole life and know absolutely nothing about the console or terminal or whatever it's called. I guess what I am asking is if there is someone or somewhere I can go to learn how to do things in the console. For example, at this point in my linux experience, I cannot install a program for the life of me. I download one off of the internet and save it to my desktop. From there I go no further because I do not know how to install it. I am so used to .exe's and having the computer doing it for me. I do not know if any of you are familiar with the program putty but it basically accesses my schools database so that I can access my timesheet and update it. I want to know how to do this through the console because I have done it before but forget how to. Any help will be greatly appreciated.

---

### Post by nthdegree on 2006-09-29
You want to install a software program am I correct?

Do the following:  Open up a terminal, then type the following and press enter:

gksudo synaptic

You will then be prompted for your password, after then you will be provided with a GUI package manager - just look for the application you wish to install my friend :)

There is an easier way but i'm more a Kubuntu user than an Ubuntu one, hope that helps.

---

### Post by malnacido on 2006-09-29
I am also having a problem with this program called wireless assistant. Every time I go to open it, it gives me an error message that says this:

You might have insufficient permissions for Wireless Assistant to function properly.
Did you run it using 'sudo'?

How would I run that program as sudo

---

### Post by Omnios on 2006-09-29
There is a link in my signature with lots of terminal command links.

---

### Post by nthdegree on 2006-09-29
Oops, sorry didn't read that properly.

If you want to install putty (assuming it's in the repositories), try the following.

Open up a terminal, then put:

sudo apt-get install putty

You will be asked for your password, DO NOT be alarmed when you type and you don't see anything appear, your password is never visible (not even *s appear) os just put in your password and hit enter.

You should then be able to proceed and install putty.  If you have any errors just post them here, and people will be happy to help.

---

### Post by mrehorst on 2006-09-29
The most common way to install programs is to use the package manager.  The advantage is that the package manager will grab the program and all its dependencies and install all of them for you.  It will also make uninstall easy because it keeps track of which packages you have installed on the machine.

There are 4 main methods to add programs.  First, on the desktop at the bottom of the Applications menu there is a selection labeled add/remove.  You can search for available apps there and select them for installation.  Second, you can access the Synaptic package manager by selecting it from the system:administration menu.  Synaptic allows you to select more than the default repositories for install packages.  Third, you can use apt-get on a terminal command line.  Fourth, you can DL source code and compile it- a pain for noobs like you and me.  There may be other ways, also, that I don't know about.

Don't sweat it.  I was completely green to Linux last week, and now I am dispensing help on forums (I am not a linux expert, but I play one on the internet!).  Use the man pages, online forums, the wiki (upper right hand corner tab on your browser).  Get a book!  Take comfort in the fact that almost anything you want to do has been done a thousand times and someone has posted instructions somewhere close-by.

MR

---

### Post by nthdegree on 2006-09-29
Oops i'm slow today.

What I just posted should help a little.

It's just sudo <command> and that runs it.  Example: sudo apt-get upgrade

---

### Post by malnacido on 2006-09-29
putty is not available. There is no way to access my schools database directly from my console? I thought I could connect to servers from the console. And BTW thanks to all who have answered so quickly. This is the other reason I switched to Ubuntu, the support I get from VOLUNTEERS is infinitely better than I get from paid "professionals" elsewhere.

---

### Post by dppowell on 2006-09-29
We'd need to know more about that database server.  If you're talking about being able to browse icons for Windows computers on your network, that involves a package called Samba (which I'm pretty sure is part of the default install now, though I haven't used it recently).

---

### Post by malnacido on 2006-09-29
I have to connect to acs.bu.edu. I dont know if SSH means anything to you. I am just shooting things out because I dont know how to describe it. I guess putty is a program that looks like a windows command prompt where you enter what server you want to access, in my case acs.bu.edu and then it prompts you for a user name and password. I can distinctly remember doing that through my console. A friend of mine showed me a while back, but I lost touch with him and wouldnt be able to ask him.

---

### Post by Aelfric5578 on 2006-09-29
Putty is a Windows frontend for SSH, in Linux, you can actually use ssh from the terminal. I don't think it's installed by default (I could be wrong), but you can easily install it with ```
sudo apt-get install ssh
``` then the command to use SSH, in your case would be
```
ssh username@acs.bu.edu
```
After installing it, you will also be able to remotely access your Ubuntu computer using SSH on another Linux machine or Putty in Windows.

---

### Post by cjssmo on 2006-09-29
Putty is also availabl for ubuntu.  Ubuntu is based on debian and putty is available in the debian repository.  It sounds like you need to add extra repositories to you repository list.  Go to this link [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)
and it will give you step by step instructions on how to add extra repositories.  Once you have done that open a terminal and type in sudo apt-get install putty.  That should give you something you are more familiar with.  I use putty to perform admin tasks on my servers.  Welcome to the linux world.

---

### Post by malnacido on 2006-09-29
Thank you so much, that is exactly what I needed. I was also wondering if you guys had aim names or other wise so I can keep in touch.

---

### Post by malnacido on 2006-09-29
Another question. When I am in SSH, how do I get out of the server I am in and go back to doing operations on my computer. What's the command I use in order to leave SSH.

---

### Post by dppowell on 2006-09-29
Well, you could just close the terminal window, but ideally you should log out of the remote server (which ends the ssh process, too).  The documentation for your database system should tell you the command for closing the connection, logging out, etc.

---

### Post by Nonno Bassotto on 2006-09-29
Moreover, if you need to transfer files on scp or sfpt try Places->Connect to the server. You'll be able to browse the remote pc just as if it was local.

---

### Post by LostShootingStar on 2006-09-29
Try 

exit
quit
bye

one of them should work

---

