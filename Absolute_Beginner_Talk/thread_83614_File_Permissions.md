---
title: "File Permissions?????"
date: 2005-10-29
forum: Absolute Beginner Talk
---

### Post by Lilac Haze on 2005-10-29
Being very much a newbie I need some help Please.......

In order to try to install my USB Modem in Ubuntu I need some files that I have downloaded from the internet onto CD. I now have to copy them from CD into my home folder to open them and stuff to get my modem working. 

Every time I try to do this whether I Drag 'n Drop _or_ copy and paste the files move but are now marked with padlocks. This seems to be about file permissions as when I look at their properties I'm told that I can't change anything. I need to be the "Owner".

I don't understand. I'm the only person using this computer, mine is the only accout on here, but if I log off and try to log in as "root" it tells me I can't do it at the login window.:???: 

Where do I loin as "root" so that I can have free access to these files?

Thanks  to everyone prepared to help us beginners learn what must seem some very basic things.

---

### Post by towsonu2003 on 2005-10-29
[QUOTE=Lilac Haze]Being very much a newbie I need some help Please.......

In order to try to install my USB Modem in Ubuntu I need some files that I have downloaded from the internet onto CD. I now have to copy them from CD into my home folder to open them and stuff to get my modem working. 

Every time I try to do this whether I Drag 'n Drop _or_ copy and paste the files move but are now marked with padlocks. This seems to be about file permissions as when I look at their properties I'm told that I can't change anything. I need to be the "Owner".

I don't understand. I'm the only person using this computer, mine is the only accout on here, but if I log off and try to log in as "root" it tells me I can't do it at the login window.:???: 

Where do I loin as "root" so that I can have free access to these files?

Thanks  to everyone prepared to help us beginners learn what must seem some very basic things.[/QUOTE]

i'm a newbie so you might wanna wait for others to take a look as well...

cd /home/username

will take you to /home/username (username=yours)

mkdir copying

will make a directory called copying

sudo cp -R /media/cdrom0 /home/username/copying

hopefully will copy everything in the cd to that new directory

sudo chown -R usename:username /home/username/copying

will change file ownership (which usually fixes everything in those situations)

if not, use chmod (i am very weak with that)

you can also

sudo nautilus

to do all this stuff in X but I hate being root in nautilus - I keep deleting or displacing important stuff!

---

### Post by matthewv on 2005-10-29
Just copy the files over. Then go to command line and run ```
sudo chmod 777 file.name
```This will allow all users to access the files.

---

### Post by aysiu on 2005-10-29
Ubuntu uses sudo, not root:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

There are a bunch of commands you can use to change ownership or change permissions, but I think the easiest way for someone new to Ubuntu/Linux is to just run the command (by pressing Alt-F2) ```
gksudo nautilus
``` Then right-clicking the offending files/folders and setting the permissions you want. If you're using KDE, the command should be ```
kdesu konqueror
```

---

### Post by Lilac Haze on 2005-10-29
Thanks to you all. I knew someone here would help me:-)

Off to try this out now. Maybe next time I login It could be from Ubuntu instead of *windows xp.*

That would be good!

---

