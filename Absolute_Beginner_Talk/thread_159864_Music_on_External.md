---
title: "Music on External"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by mcletter on 2006-04-13
Hi, I was just curious if it was possible, using RhythmBox, or any other music program, to import music from a folder on an external harddrive that is networked from a windows computer. I can acess the folder but cant acess it from the music program. Any help would be awesome. thanks

---

### Post by xerxesv5 on 2006-04-13
I have my Windows share mounted (are you familiar with the term?) at one of the directories in my linux root. That way I can access the share as if they were files on my local system... except that they're not. =)

Okay so, first open a terminal and type:

```
sudo apt-get install smbfs
```

This fetches the package that you need to mount Windows shares on your linux filesystem like you would drives.

Make a directory to mount that share folder in, type "mkdir <path>", where that <path> is the dir you want to create, eg: mkdir /media/musicshare

Then you can type this, replacing the <> stuff with your details as you go along:

```
sudo mount -t smbfs -o username=<win_user>,password=<your_passwrd> <network_share> <mount_point>
```

For example, I type something like this:

```
sudo mount -t smbfs -o username=johndoe,password=foobar //server/music /media/musicshare
```

If nothing breaks along the way, you should be able to access the music at /media/whatever-name-you-chose. If you need me to explain further on anything, feel free to ask. Hope that helps some. ;)

---

### Post by Jose Catre-Vandis on 2006-04-13
Simple answer (from a simple user)

Its not just a case of having the folder viewable and shared in File Browser. You need to mount the folder/drive:- e.g. 

//192.168.0.12/Music       /media/MyMusic 

(plus any permissions, user/pass read write etc)

in order for your music player to play the tunes. Doing this then makes it appear that your tunes are on your main machine, and speed is great. process for accessing is much as Xerxesv5 in idicates.

---

### Post by mcletter on 2006-04-13
Stupid question but the drive I am trying to mount has this location.

//jeff/EXTERNAL%20(E)

and when I enter that, it says the "(" is an invalid token, what can I do about this?

---

