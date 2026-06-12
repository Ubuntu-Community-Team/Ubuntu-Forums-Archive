---
title: "Lots of help needed"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by Bobo K on 2006-10-04
I installed Ubuntu yesterday, and I really like it. But there are some things I really need help with;

1) How do I access other disks? When I try, I only get a message like "can't mount volume - error: /dev/hdb1 isn't portable - error: couldn't run pmount".

2) How do I install .tar.gz files? In this case Macromedia Flash and OSS sound card drivers.

I know it was something more I was going to ask, but I forgot what it was. Also, this is my first experience with any OS other than Windows, so please explain as thoroughly as possible.

---

### Post by CatKiller on 2006-10-04
> **Bobo K said:**
> I installed Ubuntu yesterday, and I really like it. But there are some things I really need help with;

1) How do I access other disks? When I try, I only get a message like "can't mount volume - error: /dev/hdb1 isn't portable - error: couldn't run pmount".

[Mounting Windows Partitions in Ubuntu]("http://www.psychocats.net/ubuntu/mountwindows").

> 2) How do I install .tar.gz files? In this case Macromedia Flash and OSS sound card drivers.

[Install software]("http://www.psychocats.net/ubuntu/installingsoftware")
[Install Flash]("http://www.psychocats.net/ubuntu/flashubuntu")

> I know it was something more I was going to ask, but I forgot what it was. Also, this is my first experience with any OS other than Windows, so please explain as thoroughly as possible.

Those links should give you lots of useful information. Welcome to the community.

---

### Post by bswilson on 2006-10-04
> **Bobo K said:**
> 1) How do I access other disks? When I try, I only get a message like "can't mount volume - error: /dev/hdb1 isn't portable - error: couldn't run pmount".

2) How do I install .tar.gz files? In this case Macromedia Flash and OSS sound card drivers.

1. Can you tell us more about /dev/hdb1?  Is that a USB drive or an external drive of some sort?

2. A file ending in .tar.gz is a TAR file (originally called a Tape ARchive) which is like a Zip file on Windows without compression.  The .gz extension after that means that the file is compressed with a program called gzip.  So basically you have a compressed archive.

To install it, you have to uncompress the file, then extract the files from the archive.  I think that the easiest way is to do this at the command line.  For example, if you have the file foo.tar.gz, you would do this:

```
$ tar -zxvf foo.tar.gz
```

That command will uncompress the file (the -z part), then extract (-x) using the verbose method (-v, to show you what's going on), and it will preserve all the folders in the archive (-f).  From there, you will have probably a new folder with the files in it.

You might appreciate [this much better explanation]("http://monkeyblog.org/ubuntu/installing/") also.

---

### Post by carloslosgrande on 2006-10-04
B S Wilson - thats the sort of explanation I've been looking for. Can you tell the rest of us beginners where we can find more of the command syntax in just such simple and clear terms. No offence to any of the people who have been a great help to me but the commands I usually get are over my head.

---

### Post by Thenotsowyzewun on 2006-10-04
To install all sorts of software (bin, tar, etc, source etc) check this out:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

There's iterations of this all other the place (with different layouts), but I like that one.

For help working out what various commands do, well command -h or command /? usually tells you it's syntax, or for a slighter longer explanation, info command. If info command isn't enough (or isn't available, not all programs use it) try man command (that opens the manual).

Also, if you're looking for something, whereis or find are both good, and if you're looking for a tool but don't know it's name, try apropos, e.g. networking commands would be apropos network.

Remember you can copy stuff quickly by highlighting (to copy) and clicking the mousewheel (to paste), and if you've just typed a command and you got one letter out or whathaveyou, just press up (it remembers your previous 100 commands or so).

Lastly, if you're writing something (on command line, again) with a long name, press tab, it might complete it for you (if it can).

Hope that helps :D, soz for the long post in the wrong thread hehe.

---

### Post by Bobo K on 2006-10-04
> **bswilson said:**
> 1. Can you tell us more about /dev/hdb1?  Is that a USB drive or an external drive of some sort?

2. A file ending in .tar.gz is a TAR file (originally called a Tape ARchive) which is like a Zip file on Windows without compression.  The .gz extension after that means that the file is compressed with a program called gzip.  So basically you have a compressed archive.

To install it, you have to uncompress the file, then extract the files from the archive.  I think that the easiest way is to do this at the command line.  For example, if you have the file foo.tar.gz, you would do this:

```
$ tar -zxvf foo.tar.gz
```

That command will uncompress the file (the -z part), then extract (-x) using the verbose method (-v, to show you what's going on), and it will preserve all the folders in the archive (-f).  From there, you will have probably a new folder with the files in it.

You might appreciate [this much better explanation]("http://monkeyblog.org/ubuntu/installing/") also.

/dev/hdb1 is a permanent hard drive, Windows is not installed on it but I have all my music and stuff on that one.

I followed the instructions on the page you linked to, and it almost worked. I get the following message:

"OSS/Linux kernel module not available. Cannot continue.
It is likely that some important Linux packages are not
installed in your system which makes installing OSS impossible.

The Linux (RPM) packages required before OSS can be installed are
kernel-source, gcc, binutils and make. You can find them from the install CD/DVDor the web/ftp site which you used when installing the Linux distribution."

What does this mean?

---

### Post by bulldog on 2006-10-04
Normally your other partitions should be listed in /media.

You can look at your fstab to see if there is any information,but before altering you should make a copy of it.
```
sudo cp /etc/fstab /etc/fstab_backup
```
To open your fstab,
```
gksudo gedit /etc/fstab
```
To mount a partition which not already is mounted,
```
sudo mkdir /mnt/windows
```
Makes a mount folder and mounting is done by,
```
sudo mount /dev/hda1 /mnt/windows
```

If the drive is an NTFS format you should do,
```
sudo mount -t ntfs /dev/hda1 /mnt/windows
```

---

### Post by Bobo K on 2006-10-04
Alright, I did that and it created /mnt/windows, but when I click it, it says:

"The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "windows"."

---

### Post by andb on 2006-10-04
Hi bobo! Looks like you have a lot to do. Be patients, it will all work out with some time. then you'll really be in cotroll of your computer, so I think its worth it. 

First- Look at Automatix. Its a great utility to configure almost everything you need!
[http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405)

here's the line you need in /etc/fstab 
```
/dev/hda1       /PATH            ntfs    uid=1000        0       2
```

the uid or gid can be set, and should be somehting that you have rights to. The first account made is #1000, so this line should work fine


Here's my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /boot           ext3    defaults        0       2
/dev/hda9       /home           ext3    defaults        0       2
/dev/hda7       /tmp            ext3    defaults        0       2
/dev/hda8       /usr            ext3    defaults        0       2
/dev/hda6       /var            ext3    defaults        0       2
/dev/hda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda2       /home/andrew/winxp            ntfs    uid=1000        0       2
```


Its because NTFS doesnt have user privlidge info, and just gives verything to root, since you mounted as root (with sudo)

from the command line, just add -o uid=1000 to the sudo mount command.

---

### Post by bswilson on 2006-10-04
> **carloslosgrande said:**
> B S Wilson - thats the sort of explanation I've been looking for. Can you tell the rest of us beginners where we can find more of the command syntax in just such simple and clear terms. No offence to any of the people who have been a great help to me but the commands I usually get are over my head.

I'm very glad I was able to provide some help!  I have had some pretty good luck with the documentation for most programs that are mature.  You can *almost* always launch this documentation, called manual pages or "man pages" like this:

```
$ man <command>
```

So for example, you could type **man tar** and get (probably) more information than you care to read about the Tape Archive program.  And honestly, sometimes you have to play around with a command to learn how to make it do what you want.  

Is there a specific command that you've been confused about that I might be able to explain in detail?

---

### Post by Bobo K on 2006-10-04
> **andb said:**
> Hi bobo! Looks like you have a lot to do. Be patients, it will all work out with some time. then you'll really be in cotroll of your computer, so I think its worth it. 

First- Look at Automatix. Its a great utility to configure almost everything you need!
[http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405)

here's the line you need in /etc/fstab 
```
/dev/hda1       /PATH            ntfs    uid=1000        0       2
```

the uid or gid can be set, and should be somehting that you have rights to. The first account made is #1000, so this line should work fine


Here's my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /boot           ext3    defaults        0       2
/dev/hda9       /home           ext3    defaults        0       2
/dev/hda7       /tmp            ext3    defaults        0       2
/dev/hda8       /usr            ext3    defaults        0       2
/dev/hda6       /var            ext3    defaults        0       2
/dev/hda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda2       /home/andrew/winxp            ntfs    uid=1000        0       2
```


Its because NTFS doesnt have user privlidge info, and just gives verything to root, since you mounted as root (with sudo)

from the command line, just add -o uid=1000 to the sudo mount command.

Thanks, but I'm sorry to say it didn't work. This is how it looks now:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /PATH            ntfs    uid=1000        0       2
```

---

### Post by andb on 2006-10-07
What if you type ```
sudo mount -t ntfs /dev/hda1 /PATH -o uid=1000
```

What is the output? Try also, and your username is caps sensitive, ```
cat /etc/passwd | grep YOURuserNAMEhere
```

does it read ```
username:x:1000:1000...
``` If the first number is different than 1000, then thats your uid. and the mount command should reflect this.

Let me know how it goes!

---

### Post by Bobo K on 2006-10-08
Feels like I did something wrong... this it what it reads:

```
bobo@bobo-desktop:~$ sudo mount -t ntfs /dev/hda1 /PATH -o uid=1000
Password:
mount: mount point /PATH does not exist
bobo@bobo-desktop:~$ cat /etc/passwd | grep bobo
bobo:x:1000:1000:Bobo,,,:/home/bobo:/bin/bash
```

---

### Post by andb on 2006-10-10
:) the text "/PATH" is for you to choose, the path where you want it to mount.

First, make/choose a mount point. 
mkdir /home/bobo/winxp

This makes a directory where we will attache the other partition. Another typical choice would be /media/winxp (or anything in the media directory). *nix people are good about maintaining a general file structure scheme. Home would be just for your use, media is removable media shared by everyone.

Then, to mount, type 

sudo mount -t ntfs /dev/hda1 /home/bobo/winxp -o uid=1000

the drive partition will then mount (attach to) at that point, and its contents will be visible there.

another way to direct to your home directory is to use tilda (~) sou you couls also type
sudo mount -t ntfs /dev/hda1 ~/winxp -o uid=1000


edit: by the way, what you did wat to tell mount to mount the partition at a directory point in the root of the filesystem called PATH. If you made a directory at the base of your filestructure with this name, the command would have worked ;)

---

### Post by Bobo K on 2006-10-11
Great, it works now. Thanks a lot! :D 

But now I have some other problems:

1) Ubuntu shuts itself down from time to time. Not the computer (the fans keep running and the screen is still on) but only the OS. Windows doesn't do this so it's not hardware failure, and I've chosen "put computer to sleep when inactive for > never" in the Power Management menu. Still, it only seems to shut off when I'm not by the computer.

2) I can't get the sound card to work. I have an M-Audio Delta Audiophile 2496 and have to use semi-official drivers from [http://www.opensound.com](http://www.opensound.com) because of Linux. If anyone have this card and knows how to install it, that would be gold. The drivers are here > [http://www.4front-tech.com/release/oss3994c-linux-x86-v26-regparm.tar.gz](http://www.4front-tech.com/release/oss3994c-linux-x86-v26-regparm.tar.gz) , but when I try to install it I get this message:

```
root@bobo-desktop:/home/bobo/oss3994b-linux-x86-v26-regparm# ./oss-install
OSS/Linux kernel module not available. Cannot continue.
It is likely that some important Linux packages are not
installed in your system which makes installing OSS impossible.

The Linux (RPM) packages required before OSS can be installed are
kernel-source, gcc, binutils and make. You can find them from the install CD/DVDor the web/ftp site which you used when installing the Linux distribution.

Please take a look at /root/oss/logs/soundconf.log for more info.


**********************************
Post install configuration failed.
**********************************

Code=256
All OSS files have been installed. However there are some problems
with loading the driver module(s).

Please take a look at /root/oss/logs/soundconf.log for more info.
```

However, when I try to open up /root/oss/logs/soundconf.log it says "*The folder content can not be displayed. You do not have the permissions necessary to view the contents of "logs".*"

What does this mean? I really want to get the sound working.

---

### Post by andb on 2006-10-12
files in linux have permissions for the owner, for the group, and for others. if you type ls -l you will see these nine slots on the left, with - showing is not set, r/w/x means that read/write/execute is set. You can always use sudo from the command line to open something, this opens it like the superuser, root. For more linux basics, I recommend this site: [http://learnlinux.tsf.org.za/](http://learnlinux.tsf.org.za/)  go to the linux courses. Great stuff.

As for oss, its a very old standard. most machines are using ALSA. if you are using drivers that only work in oss, you'll probably only have sound from one program at a time. Meaning that if you are listening to music, you won't be able to use skype or eevn hear warning messages from another application... Ill try to look into your card later. Ive always used simple onboard sound and been satisfied. 

problem #1 is nasty. It goes into sleep or it powers down? do you have power management functions disabled in bios?

edit: [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Midiman%2FMAudio&card=Delta+Audiophile+2496.&chip=ICE1712+(Envy24)&module=ice1712](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Midiman%2FMAudio&card=Delta+Audiophile+2496.&chip=ICE1712+(Envy24)&module=ice1712)
seems to be the instructions you need to get the soudn card working with ALSA, however, its not the easiest install Ive ever seen...

---

### Post by Bobo K on 2006-10-12
> **andb said:**
> files in linux have permissions for the owner, for the group, and for others. if you type ls -l you will see these nine slots on the left, with - showing is not set, r/w/x means that read/write/execute is set. You can always use sudo from the command line to open something, this opens it like the superuser, root. For more linux basics, I recommend this site: [http://learnlinux.tsf.org.za/](http://learnlinux.tsf.org.za/)  go to the linux courses. Great stuff.

Didn't understand much of that, but thanks for the link. I'll check it out.

> **andb said:**
> As for oss, its a very old standard. most machines are using ALSA. if you are using drivers that only work in oss, you'll probably only have sound from one program at a time. Meaning that if you are listening to music, you won't be able to use skype or eevn hear warning messages from another application... Ill try to look into your card later. Ive always used simple onboard sound and been satisfied.

It's not really a problem if I can only hear the music or sound from a movie or something, I usually turn off all warning sounds and stuff anyways.

> **andb said:**
> problem #1 is nasty. It goes into sleep or it powers down? do you have power management functions disabled in bios?

The computer doesn't turn off, the fans and the lights keep working, it's just the OS. But it isn't "sleep" either, because it won't restart when pressing the power button. You have to power it down on the main switch and then start it again to get it to work. As for the bios, no, I haven't touched it (don't know how to do it). But since Windows doesn't do this on the same machine, could that really be the problem?

> **andb said:**
> edit: [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Midiman%2FMAudio&card=Delta+Audiophile+2496.&chip=ICE1712+(Envy24)&module=ice1712](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Midiman%2FMAudio&card=Delta+Audiophile+2496.&chip=ICE1712+(Envy24)&module=ice1712)
seems to be the instructions you need to get the soudn card working with ALSA, however, its not the easiest install Ive ever seen...

Thanks, but I think I'm too fresh to Linux to get it to work. I couldn't even get past the first step.

---

### Post by andb on 2006-10-13
Ok, Ill go slower :)  If you cant read log file, its usually because you dont have proper rights to it. *nix systems were designed to be used by multilple users, so isolating things has always been important. (this is one of the critical flaws of windows. Everyone can get to everything easily) So if you cant read the file, probably only the superuser, or administrator account can read it. This account's user name is almost always "root" on modern machines. This should not be confused with a filesystem root, which is the bottom of the file "tree", meaning the top directory. Well, you can switch to be the superuser, or even better we can execute one commmand with it's identity. This is the sudo command. sudo runs a command like someone else. The default is as root. So put sudo before your commands and you can read it! from the command line, try sudo less FILENAME and it'll show you the file you want. 

Stopping for a moment, given that you are a beginner, Id recommend a different plan of action. Get a cheap, normal sound card. The one you have looks really great, but if you have an industry standard sound blaster or integrated sound chip on your motherboard, more than likely ubuntu will automatically work with it perfectly. May not be as perfect as your card, but weighing the work vs sound improvement, it seems a good idea...

turn off problem - when it "turns off", lets say when it "halts" because its not really off yet :), try pressing ctrl-alt-f1. this takes you to a terminal window. ctrl-alt-f7 will take you back to the graphical interface. Does the machine go to the terminal window after it has halts?

---

### Post by Bobo K on 2006-10-13
> **andb said:**
> Ok, Ill go slower :)  If you cant read log file, its usually because you dont have proper rights to it. *nix systems were designed to be used by multilple users, so isolating things has always been important. (this is one of the critical flaws of windows. Everyone can get to everything easily) So if you cant read the file, probably only the superuser, or administrator account can read it. This account's user name is almost always "root" on modern machines. This should not be confused with a filesystem root, which is the bottom of the file "tree", meaning the top directory. Well, you can switch to be the superuser, or even better we can execute one commmand with it's identity. This is the sudo command. sudo runs a command like someone else. The default is as root. So put sudo before your commands and you can read it! from the command line, try sudo less FILENAME and it'll show you the file you want.

Yeah, I am used to Windows so I just tried to access the folder through "places" ;). Anyways, I think I understood and did it right this time, but I still can't get it working:

```
root@bobo-desktop:/home/bobo# /root/oss/logs/soundconf.log
bash: /root/oss/logs/soundconf.log: Permission denied
root@bobo-desktop:/home/bobo# sudo /root/oss/logs/soundconf.log
sudo: /root/oss/logs/soundconf.log: command not found
```

[QUOTE=andb]Stopping for a moment, given that you are a beginner, Id recommend a different plan of action. Get a cheap, normal sound card. The one you have looks really great, but if you have an industry standard sound blaster or integrated sound chip on your motherboard, more than likely ubuntu will automatically work with it perfectly. May not be as perfect as your card, but weighing the work vs sound improvement, it seems a good idea...[/quote]

I have an integrated AC97 sound card too, but that doesn't work either. If it's easier to get that one working I guess it's a temporary solution, at least. When I try to start a music file it says "Totem could not start up. Could not establish connection to sound server".

[QUOTE=andb]turn off problem - when it "turns off", lets say when it "halts" because its not really off yet :), try pressing ctrl-alt-f1. this takes you to a terminal window. ctrl-alt-f7 will take you back to the graphical interface. Does the machine go to the terminal window after it has halts?[/QUOTE]

Strangely, it just stopped doing that. I've left it going for a couple of hours now and it's still on. If it happens again, I will have that in mind though. When it happens, the screen is just black, no terminal window.

---

### Post by andb on 2006-10-14
to view a file, you must use a command to output it. "cat" will dump the text "more" will go page by page, "less" lets you scroll up and down. As the developers said, sometimes less is more. so, run with sudo and it will go like the superuser. sudo less /root/oss/logs/soundconf.log will print the log.

System > Preferences > Multimedia
Default input&output shoul be alsa

System > Preferences > Sound 
is ESD checked?

Alsa with ac97 works absolutely perfect out of the box for me, Id like to see it work for you without doing all the crazy voodoo that some people are doing. Its really unnecessary. Keeping things as simple as possible is a good habit.

---

### Post by Bobo K on 2006-10-14
There, the log file worked. It wasn't much of a help to me, though. There are errors and warnings on pretty much every line.

I never figured out how to install Alsa, so I don't have that Multimedia option in the Preferences menu.

In Sound Preferences, ESD is checked. There is no entry in the 'default sound card' list.

---

### Post by andb on 2006-10-14
are you using Ubuntu 5 (breezy) or Ubuntu 6 (dapper)? If you have the ac97 onboard chip, Im suprised it wasnt found. Could you try taking out the other sound card for a while? Is the onboard sound card possibly disabled in bios? You can get to BIOS setup usually by pressing F2 or DEL during the first stages of powering on the computer. What kind of computer do you have? If you built it yourself, who made the motherboard, then I can walk you through checking the onboard card. Im glad you are patient about this, the good thing is that afterwards you'll have a deep knowledge of how your computer works :)

---

### Post by Bobo K on 2006-10-14
I'm using Dapper. I looked in BIOS, but I couldn't find anything sound-related at all there. My computer is a home built thingie. I bought it five years ago, but I'm 95% sure that the motherboard is a QDI PlatiniX 2E-6A 845E.

And I'm glad you have the patience to guide a lost newb like me. ;)

---

### Post by andb on 2006-10-15
One of my first thoughts is some potential conflict between the cards. There are lots of good treads about sound problems. First I would try pulling the sound card and booting to the live cd (the install cd). Does sound work here?  You should here the "ubuntu sound" as it logs in. Make sure your speakers are plugged in :) In system > preferences > sound there should be a default sound card listed. what is the output of: cat /proc/asound/modules ? Did you make a fresh install of dapper or upgrade breezy?

---

### Post by Bobo K on 2006-10-15
The sound from the AC97 worked when I booted from the live cd. When I checked sound preferences, it detected three different sound devices; "Intel 82801DB-ICH4", "MPU-401 UART" and the M-Audio card. The code didn't work though, there is no 'asound' folder:
```
bobo@bobo-desktop:~$ cat /proc/asound/modules
cat: /proc/asound/modules: No such file or directory
bobo@bobo-desktop:~$ /proc/asound/modules
bash: /proc/asound/modules: No such file or directory
```
I made a fresh install of Ubuntu 6.06. When I installed it, I never tried the AC97. The first thing I did after installation was trying to install OSS to get the M-Audio card working. Coming to think of it, this was probably what messed up everything about the sound. Since then, the speaker icon (volume control) in the system tray has had a red square with a cross next to it. Clicking it gives the message "No volume control GStreamer plugins and/or devices found".

---

### Post by andb on 2006-10-15
I think you are right. There is no need to use oss now at all. And the ubuntu autodetect is marvolous. Since its tough to say what the condition of your machine is, I would probably suggest reinstalling the whole thing. Im sure its possible to sort out what you've changed, but it could be like looking for a needle in a haystack... Some advice, if you have a seperate home directory, you can reinstall, tell the installer to use the right partition as home, and use the same username. It'll have all your old user settings. 

 
I use the command 
dpkg --get-selections > /home/USERNAME/installed_packages.txt 
to get a list of all installed packages.

Then if I reinstall I can do:
dpkg --set-selections < home/USERNAME/installed_packages.txt apt-get update
      apt-get dselect-upgrade
      apt-get dist-upgrade
      apt-get upgrade 

and this way it will reload all the software you had before. Programs put configuration files into either your home, or /etc. Home configs are user specific and will still be there after this system restore! System-wide configs, like windows file sharing or firewall setup would be lost, but once you know which config files these are, you can easily copy them to your home directory and restore after a reinstall. Hope this is helping :)

---

### Post by Bobo K on 2006-10-16
I took the easy way out and reformated the whole drive. I tried to find a way to just reinstall or restore, but I couldn't. So I made a clean install and saved the files I wanted to keep on a flashdrive. But there is a way to reinstall Ubuntu without losing the files in the /home directory?

The sound works now, but there are still some things I haven't figured out yet:

- Is there a way to "permanently" mount a drive, i.e. as soon as I log in  hdb1 automatically mouts to a folder (like /home/bobo/storage) or something similar?

- Is there a way to wright to another disk? When I try to save or delete anything on hdb1, it says that I can't and I get the message "You are trying to save the file on a read-only disc".

- Alien is supposed to convert .rpm packages to .deb, right? I downloaded it and tried to do so using "sudo alien -i /home/bobo/Desktop/nosefart-2.2-1.i386.rpm". Then it takes ~30 seconds before I can write something in the terminal again, nothing happens and I can't find a .deb package anywhere.

- I tried to install Nosefart standalone player (NES sound emulator - [http://nosefart.sourceforge.net/](http://nosefart.sourceforge.net/)) using Alien (see above). The icon shows up under Applications > Sound & Video but I can't open it. Nothing happens, not even an error message. So I thought I would uninstall it, but there is no entry for it in Add/Remove. My question is, how do I remove the icon? It's no biggie, but it's bothering that it's there when it does nothing. :p

---

### Post by CatKiller on 2006-10-16
> **Bobo K said:**
> - Is there a way to "permanently" mount a drive, i.e. as soon as I log in  hdb1 automatically mouts to a folder (like /home/bobo/storage) or something similar?

That's what the **f**ile**s**ystem **tab**le is for.
[ How to mount Windows partitions (FAT) on boot-up, and allow all users to read/write]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite")

> - Is there a way to wright to another disk? When I try to save or delete anything on hdb1, it says that I can't and I get the message "You are trying to save the file on a read-only disc".

If the partition you're trying to write to is NTFS, then it will have been mounted as read-only on account of the ntfs driver in the kernel being experimental. There's an ntfs-3g driver that's just as experimental, but allows the daring to enable write support.

If the partition is anything else, then you've probably just mounted it incorrectly.

---

### Post by Bobo K on 2006-10-16
Oh, I see. Shame the disc I had in mind is NTFS. I guess there is no way to convert it to FAT without losing data?

---

### Post by CatKiller on 2006-10-16
I've read ("some bloke on the Internet said it...") that Partition Magic can do this. I've never tried it, so I don't know if it's true.

---

### Post by Bobo K on 2006-10-17
The disc is a full 120 gb, so it might not be such a good idea to convert it to FAT after all. Oh well, not a huge problem. :)

---

### Post by CatKiller on 2006-10-17
I think FAT32 can handle a partition that size, although ISTR that you can only have individual files smaller than 4Gig, and there's a limit on the absolute number of files on there. I can't remember exactly where we've got to, but if you wanted this to share data with Windows, there is a driver for Windows that will let you read the more sensible ext3 filesystem. Again, haven't used it, so I can't tell you how good or otherwise it is.

---

