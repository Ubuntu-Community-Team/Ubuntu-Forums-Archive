---
title: "Backup to Another PC"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by Bill Bickley on 2007-02-09
Hi, folks:

As I fiddle and learn, I'm bound to break something (again).  How would I go about backing up  the entire contents of my ubuntu PC to another (Windows 2000) PC on my home network? 

TIA.

Bill

---

### Post by bswilson on 2007-02-09
Bill,

Try setting up a shared folder on your Windows 2000 system, and then just copy your data using the **nautilus** interface.  Or, you can write a script using **cp** or **rsync** that does it automatically.

---

### Post by PartisanEntity on 2007-02-09
I would use Simple Backup Suite, aka sbackup:
[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

I am not sure how useful and helpful it is to tell beginners to *"write a script using cp or rsync that does it"* - sorry. This is after all the beginner section of the forum and so simple and easy to follow advice should be given IMHO.

---

### Post by Bill Bickley on 2007-02-10
[COLOR=Black]Using sbackup, I could use some help with the destination path statement...

ssh://username: [email]password@example.com[/email]/remote/dir/

Under this scenario:
username: uname
password: upass


Info from the destination PC:
Workgroup: SHARED
Computer Name: ABC

The intended destination of the backup is D:/ubunto.  This folder is shared, and I can see it in the file browser on the ubuntu machine.

So the path is: ssh://uname:upass@??????

Bill
[/COLOR]

---

### Post by oldgoat on 2007-04-01
Hi Bill

I just got this worked out yesterday.  Last evening my three upgraded Edgy machines all backed up to each other over my network.  My ssh path looks something like this:

ssh://Boo:Radley@192.168.1.106/home/shared

OK, that's    ssh://Boo = remote computer login name : Radley = remote computer password @ ip address of remote computer (use 'ifconfig' in the terminal) /remote computer home / remote computer shared folder (whatever its name is)

The name and password referred to above are the same name and password that you provide at the gdm (gnome display manager) in order to reach your graphical desktop.

If you have the ssh path correctly set, the first time you attempt to log in, i.e. hit the 
'Test' button, a dialogue box will pop up saying: 

"The identity of the remote computer (192.168.1.106) is unknown.
This happens when you log in to a computer the first time."

There is more about the identity of the remote computer and contacting the system
administrator.  

Choose the option to log in anyway.  You will be looking at another error message, however, do not fear.  The path should be correct if you got the above "The identity of the remote computer" dialogue box.  Simply hit the 'Test' button once again.  A green symbol should appear to the left of your ssh path.

Use the 'Time' tab to automate backups - it works great.

---

### Post by Campingman on 2007-04-01
Anyone know how long it takes to do a back up with sbackup?
I have tried a couple of manual backups and I get the backup in background box with the id number.  The main window just stays on the screen I cannot get it to minimize or close or respond to anything.  Only way to get rid of it is to log out.  I have checked what processes are running and sbackup is not one of them.  Are there any alternatives to sbackup?

---

### Post by Sbarton on 2007-04-01
Backup or clone? Have a look at this! [http://ubuntu-tutorials.com/2006/12/05/how-to-clone-an-installation-ubuntu-510-6061-610/](http://ubuntu-tutorials.com/2006/12/05/how-to-clone-an-installation-ubuntu-510-6061-610/)
regards

---

### Post by oldgoat on 2007-04-01
Campingman - 

If you're using the system monitor, to the left the 'Process Name' is 'gksudo'.  To the right, the process has an ID number and this:

'Arguments': 'gksudo simple-backup-config'

When you press 'Backup Now!', a dialogue box should appear telling you that "A backup run is initiated in the background. The process id is", and there should be a process ID number.  You will not be able to close the 'Backup Properties' box until you have closed the process ID number box.  Closing these boxes will not kill the backup.

There are many other ways to back your system up.  Most, like rsync over ssh, are much more difficult for begining users like us.  But then, sbackup is a front end for rsync and has ssh capability.

---

### Post by Campingman on 2007-04-02
Thanks Oldgoat,

I have reinstalled and started to play again.  
It seems it was working all along, it backed up so quickly I assumed it was not working, if I go into restore I can now see the back ups (plus some from yesterday!!).
I am not brave enough to see if the backups are good or not.  
I will wait till there are desperate measures needed!

Thanks again

---

