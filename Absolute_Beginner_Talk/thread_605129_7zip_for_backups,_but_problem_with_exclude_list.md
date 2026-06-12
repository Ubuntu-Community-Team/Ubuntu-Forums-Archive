---
title: "7zip for backups, but problem with exclude list"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Kilarin on 2007-11-06
I'm loving Ubuntu, but I need to build a new backup routine.  7Zip appears to be an incredibly cool program that could solve most of my backup needs. 
 
BUT, I'm having serious problems trying to make the exclude switch work using 7-Zip 4.51 beta under Ubuntu 7.10 Gutsy. 
 
I've read the following threads about this problem over on the 7zip forums: 
[http://sourceforge.net/forum/message.php?msg_id=3761319](http://sourceforge.net/forum/message.php?msg_id=3761319) 
[http://sourceforge.net/forum/message.php?msg_id=2900851](http://sourceforge.net/forum/message.php?msg_id=2900851) 
[http://sourceforge.net/forum/message.php?msg_id=3296997](http://sourceforge.net/forum/message.php?msg_id=3296997) 
[http://sourceforge.net/forum/message.php?msg_id=2942981](http://sourceforge.net/forum/message.php?msg_id=2942981) 
 
And despite trying to follow their instructions, I am no closer to a solution.  I also posted my own question there, but no answer yet.  I was hoping perhaps some of the gurus here would be more Ubuntu focused and could help me.
 
I want to back up a directory that contains my firefox profile. And I do NOT want to back up the Cache folders. 
My command line looks like this: 
 
cd /media/tc1/DCH/ 
7z a [email]-x@/media/tc1/DCH/Program-Data/7zip-backup-scripts/dch-exl.txt[/email] "/media/disk/bkp2/bkp2-dcht.7z" "/media/tc1/DCH/Program-Data/*"  
 
I also tried it with -xr instead of -x 
7z a [email]-xr@/media/tc1/DCH/Program-Data/7zip-backup-scripts/dch-exl.txt[/email] "/media/disk/bkp2/bkp2-dcht.7z" "/media/tc1/DCH/Program-Data/*"  
 
and tried stating the source path as relative: 
7z a [email]-xr@/media/tc1/DCH/Program-Data/7zip-backup-scripts/dch-exl.txt[/email] "/media/disk/bkp2/bkp2-dcht.7z" "Program-Data/*"  
 
the file dch-exl.txt looks like this: 
 
/media/tc1/DCH/Program-Data/Firefox/Cache/* 
/media/tc1/DCH/Program-Data/Firefox/Cache/ 
Program-Data/Firefox/Cache/* 
/Program-Data/Firefox/Cache/* 
Program-Data/Firefox/Cache/ 
/Program-Data/Firefox/Cache/* 
*/Cache/* 
*/Cache/ 
*Cache*/ 
*Cache*/*  
 
Thats every combination I can think of. And yet, still, the Cache folder gets zipped up with all the rest. 
How on earth to I make 7Zip exclude the Cache folder? 
 
Thank you very much in advanced!

---

### Post by Pabx on 2007-11-06
You Could install  7zip from the Add/Remove applications...

---

### Post by Kilarin on 2007-11-06
> You Could install 7zip from the Add/Remove applications...
Thank you, for replying.   I have 7zip installed and can compress files just fine using it.  the problem is that I can't get the exclude list functionality to work.   I need to say, from the command line, create an archive of everything you find in this folder, except for these files and folders.  PREFERABLY with the ability to wildcard, but I could live with just the ability to specify specific folder names.

---

### Post by gantengx on 2008-02-27
> **Kilarin said:**
> I'm loving Ubuntu, but I need to build a new backup routine.  7Zip appears to be an incredibly cool program that could solve most of my backup needs. 
 
BUT, I'm having serious problems trying to make the exclude switch work using 7-Zip 4.51 beta under Ubuntu 7.10 Gutsy. 
 
I've read the following threads about this problem over on the 7zip forums: 
[http://sourceforge.net/forum/message.php?msg_id=3761319](http://sourceforge.net/forum/message.php?msg_id=3761319) 
[http://sourceforge.net/forum/message.php?msg_id=2900851](http://sourceforge.net/forum/message.php?msg_id=2900851) 
[http://sourceforge.net/forum/message.php?msg_id=3296997](http://sourceforge.net/forum/message.php?msg_id=3296997) 
[http://sourceforge.net/forum/message.php?msg_id=2942981](http://sourceforge.net/forum/message.php?msg_id=2942981) 
 
And despite trying to follow their instructions, I am no closer to a solution.  I also posted my own question there, but no answer yet.  I was hoping perhaps some of the gurus here would be more Ubuntu focused and could help me.
 
I want to back up a directory that contains my firefox profile. And I do NOT want to back up the Cache folders. 
My command line looks like this: 
 
cd /media/tc1/DCH/ 
7z a [email]-x@/media/tc1/DCH/Program-Data/7zip-backup-scripts/dch-exl.txt[/email] "/media/disk/bkp2/bkp2-dcht.7z" "/media/tc1/DCH/Program-Data/*"  
 
I also tried it with -xr instead of -x 
7z a [email]-xr@/media/tc1/DCH/Program-Data/7zip-backup-scripts/dch-exl.txt[/email] "/media/disk/bkp2/bkp2-dcht.7z" "/media/tc1/DCH/Program-Data/*"  
 
and tried stating the source path as relative: 
7z a [email]-xr@/media/tc1/DCH/Program-Data/7zip-backup-scripts/dch-exl.txt[/email] "/media/disk/bkp2/bkp2-dcht.7z" "Program-Data/*"  
 
the file dch-exl.txt looks like this: 
 
/media/tc1/DCH/Program-Data/Firefox/Cache/* 
/media/tc1/DCH/Program-Data/Firefox/Cache/ 
Program-Data/Firefox/Cache/* 
/Program-Data/Firefox/Cache/* 
Program-Data/Firefox/Cache/ 
/Program-Data/Firefox/Cache/* 
*/Cache/* 
*/Cache/ 
*Cache*/ 
*Cache*/*  
 
Thats every combination I can think of. And yet, still, the Cache folder gets zipped up with all the rest. 
How on earth to I make 7Zip exclude the Cache folder? 
 
Thank you very much in advanced!



How about trying to use quote on the -xr?

7z a [email]-xr@"/media/tc1/DCH/Program-Data/7zip-backup-scripts/dch-exl.txt[/email]" "/media/disk/bkp2/bkp2-dcht.7z" "Program-Data/*"  

does that work? I used the command line in windows and got no problem on the exclusion list :)

---

### Post by molleradura on 2008-05-30
I can confirm that this works in linux:
7z a -xr\!filename_to_exclude.txt zipfile.7z directory/

and also does in windows:
7z a -xr!filename_to_exclude.txt zipfile.7z directory/

but i am also having problems with:
7z a -xr@full_path_filename_to_exclude zipdile.7z directory/

---

### Post by tikey on 2008-06-04
7z a [email]-xr@/home/tikey/latex_exclude.txt[/email] /home/tikey/files/_uni/Diplomarbeit/Diplomarbeit_Current08_06_04.7z /home/tikey/files/_uni/Diplomarbeit/Diplomarbeit_Current

where /home/tikey/latex_exclude.txt looks like
*.aux
*.log

works for me.

Edit: It is important that the file /.../Diplomarbeit_Current08_06_04.7z does not exist when you launch this command!

---

### Post by mdpalow on 2008-06-05
You might consider using QuickStart to create a zipped TAR file. It will do everything for you and even ask you if you want to exclude any directories from your back-up. If you want, you can then select that folder for exclusion and it'll back-up the rest for you.

Just another tool for your toolbox.

See my signature for more information.

---

