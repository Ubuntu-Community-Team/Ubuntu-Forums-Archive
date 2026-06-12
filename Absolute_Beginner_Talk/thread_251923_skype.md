---
title: "skype"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by emmaclose on 2006-09-06
i tried posting on the breezy badger forum, but wasn't getting much help. i'm using 5.10 and having problems getting skype to work download the deb

this what one forum user told me to do

'open a terminal and go to the directory it is located and type

sudo dpkg -i skype_1.2.0.18-2_i386.deb

assuming that it the version you have downloaded'

i tried this and recieved this error message	  	

'dpkg: error processing skype_1.2.0.18-2_i386.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
skype_1.2.0.18-2_i386.deb'

anyone got any ideas. i'm quite new to all this at the mo, so don't be too technical - also upgrading at the moment is out of the question

emma

---

### Post by Blondie on 2006-09-06
Put the deb in your Places / Home Folder before typing the command. Or tell the terminal to go to wherever it's actually saved before entering the command.

---

### Post by benfindlay on 2006-09-06
Is the version number definitely correct for the file you downloaded?

If you open the terminal, navigate to the directory where the file is saved and type ```
dir
``` it will list the files present. You can the select the file name with the mouse (click and drag), right click and choose copy. Then type:

```
sudo dpkg -i [insert pasted filename here]
``` and press enter.

if you're having difficulty copying the file name, you could always use tab-completion; just type the first few characters of the filename and press tab, it should fill the rest of the file in for you!

Hope this helps!

---

### Post by Blondie on 2006-09-06
> **Blondie said:**
> Put the deb in your Places / Home Folder before typing the command. Or tell the terminal to go to wherever it's actually saved before entering the command.

To do the latter you would type something like

```
cd /home/joeblogs/Desktop
```

If the file was on the desktop and your personal folder is called joeblogs. The cd command means change directory.

---

### Post by Blondie on 2006-09-06
Also, I'm pretty sure that you can get Skype using System / Administration / Synaptic Package Manager if you go Settings / Repositories / Add then select Multiverse.

Generally it's better to use Synaptic than download installation files yourself because it looks after all your dependancies for you.

---

### Post by emmaclose on 2006-09-06
ok...so this is what i get

when i type /home/joeblogs/Desktop and then dir i don't find the file
when i type cd /home/joeblogs/Desktop then dir i do find the file. but when i put the command in 'skype_1.2.0.18-2_i386.deb' (and yes this is definitly the name of the file), i get' command not found'

so where is the file actually stored - and how do i move it?
 
i tried doing it thourgh the synaptics manager, but to no avail. when i checked the multiverse box, i got this message

W: GPG error: [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466

thanks for your help

em

---

### Post by benfindlay on 2006-09-06
'skype_1.2.0.18-2_i386.deb' isn't a command, so you will get that kind of error.

Go into terminal and type the following:

```
cd /home/joeblogs/Desktop
sudo dpkg -i skype_1.2.0.18-2_i386.deb
```

That should be all you need. If you do want to move the file to another directory, this can be easily done through the GUI, so just open wherever you want to put it, and drag it from your Desktop into the folder. Then of course your cd /* will be different to before.

Hope this helps

---

### Post by arkangel on 2006-09-06
maybe you have  dpkg :S

close synaptic
open a terminal and type
sudo aptitude install  dpkg 

then go to the folder  where the deb file is 
 cd /home/joeblogs/Desktop
  sudo dpkg -i skype_1.2.0.18-2_i386.deb

if that doesnt work
donwload the precompiled "Static binary tar.bz2 with Qt 3.2" 
open this file ,double click in Nautilus,  and extract  here . then you have a folder in which is skype  open a terminal go to this folder and simply type 
   ./skype

if that works  copy the whole folder to a nice location, i haveit in /opt  which is for 3rd-party app

  sudo mv [skype_folder_name] /opt

---

### Post by toasterofirony on 2006-09-06
I know this may seem a little too simple, but you have actually downloaded the .deb, right?

If so, I would suggest opening your browser and having a look in the download history (probably under something like tool => Downloads or the like) and finding where you saved it.

Otherwise, fire up Synaptic and get it that way. Much easier and takes cares of any dependancies (though I'm not sure Skype has any...)

---

### Post by emmaclose on 2006-09-06
this is what i get this time

Selecting previously deselected package skype. 
(Reading database ... 69238 files and directories currently installed.)
Unpacking skype (from skype_1.2.0.18-2_i386.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype

also, skype has appeared in applications, but won't open. i guess it may be the same problem!

---

### Post by arkangel on 2006-09-06
ok  open synaptic and  search for  this 

libstdc++5

mark the 2 with the ubuntu symbol 
libstdc++5
libstdc++5-dev

and apply

EDIT , repeat again the installation
these libraries are  used to build  many things  better install them now than later

---

### Post by emmaclose on 2006-09-06
but will try the other thing...hang on

---

### Post by toasterofirony on 2006-09-06
ah, I tell a lie, what you have there is a lack of a lib that Skype is dependant on, hence the error in the dpkg.

I'm guessing you have access to the internet as you're posting, so I'll stress again, use Synaptic. If you try and install it through Synaptic now, it'll tell you Skype is broken (which it is) but all you have to do is re-install it.

Very simple, and very reliable.

---

### Post by emmaclose on 2006-09-06
so remove it and reinstall it on synaptic?

---

### Post by toasterofirony on 2006-09-06
uh huh.

Thats what I'd do.

Oh man, wait, you have to add the repo for it >.<

You fancy learning about that?

[This is how to do it]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Messenger_.28Skype.29")

---

### Post by emmaclose on 2006-09-06
ok...this happened 

emmaclose@ubuntu:~$ gksudo gedit /etc/apt/sources.list
(gedit:10230): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

maybe ubuntu just doesn't like me

em

---

### Post by arkangel on 2006-09-06
to edit the list  you have to close synaptic

---

### Post by emmaclose on 2006-09-06
no, still doesn't work

---

### Post by emmaclose on 2006-09-06
hang on...i've made progress

---

### Post by emmaclose on 2006-09-06
yep - i'm there. instead of gksudo i just typed sudo and all was fine. no idea why this was....but thank you for all your help. i've just moved to hong kong, so keeping in touch with people is quite a high priority for me!

thanks again

em

---

### Post by toasterofirony on 2006-09-06
wooooo~

Hooray!

---

### Post by whizbaby on 2006-09-06
Congratulations!
Now it's time to read this:
[www.secdev.org/conf/skype_BHEU06.pdf](www.secdev.org/conf/skype_BHEU06.pdf)

---

