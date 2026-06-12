---
title: "Basic Commands"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by nikolas68 on 2007-11-20
I've made these notes for me but i guess they could be handy for other beginners too:


What in Windows is the "C:\" drive, in Ubuntu is "/"  or the root.
You can switch to the root of the file system by typing the following shell command:
```
cd /
```
When used on its own, the forward slash is interpreted as a shortcut for root.
To get help for a command type:

--help   after the command
```
ls --help
``` will get you help for the listing command


In addition, most commands have manuals that you can read to gain a fairly complete understanding of how they work. Virtually every Ubuntu setup has a set of these man pages, which can be accessed by typing this:
```
man <command>
``` 
Some commands also have info pages, which offer slightly more down-to-earth guides. You can read these by typing this:
```
info <command>
```
Note that both man and info have their own man and info pages, explaining how they work. Just type man man or info info.

```
Command                  Linux Shell Usage
                      
Copy files                           cp <filename>   <newlocation>
Move files                           mv <filename> <new location>
Rename file                        mv <old filename> <new filename>1
Delete files                         rm <filename>2
Create directories               mkdir <directory name>
Delete directories                rm –rf <directory name>
Change directory                 cd <directory name>
Edit text files                       vi <filename>
View text files                      less <filename>3
Print text files                      lpr <filename>
Compare files                      diff <file1> <file2>
Find files                               find –name <filename>
Check disk integrity               fsck4
View network settings            ifconfig
Check a network                    ping <address>
connection
View a network route             tracepath <address>
Clear screen                         clear
Get help                               man <command>5
Quit                                      exit
```
___________________________________________________________
1 The BASH shell offers a rename command, but this is chiefly used    to rename many files at once.
2 To avoid being asked to confirm each file deletion, you can add the -f option. Be aware that the rm command deletes data instantly, without the safety net of the Recycle Bin, as with the GNOME desktop.
3 Use the cursor keys to move up and down in the document. Type Q to quit.
4 This is a system command and can be run only on a disk that isn’t currently in use. To scan the main partition, you’ll need to boot from the installation CD and select the rescue option. Then issue the fsck command.
5 The info command can also be used.


Another useful command for dealing with files is cp, which copies files. You can use the cp command in the following way:
```
cp myfile /home/nicola
```
This will copy the file to the location specified.
One important command-line option for cp is –r. This stands for recursive and tells BASH that you want to copy a directory and its contents (as well as any directories within this directory).
Most commands that deal with files have a recursive option.
Only a handful of BASH commands default to recursive copying. Even though it’s extremely common to copy folders, you still need to specify the -r command option most of the time.
One curious trick is that you can copy a file from one place to another but, by specifying a filename in the destination part of the command, change its name. Here’s an example:
```
cp myfile /home/nicola/myfile2
```
This will copy myfile to /home/nicola but rename it as myfile2. Be careful not to add a final slash to the command when you do this. In the example here, doing so would cause BASH to think that myfile2 is a directory.
This way of copying files is a handy way of duplicating files. By not specifying a new location in the destination part of the command, but still specifying a different filename, you effectively duplicate the file within the same directory:
```
cp myfile myfile2 
```
This will result in two identical files: one called myfile and one called myfile2.

The mv command is similar to cp, except that rather than copying the file, the old one is removed.
You can move files from one directory to another, for example, like this:
```
mv myfile /home/nicola/
```
You can also use the mv command to quickly rename files:
```
mv myfile myfile2
```

Removing a file is achieved by typing something like this:
```
rm myfile
```
You’ll be asked to confirm the deletion after you issue the command. If you want to delete a file without being asked to confirm it, type the following:
```
rm –f myfile
```
The f stands for force (that is, force the deletion) If you try to use the rm command to remove a directory, you’ll see an error message. This is because the command needs an additional option:
```
rm –rf mydirectory
```
As noted earlier, the r stands for recursive and indicates that any folder specified afterwards should be deleted, in addition to any files it contains.

Another handy command is cd, for change directory. This lets you move around the file system, from directory to directory. Say you’re in a directory that has another directory in it, named mydirectory2. Switching to it is easy:
```
cd mydirectory2
```
But how do you get out of this directory once you’re in it? Try the following command:
```
cd ..
```
The .. refers to the “parent” directory, which is the one containing the directory you’re currently browsing. Using two dots to indicate this may seem odd, but it’s just the way that Ubuntu (and Unix before it) does things. It’s one of the many conventions that Unix relies on and that you’ll pick up as you go along.

You can create directories with the mkdir command:
```
mkdir mydirectory.
```

When using ls -l command we list all the files (directory) available. They will appear in different colours:

```
Black text                                     Standard file
Light-blue text                              Directory
                                            
Black outline with yellow text       Virtual device1
                                             
Green text                                   Program or script2
                                             
Cyan text                                     Symbolic link to another file3
Pink text                                       Image file
Red text                                        Archive4
```
__________________________________________________________
1 This is found only  in the /dev directory.
2 Technically speaking, green text indicates a program or script that has merely been marked as
  being executable.
3 This is similar to a Windows desktop shortcut.
4 Installation files are also marked red because they’re usually contained in archives.

The command sudo(superuser do) will let you adopt root powers at the shell prompt—simply preface any command with sudo in order to run it with root privileges.
 If you’re an experienced Linux user and want to invoke the root account, simply type the following at the command prompt:
```
sudo passwd root
```
Then type a password. If you subsequently want to deactivate the root account, type this:
```
sudo passwd –l root
```

When you issue the ls -l command, each file is listed on an individual line. Here’s an example of one line of a file listing from my test PC:
-rw-r--r--      2 nicola nicola 673985982 2007-10-31 17:19 myfile
 The r, w, and – symbols on the very left of the listing indicate the file permissions. The permission list usually consists of the characters r (for read), w (for write), x (for execute), or - (meaning none are applicable).
 They’re followed by a number indicating the link count, which you can ignore. After this is listed the owner of the file (nicola in the example) and the group that he belongs to (nicola). This is followed by the file size (in bytes), then the date and time the file was last accessed, and finally the filename itself appears.

If you download a program to install on your computer, it can lose its executable status while in transit. In this case, issue the following command: (change modality)
```
chmod +x myprogram
```

To (find) locate a file:
```
locate myfile
```
It’s possible to update the locate database manually, although this might take a few minutes to work through. Simply issue the command:
```
sudo updatedb
```

One other command worth mentioning in the context of searching is whereis. This locates where programs are stored and is an excellent way of exploring your system. Using it is simply a matter of typing something like this:
```
whereis cp
```
This will tell you where the cp program is located on your hard disk. It will also tell you were its source code and man page are located (if applicable). However, the first path returned by the search will be the location of the program itself.

Hope this will help some of you...long life Ubuntu :)

---

### Post by nick_h on 2007-11-20
A nice guide for beginners.

I have a couple of comments.

> You&#8217;ll be asked to confirm the deletion after you issue the command. If you want to delete a file without being asked to confirm it, type the following:
By default rm does not ask you to confirm before deletion.  You need to use the -i option for this. Do you have an alias defined?

The colours for ls are also provided by an alias but one is defined by default.

The only other comment is that vi is not a very friendly editor for beginners.  They might not even work out how to exit the file.

---

### Post by Dr Small on 2007-11-20
Vi is more powerful, as I have heard, but nano is simpler and more down to earth for simple editing.

---

### Post by MegaJim on 2007-11-20
> **nick_h said:**
> 
The only other comment is that vi is not a very friendly editor for beginners.  They might not even work out how to exit the file.

hehe :) that was me for awhile, a really good beginning text editor which is installed around a lot of systems and even works through ssh most of the time is midnight commander... well its technically a file manager, but its got a really simple to use editor built in :)

```
mc
```

---

### Post by Bigbird999 on 2007-11-20
Nicolas  Excellent newb guide!!!!   THANKS!!!!!!!!!

Mods you should make this a sticky!!!!  

BB

---

### Post by fiskking on 2007-11-20
I am printing this rite now for a reference...thanks nikolas:popcorn:

---

### Post by Zyphrexi on 2007-11-20
I request a sticky as well. very informative, and useful even for me.

---

### Post by eeeandrew on 2007-11-22
I have been having trouble running a bash script. the script is meant to convert a .lit ebook into a web browser page for easy reading. I got the script and the clit12 exe file from the thread "Ebooks .lit reader for linux". I can't seem to get ubuntu run the "cleanlit.sh" script as a command. any ideas?

thanks in advance

---

### Post by skyjacker on 2007-11-22
Nice job! Thank you.:)

---

### Post by mubelhor on 2007-11-22
This is a very nice reference to have.

---

### Post by Incense on 2007-11-22
Thanks for sharing this. This is a great linux guide in general. Nice work!

---

### Post by mahiyar on 2007-11-22
A very nice and brief Howto, I feel however one word of caution needs to be added is to avoid using fsck command on a windows filesystems.

---

### Post by Brindled on 2007-11-22
what are some update commands? 

i remember seeing a command someone said to use daily, or that they told users on their network to do daily. But for the life of me, i can't find this command again. i had it bookmarked, but i reinstalled ubuntu, and lost the bookmark.

are there commands that can update things easily?

thanks in advance

---

### Post by Brindled on 2007-11-22
found it (not exactly sure what they all do though):


> **ubuntu_demon said:**
> 
apt-get update
apt-get upgrade -t hoary-security -y
apt-get upgrade --trivial-only
apt-get autoclean



---

### Post by bitterbug on 2007-11-22
I'd like to suggest two more additions:

```
cd ~
```
The tilde is a shortcut for the users home directory.

```
pwd
```
Short for 'print working directory', displays the current location of the user within the file system.

---

### Post by hogwartsnigel on 2007-11-24
Thanks Guys I've found this really useful for a newb invaluable to have simple intro

Thanks again

Nigel

---

### Post by LaRoza on 2007-11-24
> **nikolas68 said:**
> 
What in Windows is the "C:\" drive, in Ubuntu is "/"  or the root.


This is untrue. In Windows, there is nothing like root (/). C: in Windows is the partition that Windows is installed on. In Linux all files are in /, and everything is a file, including drives and directories.

---

### Post by NewDisciple on 2007-11-24
Neat tutorial!  I would recommend that new users should print this and keep it as a handy reference.

---

