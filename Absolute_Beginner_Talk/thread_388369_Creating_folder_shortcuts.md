---
title: "Creating folder shortcuts"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by jondecker76 on 2007-03-19
Hello,
Here is my situation:

I have 2 user accounts on my Ubuntu install (both admin accounts). There is information that we both share - namely a shared Music library, a shared pictures library and a shared movie library.

How I have this set up now is: In the /home folder i created a Music, Movie and Picture folders (opening Nautilus with sudo) and then changed permissions so that anyone can do anything with the files (read/write etc). And it appears to work from both accounts. But, how can i create a shortcut on my desktop to these extra folders in /home?

Also, am I going about this the right way? Is there a better way I should be sharing these folders and files between users of the local machine?

any advice would be greatly appreciated

---

### Post by LanDan on 2007-03-19
hope i can be of some help,

Changing the rights with Nautilus is one option, and if it works that good, personally i would use the commandline using for instance "chown" chgrp" with rwx flags changing the owner or the group who have access to it, but that is not your question.

as you might have noticed the desktop icons popping up on your desktop when you insert a cd or usb are located in the folder /media, so you could make a symlink to that folder like so

sudo ln -s /home/you/music /media/music


providing you've set the permissions ok, this should work

---

### Post by mcduck on 2007-03-19
'ln -s /home/Movies ~/Desktop/Movies', and repeat same for other directories. (no 'sudo' needed here, as long as you run the command as the user to whose desktop you are creating the link).

---

### Post by LanDan on 2007-03-19
> **mcduck said:**
> 'ln -s /home/Movies ~/Desktop/Movies', and repeat same for other directories. (no 'sudo' needed here, as long as you run the command as the user to whose desktop you are creating the link).

this would create a symlink folder of your own folder under home to your own desktop, but not to someone elses with whom you want to share the same files.

edit:

unless i'm mistaking and you actually created /home/Music instead of /home/you/Music, in that case this would indeed be the right aproach if you would only want to share it with user A and B

if on the other hand you would want to share it with all the users on your system, my approach would be better

---

### Post by jondecker76 on 2007-03-19
Yes, i created /home/Music

I'm looking for a place where ALL users of the computer have access to the folder and files within, along with full permissions for create/edit/delete..

So am i going about this the right way?  I think its cleaner than putting it in /home/me/music and making everyone else browse to it...

thanks again,

Jon

---

### Post by srt4play on 2007-03-19
What I do is create a separate /data directory and make it world-readable/writable.  I also put this on a separate partition so I don't have to back it up when I reinstall.

---

### Post by LanDan on 2007-03-21
> **srt4play said:**
> What I do is create a separate /data directory and make it world-readable/writable.  I also put this on a separate partition so I don't have to back it up when I reinstall.

true, partitioning would be a good idea, but its something you need to consider before you install (having /home separate is a nice idea as well) ,
nevertheless when you make a folder like "/media/Music"  it will show up on everybody's desktop

you might want to play with the permissions since you can make it available or unavailable for certain users depending on your needs.

the simplest way to make it available for all users to read write and execute would be the following command

chmod -R 770 /media/Music

---

