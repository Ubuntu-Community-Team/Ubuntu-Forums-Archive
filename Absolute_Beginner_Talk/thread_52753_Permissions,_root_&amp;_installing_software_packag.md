---
title: "Permissions, root &amp; installing software packages..."
date: 2005-07-28
forum: Absolute Beginner Talk
---

### Post by [Cyanide] on 2005-07-28
Is there an easy step-by-step tutorial as to how this works?

I'm getting various messages from lack of permission, incorrect user, can't move package to right folder etc etc...

Is there a way to login to Ubuntu as root in XWindows?

Or is there a way to do it through the root terminal that I haven't discovered yet?

What packages can I install? RPM packages give me an error message...

Lots of questions from a total Linux n00b, if someone can point me to a tutorial that'd be awesome :)

---

### Post by DJ_Max on 2005-07-28
Don't use RPM's. Use apt-get to install programs from the Ubuntu repositories that are made in the .deb format.

[http://ubuntuguide.org](http://ubuntuguide.org)
[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by [Cyanide] on 2005-07-28
[QUOTE=DJ_Max]Don't use RPM's. Use apt-get to install programs from the Ubuntu repositories that are made in the .deb format.

[http://ubuntuguide.org](http://ubuntuguide.org)
[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)[/QUOTE]

What about permissions? How do I install a program under root?

---

### Post by Sam on 2005-07-28
By using Synaptic, you'll be asked for the root password (this is yours). But did you [add extra repositories](http://ubuntuguide.org/#extrarepositories) ?

---

### Post by hod139 on 2005-07-28
[QUOTE='[Cyanide]']What about permissions? How do I install a program under root?[/QUOTE]

say you wanted to install mozilla-thunderbird from the command line.  You first type
```
apt-get update
``` 
this will update the list of available programs
```
sudo apt-get install mozilla-thunderbird
```
sudo says run the command with super user rights (i.e. as root).  It will prompt for a passoword, and you just use your regular user password.
 
If you don't know the name of the package, you can type
```
apt-cache search thunderbird
```
and it will return a list of possible packages based on the search term.

Another option is to use synaptic.  To launch with root rights, type:
```
sudo synaptic
```

---

### Post by [Cyanide] on 2005-07-28
Ok let's say I download a piece of software from a website, say a Gnome theme.

Where do I download it to? Where do I extract it to?

If I try to extract to my desktop it says I don't have the right permissions.

And if I try to delete something off my desktop it says I don't have the right permissions either.

---

### Post by Sam on 2005-07-28
[QUOTE='[Cyanide]']Ok let's say I download a piece of software from a website, say a Gnome theme.

Where do I download it to? Where do I extract it to?

If I try to extract to my desktop it says I don't have the right permissions.

And if I try to delete something off my desktop it says I don't have the right permissions either.[/QUOTE]
Seems that you change some permissions...

Could you please post the output of
```
$ ls -l /home/
$ ls -l /home/<username>
```(replace <username> with you username, of course)

---

### Post by [Cyanide] on 2005-07-28
[QUOTE=Sam]Seems that you change some permissions...

Could you please post the output of
```
$ ls -l /home/
$ ls -l /home/<username>
```(replace <username> with you username, of course)[/QUOTE]

```
root@cyanide-laptop:/home/cyanide # ls -l /home/
total 4
drwxr-xr-x  19 cyanide cyanide 4096 2005-07-28 22:06 cyanide
root@cyanide-laptop:/home/cyanide # ls -l /home/cyanide
total 4
drwxr-xr-x  4 root root 4096 2005-07-28 18:13 Desktop
root@cyanide-laptop:/home/cyanide #
```

---

### Post by Nequeo on 2005-07-28
[QUOTE='[Cyanide]']Ok let's say I download a piece of software from a website, say a Gnome theme.

Where do I download it to? Where do I extract it to?

If I try to extract to my desktop it says I don't have the right permissions.

And if I try to delete something off my desktop it says I don't have the right permissions either.[/QUOTE]
 Interesting...

If you can't delete stuff on your desktop, it sounds like you may have accidentally changed the ownership permissions on your desktop. Try this:

1. Open a command window.
2. Type in the following (making sure you replace 'sger' with your own user name)

```

sger@prodigi-02:~$ cd /home
sger@prodigi-02:/home$ chown -R sger:sger sger
[This changes the owner and group of all files and directores in your home folder.]
sger@prodigi-02:/home$ chmod -R 755 sger
[This sets security permissions on all the files in your home directory]

```

Now your file permissions should be back to normal. I'd stick to using Synaptic to install software for a while... (even if it means living without luxuries like Gnome themes) until you get the hang of how Ubuntu is put together. It usually takes a few weeks of Screwing Things Up Big Time before you learn enough to tackle things like installing themes... It is difficult for us to give you exact instructions on how to do this, as it can be very different for each piece of software! ... which is why we reccomend sticking with Synaptic for the time being. 

Hope that helps a little,

Cheers.

---

### Post by Nequeo on 2005-07-28
I forgot to mention... You will need to be root (or use sudo) to execute the above commands.

---

### Post by [Cyanide] on 2005-07-28
Now when you guys say open up a terminal, do I open the root terminal or just a plain terminal?

Also, how exactly do I use Synaptics to install software?

Sorry for all the questions.

---

### Post by Nequeo on 2005-07-28
[QUOTE='[Cyanide]']Now when you guys say open up a terminal, do I open the root terminal or just a plain terminal?

Also, how exactly do I use Synaptics to install software?

Sorry for all the questions.[/QUOTE]
 Open a regular terminal... and if you get an error message saying 'permission denied', retype the command with 'sudo' in front of it - then enter your own password when asked.

That's the safest way to play with root privaledges...

To run synaptic, go to System--->Administration--->Synaptic Package Manager on the menu. It's pretty straight-foward, but if you've got any specific questions about how to use it, please don't hesitate to ask.

Cheers,

[EDIT]
See [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) for a much better description of sudo and root under Ubuntu.

---

### Post by [Cyanide] on 2005-07-28
[QUOTE=Nequeo]Open a regular terminal... and if you get an error message saying 'permission denied', retype the command with 'sudo' in front of it - then enter your own password when asked.

That's the safest way to play with root privaledges...

To run synaptic, go to System--->Administration--->Synaptic Package Manager on the menu. It's pretty straight-foward, but if you've got any specific questions about how to use it, please don't hesitate to ask.

Cheers,[/QUOTE]

Awesome, thanks!

I guess I did mess up the permissions, CHMOD 755 fixed it and I can delete & extract stuff off & on the desktop now.

Where's a good general folder to store all the stuff that I've downloaded from the internet?

Like MP3s, videos etc...?

Also is there a way to look at swapfile size? Ubuntu doesn't seem to be running as smooth as it should be?

---

### Post by Sam on 2005-07-28
[QUOTE='[Cyanide]']Now when you guys say open up a terminal, do I open the root terminal or just a plain terminal?

Also, how exactly do I use Synaptics to install software?

Sorry for all the questions.[/QUOTE]
Never use the root terminal unless you want to do a lot of administrative tasks. Use a normal terminal, and use 'sudo' if you need root access.

For your Desktop problem, do
```
$ sudo chown cyanide:cyanide /home/cyanide/Desktop
```


To use Synaptic, you must first [add extra repositories](ubuntuguide.org/#extrarepositories) (do not forget 'sudo apt-get update' after that), then open Synaptic and search for a package name or from a category, then right-clic on the desired package and choose 'Mark for Installation'. Then clic 'Apply' and you'll install the package(s).

---

### Post by Nequeo on 2005-07-28
As far as saving your files is concerned - do whatever you like!

I just have a folder called 'Downloads' in my home directory that I save everything into for sorting. 

It's also worth noting that if you create a directory called 'Documents' in your home directory (not on the desktop), it will show up on the Gnome menu under 'Places'.

To check your swap usage you can right click on your taskbar and select 'add to this panel', then search for 'System Monitor'. That has an option to show you swap space. [EDIT] You'll need to right click on it, select 'Preferences' and then add the swap space monitor. Also, if you left click once on the monitor, then click on the resources tab, you can see a graph of swap-space/memory over time.[/EDIT]

To see the exact figures in kbs, open up a regular terminal and type in 'top'.

Cheers,

---

### Post by [Cyanide] on 2005-07-29
[QUOTE=Nequeo]As far as saving your files is concerned - do whatever you like!

I just have a folder called 'Downloads' in my home directory that I save everything into for sorting. 

It's also worth noting that if you create a directory called 'Documents' in your home directory (not on the desktop), it will show up on the Gnome menu under 'Places'.

To check your swap usage you can right click on your taskbar and select 'add to this panel', then search for 'System Monitor'. That has an option to show you swap space. [EDIT] You'll need to right click on it, select 'Preferences' and then add the swap space monitor. Also, if you left click once on the monitor, then click on the resources tab, you can see a graph of swap-space/memory over time.[/EDIT]

To see the exact figures in kbs, open up a regular terminal and type in 'top'.

Cheers,[/QUOTE]

Thanks for all your help!

One more question, what "core" or distribution of Linux is Ubuntu? For instance if I wanted to download some kind of a Linux software and it gives me RedHat, Fedora, Debian etc etc...

---

### Post by aysiu on 2005-07-29
[QUOTE='[Cyanide]']Thanks for all your help!

One more question, what "core" or distribution of Linux is Ubuntu? For instance if I wanted to download some kind of a Linux software and it gives me RedHat, Fedora, Debian etc etc...[/QUOTE] Ubuntu is Debian-based.

---

### Post by poofyhairguy on 2005-07-29
Good questions.

---

### Post by [Cyanide] on 2005-07-29
[QUOTE=aysiu]Ubuntu is Debian-based.[/QUOTE]

So if they don't have a Debian based version, I'm shit out of luck? Or is there an alternative?

---

### Post by aysiu on 2005-07-29
[QUOTE='[Cyanide]']So if they don't have a Debian based version, I'm shit out of luck? Or is there an alternative?[/QUOTE]

[http://www.highend2d.com/boards/showflat.php?Board=linuxforum&Number=200544](http://www.highend2d.com/boards/showflat.php?Board=linuxforum&Number=200544)

---

