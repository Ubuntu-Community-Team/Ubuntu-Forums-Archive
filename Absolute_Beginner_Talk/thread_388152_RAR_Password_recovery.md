---
title: "RAR Password recovery"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by milad on 2007-03-19
I've forgotten the password of one my rar files. So, does anybody know a rar password recovery tool for linux? Or for windows? cause i'm quite sure i can run them using wine.

---

### Post by justleen on 2007-03-19
might wanna try this [http://www.google.be/search?hl=nl&q=linux+rar+password+recovery&meta=](http://www.google.be/search?hl=nl&q=linux+rar+password+recovery&meta=)

---

### Post by xyz on 2007-03-19
Seems to have lots of them for Win; having a hard time finding one for Linux.
Good luck.

---

### Post by justleen on 2007-03-19
> **xyz said:**
> Seems to have lots of them for Win; having a hard time finding one for Linux.
Good luck.

dont think thats too weird, since rar is not really a *nix format..

---

### Post by xyz on 2007-03-19
Some more info here: [RAR ]("http://en.wikipedia.org/wiki/RAR#Archiver_features")
but:
> It features strong encryption capabilities. Older versions of the file format used a proprietary algorithm; newer versions use the AES encryption algorithm, which is considered very strong by today's standards. The only known ways to recover an encrypted file are via dictionary or brute force attacks, which are usually infeasible with non-dictionary passphrases starting from 8 characters.

> dont think thats too weird, since rar is not really a *nix format..
you're right! it's really not weird.

---

### Post by nudnik on 2007-03-19
> **milad said:**
> I've forgotten the password of one my rar files. So, does anybody know a rar password recovery tool for linux? Or for windows? cause i'm quite sure i can run them using wine.

Unless you have some clue what your password was, even if it is far from an exact idea, you will be running that program for the next year. The odds of actually cracking the password are against you to say the least, unless its a relatively small, common term. Maybe. If its a movie file courtesy of bittorrent with a password like ee80394kk3mom99, we will pray for you.

---

### Post by meborc on 2007-03-19
> **nudnik said:**
> ...If its a movie file courtesy of bittorrent with a password like ee80394kk3mom99, we will pray for you...
lol... yeah... i once tried to open a crypted rar file... it took my laptop 2 hours just to get to 5 letter passwords... and that was only small letters... no capital letters and no numbers/symbols :D

---

### Post by milad on 2007-03-19
Well, I tried one of the programs for windows using Wine and it worked great. found my password in few minutes.

---

### Post by xyz on 2007-03-20
Great! Could you please edit your first post and mark it (Resolved).
I think that would be nice to make it easier for people to know that it's possible even if it's only via Wine. Thnx.

---

### Post by Dod_basim on 2007-08-22
could you please name one program (don't care if via wine or not) that works in ubuntu? thanks

---

### Post by Drake2k on 2008-03-11
That's great that you got it working, but how about telling the rest of us which one you used?

---

### Post by Blario on 2008-04-06
Woww... what a jerk.  Dude completely abandoned the topic.... no help whatsoever

---

### Post by Paulo Wageck on 2008-04-08
i need this software too..

any clues?

---

### Post by diplomat.x on 2008-04-08
Even i am in queue.

---

### Post by ekravche on 2008-04-25
You can try [http://rarcrack.sourceforge.net/](http://rarcrack.sourceforge.net/)

It requires compilation though. It's not that hard to compile...

---

### Post by VMOS on 2008-06-24
you know what I ******* hate? When you search for something on google and all you find are forum pages where somebody else is looking for the same thing and the answer is some dick saying "just search google for it"

apologies for the foul language, I've been watching a lot of george carlin today, but my point still stands

---

### Post by ma2k1 on 2008-07-07
Rarcrak works good!
[http://www.ubuntu-unleashed.com/2008/04/howto-crack-rar-7z-and-zip-files-with.html](http://www.ubuntu-unleashed.com/2008/04/howto-crack-rar-7z-and-zip-files-with.html)

;)

---

### Post by webofunni on 2008-07-07
Hi,

  Thanks for introducing a new tool. I will try RarCrack :-)

---

### Post by rickycodie on 2008-07-22
So here's a quick tutorial on how to use rarcrack.

first get the file

```
wget http://superb-east.dl.sourceforge.net/sourceforge/rarcrack/rarcrack-0.2.tar.bz2
```

then extract it

```
tar xvjf rarcrack-0.2.tar.bz2

```

go to the location

```
cd rarcrack-0.2
```

install dependencies

```
sudo apt-get install libxml2-dev
```

then make and install

```
make ; sudo make install
```

next crack the file

```
rarcrack filename.rar
```

my suggestion is to rename the file if it has spaces in the name because it doesn't work well with those.

other than that, happy recovery!!

---

