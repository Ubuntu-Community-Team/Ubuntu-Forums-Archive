---
title: "cp question"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by Hotchilli on 2005-12-26
I was given an answer to a question in the ubuntu chat room but I think
I may have misread the reply

the reply was to a thread
[http://ubuntuforums.org/showthread.php?t=105766](http://ubuntuforums.org/showthread.php?t=105766)

the answer was like so

sudo cp /var/lib/dpkg/status-old/root/backup-of-status

the second command was

sudo cp /var/lib/dpkg/status-old/

/var/lib/dpkg/status


when I tpye the first command I GET a message saying something like no 
destination

I was not given a destionation in the chat room session

have I got something wrong here?

hc:smile: :smile:

---

### Post by bscbrit on 2005-12-26
Hi again

The answer to your first question is simply a missing space:

sudo cp /var/lib/dpkg/status-old      /root/backup-of-status

(I've put a few extra spaces in there to make it clear, but you only need one)  However, having looked through the original thread I cannot see who suggested that but it should make a backup of your status-old.

I do not know why I did not come back to your last response - I don't recall seeing it being flagged up on my 'User CP' page but I must have missed it.  My apologies for that.

Can you please confirm that you are still having the same problems, or is this simply a question about using 'cp'?

---

### Post by bscbrit on 2005-12-26
Sorry, i missed one of your answers:

sudo cp /var/lib/dpkg/status-old/   /var/lib/dpkg/status

should all be on one line.

---

### Post by Hotchilli on 2005-12-26
Still synapic manager error:p :p  put the correct space in


andy108@heis:~$ cd /var/lib/dpkg
andy108@heis:/var/lib/dpkg$ dir
alternatives   cmethopt        info     parts             status
available      diversions      lock     statoverride      status-old
available-old  diversions-old  methods  statoverride-old  updates
andy108@heis:/var/lib/dpkg$ sudo cp /var/lib/dpkg/status-old  /root/backup-of-sta tus
andy108@heis:/var/lib/dpkg$ sudo cp /var/lib/dpkg/status-old  /var/lib/dpkg/status
andy108@heis:/var/lib/dpkg$ dir
alternatives  available-old  diversions      info  methods  statoverride      status      updates
available     cmethopt       diversions-old  lock  parts    statoverride-old  status-old
andy108@heis:/var/lib/dpkg$

---

### Post by bscbrit on 2005-12-26
OK - we've changed threads for this problem but no matter.  Can you refresh me please.

You get the problem with synaptic, do you also see the same problem with apt-get?  (I cannot think why you wouldn't, but best to check first)

I'll go and google for some additional info.

---

### Post by bscbrit on 2005-12-26
Can you also provide me with the outputs from the following command:

ls -l /var/backups/*


And what happens if you use the command

dpkg -l

Does the file look corrupted?

---

### Post by Hotchilli on 2005-12-26
Synapic gives error as before

dpkg -l wworks fine


andy108@heis:~$ sudo apt-get install pearl
Reading package lists... Error!
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened

/var/backups/dpkg.status.1.gz to 5 are in red colour on my terinmal:smile: :smile: 


andy108@heis:~$ ls -l /var/backups/*
-rw-r--r--  1 root root   1041801 2005-12-26 12:12 /var/backups/dpkg.status.0
-rw-r--r--  1 root root    295417 2005-12-16 20:05 /var/backups/dpkg.status.1.gz
-rw-r--r--  1 root root    275677 2005-12-15 15:03 /var/backups/dpkg.status.2.gz
-rw-r--r--  1 root root    274513 2005-12-14 15:37 /var/backups/dpkg.status.3.gz
-rw-r--r--  1 root root    267763 2005-12-13 16:14 /var/backups/dpkg.status.4.gz
-rw-r--r--  1 root root    267451 2005-12-10 06:10 /var/backups/dpkg.status.5.gz
-rw-r--r--  1 root root    267402 2005-12-07 06:27 /var/backups/dpkg.status.6.gz
-rw-------  1 root root       763 2005-12-02 12:30 /var/backups/group.bak
-rw-------  1 root shadow     645 2005-12-02 12:30 /var/backups/gshadow.bak
-rw-r--r--  1 root root      4148 2005-12-16 10:59 /var/backups/infodir.bak
-rw-------  1 root root      1351 2005-12-15 15:03 /var/backups/passwd.bak
-rw-------  1 root shadow     876 2005-12-15 15:03 /var/backups/shadow.bak
andy108@heis:~$

---

### Post by bscbrit on 2005-12-26
OK, this shows that you have backups of the status file going back to 7 Dec, can you remember when the problem started?  The package file seems to be OK - that what (I think!) you saw with dpkg -l.  So we should be able to replace the current corrupted status file with an earlier version.  Did you modify your repos (/etc/apt/sources.list) just before the error occurred?

My current thinking is

save your repos somewhere safe.
save your current status file somewhere safe
restore the latest possible status file from the backup
Try to get synaptic working again.

We might have to rebuild your package list using a perl script but I'm hoping that it will not be necessary.  

You might also want to ensure that any valuable data on this computer is also backed up, preferably to a safe drive or removable media, just in case.....

---

### Post by Hotchilli on 2005-12-26
It would have been the day orthe day I posted the problem
so about 18/19 dec.

hc:D :D :D

---

### Post by Hotchilli on 2005-12-26
i think it happened just after I installed kerio mailserver which I had to use alien to
get the deb version which has a lock above it but it installed ok i think
the day after I ran the application manager thats when I stated the thread

hc:D :D

---

### Post by bscbrit on 2005-12-26
The installation of the kerio mailserver sounds as though it is the most likely candidate for the cause but there would have been no way of knowing that before you tried it so - unlucky!

Have you got any data that you _must_ preserve or backup before we begin?

---

### Post by Hotchilli on 2005-12-26
No:smile:

---

### Post by bscbrit on 2005-12-26
I have attached a very simple script to do the backup and restoration of your dpkg.status file of the 16 Dec 05.  I have done this to help you to avoid typing errors and losing more data than we might otherwise do!  Feel free to do it all manually if you wish.

Save it into your own HotChilli user area.  Right click on it with Nautilus/Konqueror and make sure that it is executable under 'Permissions'.

The script must be run as root.  So if you saved it with the default name of dpkg.txt you would then type the following in a terminal

sudo ~/dpkg.txt

What you should first see (when the initial smoke clears from your computer bursting into flames.....) is the script making a backup of your existing dpkg directory.  This takes perhaps 30-40 seconds, but that will depend on the speed of your computer!

Then, in the blink of an eye, the original file is restored and you should simply see a message telling you that the file has been restored.

If you get this far without any errors (and you have managed to put the fire out!), I suggest that you try running

sudo apt-get update

and see if the problem has gone away.

Good Luck.

---

### Post by bscbrit on 2005-12-26
The reason that I gave the script an unconventional extension for its purpose (.txt) is that the forum only allows certain types of files to be uploaded.

---

### Post by Hotchilli on 2005-12-26
ran the script and at the end ran as you said but stil as before

/var/lib/dpkg/statoverride-old
The copy of dpkg.status dated 16 Dec 05 has now been restored to the /var/lib/dpkg directory.
andy108@heis:/home$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Fetched 1B in 0s (3B/s)
Reading package lists... Error!
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.
andy108@heis:/home$

---

### Post by bscbrit on 2005-12-26
Please can you run 

ls -l /var/lib/dpkg 

again, and post the results.  On your original list there was _no_ .status file. I have now put one there but, if it has gone again, then something is deleting it.  I would just like to see that it is still there!

---

### Post by bscbrit on 2005-12-26
Sorry, just another possible tweak.

sudo mv /var/lib/dpkg/dpkg.status /var/lib/dpkg/status

It seems that it renames files for backup - I don't think that I have restored it to it original name until now.

---

### Post by Hotchilli on 2005-12-26
here is result before the mv command

andy108@heis:/var/lib/dpkg$ ls -l
total 5012
drwxr-xr-x  2 root root    4096 2005-12-14 11:11 alternatives
-rw-r--r--  1 root root  905150 2005-12-16 20:05 available
-rw-r--r--  1 root root  904584 2005-12-16 17:42 available-old
-rw-r--r--  1 root root       8 2005-11-26 01:20 cmethopt
-rw-r--r--  1 root root    2988 2005-11-26 02:25 diversions
-rw-r--r--  1 root root    3072 2005-11-26 02:25 diversions-old
-rw-r--r--  1 root root 1042264 2005-12-26 16:53 dpkg.status
drwxr-xr-x  2 root root  131072 2005-12-16 20:05 info
-rw-r-----  1 root root       0 2005-12-26 17:00 lock
drwxr-xr-x  5 root root    4096 2005-11-26 02:09 methods
drwxr-xr-x  2 root root    4096 2005-09-24 18:39 parts
-rw-r--r--  1 root root      30 2005-11-26 02:21 statoverride
-rw-r--r--  1 root root       0 2005-11-26 01:19 statoverride-old
-rw-r--r--  1 root root 1041801 2005-12-26 12:12 status
-rw-r--r--  1 root root 1041801 2005-12-16 20:05 status-old
drwxr-xr-x  2 root root    4096 2005-12-16 20:05 updates
andy108@heis:/var/lib/dpkg$


and after

andy108@heis:/var/lib/dpkg$ sudo mv /var/lib/dpkg/dpkg.status /var/lib/dpkg/stat us
Password:
andy108@heis:/var/lib/dpkg$ ls -l total 3988
drwxr-xr-x  2 root root    4096 2005-12-14 11:11 alternatives
-rw-r--r--  1 root root  905150 2005-12-16 20:05 available
-rw-r--r--  1 root root  904584 2005-12-16 17:42 available-old
-rw-r--r--  1 root root       8 2005-11-26 01:20 cmethopt
-rw-r--r--  1 root root    2988 2005-11-26 02:25 diversions
-rw-r--r--  1 root root    3072 2005-11-26 02:25 diversions-old
drwxr-xr-x  2 root root  131072 2005-12-16 20:05 info
-rw-r-----  1 root root       0 2005-12-26 17:00 lock
drwxr-xr-x  5 root root    4096 2005-11-26 02:09 methods
drwxr-xr-x  2 root root    4096 2005-09-24 18:39 parts
-rw-r--r--  1 root root      30 2005-11-26 02:21 statoverride
-rw-r--r--  1 root root       0 2005-11-26 01:19 statoverride-old
-rw-r--r--  1 root root 1042264 2005-12-26 16:53 status
-rw-r--r--  1 root root 1041801 2005-12-16 20:05 status-old
drwxr-xr-x  2 root root    4096 2005-12-16 20:05 updates
andy108@heis:/var/lib/dpkg$


:smile: :smile:

---

### Post by bscbrit on 2005-12-26
Well, lets try apt-get again, or synaptic.

And if it _still_ doesn't work

sudo mv  -f /var/lib/dpkg/status-old /var/lib/dpkg/status

and try again.

---

### Post by Hotchilli on 2005-12-26
andy108@heis:~$ ls -l /var/backups/*
-rw-r--r--  1 root root   1041801 2005-12-26 12:12 /var/backups/dpkg.status.0
-rw-r--r--  1 root root   1042264 2005-12-16 20:05 /var/backups/dpkg.status.1
-rw-r--r--  1 root root    275677 2005-12-15 15:03 /var/backups/dpkg.status.2.gz
-rw-r--r--  1 root root    274513 2005-12-14 15:37 /var/backups/dpkg.status.3.gz
-rw-r--r--  1 root root    267763 2005-12-13 16:14 /var/backups/dpkg.status.4.gz
-rw-r--r--  1 root root    267451 2005-12-10 06:10 /var/backups/dpkg.status.5.gz
-rw-r--r--  1 root root    267402 2005-12-07 06:27 /var/backups/dpkg.status.6.gz
-rw-------  1 root root       763 2005-12-02 12:30 /var/backups/group.bak
-rw-------  1 root shadow     645 2005-12-02 12:30 /var/backups/gshadow.bak
-rw-r--r--  1 root root      4148 2005-12-16 10:59 /var/backups/infodir.bak
-rw-------  1 root root      1351 2005-12-15 15:03 /var/backups/passwd.bak
-rw-------  1 root shadow     876 2005-12-15 15:03 /var/backups/shadow.bak
andy108@heis:~$ cd /var/lib/dpkg



THE above print out shows 2-6 still in red  colour should they be removed


andy108@heis:/var/lib/dpkg$ ls -l
total 2964
drwxr-xr-x  2 root root    4096 2005-12-14 11:11 alternatives
-rw-r--r--  1 root root  905150 2005-12-16 20:05 available
-rw-r--r--  1 root root  904584 2005-12-16 17:42 available-old
-rw-r--r--  1 root root       8 2005-11-26 01:20 cmethopt
-rw-r--r--  1 root root    2988 2005-11-26 02:25 diversions
-rw-r--r--  1 root root    3072 2005-11-26 02:25 diversions-old
drwxr-xr-x  2 root root  131072 2005-12-16 20:05 info
-rw-r-----  1 root root       0 2005-12-26 18:40 lock
drwxr-xr-x  5 root root    4096 2005-11-26 02:09 methods
drwxr-xr-x  2 root root    4096 2005-09-24 18:39 parts
-rw-r--r--  1 root root      30 2005-11-26 02:21 statoverride
-rw-r--r--  1 root root       0 2005-11-26 01:19 statoverride-old
-rw-r--r--  1 root root 1041801 2005-12-16 20:05 status
drwxr-xr-x  2 root root    4096 2005-12-16 20:05 updates
andy108@heis:/var/lib/dpkg$


thanks for your help but error still in place:???: :???:

---

### Post by bscbrit on 2005-12-26
I think I am rapidly running out of options.

The program complains it is unable to read the 'status' file.  So we have restored an earlier backup, and also more recently restored a local backup.  It still gives precisely the same error so I am beginning to believe that we are being led astray by the error message.  It might not be able to parse the file but it is _not_ a problem with that particular file.

We cannot re-install dpkg because neither synaptic nor apt-get will allow us to do so.  I know a way of recovering the package list, but not for recovering 'status' or any of the other associated files, and therefore, the little I do know will be of no use.

In short, unless some other reader can help dig me out of this one, I am stuck.  I'm sure that someone will have an answer - but he or she doesn't seem to be reading this thread!

I hate to admit defeat, but it is looking increasingly like a case of a re-install of Ubuntu.  By all means wait an hour or two to see if anyone else picks up on this, and I'll try to find a way out of here, but at the moment it is not looking hopefull.

Sorry about that.

---

### Post by Hotchilli on 2005-12-26
Thankyou for your constant support on this isue, I seel thar you have tried your best and still are to resolve this thread,  I can only think that perhaps it might be a good idea to direct the threads to a member of the ubuntu staff

hc:smile: :smile:

---

### Post by bscbrit on 2005-12-26
Hotchilli, You may well be right.  Create a new thread on the following forum:

[http://ubuntuforums.org/forumdisplay.php?f=91](http://ubuntuforums.org/forumdisplay.php?f=91)

with a title like 'dpkg file corruption - How to recover?' and then at least those who know more than I do (and there are billions of people who know more than me.....) will be able to pick it up.  Give them the background, or simply link to this thread.

I will watch out for the solution - I want to know how to fix it almost as much as you do!

Good Luck

Bscbrit

---

### Post by Hotchilli on 2005-12-26
Many thanks I have done as suggested please check your e-mail.

hc:smile: :smile:

---

