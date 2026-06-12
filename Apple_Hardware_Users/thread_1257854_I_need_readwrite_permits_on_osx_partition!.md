---
title: "I need read/write permits on osx partition!"
date: 2009-09-04
forum: Apple Hardware Users
---

### Post by gagginaspinnata on 2009-09-04
Hello,
I don't know why but my osx partition has gone :P Osx doesnt starts anymore. I've checked with disk utility from leopard dvd and there is an error on that partition. When I try to fix it, it says "I cannot fix it you need to format" :o I cant format it cos I need to backup some very important file yet!

I've tried to make a dmg image of che partition, still with disk utility, but it says that the partition is damaged and cant do it.

Now I'm trying to save the file from the ubuntu partition! I've mounted the osx partition and with the terminal
```
sudo nautilus
```
I can now see the whole parptition with its file. I can open each file but it doesent make me save it! There is some permits issue!

I've just tried with
```
sudo chmod -R 777 /media/Mac\ HD
```

but doesen't work!

There is any way to backup this file stored in the osx partition? 
ssh transfer? permits solution?

---

### Post by gagginaspinnata on 2009-09-05
There's noone who can help me? :confused:

---

### Post by rifak on 2009-09-05
just copy and paste it to your ubuntu partition or usb stick or whatever. you don't have to open the file and "save as.." to your ubuntu partition.

---

### Post by al_lobby on 2009-09-06
Hi :)
I have the same problem and i find that there is some mistakes in your codes above 
and here is the correction:
Go to Application/ Accessories/ Terminal:

1st:
```
cd ..
```it will lead u to home directory then:

2nd:
```
cd ..
```you'll be in "/" directory

3rd:
**[COLOR=Red]YOU MUST TO MOUNT YOUR MAC HARD DRIVE[/COLOR]** !!! after mounting it go to terminal again 
```
cd media 
```4th:
```
sudo chmod -R 777 Mac\ HD
```**Attintion:** be sure about the name of your Mac HD if it is as you wrote before or not
(Mac HD), Because in my machine it have different name it seems like this (Macintosh HD), if yours like me you must to change the 4th code into:
```
sudo chmod -R 777 Macintosh\ HD
```

---

### Post by TheStickyNoteKing on 2009-09-06
If you've got journaling enabled (and it's hfs+, which I am assuming) you won't be able to write to it no matter what you do, only read. However, if journaling is disabled, everything should work out well for you.

Just open up our terminal, and cd to wherever you've mounted your partition (if you haven't already, do so). You don't to mess up the entire partition, as that will mess up your entire partition, so cd to whichever file or folder it is that you need to write to.

Now, do ```
sudo chown [user] [file]
```followed by ```
sudo chmod u=rw [file]
```This will set up *user* as the owner of the file, and grant that user read and write permissions to it. If it is a folder, and you want to grab all the files inside, insert +R before chown/chmod.

Note that this will very likely upset your OS X, and crazy stuff might happen. There might even be a better way of doing it! It's a bad approach because of the chown command. I've found that even the root user won't be allowed to change permissions on hfs+ volumes without yoinking ownership first, and yoinking ownership is generally not a good thing. Instead you should make a copy of the file, and use that instead. If you later need it in OS X, you can put it on a usb that both systems can read (ext2/3/4 is a pain in OS X, at least in 10.6). Of course since your system is dead anyways, you probably don't care much about finesse.

---

