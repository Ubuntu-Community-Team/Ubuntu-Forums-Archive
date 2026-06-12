---
title: "Doubts"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by infin?ty on 2006-06-21
I have a few questions about linux in general

1.) What is the executable format in linux, like its *.exe, or *.com in windows/dos and y is it different at the end of the day these are machine instructions right?? So whats the difference?, and how can i execute windows executables in linux(just a curiosity :) )

2.) When i compile a program thru gcc, the a.out file generated, what is it?? Is this the executable format??

3.) Why do we need to add ./ to execute something(i may be wrong here!!), and what exactly happens by puting a ./

4.) As far as i remember ubuntu provides an option of formating the disk as FAT32, so if i do that will i be able to access my stuff on the windows drives(as of now it is only in read only mode), otherwise is there any other method to use m windows drives.

I have lots of doubts but i guess these are the main ones...

---

### Post by rbalfour on 2006-06-21
[QUOTE=infin?ty]I have a few questions about linux in general

1.) What is the executable format in linux, like its *.exe, or *.com in windows/dos and y is it different at the end of the day these are machine instructions right?? So whats the difference?, and how can i execute windows executables in linux(just a curiosity :) )
[/quote]

.bin .run .sh .pl depends on the package. You can run windoze apps either via WINE ([www.google.com](www.google.com)) or VMWARE ([www.google.com](www.google.com))


> 
2.) When i compile a program thru gcc, the a.out file generated, what is it?? Is this the executable format??


[http://en.wikipedia.org/wiki/A.out](http://en.wikipedia.org/wiki/A.out)

> 
3.) Why do we need to add ./ to execute something(i may be wrong here!!), and what exactly happens by puting a ./

./= current location
This is down, so it won't use the search path of the shell

> 
4.) As far as i remember ubuntu provides an option of formating the disk as FAT32, so if i do that will i be able to access my stuff on the windows drives(as of now it is only in read only mode), otherwise is there any other method to use m windows drives.

U can use M$-networking to access those files or enable NTFS write.

Going from Windoze to Linux is not straight forward.
Just like going from Windoze to Bapple...

Linux gives freedom of choice.
I have lots of doubts but i guess these are the main ones...[/QUOTE]

---

### Post by anaconda on 2006-06-21
1.) executable files dont have any *.exe or similar endings. Any file can be marked as executable regardress of the name. if you type "ls -la" in terminal, you can see if a file is executable.. And if you have a file, that should be executable, but it isn't marked as such, then you can't execute it...

2.) a.out is just a default filename for the compiled file (you can specify any filename for gcc to be the output filename..

3.) ./ means that you mean the current directory. Usually the current directory is in your PATH, but if it isn't then you DO have to add ./ in front of the file you want to run..  If you add ./ to your path it is a good idea to put it first. Otherwise if in some other directory in the PATH there is a file with the same filename, then it is run instead... 

4,) if you make a fat32 partition then you can access it read/write from both linux and windows. One other solution is to install 
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)
to your windows, so that you can read/write your ext3 linux-partitions from windows..

---

### Post by wylfing on 2006-06-21
[QUOTE=anaconda]
3.) ./ means that you mean the current directory. Usually the current directory is in your PATH, but if it isn't then you DO have to add ./ in front of the file you want to run..  If you add ./ to your path it is a good idea to put it first. Otherwise if in some other directory in the PATH there is a file with the same filename, then it is run instead... 
[/QUOTE]

A correction: it's just the dot that means "current directory" -- the slash is just to separate the directory name from the file name.

And much more importantly: do **not** add the dot symbol to your PATH. That is bad security practices. For one, it allows for "shadow" programs, for example someone naughty could put a fake program named 'bash' in your home directory and you'd run it instead of the real shell.

---

### Post by steve.horsley on 2006-06-21
[QUOTE=infin?ty]I have a few questions about linux in general

1.) What is the executable format in linux, like its *.exe, or *.com in windows/dos and y is it different at the end of the day these are machine instructions right?? So whats the difference?, and how can i execute windows executables in linux(just a curiosity :) )
[/QUOTE]
Executable files don't normally have an extension. For instance, ls (list files), eject (eject the CD), reboot are all executables. Whether a file is executable is a propertuy of the file in the same wa that whether a file is writeable or readable is. Google for "linux file permissions". Also, an executable need not be a binary - it could be a script (like a batch file). Scripts normally start with a line like:
**#! /usr/bin/perl**
or 
**#! /bin/sh**
which says what interpreter program to use to run them.
> 
2.) When i compile a program thru gcc, the a.out file generated, what is it?? Is this the executable format??
 Yes, it is executable. You can always ask what type of file any file is, using the command:
**file a.out**
> 
3.) Why do we need to add ./ to execute something(i may be wrong here!!), and what exactly happens by puting a ./

. is your current working directory. This is not normally in your search path (the lict of directories to search for a command)  in unix systems like it is in DOS. So ./filename  means "the file called filename in my current directory".
> 
4.) As far as i remember ubuntu provides an option of formating the disk as FAT32, so if i do that will i be able to access my stuff on the windows drives(as of now it is only in read only mode), otherwise is there any other method to use m windows drives.
To format a FAT32 disk, the command is something like
**mkfs.vfat /dev/hda1**
Replace /dev/hda1 with the appropriate partition name. mkfs is short for "make filesystem" and equates to DOS format.

Linux cannot write to NTFS partitions although it can read them, so a shared FAT partition is a good way to go. You cannot install the Linux system on a FAT drive though - FAT can't store the file permissions. I gather there is a windows driver available that allows it to read/write ext2/3 Linux partitions.

---

### Post by infin?ty on 2006-06-21
Hey, thnks a lot ppl, i think i am getting it.

But one doubt is there, tht y then the .exe's and .com's dont execute on linux(or do they??). And wat changes do we need to make 'em execute (in other words what wine does internally??)

One more problem i have an ADSL modem and the network adapter is 
RTL8139D PCI Fast Ethernet Adapter, ubntu is not recognizing this (i tried using pppoeconf), it says try modconf but bash says modconf command doesnt exist.
I got the drivers to this card on a floppy, and there were drivrs fro linux also(a C src file and a makefile), but wen i say make there are loads of errors in the C file itself and i am not able to correct them. So wat shld i do. Currently i am accessing internet thru windows and then to make any changes i have to go back to ubuntu its proving quite irritating.

---

### Post by infin?ty on 2006-06-21
One more thing, how do i install KDE on ubuntu.

---

### Post by steve.horsley on 2006-06-21
Wondows .exe files are just binary files to Linux. You need wine to run them like this:
**wine myprog.exe**
I have no idea how it works internally, but I know it creates a dummy drive c in the .wine folder. Yuk. 

Can't help you with the ethernet adapter. I would have thought that one was supported - I had an 8139 based card ages ago - before Ubuntu existed. No probs, although I used an Ethernet ADSL router not some weird modem.

To install KDE, install kubuntu-desktop either using synaptic or from the command-line:
**sudo apt-get kubuntu-desktop**
Of course if you only want KDE you could always use a Kubuntu installer CD instead.

---

### Post by u.csantiago on 2006-06-21
[QUOTE=infin?ty]I have a few questions about linux in general

1.) What is the executable format in linux, like its *.exe, or *.com in windows/dos and y is it different at the end of the day these are machine instructions right?? So whats the difference?, and how can i execute windows executables in linux(just a curiosity :) )

2.) When i compile a program thru gcc, the a.out file generated, what is it?? Is this the executable format??

3.) Why do we need to add ./ to execute something(i may be wrong here!!), and what exactly happens by puting a ./

4.) As far as i remember ubuntu provides an option of formating the disk as FAT32, so if i do that will i be able to access my stuff on the windows drives(as of now it is only in read only mode), otherwise is there any other method to use m windows drives.

I have lots of doubts but i guess these are the main ones...[/QUOTE]

I am a newbie linux administrator but i am an old unix user. Your questions are about Unix in general.  Hope i can help you. 

**1.) Executable differentiation and file tags**

In Unix the executable differentiation is NOT done by an extension but by a file tag. The tag 'x'

If you give executable permissions to a text file, that file will work as a batch file (*.BAT in DOS)

In Unix you have 3 file tags: (R)eadable, (W)ritable and e(X)ecutable
This tags are used to define the user permissions. 

Each file have 3 groups of tags, for: (U)ser, (G)roup and (O)ther
Making a total of 9 flags. 

If you make 'ls -l' you see the flags. For example
-rwxrwxrwx foo1
means that the file 'foo1' has Readable, Writable and eXecutable permission for User (the file owner), Group (the group of users that the file owner belongs), and Others (the rest of the users)

-rw-r--r-- foo2
means that the file 'foo2' has no executable permissions. Is has Read and Writable for the User (file owner), and only Read permissions for the rest of the users.

Making 'chmod g+w foo2' gives write permission to the user group
-rw-rw-r-- foo2

Making 'chmod o-r foo2' takes out the read permission to other users
-rw-rw---- foo2


Now, if you look at each group of tags as 1 or 0, the previous example came like
-110110100 foo2
converting each group of tags to decimal, came
- 6  6  4  foo2

So this permissions can be set making
chmod 664 foo2

The owner of a file can be changed by using 'chown'
chown [OWNER][:GROUP] file

**2.) a.out**
'A.OUT' is only the compiler's default output filename. With the option -o you may change the output filename.
Make for example: gcc source.cpp -o foo
Then to run the executable file you have to type ./foo

**3.) ./ and ../**
As in Windows/DOS, '.' represents the current directory and '..' represents the uplevel directory that contains the current.  
For security reasons you cannot run executables located at the current folder, unless you explicitly say it.
When you write './program' you are explicitly saying that you want to run the file 'program' that is located in your current directory.
Only the files that are located in the directories listed in the path environment variable (type 'echo $PATH') can be executed without explicit saying their location. Usually also each user has its own executable directory in the $PATH ( usually /home/user/bin)

**4.) You may access FAT32 partitions with no problem. And with write permissions!**
For that you dont need to format your main linux partition in FAT32 to have access to your Windows FAT32 partitions.

Before I explain you the procedure, let me tell you that in Unix (or Linux) you dont have drive letters like A: C: or D:
Every drive is accessed from the root directory '/'. For example the CD-Rom is usually accessed from /mount/cdrom, and the floppy drive is accessed from /mount/floppy. The directory /mount is usually used for the not permanent devices, but you can use other.

Now the procedure to access your windows partitions:

i)  Make a mountpoint. That is just a directory!
    For example 'mkdir /mount/windows'

ii) Find your windows partition device path

    Your windows device path depends on two things:

    - first, the controller in which your hard drive is connected. (/dev/hda, /dev/hdb, /dev/hdc or  /dev/hdd)

      For IDE disks it works like this
        /dev/hda -> Master in first IDE controller
        /dev/hdb -> Slave  in first IDE controller
        /dev/hdc -> Master in second IDE controller
        /dev/hdd -> Slave  in second IDE controller

    - second, the number of the partition in the hard drive. 

      You can see the partition map (by using for example '/sbin/sfdisk -l /dev/hda'),
      or you can try mount them sequentially (just remember that extended partitions start from 5)

iii) Mounting the partition

    Type 'mount -t vfat <mountpoint> <device_path>'

    For example (assuming is connected to the controller /dev/hda):
        mount -t vfat /mount/windows /dev/hda1  -> if windows/DOS is the 1st partition of your hard drive
        mount -t vfat /mount/windows /dev/hda2  -> if windows/DOS is the 2nd partition of your hard drive

    If it gives an error like:

        mount: wrong fs type, bad option, bad superblock on /dev/hda1,
               or too many mounted file systems

    Just try the next one until you find it!
    When is just dont output any error, you are on!

iv) Accessing files
    Your windows 'C:\' are now accessable from '/mount/windows'

v)  Permanent access to windows partition
    You can set this mountpoint to be permanent by adding a line to the file /etc/fstab with:

	<device_path>	<mountpoint>    vfat    	defaults       	0 	0

    For example
	/dev/hda1	/mount/windows  msdos    	defaults       	0 	0


More info ....

**5.) Executable Format vs Filename extension**
It seems to me that you are confusing executable file formats and file extensions. 
Even in windows, you dont make an executable file just by changing its name into something.EXE.
You have to compile a source code to make an executable file. You have to do the compiling procedure for every Operating System (OS).

The executable binaries in Unix and Windows are diferent. 
     In Unix you can name a file as you want, for example you can name a TEXT file as 


**6.) Data files .vs. Compiled files (executable binaries)**
You can use data files from any OS into any OS.
As data file I am talking about text files (.TXT), images (.JPG, .GIF), sound files (.WAV, MP3), movies (.AVI, .MPEG), etc. You shouldnt have problems in working with this files in any OS like Unix, Linus, Windows/DOS, Mac OS, ...

However, except for JAVA binaries, you cannot use executable files compiled for one OS in another OS.
As I said, except for JAVA, thats why JAVA is said to be plataform independent. 

As told in 4) you can use an emulator

**7.) Microsoft Office files**
You may face some problems in using .DOC or .XLS files in Unix (or Linux), but only because you dont have a Microsoft Office for this OS.
Some office suits like Open Office can open Microsoft Office files, but it always go through a conversion process.
We hope OpenDocument Format (.ODF), see [www.odfalliance.org](www.odfalliance.org), change this! ;-)


**8.) Running Windows executables in Unix**
Yes, it is possible to run Windows binaries on Linux through emulators like Wine, but it is not recommend!

If you want to change to Linux to keep running the same *.EXE from of windows, do yourself a favor and dont change.
When you decide to change to Linux search for the Linux native programs. You have programs for everything.

Wine emulation degrade your PC performance. There is a new project for DOS emulation named [http://www.alkyproject.com/](http://www.alkyproject.com/), but i didnt try it yet.

---

### Post by H.E. Pennypacker on 2006-06-21
There is a big difference between .EXE and Linux executables.  With Linux executables, you may not have everything you need, and if you don't have what you need, you need to download whatever it is.  With .EXE (Windows), everything that you need (dependencies) come with the .EXE.  Not only that, .EXE usually come with userfriendly GUIs.  You'll remember that most look like this:

[http://farm.tucows.com/2005/02/bitrock_windows.gif](http://farm.tucows.com/2005/02/bitrock_windows.gif)

Say you download a .DEB package.  You won't actually be able to double-click on it and have the file take care of everything.  You need something else to run the .DEB package, and you'll have to hope everything goes right.  It's really difficult to NOT get through the installation of an .EXE.  Try, for example, installing Macromedia Flash Player in Windows - real easy, because there's an installer that does everything for you.  On the other hand, try download Macromedia Flash Player in a Linux distro.  You simply won't be able to, with the exception of using something like Synaptic, install it without using the terminal.

See the difference?  Huge.  If I ever will be able to program in Linux, my first priority will be creating an equivalent of an .EXE installer so that people don't have to use centralised package handlers such as Synaptic.

---

### Post by infin?ty on 2006-06-21
> It seems to me that you are confusing executable file formats and file extensions.
Even in windows, you dont make an executable file just by changing its name into something.EXE.
You have to compile a source code to make an executable file. You have to do the compiling procedure for every Operating System (OS).

The executable binaries in Unix and Windows are diferent.
In Unix you can name a file as you want, for example you can name a TEXT file as


No no i am not getting confused in that, but i think i was not clear the first time. What i anted to ask is what is the basic structural difference in windows/dos executables and unix/linux executables.


And please someone help me wid my internet problem, its proving to be a real pain.

---

### Post by steve.horsley on 2006-06-22
As far as I knowm the structure of the files is similar. They will have headers, constant sections, code sections etc. But the detailed format is different I guess, and of course all the system calls will be different.Instead of DLL files, unix has .so  (shared object) files.

As for internet problems, I suggest you start a new thread and ask that question again. Putting more than one subject in a thread very often leads to one subject being overlooked by the respondents.

---

### Post by infin?ty on 2006-06-23
I have reported it in a new thread but no help.

---

