---
title: "Where is this directory ??"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by cliff0108 on 2006-04-17
I am having NO END of issues trying to get rideof an application that will neither install nor uninstall and is causing MY SYNAPTIC to freeze. I have received a lot of suggestions about using various apt-get functions to remove/clean/install etc - but a message always returns that the archive cannot be found. 
SO I am endeavouring to do the uninstall manually by deleting all references to the file 'avidemux' ( I wish I'd never heard of it!) 
However when I do a search in file system I get locations such as :

[B]/home/downloads/opt/gnome/binn avidemux2
/home/downloads/usr/share/doc/packages
/home/downloads/debain etc.
[/B]

I go to my file browser and I _CAN'T EVEN FIND_ these subdirectories and they do not appear to be hidden? I didn't even know there were apparent subdirectories of the directory 'downloads' which I created !
What is going on?
I am very discouraged and frustrated and no one is able to suggest how to get Synaptic back.

---

### Post by macdo on 2006-04-17
Those locations look rather strange to me. It looks like you've got a user called downloads...
Maybe you should try them out by typing ```
 cd /home/downloads/foo/bar
``` in the command line.
If that works, then you can probably open them from the command line with ```
nautilus /home/downloads/foo/bar/
``` Also try opening a root browser. ```
sudo nautilus
```
On the off-chance, try eliminating the /home/downloads. (that is, try /opt/gnome/bin instead of /home/downloads/opt/gnome).
You could also try typing the folder address into your web browser. It works in firefox, at least!

Good luck!

---

### Post by gborzi on 2006-04-17
Hello, I have installed avidemux2 using automatix. The package has only one file in /usr/local/bin/avidemux2. I havn't had any problem in removing it.
You can try to download the avidemux package from here
[http://www.fuckbirdflu.com/automatix/](http://www.fuckbirdflu.com/automatix/)
install and uninstall it with dpkg.

---

### Post by cliff0108 on 2006-04-17
Sorry - none of this works
It looks to me that this program (avidemux) somehow id misconfigured throughout - apparently in directoies I cannont access.
I tried what you suggested Macdo - but cannot just go to
home/downloads/usr/share/doc/packages - which shows clearly on the file browser

I involked the sudo nautilus and got ato the root file browser -m that looked promising - but the entries were file:///home/cliff/Desktop/Screenshot-5.png
and I'm not sure where to go.
I tried sudo dpkg --purge and got a message saying there were inconsistancies in the program and I should in effect install it correctly before uninstalling it this way.

Is there no command that will just obliterate any trace of this  avidemux ?

---

### Post by cliff0108 on 2006-04-17
gborzi - I did as you suggested - downloaded a 'fresh 'program and it seemed to install okay - but I think the problem is  there are other aborted and problematic installs throughout my system.

---

### Post by gborzi on 2006-04-17
You can check for broken packages with
sudo apt-get check
and if I'm not wrong synaptic is able to list the broken packages.

---

### Post by ds[de] on 2006-04-17
And you should really check if you actually have a user account named "downloads" on your system, which probably shouldn't be there if you didn't deliberately add it.

You can do this by typing
```
sudo cat /etc/passwd | grep downloads
```

Regards,
ds[de]

---

### Post by CameronCalver on 2006-04-18
[QUOTE=macdo]Those locations look rather strange to me. It looks like you've got a user called downloads...
Maybe you should try them out by typing ```
 cd /home/downloads/foo/bar
``` in the command line.
If that works, then you can probably open them from the command line with ```
nautilus /home/downloads/foo/bar/
``` Also try opening a root browser. ```
sudo nautilus
```
On the off-chance, try eliminating the /home/downloads. (that is, try /opt/gnome/bin instead of /home/downloads/opt/gnome).
You could also try typing the folder address into your web browser. It works in firefox, at least!

Good luck![/QUOTE]

Hey what nautilus anyway

---

### Post by jethro10 on 2006-04-18
[QUOTE=CameronCalver]Hey what nautilus anyway[/QUOTE]
It's the graphical file browser. Probably Windows explorer to you.

There is also a graphical tool to check for users etc in the menu's. Much easier for us newbies.

I would prefer personally that advice given used graphical tools because thats what more people are used to.

J

---

