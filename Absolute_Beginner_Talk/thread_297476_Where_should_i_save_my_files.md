---
title: "Where should i save my files?"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by milad on 2006-11-11
ok, i am a total newbie to linux and there is one thing i don't understand about managing my files.

Where should i actually save my documents? i mean in windows there is a My Documents, and i can easily make any folder i want in any partition and organize my documents, songs, pictures. but ubuntu seems to be more complicated, there are lots of folders and files in File System. Where should i save my files in ubuntu? where should i install the programs i download? How should i organise my files?/

---

### Post by Zeerak on 2006-11-11
Personally I start out with saving my files in the folder that's first opened by Nautilus (in my case Thunar) and from there I make the necessary folders. If you save it there it's saved in your home directory (I believe) which is where you should save the files you need/want to save for further viewing.

---

### Post by podunk on 2006-11-11
In Linux all your files and folders go in
/home/your_name

That's your "My Documents" :-) This is the only directory where you can save files without a password.

A good introduction to Linux and it's file structure is here:
[http://tldp.org/LDP/intro-linux/html/index.html](http://tldp.org/LDP/intro-linux/html/index.html)

---

### Post by logullo on 2006-11-11
> **milad said:**
> ok, i am a total newbie to linux/
Welcome! 
> Where should i actually save my documents? i mean in windows there is a My Documents, and i can easily make any folder i want in any partition and organize my documents, songs, pictures./
In Linux, you have the equivalent of a "My Documents" folder. It's referred to as your "home directory". It's path is typically /home/yourname.
> but ubuntu seems to be more complicated, there are lots of folders and files in File System./
True, when you look under the covers, you'll find a lot of directories, and they're there for a reason. Give this a read:
[http://www.freeos.com/articles/3102/]("http://www.freeos.com/articles/3102/")
> Where should i save my files in ubuntu?/
Trust me: save everything you create (documents, photos, downloads, etc.) in your home directory. It makes backups a snap, and when you decide to upgrade your linux system, being able to "back up all my files" is the key to making the process a lot simpler.
> where should i install the programs i download?/
You won't need to. Remember those "complicated" directories above? The linux installer tools will put the files from the programs you install in the right places. You won't need to worry about it.
> How should i organise my files?/
Here's your chance to be creative! :) Just do everything inside your home directory.
Good luck!

---

### Post by milad on 2006-11-11
Tx everybody for responding so fast. just one more question: I wanted to install Real Player but something went wrong with the package so i decided to download it myself. I saved the file on my desktop and followed the instructions, in the end it just created a folder on my desktop, and whenever i want to use it i have to run the bin file, i mean it didn't create any shortcut or icon or anything. Should it really be on my desktop? what happens if i move it to another place like /bin which seems to be the "Program Files" of linux?
What happens if i simply delete the folder? is there anyway to uninstall a program which i manually install?

---

### Post by bodhi.zazen on 2006-11-11
> **milad said:**
> Tx everybody for responding so fast. just one more question: I wanted to install Real Player but something went wrong with the package so i decided to download it myself. I saved the file on my desktop and followed the instructions, in the end it just created a folder on my desktop, and whenever i want to use it i have to run the bin file, i mean it didn't create any shortcut or icon or anything. Should it really be on my desktop? what happens if i move it to another place like /bin which seems to be the "Program Files" of linux?
What happens if i simply delete the folder? is there anyway to uninstall a program which i manually install?

LOL :lol:

First welcome !

Second some small advice. Yes I agree, keep your files in /home/user_name

But, organize /home/user_name a little.

You may want to make a few directories (folders). Linux does not like a space in the name so use, for example "My_Documents" rather then "My Documents". You can make a new directory from the CLI or nautilus.

I Advise:[list=number][*]documents[*]music[*]pictures[*]downloads[*]src[*]bin[/list]
```
mkdir ~/documents ~/music ~/pictures ~/downloads /~src ~/bin
```
_Note_: ~/ is shorthand in the terminal for /home/user_name
Most of these are obvious, but...

src is where you should download and keep source code, for example the "Real Player" folder on your desktop.
bin is for any scripts or programs you may write.

As far as uninstalling Real Player, how did you install it ?

If with ./configrure; make; make install try make uninstall. Use [checkinstall](https://help.ubuntu.com/community/CheckInstall) rather then make install and you will have a .deb package which is easier.

If with a script (within the Real Player directory) look for an uninstall script.

Otherwise you will have to delete manually. Type:```
locate "Real Player"
``` In a terminal to list all the installed files. You will have to delete all these manually.

See also: [How to install anything in Ubuntu](http://monkeyblog.org/ubuntu/installing/)

As far as location of installed programs, something akin to "Program Files" Linux uses a different system. /bin for executable, etc.

See here for an overview of the file system: [Ubuntu File system](http://doc.gwos.org/index.php/FileLocations)

Well, that should cover it for now :p

---

### Post by milad on 2006-11-11
Thanks man ... That's all i needed

---

### Post by EGE-FB on 2006-11-12
Hi, 

I'm also having the same problem. When I partitioned my drive, I made a partition around 38 GB named as /documents (this is where I initally hoped to put all my files in). But, I cannot change or edit anything in this folder because it's in Filesystem. My home_username folder is only about 2.7 GB in comparison. What do I do if I run out of space? 

Thanks

---

### Post by bodhi.zazen on 2006-11-12
> **EGE-FB said:**
> Hi, 

I'm also having the same problem. When I partitioned my drive, I made a partition around 38 GB named as /documents (this is where I initally hoped to put all my files in). But, I cannot change or edit anything in this folder because it's in Filesystem. My home_username folder is only about 2.7 GB in comparison. What do I do if I run out of space? 

Thanks

You need to have the proper entry in [fstab](http://ubuntuforums.org/showthread.php?t=283131).

Setting permissions depends on what type of FS is on the partitions (ntfs, fat, ext3, etc...).

If you are having troubble please post more information (partition and FS type).

---

