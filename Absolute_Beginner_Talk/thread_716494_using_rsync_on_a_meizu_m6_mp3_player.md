---
title: "using rsync on a meizu m6 mp3 player"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by mooglinux on 2008-03-06
i have a meizu m6 miniplayer, great mp3 player all around. i heard about the rsync command and it sounds perfect for keeping my music on my mp3 player up to date with my music folder on my home drive. so i enter this: ```
 rsync -rtv ./Music/ /media/disk/MUSIC

```

and then it goes and copies most (but not all) of my music onto my mp3 player, some of the songs i have not even listned to since the last time i use rsync. i know files that have been moved are copied into the new location but most of these files have not been moved...what gives? am i entering the wrong options?

---

### Post by julian67 on 2008-03-07
> **mooglinux said:**
> i have a meizu m6 miniplayer, great mp3 player all around. i heard about the rsync command and it sounds perfect for keeping my music on my mp3 player up to date with my music folder on my home drive. so i enter this: ```
 rsync -rtv ./Music/ /media/disk/MUSIC

```

and then it goes and copies most (but not all) of my music onto my mp3 player, some of the songs i have not even listned to since the last time i use rsync. i know files that have been moved are copied into the new location but most of these files have not been moved...what gives? am i entering the wrong options?

I assume you're opening the terminal and running the command from your home and that your Music folder is in your home. You don't need the ./

try ```
rsync -rtv Music/ /media/disk/MUSIC
```

or ```
rsync -avh Music/ /media/disk/MUSIC
```

either of those should copy all your songs to your portable.

---

### Post by mooglinux on 2008-03-07
sorry, should have clarified a little. the music is all there alreay, since i have copied it all with rsync several times. what i want to see happen is only the files that i added or changed being copied onto my player, so i donthave to wait for 2 gigs of files to copy anytimei  want to update my library. thats the whole point of rsync after all. im trying ```
rsync -rtv Music/ /media/disk/MUSIC
``` command and that sopied everything. perhaps when i run it a second time it wil do what i want

---

### Post by julian67 on 2008-03-07
> **mooglinux said:**
> sorry, should have clarified a little. the music is all there alreay, since i have copied it all with rsync several times. what i want to see happen is only the files that i added or changed being copied onto my player, so i donthave to wait for 2 gigs of files to copy anytimei  want to update my library. thats the whole point of rsync after all. im trying ```
rsync -rtv Music/ /media/disk/MUSIC
``` command and that sopied everything. perhaps when i run it a second time it wil do what i want

I doubt it copied everything. I think you're either misunderstanding the verbose output (-v), or the destination you selected is not what you think it is.  I use rsync to incrementally  back up over 50GB of data at a time and it absolutely does not copy everything, only the differences. Or maybe I have the world's fastest hard drives and motherboard and can copy 55GB in a minute or 2 (unlikely with an old PcChips board and multiple ATA drives).

---

### Post by mooglinux on 2008-03-07
```
rsync -rtv Music/ /media/disk/MUSIC
``` seems to work actually. running it a second time and it copied nothing. but once i unmount it and reconnect it, it copies everything over. o.O?

---

### Post by herbster on 2008-03-07
You're missing the --delete option.

```
rsync -rtv
```

^^^ Why do you need to preserve timestamps? No biggie but that's not necessary just to copy over music files.

This would keep a constant mirror between the device and your Music folder in your /home:

```
rsync -vz --delete Music/ /media/disk/MUSIC/
```

You may also want to add --progress which gives more info on the transfer, as well as -a which will compress the data as it transfers, again, not necessary but nonetheless:

```
rsync -avz --delete --progress Music/ /media/disk/MUSIC/
```

Pretty much what all rsync commands that I use to backup tons of stuff look like.

---

### Post by mooglinux on 2008-03-07
i understood timestamps to be neccessary for it to know what files have changed and what havent. as for your last command, i ran that but it puts out gazzillions of errors like this:> rsync: chgrp "/media/disk/MUSIC/LOTR/The Lord Of The Rings - The Fellowship O" failed: Operation not permitted (1)
 why does it need to change the permissions? 

oh, and just in case i tried running that with sudo, same errors

---

### Post by herbster on 2008-03-07
Take out -az. And I was mistaken, -a archives and -z compresses. Try it again, should work.

---

### Post by julian67 on 2008-03-08
> **herbster said:**
> Take out -az. And I was mistaken, -a archives and -z compresses. Try it again, should work.

-a does not archive the files in the sense of making an archive! It's an rsync option equivalent to the options rlptgoD (no -H,-A,-X) Option -z is to use compression when copying across a network. 

suggest most of these difficulties can be solved simply by reading man rsync which does include good examples. It sounds to me like you need to check ownership & permissions on your music player and the files it contains, also check your computers music folder.

---

### Post by herbster on 2008-03-08
I know that julian, and if compression is what is inferred from my post above then I should have been more clear :)

---

