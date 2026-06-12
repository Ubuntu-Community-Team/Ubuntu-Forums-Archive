---
title: "wget how to install"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Ex-windows on 2007-12-19
I would like 2 know how 2 get wget. Is it already installed in ubuntu?? I am trying to download systemRescue and it say to use wget. How do I do that????
Thanks in advance

---

### Post by oeolycus on 2007-12-19
It should be included. Have you tried typing 'wget' in a terminal (without quotes)?

If it's not there, reinstall: ```
sudo apt-get install wget
```

You can also look at the manual page for wget with: ```
man wget
```

---

### Post by nickoli_02 on 2007-12-19
wget should already be installed. To find out more on how to use wget, type "man wget" into a terminal (applications -> accessories)

---

### Post by jken146 on 2007-12-19
wget is already installed.  It's a command line thing, used like this: ```
wget http://somewhere.domain/bla/bla/file.whatever
```

Read the man page for more info. ```
man wget
```

---

### Post by Hospadar on 2007-12-19
it's already installed, it's a command-line tool you do like "wget <internet address of file to download>", it runs from a terminal Applications->Accessories->Terminal". where is this page telling you to use wget?  there's no reason you can't just go to the address and download it from firefox, but if it's part of a set of terminal instructions, it might be easier to just use wget.

---

### Post by Ex-windows on 2007-12-19
WOW Thats what I call QUICK. Thank all of you for the reponse  I had not yet heard of this, as I ma just now comfortable with the apt-get lol. Anyway the page that suggestesd to use wget is
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download). I am trying to start learning/doing regular backups. "complete" backups as I am spending to much time re installing when I change things or (more likely)  screw things up lol. Especially my other comp which has ubuntu and all files, photos, music and soon mtyhtv .
Again thanks for the help. 
Sorry forgot to ask how do I know what "archtecture I am
I have 2002 model Compaq 5300 series, 756mg, sd ram, 1.3 gig Amd processor. 80 g HD

---

### Post by nickoli_02 on 2007-12-19
In the linux world, the most important part of your filesystem to back up is your /home directory. This directory holds your personal settings for all users (except root user, which is in /root, but you don't need to worry about that). If you make a habit of keeping all your personal information in /home/<your_username> then all you have to do to create a backup is to copy that folder somewhere, like on an external hard drive or other storage device. 

:)

---

### Post by Ex-windows on 2007-12-19
Does this re install the entire os with the docs????

---

### Post by nickoli_02 on 2007-12-20
I'm not entirely sure what you mean... 

Your /home directory stores all user-defined preferences for how you use your programs and set up your desktop and such. If you have to reinstall ubuntu in the future then you can simply copy your backup /home directory over to the newly installed OS. Then everything would look as how it looked before you reinstalled. 

You will still have to install programs and everything, but thats it. It's easier to install programs fresh than backing up existing programs.

---

### Post by hyper_ch on 2007-12-20
You have different places that need to be backed up, depending on what you use/need.

As mentions, there's the /home folder which equivaltes to the windows "c:\Document and Settings". Personal configuration file of programs and your data/documents should be in there.

Then you have the /etc folder which contains systemwide configuration tools (e.g. Xorg.conf, configuration files for apache, php, mysql and other system services).

Then you also have /var/www which is the default web root (in case you do web developping and use the standard folders...)

If you're using mysql then the DBs are in /var/lib/mysql (I think).


------------------------


As for backups, I make a "full" backup every 4h back for 90 days. I don't use disk imaging tools but I use the power of synchronization with rsync and hardlinks. That way I can do incremental snpshot-style backups  to my old computer and don't need much more disk space.

---

### Post by Ex-windows on 2007-12-20
Sorry I'm late, Thank you 4 replies. As for what I need/want It is a Full backup =Insatlled programs,setting GRUB FOLDER lol lol and that pesky etc/fstab file. Something similar to Windoz "System Restore" But of course I know this would have to be done by the user . I am trying to learn this on THIS comp so as to insure the safety of My Main comp which has and will have more stuff. I have tried the "sysrec" cd , I couldn't get it to work. I tried using imagepart as explained on this page
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

However it worked up to the part of Making the copy and then told me I didn't have enuff space.
SO Last nite I burned a Fiesty Cd did md5sum check burned it 4x and proceeded to re-install..
 I created an extra Partiton for Storage of back ups.
Install went ok though a lil different from edgy. and Now I have whole new set of troubles lol lol.
 I couldn't access my other partitions. Now I can Access them but I can't un-mount them.  But I will get to that later. As for Back ups I have also used the Archiving tools  and Simple back u[p utility are these ok for the data type backups (for now).  OK thats enuff babbling Thank you again.

---

