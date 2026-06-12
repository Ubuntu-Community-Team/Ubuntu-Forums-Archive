---
title: "storing music"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by jasonsexton on 2007-03-23
ok, fresh start here.  just installed 6.10  with all updates current on a new 320gb drive.  I need to know the best place to store all my mp3 files.  I previously had them stored on the desktop but someone told me that is not a good place. any advice?

---

### Post by johnc4510 on 2007-03-23
My /home is on a separate partition, and I store my music in a folder named Music on that partition. That way when I install a new version of Ubuntu, my home folder is unaffected.

---

### Post by devnulljp on 2007-03-23
Anywhere you want them really. 
How about something like ~/music ?
Nothing wrong with storing on the desktop, but doesn'tit get real messy? 
You can always make a link to the ~/music directory on your desktop too (ln -s ~/music ~/Desktop/ should do it)

...unless you're sharing with other users, then stick it somewhere where they have read access.

---

### Post by jasonsexton on 2007-03-23
if I have a seperate login for my wife and I want to share he music so she can listen when she logs in, where should I store the files?

---

### Post by Foudre on 2007-03-23
hmm, you could just creat a new folder on the main tier of the hard drive,

but ubuntu has funny user rights, so to get around this you need to open konquerer with rights. Just (you may not like the idea of command lines, but its just one line, and it explains itself)

open the konsole
type:

sudo konqueror

now just right click create folder, 
name it music (or what ever)
right click it, properties
go over to the premmessions tab, on all the ones, owner can read/ write, change it to all groups can read slash right

its an easliy accessable folder now with the url:  /music that all users can see and use

---

### Post by jasonsexton on 2007-03-23
should have been more clear
using ubuntu 6.10

konsole is in kde right?

---

### Post by Foudre on 2007-03-23
oh sorry, konsole, terminal same thing, (sorry I'm used to kde so much) what ever the terminal for gnome is just use that, or if you can't find it one that works on both gnome and kde is, xterm might be the name of it (can't remember if the alt+f2 shortcut works on gnome (it opens the run dialog and you can just type konqueror, oh and sorry umm konqueror is also kde)) 

umm what the name of the programme you use to like browse your computer just do that

sorry i had a good idea, but i forgot what gnome uses, i havn't used it in a long time
but you get the idea of it, terminal  sudo insert_name_of_file_browser

---

### Post by Foudre on 2007-03-23
oh and using 6.06 ot 6.10 won't make a differance here,

---

### Post by jasonsexton on 2007-03-23
thanks

---

### Post by devnulljp on 2007-03-26
> **jasonsexton said:**
> if I have a seperate login for my wife and I want to share he music so she can listen when she logs in, where should I store the files?

Make a new group (something like musiclisteners orsomething), add you and your wife's usernames to that group, create a new directory somewhere (pretty much anywhere), move the music files in there and give the new group read and write access to that directory.
```
sudo -s
groupadd musicusers
usermod -G musicusers wife's_user_name
mkdir /home/sharedmusic
```
Copy all your music files in there, then...
```
chown -R your_user_name:musicusers /home/sharedmusic
chmod -R ug+rw /home/sharedmusic
```

You could get clever and use mount --bind to remount that directory in each of your home directories too...add something like this to /etc/fstab:
```
/home/musicusers        /home/your_user_name/music    bind    default,bind    0       0
/home/musicusers        /home/wife's_user_name/music    bind    default,bind    0       0
```

---

### Post by fakie_flip on 2007-03-26
She is using windows right? That's too bad if she is. You need samba to share you music files with her to a windows computer. After installing samba, you must right click your music folder where ever it is and click on share this folder. You need to be in the same workgroup as her computer is. You can configure that in samba. You also need to create a password for her to login with to view your shared folders/files. In windows, she should go to Network Places>Entire Network> click on the name of the workgroup, and your computer should show up there.

---

### Post by fakie_flip on 2007-03-26
> **jasonsexton said:**
> if I have a seperate login for my wife and I want to share he music so she can listen when she logs in, where should I store the files?

Oh, sorry. I did not see this post. I did not know you shared the same computer with her. I thought she was using a different one. In that case you should put the music in a folder here.

/media/Music

First change the permissions, so that you are both able to access and modify the music.

sudo chown -Rc yourusername:yourusername /media/Music
sudo chmod -Rc 777 /media/Music

And then create a symbolic link to both of your home directories.

sudo ln -s /home/herusername/
sudo ln -s /home/yourusername/

---

