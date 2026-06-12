---
title: "Question about .rar , VLC, totem-xine"
date: 2005-05-15
forum: Absolute Beginner Talk
---

### Post by NoTiG on 2005-05-15
Hey i have a question. I recently DLed an xvid video file from torrent....

In the directory the files are listed like this :


alli-lit.2003.xvid.r00
alli-lit.2003.xvid.r01
alli-lit.2003.xvid.r02
alli-lit.2003.xvid.r03
alli-lit.2003.xvid.r04
alli-lit.2003.xvid.r05
alli-lit.2003.xvid.r06
alli-lit.2003.xvid.r07
alli-lit.2003.xvid.r08
alli-lit.2003.xvid.r09
alli-lit.2003.xvid.r10
alli-lit.2003.xvid.r11
alli-lit.2003.xvid.r12
alli-lit.2003.xvid.r13
alli-lit.2003.xvid.r14
alli-lit.2003.xvid.r15
alli-lit.2003.xvid.r16
alli-lit.2003.xvid.r17
alli-lit.2003.xvid.r18
alli-lit.2003.xvid.r19
alli-lit.2003.xvid.r20
alli-lit.2003.xvid.r21
alli-lit.2003.xvid.r22
alli-lit.2003.xvid.r23
alli-lit.2003.xvid.r24
alli-lit.2003.xvid.r25
alli-lit.2003.xvid.r26
alli-lit.2003.xvid.r27
alli-lit.2003.xvid.r28
alli-lit.2003.xvid.r29
alli-lit.2003.xvid.r30
alli-lit.2003.xvid.r31
alli-lit.2003.xvid.r32
alli-lit.2003.xvid.r33
alli-lit.2003.xvid.r34
alli-lit.2003.xvid.r35
alli-lit.2003.xvid.rar
alli-lit.2003.xvid.sfv

When i tried to play them with totem-xine... it says it doesnt have the plugin. What plug in does it need to play xvid?????

I dl'ed VLC.. another movie player. the only file itwould play in this directory was the .rar one... but it is only a piece of the movie. 

So i thought the next step was to make them all one big file right? 

i used the rar command:

rar -a Movie

and it made a movie.rar file... but when i try to play this file with VLC... it doesnt show video or audio .. or anything. and instead of it lasting the length of the movie it only lasts like 30 seconds... just wondering what i did wrong. Oh and also...

when i tried to unrar Movie.rar ..... it tries but they all "fail" .

---

### Post by dave9191 on 2005-05-15
Before you can play the movie, you need to join all the .rxx files into one archieve and then unrar it. Once its uncompressed you can play the xvid file in your player or choice. 

rar -a adds files to an aricheve, it does not reassemble an archieve thats been split up. Try to unrar either the first .rxx or if the .rar file at the end came with the download, unrar that one and it should reassemble the files for you. 

I cant be too much help as I dont use rar much tho. 

Dave

---

### Post by TravisNewman on 2005-05-15
you need to extract it. using the original files, use

unrar e alli-lit.2003.xvid.rar

to extract it. If you don't have the original files, the same command SHOULD work on the one big one you created. If not, it could be that your download was corrupted.

You don't need to create one big rar file out of all of those, just so you know. the info is in the .rar archive and it will automatically pull from the rest.

---

### Post by NoTiG on 2005-05-16
```
 sudo unrar -x ocean.rar

unrar 0.0.1           Copyright (c) 2004 Ben Asselstine


Extracting from /home/notig/Oceans.Twelve.DVDRiP.XviD-BRUTUS/CD1/ocean.rar

Extracting  b-oc12a.r00                                               Failed
Extracting  b-oc12a.r01                                               Failed
Extracting  b-oc12a.r02                                               Failed
Extracting  b-oc12a.r03                                               Failed
Extracting  b-oc12a.r04                                               Failed
Extracting  b-oc12a.r05                                               Failed
Extracting  b-oc12a.r06                                               Failed
Extracting  b-oc12a.r07                                               Failed
Extracting  b-oc12a.r08                                               Failed
Extracting  b-oc12a.r09                                               Failed
Extracting  b-oc12a.r10                                               Failed
Extracting  b-oc12a.r11                                               Failed
Extracting  b-oc12a.r12                                               Failed
Extracting  b-oc12a.r13                                               Failed
Extracting  b-oc12a.r14                                               Failed
Extracting  b-oc12a.r15                                               Failed
Extracting  b-oc12a.r16                                               Failed
Extracting  b-oc12a.r17                                               Failed
Extracting  b-oc12a.r18                                               Failed
Extracting  b-oc12a.r19                                               Failed
Extracting  b-oc12a.r20                                               Failed
Extracting  b-oc12a.r21                                               Failed
Extracting  b-oc12a.r22                                               Failed
Extracting  b-oc12a.r23                                               Failed
Extracting  b-oc12a.r24                                               Failed
Extracting  b-oc12a.r25                                               Failed
Extracting  b-oc12a.r26                                               Failed
Extracting  b-oc12a.r27                                               Failed
Extracting  b-oc12a.r28                                               Failed
Extracting  b-oc12a.r29                                               Failed
Extracting  b-oc12a.r30                                               Failed
Extracting  b-oc12a.r31                                               Failed
Extracting  b-oc12a.r32                                               Failed
Extracting  b-oc12a.r33                                               Failed
Extracting  b-oc12a.r34                                               Failed
Extracting  b-oc12a.r35                                               Failed
Extracting  b-oc12a.r36                                               Failed
Extracting  b-oc12a.r37                                               Failed
Extracting  b-oc12a.r38                                               Failed
Extracting  b-oc12a.r39                                               Failed
Extracting  b-oc12a.r40                                               Failed
Extracting  b-oc12a.r41                                               Failed
Extracting  b-oc12a.r42                                               Failed
Extracting  b-oc12a.r43                                               Failed
Extracting  b-oc12a.r44                                               Failed
Extracting  b-oc12a.r45                                               Failed
Extracting  b-oc12a.r46                                               Failed
Extracting  b-oc12a.r47                                               Failed
Extracting  b-oc12a.r48                                               Failed
Extracting  b-oc12a.rar                                               Failed
Extracting  b-oc12a.sfv                                               Failed
51 Failed
``` 

ISo does that mean the DL was corrupted ?

---

### Post by Poul on 2005-05-17
I suppose that you downloaded that movie through torrent of ftp.
They usually use rar above 3.40 which isn't included in file roller (default ubuntu packager), which is more annoying it's not supported by free version of rar either.

You need to get rar and unrar-_nonfree _through synaptic. I assume you know how tto do it. I think that multiverse repository must be enabled. 
Program runs in console.
Change to the directory fith all rar files and type:
unrar -e alli-lit.2003.xvid.rar 
I picked the name from list in your post. Change if needed. Always extract file with .rar extension - it will use all the rest automaticaly.

It should extract the file alli-lit.2003.xvid.avi
 
Now you can run it with player of your choice (assuming that you have nessesary codecs installed.

---

### Post by NoTiG on 2005-05-17
thanks for the help. its good to know but i have since Deleted it. YEa I used torrent :P was just testing >:P i think DL'ing movies sucks anyways... it took forever to DL and used up alot of Bandwith . i would rather dl books (you can dl a whole library in minutes) :P

but anyways.. how is it possible that VLC played a .rar file without first extracting it i wonder?

---

### Post by betrayed on 2005-05-23
vlc played it because it has the ability to extract that bit of the rar file.  It didn't play the whole movie but the 15 or so mbs that was in that rar.  The best option of course is to get unrar not free or what ever it is called and extract the files

---

### Post by vinchi007 on 2007-03-09
> **Poul said:**
> I suppose that you downloaded that movie through torrent of ftp.
They usually use rar above 3.40 which isn't included in file roller (default ubuntu packager), which is more annoying it's not supported by free version of rar either.

You need to get rar and unrar-_nonfree _through synaptic. I assume you know how tto do it. I think that multiverse repository must be enabled. 
Program runs in console.
Change to the directory fith all rar files and type:
unrar -e alli-lit.2003.xvid.rar 
I picked the name from list in your post. Change if needed. Always extract file with .rar extension - it will use all the rest automaticaly.

It should extract the file alli-lit.2003.xvid.avi
 
Now you can run it with player of your choice (assuming that you have nessesary codecs installed.


Thank you for mentioning MULTIverse repo !!! (People always mentioned universe for these)
Works great! Thanks again :D

---

