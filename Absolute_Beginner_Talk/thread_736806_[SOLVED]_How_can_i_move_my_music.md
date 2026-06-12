---
title: "[SOLVED] How can i move my music"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Kedster on 2008-03-27
o in my music folder ~/music  but then has all my music categorized by artist and in that by album but i want to just have all my music i one folder (for psp and mp3 and other stuff)i dont what any sub folder.

---

### Post by tgalati4 on 2008-03-27
Here's an idea:

Take a fresh music player say Banshee.  Import your music into the new library so it scans all directories.  

Select all of your music and drag into a new playlist.  Export that playlist to a new directory.

---

### Post by aysiu on 2008-03-27
Or do Alt-F2 ```
gnome-search-tool
``` and search the ~/music folder and cut and paste the search results into a new folder.

---

### Post by Kedster on 2008-03-28
hey guys those dint work 
is there a way just to extract all mp3 files out of my music folder to a new one

---

### Post by nick_h on 2008-03-28
Use the *find* command:
```
find . -type f -name "*.mp3" -exec mv '{}' /newfolder \;
```
You may want to do a copy rather than a move and then delete the old directory when you are sure all the files have copied correctly.

---

### Post by Kedster on 2008-03-28
and how do i change it to copy instead of extract ohh and i want to put it in
```
/home/kedster/Desktop/Music new 
```            
 how would i alter it to do that

and i just run it in terminal right  

and it should only find my music because ubuntu cant use mp3 as a part of the os right

---

### Post by nick_h on 2008-03-28
Run the following from the top level of your source directory:
```
find . -type f -name "*.mp3" -exec cp '{}' /home/kedster/Desktop/Music\ new \;
```
It will copy all files below that directory with the .mp3 directory into the "Music new" directory on your desktop.  You must create the destination directory first.

---

### Post by Kedster on 2008-03-28
will this still work if the old organized music is in the 
/home/kedster/Music
and i want it to save to 
/home/kedster/Desktop/Music

---

### Post by Kedster on 2008-03-28
it dint work
i dont think im dion it right tho

---

### Post by Tomone on 2008-03-29
Here's how I would do it (I'm assuming that all of your music is stored like ~/music/artist/album/song). This is for moving all the .mp3 files from their individual folders in ~/music to ~/mp3s. In the terminal, type in:
```
cp ~/music/*/*/*.mp3 ~/mp3s
```

---

### Post by Paqman on 2008-03-29
> **Kedster said:**
> it dint work
i dont think im dion it right tho

Did it return an error message? What did it do that wasn't right?

---

### Post by Kedster on 2008-03-29
```
kedster@kedster-laptop:~$ cp ~/music/*/*/*.mp3 /home/kedster/mp3s
cp: cannot stat `/home/kedster/music/*/*/*.mp3': No such file or directory
kedster@kedster-laptop:~$ 

```

thats what came up when i did that

---

### Post by nick_h on 2008-03-29
> **Kedster said:**
> will this still work if the old organized music is in the 
/home/kedster/Music
and i want it to save to 
/home/kedster/Desktop/Music

Try:
```
find /home/kedster/Music -type f -name "*.mp3" -exec cp '{}' /home/kedster/Desktop/Music \;
```

I thought you destination directory had the word "new" on the end. :)

The original "." after the find specified directories below the current directory as the source.  I have now specified it with your actual directory.

---

### Post by Kedster on 2008-03-29
THANK YOU SO much that worked perfect

---

