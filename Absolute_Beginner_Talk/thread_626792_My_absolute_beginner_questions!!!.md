---
title: "My absolute beginner questions!!!"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by faraz_k86 on 2007-11-29
Hello,

I installed ubuntu 7.10 today so now i have questions.


first of all my modem is not supported by ubuntu, so i cannot connect to the internet, so i cannot download the codecs to run my multemedia files.

So what i am asking for is a solution, is there a way that i can download a complete codec pack or some codec packs from my windows installation and then install them in my ubuntu. if such a pack exists can you please provide the download link. 


second, I dont understand the file manager of ubuntu??


like first off what  is root folder, is it equivalent to the "windows" folder of my win xp, 


when i press the windows explorer button, i get a neat look of all the folders and files in it, but in ubuntu all the files are not shown, for example when i press the places button on the desktop there are the music, videos and documents folder. I copied some songs in the music folder.

now the problem is that i cannot find those songs when i browse the hdd via file manager(the my computer icon) where are these documunts located in the hard disk??

are these folders in the root folder?? if so where???

---

### Post by staticvoid on 2007-11-29
> second, I dont understand the file manager of ubuntu??


like first off what is root folder, is it equivalent to the "windows" folder of my win xp,


when i press the windows explorer button, i get a neat look of all the folders and files in it, but in ubuntu all the files are not shown, for example when i press the places button on the desktop there are the music, videos and documents folder. I copied some songs in the music folder.

now the problem is that i cannot find those songs when i browse the hdd via file manager(the my computer icon) where are these documunts located in the hard disk??

are these folders in the root folder?? if so where???

wish i could help you with the codecs problem and connecting to the net to get them. post what modem you have. are you sure it will not work?

ok, linux folders are layd out like this:
/ is the file system. everything is there.

if you go to /home then you will find user folders, if you are the only one who uses the computer there will be one folder with your name on it. in THERE is where music , videos are etc...

perty much everything you need is in /home/*user name* 

try hitting Ctrl H and you'll see what I mean. it shows the hidden folders containing program data and stuff.

there are also other folders in / as you can see, in /bin there are ".exe's" as a windows usr would call them. They are executable... so i guess they are?

if you want to know more specific look up linux filesystem on wikipedia.org

cya! have a lotta fun,

sv

---

### Post by smacattack on 2007-11-29
the music, videos and all those folders are in your home folder, which is /home/yourusername

so if your name is hank your music folder will be in /home/hank/Music and your videos in /home/hank/Videos.

home folder should be listed in the side panel in your file manager.

---

### Post by scrooge_74 on 2007-11-29
Hi, first did you check if you can make your modem work? Check here first for it [http://linmodems.org/](http://linmodems.org/)
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

About downloading the packages, yes you can download the deb packages plus their dependencies (so you have to read the details to get all at once) Look in the Ubuntu site for a list of servers where you can downlaod them

The file system in Linux is different from XP, things are not just all together under c:\windows

/root has the admin file
/etc the config files
/bin has the executables
/sbin has the admin executablers
/home has your user files
/tmp  temp files
/var lots of stuff including logs
/media  your mount point for external drives
/lib your libraries for your apps
/dev has all the devices in the system
/usr  is where most programs keep their files
/boot you get the idea
/proc are the process running
/mnt you can mount drives there easy to remember

things are different, but once you get the hang of it you find it to be very simple

---

### Post by Afkpuz on 2007-11-29
1.) Modem
Check the restricted drivers menu.  System>Administration>Restricted Drivers
If your modem is listed there, try to install.  I think you need an internet connection for this.  If it is listed here and you have no internet, maybe you could try wireless.    

2.) Codecs
Can't help here.  Try to get an internet connection and then it's easy.  

3.) File manager
[http://youtube.com/watch?v=460IxkYmZxQ](http://youtube.com/watch?v=460IxkYmZxQ)
Thats a helpful youtube video that can explain alot, but here's a little bit that will help you.

The very top of the system is call "/"
That's the same as C: in windows.  From "/" , an important place to note is the "home" folder.  "This is very much like "My documents" in windows.  Click on your user name in "home" and you'll get to your home folder.  Here is where you copied your music.  Also, you have a documents folder and other useful places.  So, to get there, its
/home/username/
Watch that video for more about the other files and folders.

---

### Post by faraz_k86 on 2007-11-29
thx a lot guys, i think i almost have the file manager thing understood.

as for my modem, i have made another post about it long ago and it was confirmed there that it does not work, i have also tried lin modems and yes my modem is not supported. 
its a connexant modem.


so can i download the entire codec pack??  from where???

---

### Post by maljaros on 2007-11-29
The file layout is quite different from that of Microsoft and a problem is that each flavour of Linux has different rules.  Also the directory names are pretty archane, having changed from their original purpose over the years.  Your Microsoft directory would be the lowest numbered disk, usually disk-0.
You should be able to find "My Music" under Disk-0/Documents and Settings/Username.
Keep out of Root.
I think you will find new downloads made through Linux in "Home".
Some so-called "soft-modems" cannot work with Linux.

---

### Post by erfahren on 2007-11-29
for not having an internet connection to download packages you might want to check out this post:
[http://ubuntuforums.org/showpost.php?p=3851343&postcount=7](http://ubuntuforums.org/showpost.php?p=3851343&postcount=7)

for more info on general Linux directory structure check out:
[http://www.linuxcommand.org/lts0040.php](http://www.linuxcommand.org/lts0040.php)
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[a graphical image of the Linux directory structure](http://bp3.blogger.com/_Vbsj-yhipTw/RvaiatPBPBI/AAAAAAAAABs/yjx3hPlEUNw/s1600-h/linux_file_structure.jpg)

You probably already know that if you go to "Places" in the Gnome menu (at the top) there are direct links to your Home, Documents, Music, etc. folders. You can add to (or remove) those links.

In a file browser window (like your home folder) at the top you see "Bookmarks" and the dropdown of it there's "Add bookmark" and "Edit bookmarks". The bookmarks that you put in there will also show on the side pane of the file browser windows.

BTW: the file browser itself is called "Nautilus"  (you might have heard that name before). It's actually an application in itself. If you just type "nautilus" into the terminal it'll pop up. It'll be your home folder since you're currently logged in under your user name (the terminal opens to your /home/<username> directory).

---

### Post by erfahren on 2007-11-29
someone mentioned to "keep out of root". That's really not necessary. When just browsing the root directory with Nautilus while logged in as a regular user you can't make any changes anyway. If you open a configuration file it opens as "read only". 

That's one of the main points of running under a user. To change system configuration files you have to use the "sudo" command which gives root privledges temporarily (that's why it's necessary to be careful using it!). It's possible in Linux to delete the entire file system using root priviledges.

---

### Post by quandary on 2007-11-29
> **faraz_k86 said:**
> 
when i press the windows explorer button, i get a neat look of all the folders and files in it, but in ubuntu all the files are not shown, for example when i press the places button on the desktop there are the music, videos and documents folder. I copied some songs in the music folder.

now the problem is that i cannot find those songs when i browse the hdd via file manager(the my computer icon) where are these documunts located in the hard disk??

are these folders in the root folder?? if so where???

You're mixing up a few things. First:
there is a difference between the root folder and the root user folder.
the root folder is what in Windows is called c:\  , which you can also access as \
In Linux, this is called /
That is what is commonly refered to as "the root folder" or in short "root".

But Root is also a username, namely the Linux equivalent of Administrator in Windows.
Now, there is also a "root user folder", which is something different from "the root folder", but also refered to as "root".  It's simply the home folder of the Administrator.

---
So you have 3 things called root in short: the c:\ directory, the administrator name, and the administrator home directory. Don't confuse them.
----

Every user has a home directory, the equivalent of "My Folders" in Windows.
For normal users, they are located in /home/USERNAME/
The user called anonyomous for example has the following directories:
/home/anonymous/Desktop
/home/anonymous/Music
/home/anonymous/Pictures
/home/anonymous/Videos
and some more.

If you are root user (admin), your home folder is at a different location, in:
/root/
So the files for root (admin) for example are located here:
/root/Desktop
/root/Music
/root/Pictures
/root/Videos

That also answers your question as to where on the HD you find them.

---

### Post by faraz_k86 on 2007-11-30
thx a lot on the file system clarification guys.



but i take from the replies that there is no codec pack for ubuntu just like k-lite for windows??

---

### Post by quandary on 2007-11-30
> **faraz_k86 said:**
> 
but i take from the replies that there is no codec pack for ubuntu just like k-lite for windows??

Yes, as far as i know that's true. But i'm not omnisicient...

Why do you need codec pack? Until now Totem Video Player was able to playback just about anything...

---

### Post by scrooge_74 on 2007-11-30
Check here

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by quandary on 2007-11-30
> **scrooge_74 said:**
> Check here

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Oh, oops, yes i already had installed the restricted package, but forgot ;-)

---

### Post by staticvoid on 2007-12-04
faraz_k86, all you have to do is go into "Add/Remove Programs..." and install "Restricted Extras"

then you can play mp3s mpg3 wma acc etc...


:D

---

### Post by faraz_k86 on 2007-12-22
a lot of places i see the update command before installing anything?? what does the update command do and is it really necessary? what if i dont use the update command and install directly, will it work?

> sudo aptitude update
sudo aptitude install gtkorphan

---

### Post by LaRoza on 2007-12-22
> **faraz_k86 said:**
> a lot of places i see the update command before installing anything?? what does the update command do and is it really necessary? what if i dont use the update command and install directly, will it work?

It just updates the files. It is done when you open Synaptic or Add/Remove (that is why there is a delay)

It is needed? Not always, but it is a good idea. When you add or remove a repository, you should do it especially.

---

