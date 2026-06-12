---
title: "Dvd"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by IrishGangsta on 2006-07-31
i am looking for easy step by step instructions on how to burn a movie that i downlaoded to a blank disc  and play it on my dvd player.

NOTE: The movie is not pirated.

---

### Post by OU812 on 2006-07-31
Assuming they are dvd files (.vob) - Maybe use dvdauthor to build the .ifo files, then maybe you can burn it. dvdauthor should be in the repo. The code to build the .ifo files should be 

```
dvdauthor -T -o /movies/movie1
```

john

---

### Post by IrishGangsta on 2006-07-31
well the files are not .vob i think
they are bit torrents
and are rar
others are .bin and .cue

any help with that?

---

### Post by OU812 on 2006-07-31
Sorry, no. My network admin won't let me use bittorrent. Maybe google?

I think [www.doom9.org](www.doom9.org) is pretty authoratative on the subject.

john

---

### Post by gils0040 on 2006-07-31
1. sudo apt-get install avidemux dvdauthor
2. open avidemux and open your video file
3. select auto -> dvd. make sure that the input and output aspect ratios are correct.
4. save video file to filename.mpeg
5. open terminal and cd to location of filename.mpeg
6. dvdauthor ./filename.mpeg -o dvdstruct
7. dvdauthor -T -o ./dvdstruct
8. mkisofs -dvd-video -o filename_dvd.iso ./dvdstruct
9. growisofs -dvd-compat -Z /dev/dvd=filename_dvd.iso

this is based off of endys guide [http://ubuntuforums.org/showthread.php?t=50063&highlight=plan9](http://ubuntuforums.org/showthread.php?t=50063&highlight=plan9).

---

### Post by gils0040 on 2006-07-31
rar files are compressed, similar to zip files. do sudo apt-get install unrar to be able to uncompress them (this can be done through fileroller). bin and cue files are cd or dvd images (meaning that there is already a file structure in place, this could be a vcd or dvd). the bin file is the actual cd image and the cue file contains the information about the image. this is nice because they are ready to burn, no conversion required. im not sure but you may just be able to right click on either of them and select write to disc. if not i would think that gnomebaker would be able to burn the image.

---

### Post by TLE on 2006-07-31
Hey IrishGangsta

I serached the forum for "burn cue bin" and found this thread: [Howto burn .cue .bin images]("http://www.ubuntuforums.org/showthread.php?t=209547&highlight=burn+cue+bin"), I think that's what you are looking for.

Regarding the .rar files, .rar files are archives just like .zip files so you need to unpack them first to see what's inside. I don't have time right now, but if no one else fils you on that, I'll get back to you.

Regards TLE

---

### Post by IrishGangsta on 2006-07-31
well these instructions look very detailed and i thank you guys for your time
I actually have rar and unrar installed and gnomebaker and a million other things, but i havn't really been informed on how to use them to make a dvd exactly.
i will try all of your guys suggestions.

thank you!

---

### Post by IrishGangsta on 2006-07-31
> **gils0040 said:**
> 1. sudo apt-get install avidemux dvdauthor
2. open avidemux and open your video file
3. select auto -> dvd. make sure that the input and output aspect ratios are correct.
4. save video file to filename.mpeg
5. cd to location of filename.mpeg
6. open terminal: dvdauthor ./filename.mpeg -o dvdstruct
7. dvdauthor -T -o ./dvdstruct
8. mkisofs -dvd-video -o filename_dvd.iso ./dvdstruct
9. growisofs -dvd-compat -Z /dev/dvd=filename_dvd.iso

this is based off of endys guide [http://ubuntuforums.org/showthread.php?t=50063&highlight=plan9](http://ubuntuforums.org/showthread.php?t=50063&highlight=plan9).



Right now the file is currently saving it is gonna take about an hour.
But in step 5 u said cd to location, does that mean in terminal cd to location? 
Then step 6 should i just leave the terminal open and type dvdauthor ./filename.mpeg -0 dvdstruct???

Basically, step 5 and 6 are confusing me
If you could please help me thanx

---

### Post by gils0040 on 2006-07-31
by cd i mean change directory to the location of the video file. then just leave the terminal open so that all commands are launched from that directory. good luck

* i edited my first post. you should be able to follow the directions exactly now.

---

### Post by IrishGangsta on 2006-07-31
Thank you for your help
I did just like you said and i accomplished burning a dvd in .avi format
It worked out great!!!

---

