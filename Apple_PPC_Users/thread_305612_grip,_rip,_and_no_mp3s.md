---
title: "grip, rip, and no mp3s"
date: 2006-11-23
forum: Apple PPC Users
---

### Post by n.d.turnip on 2006-11-23
Hi,


I'm trying to rip mp3 from a CD with GRIP. My encoder is lame. My machine PPC B&W

The files appear to rip, as status in GRIP shows>

Ripping track 1 to /home/nick/mp3/parker_charlie/with_strings__the_master_takes/just_friends.mp3
Rip finished
1: Encoding to /home/nick/mp3/parker_charlie/with_strings__the_master_takes/just_friends.mp3

:confused: yet, each mp3 file is deleted as the next track starts to rip, thus>

nick@turnip:~/mp3/parker_charlie/with_strings__the_master_takes$ ls -l
total 14324
-rw-r--r-- 1 nick nick 14643596 2006-11-20 20:46 everything_happens_to_me.mp3
nick@turnip:~/mp3/parker_charlie/with_strings__the_master_takes$ ls -l
total 3552
-rw-r--r-- 1 nick nick 3629180 2006-11-20 20:47 april_in_paris_take_1.mp3

suggestions most welcome

best turnip

---

### Post by x64Jimbo on 2006-11-23
Have you checked your options in grip? There's an option to delete the files after they're done ripping (dunno why) and that might be turned on.

---

### Post by n.d.turnip on 2006-11-24
> **x64Jimbo said:**
> Have you checked your options in grip? There's an option to delete the files after they're done ripping (dunno why) and that might be turned on.

Yep, I've tried that. No joy I'm afraid.](*,)

---

### Post by x64Jimbo on 2006-11-24
Have you tried SoundJuicer? It's a very nice ripping program. I know it doesn't exactly solve the problem, but at least it lets you do what you wanted to do.

---

### Post by stmiller on 2006-11-24
Start grip from a command line and give the output here. What are your lame encoder settings?

---

### Post by n.d.turnip on 2006-11-25
> **stmiller said:**
> Start grip from a command line and give the output here. What are your lame encoder settings?

still keen to get grip to rip mp3s

starting grip from command line didn't work, sadly:rolleyes: 

Encoder settings are

Encoder command line -h -b %b %w %m
Encode file format mp3
Encode file extension~/mp3/%A/%d/%n.%x

---

### Post by stmiller on 2006-11-25
Okay I made screen shots of my grip settings. These work fine for me. 
Note: my lame executable is in an alternate place, from Lame 3.97 that I compiled. And I have very picky encoding settings I like to use as you can see. But look over these, and maybe this will help.

---

### Post by n.d.turnip on 2006-11-26
> **stmiller said:**
> Okay I made screen shots of my grip settings. These work fine for me. 
Note: my lame executable is in an alternate place, from Lame 3.97 that I compiled. And I have very picky encoding settings I like to use as you can see. But look over these, and maybe this will help.

Thanks stmiller, shifting the lame executable seems to have worked

---

### Post by Uta on 2006-12-30
> **stmiller said:**
> 
Note: my lame executable is in an alternate place, from Lame 3.97 that I compiled.

Where do you get "lame" for Edgy ppc?It doesn't seem to come pre-installed. Thanks!

---

