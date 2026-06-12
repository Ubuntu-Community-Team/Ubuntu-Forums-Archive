---
title: "[SOLVED] Where did my music go?!"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by chris200x9 on 2008-01-20
Hi i'm on a mac so I mounted my mac hd nd put in these commands

 root@chris200x9-laptop:/media/Macintosh HD/Users/chris200x9/Music/itunes/iTunes Music# ls
7 Seconds                 In My Eyes                      Rise Against
Against Me!               Johnny Cash                     Scream
All                       Kid Dynamite                    Screeching Weasel
Angry Amputees            Lagwagon                        Skewbald
Armia                     Lifetime                        Slapshot
Bad Brains                Lustra                          Snow Patrol
Bad Religion              Match Box Twenty                Snuff
Bane                      Minor Threat                    Social Distortion
Barenaked Ladies          Modest Mouse                    Sum 41
blink-182                 Movies                          Teen Idles

root@chris200x9-laptop:/media/Macintosh HD/Users/chris200x9/Music/itunes/iTunes Music# cd
root@chris200x9-laptop:~# cp -R /media/Macintosh HD/Users/chris200x9/Music/itunes/iTunes Music# 
cp: target `Music#' is not a directory
root@chris200x9-laptop:~# /media/Macintosh HD/Users/chris200x9/Music/itunes/iTunes Music# 
bash: /media/Macintosh: No such file or directory
root@chris200x9-laptop:~# cp -R '/media/Macintosh HD/Users/chris200x9/Music/itunes/iTunes Music' ~/Music 
root@chris200x9-laptop:~# 

but no music in my music folder but my hardrive space shrunk?!


any ideas what happend?

---

### Post by Rocket2DMn on 2008-01-20
From the terminal, when you use a directory with a space in it, you need to use an escape character ("\") otherwise it thinks whatever comes after the space is the next argument for the program you're running (cp in this case)
```
cp -R /media/Macintosh\ HD/Users/chris200x9/Music/itunes/iTunes Music
```
That will copy everything fron the iTunes directory on the other disk to the Music folder in your current directory.
Note that you can autofill a directory path by pressing TAB after you start typing.  If there isn't a unique option, double press TAB and it will list your options.

---

### Post by stevescripts on 2008-01-20
> **chris200x9 said:**
> Hi i'm on a mac so I mounted my mac hd nd put in these commands

(...)

any ideas what happend?


duh ... any chance they might be located in a directory named Music, which
just might be located as a sub-directory of your home directory?

On Linux, the tilde character "~" is short for the current users home directory.

Hope this helps.

Steve

---

### Post by jleaker01z on 2008-01-20
Im not sure where your files are, but I can tell you what you did wrong.  Linux doesnt recognize the space.  You either have to enclose it in quotes ("text here") or put a backslash (\) after the first work (text\ here).

Try to enter "locate barenaked" and see if it might find them.  Other than that, I got nuthin.  :)

---

### Post by chris200x9 on 2008-01-20
> **Rocket2DMn said:**
> From the terminal, when you use a directory with a space in it, you need to use an escape character ("\") otherwise it thinks whatever comes after the space is the next argument for the program you're running (cp in this case)
```
cp -R /media/Macintosh\ HD/Users/chris200x9/Music/itunes/iTunes Music
```
That will copy everything fron the iTunes directory on the other disk to the Music folder in your current directory.
Note that you can autofill a directory path by pressing TAB after you start typing.  If there isn't a unique option, double press TAB and it will list your options.


if it thought the HD was the next argument why did it still copy them *somewhere* not  doubting you or anything I'm just curious

edit: Why didn't my single quotes work encapslating the directory work?

---

### Post by GavinZac on 2008-01-20
you're logged in as root at the terminal, so perhaps its in the root user's home/Music directory, rather than our normal user's Music directory?

---

### Post by Rocket2DMn on 2008-01-20
I think you can copy from multiple sources to a single directory, so having 3 arguments is ok.  The parsing algorithm in the cp program probably checked the destination location first (the last argument of the command) and when it saw it was wrong, it threw the error and exited the program.  That's just my 2 cents.
Is your problem fixed?  If so, then great, mark your thread as solved and get back to enjoying Ubuntu, otherwise we'll keep working on it!

PS: you shouldn't be in root if you don't need to be.

---

### Post by chris200x9 on 2008-01-20
nope it's not solved

---

### Post by GavinZac on 2008-01-20
> **chris200x9 said:**
> nope it's not solved

what happens if you look in /home/root/Music ?

---

### Post by chris200x9 on 2008-01-20
> **GavinZac said:**
> what happens if you look in /home/root/Music ?

there is no such directory

---

### Post by Rocket2DMn on 2008-01-20
root's home folder is at /root not /home/root
You should have a terminal logged in under your username so you will own the files when you move them to wherever you're putting them.  Please don't use root if it's not necessary, it's a great way to break things.
So if you are trying to copy that directory to a folder called Music in your home folder, the command should be
```
cp -R /media/Macintosh\ HD/Users/chris200x9/Music/itunes/iTunes\ Music ~/Music
```
Check your capitalizations and whatnot, linux is case sensitive.

---

### Post by chris200x9 on 2008-01-20
ah yes it's in /root/Music



thank you all!

---

### Post by jleaker01z on 2008-01-20
Is there an HD folder in your root directory ( / )?

It looks to me that with this command: root@chris200x9-laptop:~# cp -R /media/Macintosh HD/Users/chris200x9/Music/itunes/iTunes  

You told it to CoPy the contents of /media/Macintosh to HD/Users/chris200x9/Music/itunes

---

### Post by GavinZac on 2008-01-20
> **chris200x9 said:**
> ah yes it's in /root/Music



thank you all!

D'oh! I was so close :)

---

### Post by stevescripts on 2008-01-20
How about /root/Music ?

---

### Post by rosegarden78 on 2008-01-20
The author of this thread may consider giving us more information to work with, but 

1)  the cp -R is for recursive file copy only that's not the way to copy all files
2)  your need to put a \ before every space in a file name, when using the terminal (e.g.  cd /media/sda1/Documents\ and\ Settings/file.txt)

To copy all files I think you use the cp /your/Music/Folder/* -t /home/your/destination

As far as your missing music is concerned use a file search from your OS and check the portable device.  If both locations are devoid of music then it's possible you are the victim of permanent data loss.

---

