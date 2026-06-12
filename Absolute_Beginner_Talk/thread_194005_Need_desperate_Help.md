---
title: "Need desperate Help"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by Andenium on 2006-06-10
okok listen i just switched to ubuntu i had win XP and i have 2 hard drives so, i put all the data in the 100 gb hard drive and the OS on the 80 one so when i wanted to switch OS i just needed to format the 80 one ,  well i formated and installed ubuntu and normally didnt format the 100gb one, now i cant c or do anything on the 100gb drive cuz its on NTFS is there something i can do so i wont lose all the stuff i have in that drive???
in advance thx a lot

---

### Post by 5-HT on 2006-06-10
This well-written guide by aysui will help you mount the NTFS drive in Ubuntu.
[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

Please note that while it is *possible*  to get Linux to write to NTFS (there are HOWTO's posted in this forum), it is really not recommended as Mircosoft have not realeased all the specs on the filesystem. There is a chance for corruption if you are writing to NTFS from Linux!

However, read support for NTFS on Linux works well.

Hope that helps.

---

### Post by Andenium on 2006-06-10
where can i open this terminal stuff?

---

### Post by Andenium on 2006-06-10
ok heres what im gonna do
im going to do that and put all the files on the 80 gb drive then put the 100 gb drive on the format i need for linux thx a lot but i think i may need help on some stuff since im really newb on this linux stuff ><

---

### Post by 5-HT on 2006-06-10
[quote=Andenium]where can i open this terminal stuff?[/quote] 
If you are running GNOME (standard for Ubuntu): Click on the 'Applications' menu up top -> Accessories -> Terminal


[quote=Andenium]ok heres what im gonna do
im going to do that and put all the files on the 80 gb drive then put the 100 gb drive on the format i need for linux thx a lot but i think i may need help on some stuff since im really newb on this linux stuff >< [/quote] 
That sounds like a good Idea if you won't be needing any of the drives for Windows. Now that you know how to get to the terminal, just follow that guide to mount the NFTS drive.

Once the drive is mounted, you can copy all the files over to the 80 gig drive. To do so, just click on 'Places' up top -> Computer (or just double-click on the icon for the NFTS drive or your home folder on the desktop). You'll be presented with a filebrowser (called Nautilus. It is just like Windows Explorer) that will let you copy over the files to your home folder on the 80 gig drive.

If you have any problems, just post back and I'm sure someone here will gladly help you out.

Hope that helps.

---

### Post by Andenium on 2006-06-10
kkk now this happened im on terminal following instructions but when i do sudo unmount and the drive it asks me for a password
normally i would put the only password ive put for the computer but i cant write when i try to put it? wth is that all about

---

### Post by u.b.u.n.t.u on 2006-06-10
Check the file dates of your data when transferring. Mine were all corrupted to 2007 and I had to use my DVD backups.

---

### Post by Andenium on 2006-06-10
lol sry to ask ](*,)  but would u mind giving me your msn or w/e u use so i can talk with u plz?? :confused:

---

### Post by u.b.u.n.t.u on 2006-06-10
[QUOTE=Andenium]kkk now this happened im on terminal following instructions but when i do sudo unmount and the drive it asks me for a password
normally i would put the only password ive put for the computer but i cant write when i try to put it? wth is that all about[/QUOTE]

When you first install ubuntu as a user, you have a username and password. Whenever do perform an administrative task, you will be asked to enter your password. Using the terminal and synaptic usually requires a password. You are then authorised to be admin for about 15 mins. At that point you will need your password again.

---

### Post by 5-HT on 2006-06-10
[quote=Andenium]kkk now this happened im on terminal following instructions but when i do sudo unmount and the drive it asks me for a password
normally i would put the only password ive put for the computer but i cant write when i try to put it? wth is that all about[/quote] 
That's normal, and is for security purposes. When you enter the password in the terminal, it will not be displayed (even as *'s) but it will be entered. As u.b.u.n.t.u mentioned, the password will be the same one you used for the installation.

HTH

---

### Post by Andenium on 2006-06-10
ok u.b.u.n.t.u what i read on ur post was "añlsdkfañlksdjfñaksdjfkajdfñalksfjañlsdfjñ" lol sry but i didnt understand :P mind giving me ur aim or something?

---

### Post by RRS on 2006-06-10
[QUOTE=Andenium]kkk now this happened im on terminal following instructions but when i do sudo unmount and the drive it asks me for a password
normally i would put the only password ive put for the computer but i cant write when i try to put it? wth is that all about[/QUOTE]

When you type in your password in the terminal it remains invisible, no ***'s or anything show, simply type it in and hit "enter" and the command will execute.

---

### Post by u.b.u.n.t.u on 2006-06-10
Andenium working with ubuntu, with little or no previous Linux experience is not something one can normally do overnight. There are things to learn and that takes time.

I had a similar situation, 80GB HDD with ubuntu and 160GB HDD with data on NTFS. I could not get the NTFS mount to work - I could not read my data. As I  have a LAN I put the 160GB HDD into a XP box and networked across. When I transfered my data to my 80GB HDD all the dates were corrupted to 2007. I have since filed a bug report.

I then put my 160GB HDD into my ubuntu box and formated it to ext3. I had to use my DVD data backup to retrieve my data. All the dates being 2007 effectively destroyed the value of my data.

In your situation you need to mount the NTFS HDD. Then you can have read access and transfer your data over. As I didn't do this, because I couldn't get it to work and I knew how to network Linux and XP I did it that way - which failed as mentioned.

You need to "mount the NTFS HDD so you have read access". Then you can transfer data. I don't know how to do this.

---

### Post by Andenium on 2006-06-10
you know how to do that ht?

---

### Post by u.b.u.n.t.u on 2006-06-10
Andenium I understand what it is you wish to do. Unfortunately I do not know how to do this. This however is your question:

"How do I mount a NTFS HDD in a ubuntu box, so I can transfer my NTFS HDD data to my ubuntu HDD?"

I do know you will need to edit a file called "fstab". That file states what HDDs you have and where they are mounted. Mounted means located.

You have these steps.

1. make a directory (XP language = folder).
2. edit the fstab file with a text program, preferably gedit as it easy to use.
3. use the terminal to do steps 1 and 2 and also to mount the HDD.

Someone here will be able to tell you, but patience is a good thing.

---

### Post by 5-HT on 2006-06-10
[quote=Andenium]you know how to do that ht?[/quote] 
Can you please type this into a terminal, press enter, type your password when asked, and type enter again?
```
sudo fdisk -l 
``` 
Once you get some output, can you highlight it in the terminal, create a new reply to this thread, and press the middle mouse button in the reply-window to paste the output here?

We'll need that to find out which device Ubuntu recognizes as  the NFTS drive.

As an aside: Yes, it can be really frustrating learning to use Linux. It's not difficult though, there are just some *new* things to learn and this can take a little time and effort. However, it can be well worth the investment of your time. You may end up loving Linux and preferring it to Windows.

---

### Post by Andenium on 2006-06-10
Disk /dev/sda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12187    97892046    7  HPFS/NTFS

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9352    75119908+  83  Linux
/dev/hda2            9353        9729     3028252+   5  Extended
/dev/hda5            9353        9729     3028221   82  Linux swap / Solaris
 thats what it says

---

### Post by 5-HT on 2006-06-10
[quote=Andenium]Disk /dev/sda: 100.2 GB, 100256292864 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12187    97892046    7  HPFS/NTFS [/quote] 
Thanks. Ok, so /dev/sda1 is the NTFS partition.

To have the drive mounted everytime you bootup, enter the following into the terminal:


1. ```
 sudo mkdir /media/windows 
``` 
2. ```
 sudo cp /etc/fstab /etc/fstab_backup 
``` 
3. ```
 sudo gedit /etc/fstab
``` Add this line to the end of the file, save, and exit
```
 /dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0" >> /etc/fstab 
``` 




After doing the previous, when you reboot you will see the NTFS drive icon on the desktop (and it'll be mounted everytime you boot up).

If you want to eventually reformat the NTFS drive and set it up to be mounted automatically after it has a Linux filesystem on it, please post again and someone will walk you through it.

---

### Post by Andenium on 2006-06-10
linux pwns ^^ now i did what ur page told me to do and it says there is no directory called that what am i doing wrong?

---

### Post by Andenium on 2006-06-10
carlos@carlos-desktop:~$ sudo echo "/dev/sda1 /media/windows ntfs nls=utf8,ro,umask=0222 0 0" >> /etc/fstab
bash: /etc/fstab: Permission denied
carlos@carlos-desktop:~$
wth?

---

### Post by 5-HT on 2006-06-10
[quote=Andenium] carlos@carlos-desktop:~$ sudo echo "/dev/sda1 /media/windows ntfs nls=utf8,ro,umask=0222 0 0" >> /etc/fstab
bash: /etc/fstab: Permission denied
carlos@carlos-desktop:~$
wth? [/quote] Sorry, the command wasn't working for me either (one of the problems present in trying to redirect with sudo).
This should work (I've update the previous post as well).

 ```
 sudo gedit /etc/fstab 
``` Add this line to the end of the file, save, and exit
```
 /dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0" >> /etc/fstab 
``` 

After doing the previous, when you reboot you will see the NTFS drive icon on the desktop (and it'll be mounted everytime you boot up).

EDIT: I changed these steps from those giving a root shell to avoid the dangers of having a full root shell open.

---

### Post by Andenium on 2006-06-10
dude rly thx a lot you prolly will b hearing from me later :P i did it with the open shell thingy should i change it or what should i  do

---

### Post by 5-HT on 2006-06-10
[quote=Andenium]dude rly thx a lot you prolly will b hearing from me later :P i did it with the open shell thingy should i change it or what should i  do[/quote] 
So you got it? If so great! :)

About the root (i.e., superuser that can do anything to the system) shell, no worries. The only problem is if you stay as root and do some other commands that may mess-up your system (you wouldn't be allowed to do them as a regular user for security reasons).

Using 'sudo' gives you root permissions, but only for that one command.

As long as your prompt says 'carlos' and not 'root' you are ok.
If it still does, just type ```
 exit 
``` and the terminal should say 'carlos' again.

---

### Post by Andenium on 2006-06-10
o okay i did that from the begginning ^^ so yes it worked and now im copying the files
soon i will ask how to format the drive :confused: LOL

---

### Post by Andenium on 2006-06-10
okay im almost freaking out now so im copying the files right and im trying to play some music while i do it so i used amarok and songs just kept passing by
then i tried to just play a single file and it said to get its plugins u know where i can get them?

---

