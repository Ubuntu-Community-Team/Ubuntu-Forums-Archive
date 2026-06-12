---
title: "Where do I put things.."
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by Aybara on 2006-01-20
Hi. Just went from XP to Ubuntu, and need some advice.

Where is it "normal" to store music/video/photos and such? I made a dir called /home/anders/music, but I have no idea if this was a good idea.

I dl'ed azureus yesterday, since I couldn't seem to find it on apt-get. After unpacking it I ran it by typing ./azureus.
1. Where should I put the files I unpacked?
2. Where should azureus download to? I set it to /home/anders/downloads/azureus, but it seems that Azureus isn't allowed to create files there.

Have a nice weekend!

---

### Post by 23meg on 2006-01-20
That's a good idea; store data files in subfolders under your home directory, including Azureus downloads. If there's an access problem make sure you have read/write permissions for the folder (right click, properties, permissions)

For Azureus see this: [https://wiki.ubuntu.com/AzureusHowTo](https://wiki.ubuntu.com/AzureusHowTo)

---

### Post by chimera on 2006-01-20
well, your home directory (the /home/anders in your case) is the place where you should put everything you download/install, since it's the only directory you have the perimmision to write to by default (you can change that, but I wouoldn't recommend you to), and yeah, organizing it into folders like music, downloads etc... is a good idea...I just might do it too:)

---

### Post by Dr Von Bon Bon on 2006-01-20
Things that I download or don't need to access that often I put in my home folder but for things like videos and documents I create and put them all on the desktop for easy access.


It works for me at least.

---

### Post by chimera on 2006-01-20
desktop is just a subdirectory of your home dir, so technically you're still putting them in your home dir;)

---

### Post by matthew on 2006-01-20
[quote=Aybara]Hi. Just went from XP to Ubuntu, and need some advice.

Where is it "normal" to store music/video/photos and such? I made a dir called /home/anders/music, but I have no idea if this was a good idea.[/quote]This is very typical and a good idea. Good job!

---

### Post by hen3rz on 2006-01-20
You can find a wiki about how the file system works in linux from the link below. 

[http://en.wikipedia.org/wiki/Filesystem_hierarchy_standard](http://en.wikipedia.org/wiki/Filesystem_hierarchy_standard)

I found it very helpful when I was starting out as it lets you know what each folder in your / is used for and what its purpose is.

---

### Post by Aybara on 2006-01-21
Thanks for the helpful answers. The filesystem explanation was _exactly_ what I needed :-)

When I do an ls on my /home/anders/download/azureus folder, I see

drwxr-xr-x  2 root root 4096 2006-01-21 10:17 azureus

Shouldn't my permissions be ok?

Off topic: I have set up instant mail notification, but I never get any e-mails when people reply to my posts. Anyone else had  this problem?

---

### Post by ysse on 2006-01-21
Hi, 

Your own folders really should have **anders** as owner and as group. As things are now you don't have write permission, as only the owner (root) can write to the folder. Maybe you were working as root (sudo -i) when you created your download folders.

You can fix the permissions from the command line ```
sudo chown anders:anders azureus
```.

---

### Post by Mustard on 2006-01-21
[QUOTE=ysse]Hi, 

Your own folders really should have **anders** as owner and as group. As things are now you don't have write permission, as only the owner (root) can write to the folder. Maybe you were working as root (sudo -i) when you created your download folders.

You can fix the permissions from the command line ```
sudo chown anders:anders azureus
```.[/QUOTE]

I'd expand that to..

```
sudo chown anders:anders /home/anders/download/azureus
```

as the first version assumes you are in the /home/anders/download directory, whereas the one above should work from the default working directory that gnome terminal starts in ie /home/anders.

You can find your current working directory by entering..

```
pwd
```

You can read about the above commands using the 'man' command...

```
man chown
man pwd
```

Hit the 'q' key to exit from the manuals.

---

