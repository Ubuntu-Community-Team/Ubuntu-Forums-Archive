---
title: "Unable to play music - part one - can't recognize a DVD"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by babel on 2006-04-30
I am just learning the basics of a Ubuntu system.

I decided to try to play some music on the system.

I have an data archive of music as MP3's on a DVD.  When I put the DVD into the drive, 

Ubuntu recognized the drive but not the DVD in the drive.

I received the message:

"Opening CD-ROM/DVD-ROM drive"

Then a second message:

"Unable to mount the selected volume. The volume is probably in a format that cannot be 

mounted.

Warning: device /dev/hdc is already handled by /etc/fstab,supplied label is ignored
mount: block device /dev/hdc is write-protected, mounting read only
mount: wrong fs type, bad option, bad superblock on dev/hdc, missing codepage or other error
in some cases useful infois found in syslog - try dmesg tail or so

Error: could not execute pmount"

In addition to not reading this DVD, I could also not read a CD.

I know the disks are good as I tested them on my Windows systems.

What am I doing wrong?

---

### Post by NiceGuy on 2006-04-30
I'm not sure what is happening here...

Can you read any cd's or dvd's or is it just these disks?

If it is just these particular disks then what program (I assume in windows) did you use to make them? Was it the standard windows or nero stuff or was it something like nero's InCD or a program called Sonic or Roxio (I think they are the names - it is somtimes shipped with some dell's and HP systems). If the disk was made using one of these programs then the problem might be that it was formatted using a non-standard format. I'm not sure how you would get around that (I'd try googleing the format name and 'linux' and see what you get).

If your not sure then try the disk in another computer in which doesn't have the software you used installed and see if it can read them.

---

### Post by babel on 2006-04-30
I just tried a store-bought movie DVD in the Ubuntu computer and it couldn't read it either.  It was able to identify title in the DVD icon in Nautilis but couldn't play the DVD. Also, a DVD icon appeared on the desktop with the correct title.  When I click it, a file browser opens.

I use Nero to create my data CD's & DVD's. I do not use what I think is called "packet writing", that is, "InCD" on Nero.

I next tried a store-bought music CD.  An icon appeared on the desktop.  When I clicked it, Sound juicer opened and the CD played !  I could not find a way to get SoundJuicer to browse to a MP3 on my hard drive to test it there.

Si it appears I can play neither store-bought movie DVD's nor home-burned data (MP3) DVD's.  I cannot play a home-burned data (MP3) CD but I can play, with Sound Juicer, a store bought music CD.

When I tried to browse to the CD with Rhythmbox, Rhythmbox would not even see whichever of my two CD drives the CD was in !

I'm confused :(

---

### Post by muep on 2006-04-30
Hi

I think the problem may be that you have your dvd drive listed in /etc/fstab which is a configuration file for filesystem mounting. I think Ubuntu should use fstab only for hard drives and pseudo-filesystems, not for DVD drives or other removable media.

You need to edit /etc/fstab. This can easily be done by typing the following command into the Terminal:

sudo gedit /etc/fstab

Place a # into the beginning of the line that has /dev/hdc in it. Lines starting with a # are comments and are thus ignored. If this setting doesn't solve your problem, you can just remove the # and the file is like the original.

After editing, save the file, exit the editor and use this command:

sudo mount -a

This re-reads the configuration file and should free your dvd drive from fstab. After that you should be able to read your mp3 disks. Note that the files may probably not play yet because the mp3 codec isn't installed as default. When you can read the disks, we can start solving that if need to.

---

### Post by richbarna on 2006-04-30
I got given a link about dvd's by Barbarian regarding another matter.
Try this :-
How to relax restrictions on CD/DVDs?
 When accessed, a CD/DVD is auto-mounted ("started") with certain restrictions that prevent running programs or seeing hidden files on the CD/DVD. To allow program execution directly off the CD, "exec" option has to, and "suid" option might have to be enabled. To see hidden and associated files, "nohide" should be enabled. In order to enable all of them, after mounting the CD, issue: 
> sudo mount -o remount,user=$USER,nohide,exec,suid /media/cdrom0
 Use "/media/cdrom0" for the first drive, "/media/cdrom1" for the second, etc.

---

### Post by babel on 2006-05-01
Sounds complicated for someone as inexperienced as I am.

muep**:** Does typing "sudo gedit /etc/fstab" into the terminal make any changes in the system or does it merely show me the line I need to deactivate by placing a # in front of it?

richbarna**:** I put a CD in the drive, the icon appeared, I double-clicked it and a File Browser opened.  I clicked File > Show Hidden Files.  Nothing new appeared.

How do I "issue" sudo mount -o remount,user=$USER,nohide,exec,suid /media/cdrom0  ?

---

### Post by richbarna on 2006-05-04
Hi Babel,
To issue or use any of these types of posts with "command line" instructions you have to open the console.
You normally go to Start (or Kmenu etc) click the System tab and then look for Terminal Program (a black monitor icon normally). This is the console.
Open it and you will get a black window with white text that says something like :- user@computer0:~$
To make things easy you can just copy and paste these commands that you see posted on the forums directly after the $ and then press enter, that is how you "issue" these commands.
Sometimes you need to be root to "issue" these commands, in this case, after the $ you type su (super user) and press enter.
Then you will be asked for a password: type the root password and click enter again. (note that when you type the password you won't see anything appear such as *******, it'll be invisible, but it IS there)

---

### Post by richbarna on 2006-05-04
> muep: Does typing "sudo gedit /etc/fstab" into the terminal make any changes in the system or does it merely show me the line I need to deactivate by placing a # in front of it?
 
"sudo gedit" means open my text editor called "gedit" and got to the document in the "/etc"  folder called "fstab" and open fstab so that I can edit the text with gedit.

---

### Post by tommy18crowe on 2006-06-03
You may also have to download a few programs that'll play DVD movies...my fave is Xine.

---

### Post by tommy18crowe on 2006-06-03
# apt-get install xine-ui
# aptitude install gxine

---

