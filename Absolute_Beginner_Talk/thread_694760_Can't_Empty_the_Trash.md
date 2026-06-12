---
title: "Can't Empty the Trash"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-02-12
Hello!
I can not empty the trash. After I right click on the trash icon and click empty the trash nothing happens! And I had flash disk. Now there is a trash folder inside it and I can't delete it too. What should I do?
+++
I can't delete that folder even in windows. + Windows said that autorun.inf is a virus and removed it. Is there any virus in my linux?
+++
Making the hard disk trash empty is more important than the flash disk to me.
____
Thanks.

---

### Post by ptn107 on 2008-02-12
```
cd ~/.Trash
```

then force delete everything in the folder (be EXTREMELY careful with this, only execute this command from within the /.Trash folder, you may need to use 'sudo' if this doesn't allow you to delete the files)
```
rm -rf *
```

---

### Post by Hoom@n on 2008-02-12
```
hooman@hooman-laptop:~$ cd ~/.Trash
hooman@hooman-laptop:~/.Trash$ rm -rf *
rm: cannot remove `dictconv-0.2xyz/src/.deps/sdict.Po': Permission denied
rm: cannot remove `dictconv-0.2xyz/src/.deps/plaintextdictbuilder.Po': Permission denied
rm: cannot remove `dictconv-0.2xyz/src/.deps/babylon.Po': Permission denied
rm: cannot remove `dictconv-0.2xyz/src/.deps/dictdbuilder.Po': Permission denied
rm: cannot remove `dictconv-0.2xyz/src/.deps/sdictreader.Po': Permission denied
rm: cannot remove `dictconv-0.2xyz/src/.deps/dictconv.Po': Permission denied
rm: cannot remove `dictconv-0.2xyz/src/.deps/stardictreader.Po': Permission denied
rm: cannot remove `dictconv-0.2xyz/src/.deps/freedictreader.Po': Permission denied
rm: cannot remove `dictconv-0.2xyz/src/.deps/stardict.Po': Permission denied
rm: cannot remove `dictconv-0.2xyz/src/.deps/stardictbuilder.Po': Permission denied
rm: cannot remove `dictconv-0.2xyz/src/.deps/babylonreader.Po': Permission denied
hooman@hooman-laptop:~/.Trash$ 
```
As you sea it doesn't work. Is there any other way?
+++
Please tell me if I have a virus.
____
Thanks.

---

### Post by Hoom@n on 2008-02-12
Oops! It worked with sudo. Now please tell me what is rm and how can I use it. Because I have to use it with sudo to remove something from my flash disk. Thansk.

---

### Post by dca on 2008-02-12
rm = Remove
Same as del or deltree in DOS.  
When adding the -f switch or option forces the removal of files
When adding the -r switch or option recursively deletes similar to deltree removing all subsequent directories and files...
 
Be careful.  When you add sudo you are working as the root or super user.  No protection, once it's gone, it's gone kinda' thing...

---

### Post by themusicwave on 2008-02-12
rm is a linux command to delete files and folders.

type:

man rm

to get a listing of all it's commands.  man will give you the manual for any command

type:

man man to get man's manual :)

If you read through the man page you can learn all the things rm can do.  Be very caurfule with the 

rm -rf *

Command.  The r is recursive and the f is force.  So basically it starts in whatever folder you are in and delete EVERYTHING contained in it and it's sub folders.

---

### Post by ExpatPaul on 2008-02-12
> **Hoom@n said:**
> Please tell me if I have a virus.
____
Thanks.

You don't have a virus. For some reason you didn't have permission to change (or delete) the files in your trash folder. I'm guessing that this is a result of how you downloaded them.

Sudo adopts the root permissions which is why you could delete them with sudo. It's also why you should be very careful when using sudo.

You can see the permissions on any file by right clicking on it, selecting properties and then  clicking on the permissions tab.

---

### Post by Hoom@n on 2008-02-12
Thank you. I gonna test it on the flsh disk!

---

### Post by recluse2 on 2008-02-14
Thank you guys! I just ran into this problem myself.

---

### Post by Hoom@n on 2008-02-14
Is it the right path:
```
hooman@hooman-laptop:/media/disk/.Trash-hooman$ sudo rm -rf *
[sudo] password for hooman:
hooman@hooman-laptop:/media/disk/.Trash-hooman$ 

```
There are still alot of files in the trash. What should I do?

---

### Post by meho_r on 2008-02-14
For some reason, even when I ran "sudo rm -rf *" in my ~/.Trash folder, there still remained couple of folders. I ran command again and they were still there. Then I simply selected them, done regular "Delete" and they dissapeared :)

---

### Post by Hoom@n on 2008-02-16
By deleteing them I get this: ""/media/disk...2_i386.deb" cannot be deleted because it is on a read-only disk." How should I remove them?

---

### Post by bumanie on 2008-02-16
If you type command >  gksudo nautilus in terminal, you should be able to go to 'computer' and find your way to the garbage bin. gksudo is the graphical super user version, so be careful what you delete because it will be irrecoverable, however in this mode, you should, theoretically, be able to delete the items in garbage.

---

### Post by karlwilbur on 2008-03-27
Here's one for ya...
What happen to the file permissions? Well, actually I don't care what happened, I just want to delete these files. I get "Permission denied" even with sudo. Can't view file attributes, even with sudo.

Here is command history:

```

karl@karl-desktop:~/.Trash/subtitles/015/00$ rm *
rm: cannot remove `pic0843.pgm': Permission denied
rm: cannot remove `pic0844.pgm': Permission denied
rm: cannot remove `pic0845.pgm': Permission denied
karl@karl-desktop:~/.Trash/subtitles/015/00$ sudo rm *
rm: cannot remove `pic0843.pgm': Permission denied
rm: cannot remove `pic0844.pgm': Permission denied
rm: cannot remove `pic0845.pgm': Permission denied
karl@karl-desktop:~/.Trash/subtitles/015/00$ ls -l
total 0
?--------- ? ? ? ?                ? pic0843.pgm
?--------- ? ? ? ?                ? pic0844.pgm
?--------- ? ? ? ?                ? pic0845.pgm
karl@karl-desktop:~/.Trash/subtitles/015/00$ sudo lsattr
./pic0843.pgm: Permission denied
./pic0844.pgm: Permission denied
./pic0845.pgm: Permission denied
karl@karl-desktop:~/.Trash/subtitles/015/00$ unlink pic0843.pgm 
unlink: cannot unlink `pic0843.pgm': Permission denied
karl@karl-desktop:~/.Trash/subtitles/015/00$ WTF!
bash: WTF!: command not found
karl@karl-desktop:~/.Trash/subtitles/015/00$

```

---

### Post by karlwilbur on 2008-03-27
OK...I got rid of them...here's what I did:

1) sudo nautilus

2) navigate to: File System -> home -> karl -> .Trash 

3) Right click on "subtitles"

4) Select "Move to Trash"

and they're gone. Cool.

I hope that this helps someone somewhere.

---

### Post by asnd16 on 2008-03-31
Yeah this did not work for me. . . The folders still appear in the trash . .  They are libgpod and pidgin install folders so I know they have contents that were created with sudo but I am unable to even move them out of the trash. . . IT COPIES . . intersting . . . possible that in the install of Hardy has an issue? they have sat there for about a month. . . . lOL


With the sudo nautilus  way I go in and in the trash folder there is nothing . . . another thing I notice is that in the Trash:///  ligpod and gspcav are labled like this _libgpod  _gspcav    what does that mean?

---

### Post by tonyshangrila on 2008-06-06
In case anyone else is going insane trying to do this in Hardy Heron, please refer to this thread:
[http://ubuntuforums.org/showthread.php?p=5014310](http://ubuntuforums.org/showthread.php?p=5014310)

The location of the Trash has moved in Hardy...

---

