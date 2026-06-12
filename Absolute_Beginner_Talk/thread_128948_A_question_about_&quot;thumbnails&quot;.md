---
title: "A question about &quot;thumbnails&quot;"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by qwazert on 2006-02-12
In my HOME directory is a folder named .THUMBNAILS. There are about 50 files in there that don't seem to serve much purpose. They are thumbnails of pictures that I have viewed some time ago.

Are they safe to delete, or will the full-sized pics associated with them disappear as well?

---

### Post by matthew on 2006-02-12
They are perfectly safe to delete. Your original full-sized files will remain.

---

### Post by qwazert on 2006-02-12
Thank you!

---

### Post by TitusDalwards on 2006-03-31
but i delete them manually but when i reboot my computer all pictures and screenshots appear again.do i have to delete them by using console?
can you say the command for this.

---

### Post by Mustard on 2006-03-31
I just went into these directories and tried it out.

I cd'ed into each of the three seperate directories and tried this, but it gave me an error 'argument too long'..

```

cd. /home/mustard/.thumbnails/normal/
#change working directory

rm *.png

#remove all files that end in .png extension
#this failed because there were so many

```

So I ended up doing this...
```

cd. /home/mustard/.thumbnails/normal/
#change directory to the relevant directory

#then I picked the first letter or number of a file

rm a*.png

#this removed all files that start with the letter 'a' and end in .png
#then I repeated this for the rest of the files

rm b*.png
rm c*.png
rm d*.png

#eventually I got rid of enough that I no longer
#got the 'argument too long' error when I tried the
#command below

rm *.png

#this deleted the remaining files.
#then I went to the other directory

cd /home/mustard/.thumbnails/large/

#repeat the above process with rm commands
#then cd to the last directory

cd /home/mustard/.thumbnails/fail/gnome-thumbnail-factory/

#repeat above process with rm commands

```

Now what I probably could have done is this (but I don't like using the Recursive option with the rm command.  I like to limit the damage if I make a mistake).

```
cd /home/mustard/.thumbnails/
#change directory to .thumbnails

rm -R *.png

#remove all files that end in .png recursively
#recursive basically means that it removes
#the files from the current directory and all
#directories underneath the current one

#You will still need to delete them a bit at a time
#because with so many files its going to give the 
#'argument too long' error until you get rid of a large
#chunk of the files first.

```

Now someone with some good scripting knowledge could probably do this much easier, but this worked for me. :)

---

### Post by bored2k on 2006-03-31
Why would you remove your cached thumbnail images? By doing so, the computer has to work on thumbailing it _Every_ time you use them, instead of going to that folder and showing the already small image.

---

### Post by TitusDalwards on 2006-03-31
@mustard: thanks lot,
@bored2k: i have alittle bit free space on my disk and i have to clean every unwanted things so i have to delete these images.

---

### Post by Mustard on 2006-03-31
[QUOTE=bored2k]Why would you remove your cached thumbnail images? By doing so, the computer has to work on thumbailing it _Every_ time you use them, instead of going to that folder and showing the already small image.[/QUOTE]

It caches every image which may include pictures of a personal and private nature. I can think of many reasons why people would not want the cached images sitting on their hard drives. :D

---

