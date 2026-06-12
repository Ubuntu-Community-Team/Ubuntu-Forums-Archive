---
title: "external harddrive folder permissions"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by lunaz on 2007-08-29
well, i see pages of threads about this but no real answer:

my external hd has 3 folders on it: music, oldpos_bak, badassness_bak

i want both me & my roommate to access music but only me to access the other 2.

i tried to make a new group called music, and i added both of us to it, then right clicked on usbdisk, went to permissions, and changed folder group to music, owner is luna (me) and set owner & grp permissions to rwx. here's what i see

```

luna@oldpos:/media/usbdisk$ ls -la
total 20
drwxr-xr-x  5 root root  4096 2007-08-29 19:44 .
drwxr-xr-x  6 root root  4096 2007-08-29 18:57 ..
drwxr-xr-x 11 root root  4096 2007-06-18 18:43 badassness_bak
drwxrwx--- 47 luna music 4096 2007-05-30 23:34 music
drwxr-xr-x  2 root root  4096 2007-08-29 18:50 oldpos_bak
luna@oldpos:/media/usbdisk$

```

i went to the usbdisk as my roommate's acct, and she could get to the some folders in /music but not others!

what did i do wrong?

---

### Post by finer recliner on 2007-08-29
run the same commands you did before, but add a recursive flag to them (usually -r or -R)

example:
```

chmod -R 777 folder_name

```

by adding the recursive flag to the command, you are effectively saying, "apply these permissions to the following folder *and any subfolders and files that reside in it*"

---

### Post by lunaz on 2007-08-29
well, i did try that, only i did 770, us rwx, everyone else, nothing.
i logged her off & back on again, but still she's having issues. :(
we're both in group music.

```

luna@oldpos:/media/usbdisk$ sudo chmod -R 770 music
Password:
luna@oldpos:/media/usbdisk$ ls -la
total 20
drwxr-xr-x  5 root root  4096 2007-08-29 19:44 .
drwxr-xr-x  6 root root  4096 2007-08-29 18:57 ..
drwxr-xr-x 11 root root  4096 2007-06-18 18:43 badassness_bak
drwxrwx--- 47 luna music 4096 2007-05-30 23:34 music
drwxr-xr-x  2 root root  4096 2007-08-29 18:50 oldpos_bak
luna@oldpos:/media/usbdisk$ groups bachmanswarbler
bachmanswarbler : users cdrom floppy audio plugdev music
luna@oldpos:/media/usbdisk$

```

---

### Post by Techno.Scavenger on 2007-08-29
Can you try:

cd /media/usbdisk/music
ls -la

And post the output?

Regards,
TechnoS

---

### Post by lunaz on 2007-08-29
```

luna@oldpos:/media/usbdisk/music$ ls -la
total 188
drwxrwx--- 47 luna music 4096 2007-05-30 23:34 .
drwxr-xr-x  5 root root  4096 2007-08-29 19:44 ..
drwxrwx---  2 luna luna  4096 2007-02-03 15:28 70oz of gold
drwxrwx---  2 luna luna  4096 2007-05-30 23:34 assorted
drwxrwx---  2 luna luna  4096 2007-02-03 15:30 Billboard Top Hits- 1979
drwxrwx---  2 luna luna  4096 2007-05-22 23:33 Bolero
drwxrwx---  2 luna luna  4096 2007-01-26 20:26 celine_dion_a_new_day
drwxrwx---  2 luna luna  4096 2007-05-22 23:11 Christmas Extraordinaire
drwxrwx---  3 luna luna  4096 2007-05-30 22:01 chrono_trigger
drwxrwx---  2 luna luna  4096 2007-05-29 18:55 Creedence Clearwater Revival
drwxrwx---  2 luna luna  4096 2007-05-29 20:41 Crosby, Stills, Nash & Young
drwxrwx---  6 luna luna  4096 2007-05-23 00:07 enya
drwxrwx---  3 luna luna  4096 2007-05-30 22:02 final_fantasy_6
drwxrwx---  2 luna luna  4096 2007-05-22 23:06 Girl, Interrupted Original Motion Picture Soundtrack
drwxrwx---  2 luna luna  4096 2007-02-03 15:18 Greatest Hits Rock 'N' Roll of the 60's
drwxrwx---  2 luna luna  4096 2007-02-03 15:18 GROOVIN GREATS VOL. THREE
drwxrwx---  2 luna luna  4096 2007-02-03 15:19 Hits of the 60's
drwxrwx---  2 luna luna  4096 2007-05-22 23:26 Humoreska - Humoresque
drwxrwx---  2 luna luna  4096 2007-05-29 23:15 If You Want Me To: The Best of Ginny Owens
drwxrwx---  2 luna luna  4096 2007-05-29 21:48 jeanette_crosswait
drwxrwx---  3 luna luna  4096 2007-02-03 15:19 Jim Croce
drwxrwx---  2 luna luna  4096 2007-05-29 20:42 josh_turner
drwxrwx---  3 luna luna  4096 2007-02-03 15:19 LeAnn Rimes
drwxrwx---  3 luna luna  4096 2007-05-30 22:02 legend_of_zelda_alttp
drwxrwx---  2 luna luna  4096 2007-01-26 20:24 legend_of_zelda_oot
drwxrwx---  3 luna luna  4096 2007-05-30 22:03 lufia_1
drwxrwx---  3 luna luna  4096 2007-05-30 22:03 lufia_2
drwxrwx---  2 luna luna  4096 2007-05-22 23:44 Music From Hungary
drwxrwx---  2 luna luna  4096 2007-05-29 19:24 Nature Quest
drwxrwx---  2 luna luna  4096 2007-01-26 20:23 norah_jones_feels_like_home
drwxrwx---  2 luna luna  4096 2007-05-30 23:34 phil_collins
drwxrwx---  4 luna luna  4096 2007-05-29 23:06 Point Of Grace
drwxrwx---  2 luna luna  4096 2007-05-29 20:42 Polovtsian Dances - Symphonies 2 & 3
drwxrwx---  2 luna luna  4096 2007-01-26 20:23 rascal_flatts
drwxrwx---  2 luna luna  4096 2007-02-03 15:21 Rockin' 70's, Vol. 2 [Universal]
drwxrwx---  2 luna luna  4096 2007-02-03 15:21 Rock N Roll Grovin' Greats Vol. 2 Disc 2
drwxrwx---  2 luna luna  4096 2007-02-03 15:22 Roy Orbison
drwxrwx---  3 luna luna  4096 2007-05-30 22:03 secret_of_mana
drwxrwx---  3 luna luna  4096 2007-05-30 22:03 seiken_densetsu_3
drwxrwx---  2 luna luna  4096 2007-02-03 15:22 Shrek
drwxrwx---  2 luna luna  4096 2007-02-03 15:27 soundsofthe80s_80-89
drwxrwx---  2 luna luna  4096 2007-01-26 20:21 spirit_of_the_dance
drwxrwx---  2 luna luna  4096 2007-05-22 23:28 Symphony No. 3
drwxrwx---  2 luna luna  4096 2007-02-03 15:27 The Ultimate History of Rock 'N' Roll Collection Disc 9
drwxrwx---  2 luna luna  4096 2007-05-29 19:29 tim_falk
drwxrwx---  2 luna luna  4096 2007-02-03 15:28 War
drwxrwx---  4 luna luna  4096 2007-05-29 23:07 WOWWorship
luna@oldpos:/media/usbdisk/music$

```

---

### Post by finer recliner on 2007-08-30
all of your subfolders and files are not part of group music. you have to recursively call group command as well.

---

