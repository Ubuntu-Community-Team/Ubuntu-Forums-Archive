---
title: "Dire help needed!!!"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by nite owl on 2007-03-22
Hi I am at university at the moment and run windows XP on my laptop, with my completed assignment that has taken me absolute weeks to complete and is due only three days away... And just as luck would have it my laptop somehow got a virus or hacked, who knows??? and now XP will not boot because its missing files and has bad clusters in files???. Anyway I frantically spoke to a friend today who gave me the great idea of booting with the ububtu live cd and retrieving the files that way. So I've done that, mounted the hard disk ('sudo mount /dev/hda2 /mnt/xp'), I can see some files I need that are still there but they are in some .lnk extension????? Please if anyone could help :)

---

### Post by AtrejuT on 2007-03-22
> **nite owl said:**
> Hi I am at university at the moment and run windows XP on my laptop, with my completed assignment that has taken me absolute weeks to complete and is due only three days away... And just as luck would have it my laptop somehow got a virus or hacked, who knows??? and now XP will not boot because its missing files and has bad clusters in files???. Anyway I frantically spoke to a friend today who gave me the great idea of booting with the ububtu live cd and retrieving the files that way. So I've done that, mounted the hard disk ('sudo mount /dev/hda2 /mnt/xp'), I can see some files I need that are still there but they are in some .lnk extension????? Please if anyone could help :)


well I don't really know your setup but .lnk files in windows usually just refer to the real files, but are not the actual files.
Maybe the actual files are in some other location? Where did you have your files on windows, and where did you look now?

---

### Post by Bias on 2007-03-22
In windows a .lnk file is a shortcut to something. Hope this helps. Good luck with retrieving the files.

---

### Post by nite owl on 2007-03-22
I had them in a folder on my Desktop, which dosent seem to be there anymore when I look at my Desktop folder, However when I looked in the recent documents folder I found it. But it's a .lnk file??

---

### Post by enopepsoo on 2007-03-22
Just do a search on the hard drive for the file, as the .lnk is probably not going to work in Linux.

You should be able to find the file there somewhere, and hopefully it was not corrupted when your system came down..................................... :confused: 

Good luck /

---

### Post by nite owl on 2007-03-22
Would anyone know the command to open these files??? even guesses?? oh and I forget the command to search, its been a while lol...Sorry about double pos

---

### Post by mcduck on 2007-03-22
> **nite owl said:**
> Hi I am at university at the moment and run windows XP on my laptop, with my completed assignment that has taken me absolute weeks to complete and is due only three days away... And just as luck would have it my laptop somehow got a virus or hacked, who knows??? and now XP will not boot because its missing files and has bad clusters in files???. Anyway I frantically spoke to a friend today who gave me the great idea of booting with the ububtu live cd and retrieving the files that way. So I've done that, mounted the hard disk ('sudo mount /dev/hda2 /mnt/xp'), I can see some files I need that are still there but they are in some .lnk extension????? Please if anyone could help :)

You are not seeing the actual files, .lnk is used for links (like a shortcut icons on your desktop). Your actual files are somewhere else. I'm not sure if you could somehow open the .lnk in Ubuntu to check where it's pointing to..

---

### Post by mahiyar on 2007-03-22
The command from the CLI is locate, or you can use search function from nautilus. However AFAIK getting to the desktop in a windows directory is a bit tricky e.g my desktop will be located in C:\Documents and Settings\User Name\Desktop.

---

### Post by Bias on 2007-03-22
> **nite owl said:**
> Would anyone know the command to open these files??? even guesses?? oh and I forget the command to search, its been a while lol...Sorry about double pos

Locate <filename>

you maybe able to open a .lnk file with a text editor and find the path but it's a long shot.

---

### Post by nite owl on 2007-03-22
yeh i tried gedit Bias it didnt work unfortunatly...I really do hate windows now, I reinstalled windows back on my desktop at one stage and had to format it 4 times due to its vunerability to attacks of all sorts.

---

### Post by mahy on 2007-03-22
.lnk files are normal windows shortcuts. The .lnk extension is never displayed on windows, but it's always there. You have to find the actual documents you wanna salvage and copy them to a USB stick or some such. They'll likely be in /mnt/something/Documents\ and\ Settings/your_username/My\ Documents/ I don't quite get where the problem might be. Just forget about .lnk files.

---

### Post by xadder on 2007-03-22
locate usually needs sudo updatdb to have been run, since it just looks into a database of files created earlier. If you are using a live-CD to look at a Window's system, there won't be such a database.

You can use find instead, e.g.:

 find . -iname "xxx*"

or whatever. The "." is for current directory, so change to the top of the system you want to search before trying this.

Otherwise I'm sure that the desktop has GUI equivalents

---

### Post by mahiyar on 2007-03-22
I do not think you can use any of the linux programmes to open files created in windows, the best option after locating the lost files would be to copy them to a pen drive and thes use somebody elses windows to do the work.

---

### Post by nite owl on 2007-03-22
locate isnt working for any of the files on the mounted hda2

---

### Post by Bias on 2007-03-22
Maybe the linux route to recovery is not the way to go!

Ever heared of bart PE?

[http://www.nu2.nu/pebuilder/#download](http://www.nu2.nu/pebuilder/#download)

You can build a cd that boots to a basic windows environment (on a different machine) then use this to boot your machine and just maybe get to the files you want. I have used this in the past with some success and keep a bart pe boot cd with my kit just in case. This might take some time but if you don't have the option of putting your HDD in another machine as a secondary disk it should do the trick.

---

### Post by mcduck on 2007-03-22
I just tested, and you can actually run 'cat file.lnk', it will output some gibberish but you'll also see in plain text the destination where the link is pointing to. Then just browse there and get the actual file ;)

---

### Post by Fatjoint on 2007-03-22
> **mcduck said:**
> I just tested, and you can actually run 'cat file.lnk', it will output some gibberish but you'll also see in plain text the destination where the link is pointing to. Then just browse there and get the actual file ;)

This is what I was going to suggest.  Even though .lnk files contain other meta-data gibberish, the location of the target document is in plain text.

If you had the document in a folder on your desktop, which is what I believe you stated earlier, then you would open either hda1 or hda2 then browse to :

Documents and Settings/<username /Desktop

If you believe it was in your My Documents, then it would be:

Documents and Settings/<username>/My Documents

If you need anymore help, you're free to contact me [email]ghostfacedkillerATyahooDOTcom[/email] (my instant messenger account)

---

