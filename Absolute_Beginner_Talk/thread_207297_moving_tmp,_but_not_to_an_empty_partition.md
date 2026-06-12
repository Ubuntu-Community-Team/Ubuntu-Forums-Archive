---
title: "moving /tmp, but not to an empty partition"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by gaggle on 2006-07-01
Hello all,


I'm rather new to this Linux business, but after several weeks of setting my box up *just so* I'm almost there. Got a nice server going with LAMP and a lightweight window manager and everything. Hooray. So by now I'm down to the last couple of things that needs solving, but they're also the things that are causing me most grief #-o.


My question today has to do with how one moves various systemfolders around, I'll specifically focus on the /tmp folder for now. I have 70 MiB left on my systemdrive, which is a bit.. uncomfortable, as you may imagine.


I basically just want /tmp to be physically placed somewhere other than the system drive (hda1). If this was Windows I'd go change the path that designates "temp = /path", but how one accomplishes this with Ubuntu is beyond my abilities. I'm not the first guy to ask this, but all the search results I can find is aimed at people who want to mount /tmp to a completly seperate partition, which is a bit more drastic than what I'm looking for.

Is there a way to have /tmp be physically placed on my already existing and active hda2 disk? (hda2 is mounted to "/mnt/data" for what it's worth). I've tried the command: 
```
mount /mnt/data/tmp /tmp
```
but it fails and says it requires a filesystem defined and whatnot, so I'm probably doing it wrong.


Can anyone help? I think my way of thinking here may be marred by my Windows brainwashing since it's very straightforward and simple there. It might be simple with Ubuntu too, but I just can't get my brain around it on my own :\.


Thanks in advance,
Jon

---

### Post by scxtt on 2006-07-01
you've got it backwards ...

[indent]mount /tmp /mnt/data/tmp[/indent]tho i'm not sure you can do that if /tmp is already part of your / partition -- never tried, could work fine ...

---

### Post by gaggle on 2006-07-01
[QUOTE=scxtt]you've got it backwards ...[/QUOTE]

Ooops :-\", heh shows how fragile my knowledge is.

The same error occurs though, it spits out "*you must specify the filesystem type*". If I include "*-t reiserfs* it gives "*/tmp is not a block device*". Feels like I'm barking up the wrong tree.. 

(though I believe this technique worked for me earlier when I linked "*/mnt/data/files*" to "*/mnt/data2/ftpRoot/files*". But those aren't system folders I guess)


Thanks for the quick reply though, I am much impressed :)

---

### Post by Joeak on 2006-07-01
I would think you can only mount /tmp either as a separate partition, or as part of the root "/" partition.  (If /tmp is part of root, /tmp wouldn't be mounted separately.)

---

### Post by gaggle on 2006-07-11
Joeak, if that's the case then I should boot from the cd and run partitioner right? Change things around in there, dedicate a whole partition to temp?
I'm running out of diskspace on / after a week or so worth of uptime, because the temp folder gets filled with crud. If I have to repartition I guess I'll just have to do that, but geez this seems like a horrible crutch.

Again, in Windows I'd just change the variable defining the path of the temp folder, it's a 10 second tweak. Here I wanted the temp files to go to /mnt/data/temp, and I'm certainly surprised there's no easier fix than dedicating *n* gigabytes to a temp partition that for the most part probably won't hold much data.


I won't have time to work on my machine for a week or so until work dies down a bit, so anyone out there has alternate suggestions I'd love to hear about them. If only a mighty guru would sweep down from the heavens and explain the path to take :).

---

### Post by scxtt on 2006-07-11
what do you have in /tmp that's filling it up like that? -- and you should be able to delete anything/everything in /tmp, that's the whole idea behind it being a 'temporary' folder ...

and i'm also thinking you should be able to 'delete' your current /tmp and then re-create it as a symbolic link to somewhere else ...

---

### Post by aysiu on 2006-07-11
I'm scxtt on this one. What's so precious in your /tmp folder that can't be deleted?

In any case, if you want it to appear in /mnt/data/tmp, instead of doing ```
mount /mnt/data/tmp /tmp
``` Do this: ```
sudo cp -R /tmp /mnt/data/tmp
sudo rm -rf /tmp
ln -s /mnt/data/tmp /tmp
```

---

### Post by gaggle on 2006-07-11
Hang on, aysiu's suggestion seems to work. How marvelous!, thank you very much sir.

---

### Post by aysiu on 2006-07-11
It was scxtt's idea. I just expanded on the implementation of it.

---

### Post by scxtt on 2006-07-11
nice work aysiu - and thanks for the credit, you are a gentleman and a scholar :D

and congrats gaggle ... :)

---

### Post by gaggle on 2006-07-12
Well, thank you both then :).


Epilogue: Should someone in the future come across this thread in their search for answers then I just want to mention that this solution breaks MySQL, it throws out "cannot find /tmp" errors. A simple update to the my.cnf file is all that's needed so it's no biggie, just keep in mind to check your programs to make sure they still work.

---

