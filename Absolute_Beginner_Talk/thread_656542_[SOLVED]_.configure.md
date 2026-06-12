---
title: "[SOLVED] ./configure"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Arcnsparc on 2008-01-02
My first post, I made it for 3 months before having to ask!  Thankfully Ubuntu Gutsy is so easy...

I am having a problem with this command: ./configure
I cant instal .tar or .tar.gz because it wont configure, i keep getting this:

jake@MultiVAC:/$ ./configure
bash: ./configure: No such file or directory

I don't know what to do!  I was thinking that maybe I was missing some needed tools or something.  
Its not a hardhare thing but you guys like to know what the askers are running so it is a Lenovo Thinkpad R60 with Gutsy 7.10 custom university install(that may be why I am missing the command?)

Thanks for any advice in advance
 Jake

---

### Post by llamakc on 2008-01-02
Yes. You do not compile a tar or tar.gz file. Those are compressed archives, and need to be uncompressed. You can do that from the commandline with:

tar zxvf nameof.tar.gz

or with file-roller (the archive/unarchive GUI).

Here's a howto on compiling:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by ~LoKe on 2008-01-02
You have to extract it.

```
tar xzvf nameofarchive.tar.gz
```
Then you'd cd into the directory...
```
cd nameofarchive
```
then...
```
./configure
make
sudo make install
```

---

### Post by aeiah on 2008-01-02
just to add to this thread, the ./ bit in ./configure is essentially an execute-the-script command. you may find if you're installing flash, for example, that you'd have to execute flash-install.sh (with ./flash-install.sh), or other such things. but most of the time it's ./configure followed by make and sudo make install. it usually tells you in the archive's readme if you need to do something else.

i always open tar.gz files like i used to open .zips in windows, just by double clicking and extracting. i always forget the order of the letters xzvf :p

---

### Post by Borbus on 2008-01-02
The ./ is because in bash, and most shells, when you type something, it searches for an internal command first and then it searches your paths. Your paths include /bin and /usr/bin which is where most programs are (coreutils in /bin) so that's why you can just type "rm" to run /bin/rm. For everything else you have to type a whole path, . is the current dir, so it's a whole path. You can add . to your paths but it is a bit of a security risk.

---

### Post by Arcnsparc on 2008-01-02
Thanks for all of the help so far!

Im still not getting it to work though, i have decompressed the Tar file, poweriso-1.1.tar.gz to poweriso in this case.  I tried ./poweriso to see if that would configure it and it did something, but i think it just told me about the file:

jake@MultiVAC:~/Desktop/poweriso$ make poweriso
make: Nothing to be done for `poweriso'.
jake@MultiVAC:~/Desktop/poweriso$ make
make: *** No targets specified and no makefile found.  Stop.
jake@MultiVAC:~/Desktop/poweriso$ ls
poweriso  poweriso-1.1.tar.gz
jake@MultiVAC:~/Desktop/poweriso$ ./poweriso

PowerISO   Copyright(C) 2004-2006 PowerISO Computing, Inc
            Type poweriso -? for help

jake@MultiVAC:~/Desktop/poweriso$ ./configure
bash: ./configure: No such file or directory
jake@MultiVAC:~/Desktop/poweriso$ ./configure poweiso
bash: ./configure: No such file or directory
jake@MultiVAC:~/Desktop/poweriso$ ./ configure
bash: ./: is a directory


These are all of the commands I have tried.  I am doing this so I can install a NTFS mounter so I can move files over to my little XP partition (i know i know, xp is lame but damnit im an ms excel addict for all of my spreadsheet needs)  I just installed XP yesterday and redid GRUB and all that and I thought I was home free!  Almost...

It seems that my OS doesn't know what ./configure is!

---

### Post by Arcnsparc on 2008-01-02
oh and plain old "configure" gets me this:

ake@MultiVAC:~/Desktop/poweriso$ configure
bash: configure: command not found

---

### Post by YoG%*@ on 2008-01-02
hi,

> **Arcnsparc said:**
> 
jake@MultiVAC:~/Desktop/poweriso$ ls
poweriso  poweriso-1.1.tar.gz



judging from the 'ls' output i'd say you didn't change into the directory the files were extracted to. cd into that directory (Desktop/poweriso/poweriso) and try again.

hth,
mux

[edit]
more info on installing software: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[/edit]

---

### Post by Borbus on 2008-01-02
Well "configure" doesn't work because, as I said, it isn't in any of your paths. If bash says no such file or directory then it means the file doesn't exist. Some things don't use a configure script. Type ls and, if necessary, show the output here.

Also, have you read the readme or install file which probably comes with it?

---

### Post by Steveway on 2008-01-02
Why not use the normal way? Throw away what you allready downloaded and use this HowTo:
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by Arcnsparc on 2008-01-02
Cool!  I get that whole ./ thingy now, it RUNS something.  Okay now the extracted file didnt make a directory, only a "application/x-executable" according to the file properties.  I tried to just open it but it didnt do anything.  i can run it through the terminal but that wont install it either, it just brings up this:

jake@MultiVAC:~/Desktop/poweriso$ ./poweriso

PowerISO   Copyright(C) 2004-2006 PowerISO Computing, Inc
            Type poweriso -? for help

jake@MultiVAC:~/Desktop/poweriso$ ./poweriso -?

PowerISO   Copyright(C) 2004-2006 PowerISO Computing, Inc
            Type poweriso -? for help

Usage:    poweriso <command> [parameters] [-switches]

<Commands>

 list <image file> <directory>    List files and directories in image file.
     Example:  List all files and directories in root direcory of /home/sam/test.iso .
     Command:  poweriso list /home/sam/test.iso / -r

 extract <image file> <dir/file name>   Extract files/directories from image file.
     Example:  Extract all files and directories in root direcory of /home/sam/test.iso
               to /home/sam/test recursively.
     Command:  poweriso extract /home/sam/test.iso / -od /home/sam/test

 convert <image file>    Convert image file to other format.
     Example:  Convert /home/sam/test.daa to standard iso file 
     Command:  poweriso convert /home/sam/test.daa -o /home/sam/test.iso -ot iso

<Switches>

 -r             List or extract recursively.
 -o             Specify output image file name.
 -od            Specify output folder.
 -ot <iso|daa|bin>    Specify output image file type. If not specified, 
                the image type will be determined by file name suffix.
 -volsize <n>   Split output image file to multiple volumes, and set volume
                size to <n>. Example: -volsize 100M
 -setpassword <password>   Set password for output image file. 
                Example: -setpassword 12345678



Maybe I need to get myself a copy of the configure script and put it where is belongs?

---

### Post by fenian on 2008-01-02
I took a look at that program it's not a source file so it doesn't need to be compiled.Apparrently you use it from the command line you can look at the guide [here.]("http://www.cyberciti.biz/faq/how-do-i-open-daa-direct-access-archive-files-under-linux-or-unix-oses/")

---

### Post by Arcnsparc on 2008-01-02
Thanks for all of your help guys, ive been to afraid to ask on the forums for a long while and it is nice to see how amazingly helpful everyone is.  Hopefully I can get good enough to return the favor to new users!

---

### Post by Sockerdrickan on 2008-01-02
:lolflag: You tried to compile an archive that contains a binary file?

---

### Post by Arcnsparc on 2008-01-02
Hahahaha, yeah I did...

And kids, we all learned something this episode.  I learned that a binary is just ran right through the command line, and that the Ubuntu forums weren't such a scary place after all.  The only thing I haven't learned is how to mark my thread closed....  I don't want to leave it hanging.

---

### Post by cjm5229 on 2008-01-02
Why not just go to Add/Remove and search for NTFS Configuration Tool and install it? If you use programs from the repositories instead of trying to compile them you will get updates and be able to upgrade a lot easier. Most Apps are in the repositories these days, and if not there is probably something else that will work better. I would also bet that if you worked with OpenOffice.org Spreadsheet a bit and got used to it you would find that you could live quite well without Excel. 
Good Luck and I'll bet you give up on Windows altogether in another six months:)

---

### Post by cjm5229 on 2008-01-02
I guess ISO Master might be more along the lines of Power ISO. and $30.00 cheaper.

---

### Post by Sockerdrickan on 2008-01-03
PowerISO is freeware for Linux afaik I have the binary too (for daa decompression)

---

