---
title: "Amarok Missing Some of My Collection"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by mdvigi7536 on 2007-07-30
Hi there...I'm still pretty new to Ubuntu, and I'm not a computer programmer or anything, so be gentle, please. :-)

I have been songs to my computer from CDs.  I have set up a folder in my Home called "Music."  The SoundJuicer program has kindly put a separate folder in Music for each artist, separate folders inside that for each of their albums, and then the files for that CD.  It works well, and I'm generally pleased.

I have heard all these great things about Amarok, so I thought I would give it a try.  Like the other music programs, I told it all my songs were stored under "Music" and its subdirectories.  I was told to wait while it built my collection.

The thing is, Amarok skipped many of my albums, and randomly, too.  Example:  A have four albums by a certain artist.  Amarok got three folders and skipped the fourth.  I have about 1,400 songs in my Music folder and Amarok only got less than 800.

What's the solution?  I really don't want to load them by hand--other programs haven't had any problems at all with finding all my music.  Please let me know what I can do--I'd really like to try Amarok!

Thanks for all your help.

--Mike

---

### Post by DBStevens on 2007-07-30
"A have four albums by a certain artist. Amarok got three folders and skipped the fourth."

Could you go to your Music folder and the particular artist follder and run:

ls -Ro

Then post the results

Also could you provide the contents of:

cat /your Home/.kde/share/apps/amorak/collection_scan.files

you might want to compress that file and attach it to your post.

---

### Post by mdvigi7536 on 2007-07-30
I will be happy to do this, but I'm afraid I'm a little confused.

What do you mean by "go into the folder?"  I realize that sounds stupid, but I think you mean more than going to Places/Home Folder/Music/[Artist]/[4th folder].

And where do I find that file you asked me to post, and how do I compress it?

Sorry to ask such dumb questions--I really am a rookie, but I'm trying to learn.

Thanks again.

---

### Post by mdvigi7536 on 2007-07-30
OK, I think I figured out what you meant by the first part of your request.

I opened the Terminal and found my way to the Lil' Kim folder [she's the artist I used as an example in the original message].  Here's what happened when I ran that command in the artist folder:

mike@laptop:~/Music/Lil' Kim$ ls -ro
total 12
drwxr-xr-x 2 mike 4096 2007-05-05 20:39 The Naked Truth
drwxr-xr-x 2 mike 4096 2007-05-05 23:46 La Bella Mafia
drwxr-xr-x 2 mike 4096 2007-06-30 23:07 Hard Core

Also, I went into the Hard Core album folder--that's one that Amarok missed--and ran the command again:

mike@laptop:~/Music/Lil' Kim/Hard Core$ ls -ro
total 49608
-rw-r--r-- 1 mike 2785148 2007-06-30 23:07 15 - **** You.mp3
-rw-r--r-- 1 mike  863794 2007-06-30 23:07 14 - Player Haters.mp3
-rw-r--r-- 1 mike 4350826 2007-06-30 23:07 13 - Not Tonight.mp3
-rw-r--r-- 1 mike 4007268 2007-06-30 23:06 12 - We Don't Need It.mp3
-rw-r--r-- 1 mike 4447378 2007-06-30 23:05 11 - M.A.F.I.A. Land.mp3
-rw-r--r-- 1 mike 4469103 2007-06-30 23:05 10 - Dreams.mp3
-rw-r--r-- 1 mike 3157969 2007-06-30 23:04 09 - Queen [email]B@#$H.mp[/email]3
-rw-r--r-- 1 mike  799006 2007-06-30 23:04 08 - Scheamin'.mp3
-rw-r--r-- 1 mike 4175694 2007-06-30 23:04 07 - Drugs.mp3
-rw-r--r-- 1 mike 4411848 2007-06-30 23:03 06 - Crush On You.mp3
-rw-r--r-- 1 mike  737565 2007-06-30 23:03 05 - Take It!.mp3
-rw-r--r-- 1 mike 5363129 2007-06-30 23:03 04 - Spend a Little Doe.mp3
-rw-r--r-- 1 mike 4813502 2007-06-30 23:02 03 - No Time.mp3
-rw-r--r-- 1 mike 4116784 2007-06-30 23:01 02 - Big Momma Thang.mp3
-rw-r--r-- 1 mike 2154036 2007-06-30 23:01 01 - Intro in A-Minor.mp3

Hope this helps...thanks for all your help...please don't laugh at me or my newness! :-)

--Mike

---

### Post by DBStevens on 2007-07-30
Applications > Accesories > Terminal

cd /your home directoryname/Music/artist

ls -Ro

Should produce a list of the albums and tracks on the albums

copy and paste that list into a post.

---

### Post by DBStevens on 2007-07-30
I really want to see all of the entries for the artist and that is a capital R and yes it makes a difference.

As for the other request since the file is going to be relatively large it needs to be compressed.

You can use the file manager to get to the file and a program like Ark to provide a compressed version which you can attach to a post.

The file that I am asking you to compress is hidden so you'll have to unhide it to see it in the file manager the unhide is in the view menu of the file manager.

I have tons of patience.

---

### Post by mdvigi7536 on 2007-07-30
Oops...didn't know it needed to be "R."

I ran it from the main folder for the artist and it spit out stuff for everything in the album folders...I assume this is what you wanted:

mike@laptop:~/Music/Lil' Kim$ ls -Ro
.:
total 12
drwxr-xr-x 2 mike 4096 2007-06-30 23:07 Hard Core
drwxr-xr-x 2 mike 4096 2007-05-05 23:46 La Bella Mafia
drwxr-xr-x 2 mike 4096 2007-05-05 20:39 The Naked Truth

./Hard Core:
total 49608
-rw-r--r-- 1 mike 2154036 2007-06-30 23:01 01 - Intro in A-Minor.mp3
-rw-r--r-- 1 mike 4116784 2007-06-30 23:01 02 - Big Momma Thang.mp3
-rw-r--r-- 1 mike 4813502 2007-06-30 23:02 03 - No Time.mp3
-rw-r--r-- 1 mike 5363129 2007-06-30 23:03 04 - Spend a Little Doe.mp3
-rw-r--r-- 1 mike  737565 2007-06-30 23:03 05 - Take It!.mp3
-rw-r--r-- 1 mike 4411848 2007-06-30 23:03 06 - Crush On You.mp3
-rw-r--r-- 1 mike 4175694 2007-06-30 23:04 07 - Drugs.mp3
-rw-r--r-- 1 mike  799006 2007-06-30 23:04 08 - Scheamin'.mp3
-rw-r--r-- 1 mike 3157969 2007-06-30 23:04 09 - Queen [email]B@#$H.mp[/email]3
-rw-r--r-- 1 mike 4469103 2007-06-30 23:05 10 - Dreams.mp3
-rw-r--r-- 1 mike 4447378 2007-06-30 23:05 11 - M.A.F.I.A. Land.mp3
-rw-r--r-- 1 mike 4007268 2007-06-30 23:06 12 - We Don't Need It.mp3
-rw-r--r-- 1 mike 4350826 2007-06-30 23:07 13 - Not Tonight.mp3
-rw-r--r-- 1 mike  863794 2007-06-30 23:07 14 - Player Haters.mp3
-rw-r--r-- 1 mike 2785148 2007-06-30 23:07 15 - **** You.mp3

./La Bella Mafia:
total 24764
-rw-r--r-- 1 mike 1366163 2007-05-05 23:43 01 - Intro.mp3
-rw-r--r-- 1 mike 5216841 2007-05-05 23:44 02 - Hold It Now (feat. Havoc).mp3
-rw-r--r-- 1 mike 3845508 2007-05-05 23:44 03 - Doing It Way Big.mp3
-rw-r--r-- 1 mike 4778452 2007-05-05 23:45 04 - Can't F**k With Queen Bee (feat. Governor & Shelene Thomas with Full Force).mp3
-rw-r--r-- 1 mike  819482 2007-05-05 23:45 05 - Hollyhood Skit.mp3
-rw-r--r-- 1 mike 3184736 2007-05-05 23:46 06 - Shake Ya Bum Bum (feat. Lil' Shanice).mp3
-rw-r--r-- 1 mike 3137931 2007-05-05 23:46 07 - This Who I Am (feat. Swizz Beatz & Mashonda).mp3
-rw-r--r-- 1 mike 2944462 2007-05-06 00:07 08 - The Jump Off (feat. Mr. Cheeks).mp3

./The Naked Truth:
total 72032
-rw-r--r-- 1 mike  618521 2007-05-05 20:30 01 - Intro.mp3
-rw-r--r-- 1 mike   59874 2007-05-05 20:30 01 - Intro.ogg
-rw-r--r-- 1 mike 3474442 2007-05-05 20:31 02 - Spell Check.mp3
-rw-r--r-- 1 mike 4204617 2007-05-05 20:31 03 - Lighters Up.mp3
-rw-r--r-- 1 mike  893970 2007-05-05 20:32 04 - Shut Up Bitch Intro.mp3
-rw-r--r-- 1 mike 4151956 2007-05-05 20:32 05 - Shut Up Bitch.mp3
-rw-r--r-- 1 mike 3965955 2007-05-05 20:33 06 - Whoa.mp3
-rw-r--r-- 1 mike 4092182 2007-05-05 20:33 07 - Slippin.mp3
-rw-r--r-- 1 mike 2354325 2007-05-05 20:34 08 - Answering Machine Skit 1.mp3
-rw-r--r-- 1 mike 4339197 2007-05-05 20:34 09 - All Good.mp3
-rw-r--r-- 1 mike 3734838 2007-05-05 20:35 10 - I Know You See Me.mp3
-rw-r--r-- 1 mike  482691 2007-05-05 20:35 11 - W.P.I.M.P..mp3
-rw-r--r-- 1 mike 3874023 2007-05-05 20:35 12 - Quiet (feat. The Game).mp3
-rw-r--r-- 1 mike 4009007 2007-05-05 20:36 13 - Durty.mp3
-rw-r--r-- 1 mike 2293304 2007-05-05 20:36 14 - Answering Machine Skit 2.mp3
-rw-r--r-- 1 mike 4193366 2007-05-05 20:37 15 - We Don't Give a **** (feat. Bun B. & Twista).mp3
-rw-r--r-- 1 mike 4281537 2007-05-05 20:37 16 - Gimmie That (feat. Maino).mp3
-rw-r--r-- 1 mike 3666285 2007-05-05 20:38 17 - Kitty Box.mp3
-rw-r--r-- 1 mike 4359695 2007-05-05 20:38 18 - Kronik (feat. Snoop Dogg).mp3
-rw-r--r-- 1 mike  911525 2007-05-05 20:38 19 - Winners and Losers.mp3
-rw-r--r-- 1 mike 3984794 2007-05-05 20:39 20 - Get Yours (feat. T.I. & Sha-Dash).mp3
-rw-r--r-- 1 mike 9642682 2007-05-05 20:40 21 - Last Day.mp3
mike@laptop:~/Music/Lil' Kim$ 

Hard Core is the album that's in my other music programs but not in Amarok

I'm working on your other request but finding it difficult...will keep trying.

---

### Post by mdvigi7536 on 2007-07-30
See if this makes sense:

mike@laptop:~/Music/Lil' Kim$ /home/mike/.kde/share/apps/amarok/collection_scan.files
bash: /home/mike/.kde/share/apps/amarok/collection_scan.files: Permission denied
mike@laptop:~/Music/Lil' Kim$ sudo cat /home/mike/.kde/share/apps/amarok/collection_scan.files
Password:
/var/run/console/mike:7
/tmp/.X0-lock
/tmp/orbit-mike/bonobo-activation-register.lock
/tmp/orbit-mike/bonobo-activation-server-iormike@laptop:~/Music/Lil' Kim$

---

### Post by DBStevens on 2007-07-30
Mike,

I'd try that from the file manager and the file isn't something that you can run which is why you got first Permission denied message.

Now I hve no idea what produced the the other mess.

That file manager is  Places > Computer mike in the left pane.

Then unhide in view ..... etc 

When you get to the file you can highlight it and right click chose make an archive.

It is the output from the archive that you should attach to a post.

---

### Post by DBStevens on 2007-07-30
Ok there are actually three albums on your file system:

```

mike@laptop:~/Music/Lil' Kim$ ls -Ro
.:
total 12
drwxr-xr-x 2 mike 4096 2007-06-30 23:07 Hard Core                   1
drwxr-xr-x 2 mike 4096 2007-05-05 23:46 La Bella Mafia              2
drwxr-xr-x 2 mike 4096 2007-05-05 20:39 The Naked Truth             3

```

---

### Post by mdvigi7536 on 2007-07-30
Try this...hope I did it right!

---

### Post by DBStevens on 2007-07-30
Now is it possible that there is a second artist folder named something like Lil Kim or lil' kim etc... etc ... which given the data on cddb wouldn't surprise me.  Remember like R not being the same as r when doing ls  so it is with everything.

---

### Post by DBStevens on 2007-07-30
I don't see the attachment.

---

### Post by mdvigi7536 on 2007-07-30
I reattached the file.  I created it by finding the collection_scan.files file, right-clicking on it, and clicking on Create Archive.

Yes there are three albums, not four like I had though.  My bad.  There is still one, "Hard Core" missing from Amarok.

I checked and there are no other folders in my Music folder with names similar to Lil' Kim.  Just that one folder.

I thought it wouldnt' matter even if there were because I told amarok my music was in the Music folder and all the ones under it [I think it was called "scan folders recursively"].

---

### Post by DBStevens on 2007-07-30
It shows now is that file basicly empty it shouldn't be normally.   It should have the information from your collection from the last scan.

---

### Post by mdvigi7536 on 2007-07-30
I noticed that the file size had changed from 100 bytes to like 3.3kb so I created another file.  If it doesn't work I can just have the scan start over.

---

### Post by DBStevens on 2007-07-30
Yes scan folders recursively would allow amarok to see all files in all directories below the current level starting with the first directory name provided.

What can happen is that some programs don't always react to certain characters in a sane manner.  So you have several places that can cause things to get dropped. The trail starts with the ripper and includes a number of players.

---

### Post by DBStevens on 2007-07-30
/var/run/system-tools-backends.pid
/var/run/dhcdbd.pid
/var/run/syslogd.pid
/var/run/motd

Don't think this is even close.

---

### Post by mdvigi7536 on 2007-07-30
> **DBStevens said:**
> /var/run/system-tools-backends.pid
/var/run/dhcdbd.pid
/var/run/syslogd.pid
/var/run/motd

Don't think this is even close.


I don't know what this means.  Are these commands you want to run in the terminal?  Do you want me to scan my computer again?

---

### Post by cookies on 2007-07-30
I had this happen too, had NO idea what caused it. I just moved the songs into the main Music folder and deleted all the subfolders, it was fixed....

---

### Post by DBStevens on 2007-07-30
I'm going to turn off this system I'd recommend that you have amorok rebuild your collection.

I've been running that player for some time and have only had issues when cddb provided duplicate information for different albums and the normal I have x albums by y only to find out the speeling was done by someone like me who doesn't always hit the keys let alone the right keys in the proper order ;-).   Special characters in file names however can lead to strange things.

---

### Post by DBStevens on 2007-07-30
mike that was what was in the collection_scan file you archived.

No don't run any of that.

---

### Post by mdvigi7536 on 2007-07-30
I will try dragging all the files out of their folders.

Thank you, both of you, for your help.

I'm sure I'll be on here again when I screw something up again!

Thanks so much.  --Mike

---

### Post by DBStevens on 2007-07-30
Mike,

You might want to keep a copy of the original Music directory as it is.

Like I said I'd have Amorok rebuild its collection.

If anything interrupted a prior build or the albums got added after a build then you could be missing things in chunks.

---

