---
title: "I think I am going to cry."
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by jbmalone on 2006-01-24
I had a folder on my desktop that wouldn't delete so I used the sudo rm -rf command and it deleted other stuff off of my desktop.  I lost ten gigs of music, my documents, pictures and torrents.  Is there anyway to recover this or am I just screwed?

---

### Post by ardchoille on 2006-01-24
[QUOTE=jbmalone]I had a folder on my desktop that wouldn't delete so I used the sudo rm -rf command and it deleted other stuff off of my desktop.  I lost ten gigs of music, my documents, pictures and torrents.  Is there anyway to recover this or am I just screwed?[/QUOTE]
Just restore from backups. You **do** make backups, right?

---

### Post by hotrod1 on 2006-01-24
Ouch but if he had backups I am sure he could of restored them himself without even posting here?

---

### Post by ardchoille on 2006-01-24
True, posting here showed that he didn't have backups. I was trying to make a point for him to use this incident to learn the value of making backups so that he won't be stuck if this happened again in the future :)

---

### Post by gonçalo on 2006-01-24
but isn't there anyway to recover some of it?

---

### Post by jbmalone on 2006-01-24
This was new stuff, I usually back up when I do really big stuff.  I didn't think trying to delete a folder would be so drastic.

---

### Post by matthew on 2006-01-24
I'm truly sorry. It's gone.

---

### Post by dueY on 2006-01-24
Eh 10 gigs of music and torrents is nothing.  Just be glad you learned your lesson ](*,)

---

### Post by jbmalone on 2006-01-24
Any ideas on how to delete these two last folders?

Yeah, well I have like 100gigs on another harddrive.

---

### Post by matthew on 2006-01-24
Command line is going to be your best bet. 

Open a terminal from the menus at Application->Accessories->Terminal and do this
```
cd Desktop
ls
```if the file/folder you want to delete is listed then try
```
rm filename
```or ```
rm -rf foldername
``` You should not need root authority because this is in your home directory. That is, unless you created the file/folder while operating as root. In which case you might need to put sudo in front of those commands

---

### Post by mishranurag on 2006-01-24
Is there an automated method of backup as in Windows, where we can choose what to backup. Anurag

---

### Post by BoyOfDestiny on 2006-01-25
[QUOTE=jbmalone]I had a folder on my desktop that wouldn't delete so I used the sudo rm -rf command and it deleted other stuff off of my desktop.  I lost ten gigs of music, my documents, pictures and torrents.  Is there anyway to recover this or am I just screwed?[/QUOTE]

Actually it might still be there, if it still gets sent to .trash... but maybe not the one in /home... check /home first, press ctrl + h, check the folder marked .Trash... (or use the trash can desktop icon...)

next try this from a terminal:

sudo nautilus /root/.Trash

If your files are anywhere I'd guess there...anyway good luck to you... to be honest I don't remove files with sudo rm... I just launch nautilus with sudo...

---

### Post by Jason_25 on 2006-01-25
[QUOTE=mishranurag]Is there an automated method of backup as in Windows, where we can choose what to backup. Anurag[/QUOTE]
I have had good luck with [Sbackup]("http://sourceforge.net/projects/sbackup/").  It's in the repositories.

---

### Post by Lord Illidan on 2006-01-25
rm doesn't put files in trash..it just deletes them, so yes, they are gone...

Use rm sparingly, or better still, don't use it.

---

### Post by ignorance on 2006-01-25
this has nothing really to do with this post but how do you make back-ups?

---

### Post by alamba on 2006-01-25
ignorance: backups have everything to do with this post!!

Akshay

---

### Post by Mustard on 2006-01-25
[QUOTE=ignorance]this has nothing really to do with this post but how do you make back-ups?[/QUOTE]

One way of doing it is this.

[http://www.ubuntuforums.org/showthread.php?t=81311](http://www.ubuntuforums.org/showthread.php?t=81311)

---

### Post by IronWolve on 2006-01-25
[http://e2undel.sourceforge.net/](http://e2undel.sourceforge.net/)

Not sure how well it works, but it was listed on freshmeat. 

Also dont use the HD until you recover the programs. (Boot from another partition, or livecd if you need to browse the web and download a program) or the data on the harddrive could get overwritten.

---

### Post by patrick295767 on 2006-01-25
If it was in windows, there is a program : 

getdata back for windows / nt

IN case u dont touch / write in ur harddisk ... 
  
That's maybe exisiting for linux ?
  
I would recommand to make a RAW backup of ur harrdisk in order to get ur data back with one program later ... 
Once u made this RAW backup of ur partition, u would have possibility of writinig on it since u can try to get back ur data from the RAW file (backed_up !)
  
Let's us konw ur  progress ... 

Did you write in ur harddisk since the rm -rf .... ?

greetz

---

### Post by matthew on 2006-01-25
Hmmm... Re: backups. I don't recall installing anything special, but I have an option in my menus that I've never used.

System->Administration->Simple Backup Config
System->Administration->Simple Backup Restore

It looks like in Synaptic they are called simple-backup-config and simple-backup-restore or something similar...you might do a search

---

### Post by dueY on 2006-01-25
[QUOTE=alamba]ignorance: backups have everything to do with this post!!
[/QUOTE]

I imagined this as one of those motivational posters when I read it the first time. :D

Mistakes:  It could be that the purpose of your life is only to serve as a warning to others.

---

### Post by Jason_25 on 2006-01-25
[QUOTE=matthew]Hmmm... Re: backups. I don't recall installing anything special, but I have an option in my menus that I've never used.

System->Administration->Simple Backup Config
System->Administration->Simple Backup Restore

It looks like in Synaptic they are called simple-backup-config and simple-backup-restore or something similar...you might do a search[/QUOTE]
That's sbackup.  It's called sbackup in synaptic.

---

### Post by GreyFox503 on 2006-01-25
rsync can also be used for backups.

---

### Post by stfu on 2006-01-25
I'm pretty sure there are a lot of freeware programs on windows side that scan and restore linux partitions and filesystems.

For example, google: "linux ext3 data recovery" or whatever filesystem you're using and you get tons of programs. All you have to pick is a freeware one, find a windows machine to install it into and scan the drive.

I've actually recovered all my data from a previous linux ext3 drive after formatting it couple of times.

Geesh, you guys are being kinda negative aren't you?

---

### Post by jbmalone on 2006-01-25
Thanks for the help.  I got the rest of the folder deleted, and I surely learned my lesson.  I still have my external harddrive and I am still happy that I have that.  Thanks for all of the help again.

Jacob

---

### Post by patrick295767 on 2006-01-26
[QUOTE=stfu]I'm pretty sure there are a lot of freeware programs on windows side that scan and restore linux partitions and filesystems.

For example, google: "linux ext3 data recovery" or whatever filesystem you're using and you get tons of programs. All you have to pick is a freeware one, find a windows machine to install it into and scan the drive.

I've actually recovered all my data from a previous linux ext3 drive after formatting it couple of times.

Geesh, you guys are being kinda negative aren't you?[/QUOTE]
 
Nice Reply, 
I support you !

Greetings, 

Pat

---

