---
title: "Exaile's Random Shutdown Feature"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by KevNice on 2007-12-12
Sometimes Exaile will just freeze up, or just terminate randomly. Like suddenly the music stops and the window disappears. I ran it through terminal the next time to see whats happening, and this is the output:

```
sh: jackd: not found
updated plays 1, rating 1
next track was reported as  Rear Moth from Tiger, My Friend by Psapp
sh: jackd: not found
updated plays 1, rating 1
next track was reported as  Leaving In Coffins from Tiger, My Friend by Psapp
sh: jackd: not found
updated plays 1, rating 1
next track was reported as  Calm Down from Tiger, My Friend by Psapp
sh: jackd: not found
updated plays 1, rating 1
next track was reported as  Velvet Pony from Tiger, My Friend by Psapp
sh: jackd: not found
updated plays 1, rating 1
next track was reported as  About Fun from Tiger, My Friend by Psapp
sh: jackd: not found
updated plays 1, rating 1
next track was reported as  Curuncula from Tiger, My Friend by Psapp
sh: jackd: not found
updated plays 1, rating 1
next track was reported as  King Kong from Tiger, My Friend by Psapp
sh: jackd: not found
updated plays 1, rating 1
next track was reported as  The Counter from Tiger, My Friend by Psapp
sh: jackd: not found
Segmentation fault (core dumped)

```

absolutely no idea whats going on here. any advices??

kev

---

### Post by skrribble on 2007-12-12
here's one thing that i've done that has helped with exaile when it starts to act stupid:

go into your home folder and delete your /.exaile folder

this wont delete any system files or songs or anything like that, it will basically just delete settings and stuff that can be easily reconfigured... you'll have to tell it where your music files are again and re-do any preference changes from the default, but its usually not that bad.. again this has worked for me several times, so it may or may not work for you

---

### Post by tich on 2007-12-12
i had a similar problem for about a month but then it mysteriously disappeared.  i live in constant fear waiting for the day that it reappears.

my terminal output was identical.
i do know that it is not a problem with corrupted music files which was my first concern.
if you reopen and play the song that it crashes on it has no problems playing it the second time.

also i think it is nice that you called it a feature!

---

### Post by TWO on 2007-12-18
This has just happened to me today.

I've been trying several music players to find out which one I like the best.

On two occasions where I've right clicked on a song, then selected 'information' and then clicked one of the tabs such as 'tablature' or 'lyrics,' the program froze and then shut itself down. 

It hasn't happened since though and I'm trying to get it to do it again.

---

