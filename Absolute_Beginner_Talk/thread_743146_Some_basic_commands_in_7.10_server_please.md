---
title: "Some basic commands in 7.10 server please"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by AnthonyArde2 on 2008-04-02
Hi all,

I require a few basic commands so that i can navigate through my computer :) i have installed ubuntu 7.10 server and have followed a tutorial on how to set a few things up, however my questions below wernt covered in the tutorial.

i require to know the commands by example on how to :

1.How do i get a full directory listing for the current dir that i`m in, for example in MSDos i would say "dir/p"

2.Does it matter if i type commands if i am in a specific directory that affects another?

3.How do i change directories, eg, how to i get back to my /etc dir?

4.i have put my usb flash drive in the computer but i have no idea how to access it. does it matter if it is ntfs?

5.How do i mount this drive after detection?

6. It doesnt look like it picks it up, doesnt say sda1 or anything like that.

7.How do i copy files, and basically move around in my directories?

8. How do i get a listing of my drives in my computer?

9.What is the main directories in linux, by the looks of things all config files are installed in /etc/"APP NAME"

10. how do i access my cd rom?

11. am i able to write cd's with this version of ubuntu

12. will a windows computer be able to access this computer over a network without samba installed?


Sorry for the noob questions but i have looked on the net and none give proper examples for the server version.

Thanks

Anthony

---

### Post by blazercist on 2008-04-02
1. dir
2. yes if you are in a certain dir and want to manipulate files in another you will have to specify a path EX: you are in /home/YOUR_NAME_HERE  and want to create a dir in another user's home folder the command would be mkdir /home/OTHER_USER/NEW_FOLDER
3. cd /dir/path/here
4. you will need the ntfs-3g driver which can be installed by issuing sudo apt-get install ntfs-3g after you install the ntfs driver your usb flash card should be automounted and all you need to do is cd to the mount point
5. see above
6. see above
7. the copy command is cp EX: you are in /home/YOUR_NAME/ and wish to copy text.file to /home/OTHER_NAME the command would be cp text.file /home/OTHER_NAME/
8. I forgot this one fdisk -l  ?
9. Main directory?  all your user stuff will normal go in /home/YOUR_USERNAME/
10. cd /media/ 
dir
it should list your cdroms and removable media such as mounted iso's and flash drives you can cd them and list their contents as normal.
11. yes there are instructions for doing this with the command line in the forums and on the wiki
12. no in order to share files with a windows machine you will need samba.

---

### Post by Fire_Chief on 2008-04-02
Hi AnthonyArde2,

Welcome to Ubuntu!
Out of curiosity, Is there a reason you chose to start learning Linux with the server version of Ubuntu instead of the Desktop version? The two versions are identical except the server version does not install the GUI interface or multimedia stuff and may automatically install apps like Apache and MySQL. The apps can easily be installed on the desktop version or you could install the GUI on the server version (Yes, it's not a recommended approach for production servers I know). But for your purposes learning and getting familiar with the system it may ease your transition.

Good Luck!:guitar:

---

### Post by ShodanjoDM on 2008-04-02
You may try this for the manual of each commands (example for ls command):

```
man ls
```

> **AnthonyArde2 said:**
> Hi all,
1.How do i get a full directory listing for the current dir that i`m in, for example in MSDos i would say "dir/p"

```
ls
ls -hal
```

> 
8. How do i get a listing of my drives in my computer?

```
mount
```

and 

```
sudo fdisk -l
```

the entries with /dev/sda1 /dev/sdb etc are your mounted drives. 

For further reads, try google for "Basic Linux Commands". Hope it helps :)

---

### Post by Pigsflew on 2008-04-02
> 1.How do i get a full directory listing for the current dir that i`m in, for example in MSDos i would say "dir/p"

the command is "ls". Try "ls -al" for a more verbose list, too.

> 2.Does it matter if i type commands if i am in a specific directory that affects another?

I'm not entirely certain what you mean here, but if you're in a directory and use a command, specifying another directory, it should not effect the current directory.

You can specify another directory by either relative location (using "./" to mean this directory and "../" to mean the parent) or by absolute location by beginning the directory location with "/", which is the "root" directory.

> 3.How do i change directories, eg, how to i get back to my /etc dir?

The command is "cd" for "change directory". Therefore, "cd .." moves up one directory, "cd /" moves to the root of your filesystem, and as a special token, "cd ~" moves to your user home directory.

> 4.i have put my usb flash drive in the computer but i have no idea how to access it. does it matter if it is ntfs?

as the previous responder mentioned, look up NTFS-3G.

> 5.How do i mount this drive after detection?

It should automount.

> 6. It doesnt look like it picks it up, doesnt say sda1 or anything like that.

This is because it simply won't recognize the filesystem type until the NTFS driver is introduced into the kernel.

> 7.How do i copy files, and basically move around in my directories?

To copy, use "cp /path/to/fromfile /path/to/tofile"; for moving files use "mv /path/to/fromfile /path/to/tofile". You can also use relative paths in either command.

> 8. How do i get a listing of my drives in my computer?

your "/media" folder contains things that are automounted after boot, like removable media. To get a list of block devices, you can do "ls /dev/?d*" which will list everything with the second character "d". Your hard drives are usually "hd" and then a letter, or "sd" and then a letter. Floppy drives are usually "fd", and "cdrom" should show up in here too.

To see where things are mounted (so that you can read/write to them), type "mount" with no arguments.

> 9.What is the main directories in linux, by the looks of things all config files are installed in /etc/"APP NAME"

[Look here for a list]("http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html").

Your normal user access is to /home/your-user-name, so this is where most of your personal files will be.

> 10. how do i access my cd rom?

Cdrom's are usually automounted to /media/cdrom, so change directory to that. If you're having trouble, "cd" to the /media directory and use "ls" to see what directories are currently mounted.

> 11. am i able to write cd's with this version of ubuntu

I'm unsure if Ubuntu Server has cd burning software, but if you have a Gnome Session, I strongly suggest looking through Add/Remove software under Applications->Add/Remove. There are plenty of very good utilities to do this.

> 12. will a windows computer be able to access this computer over a network without samba installed?

Samba is used by the linux machine to access Windows Shared folders. This means that Windows has Samba by default. If your linux machine does not have Samba, it will not prevent windows machines from connecting to other services (ftp, etc) but will prevent you from running a Samba (windows shared) directory.

---

### Post by AnthonyArde2 on 2008-04-02
Thanks all for your assistance it has assisted alot!
i have chosen to use 7.10 server because i didnt know any better :) hahaha
i have used the desktop version before and it is very easy, i thought the server version would use less resources and have additional security features, if this is not the case then i will install the gui. am i able to swap between the two - ie: have the vanilla server text interface and change to gui with the same installation?

Where can i download just the gui to add this on? i would prefer it if i didnt have to re-install my server as i have set it up with apache, php, mysql, postfix and done all the ssl certificates already.

thanks again

---

### Post by louieb on 2008-04-02
> **AnthonyArde2 said:**
> ...Where can i download just the gui to add this on? ...

If you want to see what is available in the way of meta packages for your server use:
```
sudo tasksel
```or for a full desktop
```
sudo apt-get install ubuntu-desktop

```and because its Linux you have a lot of options Heres some light weight GUIs you can add to your server and try.
[Installation/LowMemorySystems - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

---

