---
title: "[SOLVED] help with download"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by dylondadank on 2007-11-12
would it be possible to get step by step instructions to downloading tile racer 0.6?
this is the link [http://tileracer.model-view.com/tl/index.php/downloads.html](http://tileracer.model-view.com/tl/index.php/downloads.html)

ive tried just downloading it, and i get an error

---

### Post by chamberlain2006 on 2007-11-12
I was in the middle of typing your answer when I saw that.  Very sorry for your confusion!  I'm just finishing up an explanation for you.  Just give me a few moments.  Thanks!

---

### Post by chamberlain2006 on 2007-11-12
Is the error you're getting like this: TileRacer: pcm_params.c:2351: sndrv_pcm_hw_params: Assertion `err >= 0' failed.
Aborted (core dumped)

---

### Post by dylondadank on 2007-11-12
> **chamberlain2006 said:**
> Is the error you're getting like this: TileRacer: pcm_params.c:2351: sndrv_pcm_hw_params: Assertion `err >= 0' failed.
Aborted (core dumped)

alright, hold on, i have to re-download it.
i dont know what happened. hold on a bit

---

### Post by dylondadank on 2007-11-12
> **dylondadank said:**
> alright, hold on, i have to re-download it.
i dont know what happened. hold on a bit

alright, i just re-downloaded it, and nothing is even happening this time, its in the firefox download box, and it wont open, and im not going to remove it.

---

### Post by dylondadank on 2007-11-12
> **dylondadank said:**
> alright, hold on, i have to re-download it.
i dont know what happened. hold on a bit

is there some terminal command that will just make it so i can have the game, cuz nothing has worked for me

---

### Post by chamberlain2006 on 2007-11-12
Ok.  It is probably downloaded.  Can you open up a terminal (Applications>Accessories>Terminal) and type in the following:

```

cd Desktop
tar xvzf TileRacer0.6.tar.gz
cd TileRacer
./TileRacer.sh

```

---

### Post by dylondadank on 2007-11-12
> **chamberlain2006 said:**
> Ok.  It is probably downloaded.  Can you open up a terminal (Applications>Accessories>Terminal) and type in the following:

```

cd Desktop
tar xvzf TileRacer0.6.tar.gz
cd TileRacer
./TileRacer.sh

```

nope didnt work

dylan@chaos:~$ cd Desktop
dylan@chaos:~/Desktop$ tar xvzf TileRacer0.6.tar.gz
tar: TileRacer0.6.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
dylan@chaos:~/Desktop$ cd TileRacer
bash: cd: TileRacer: No such file or directory
dylan@chaos:~/Desktop$ ./TileRacer.sh
bash: ./TileRacer.sh: No such file or directory

---

### Post by dylondadank on 2007-11-12
> **chamberlain2006 said:**
> Ok.  It is probably downloaded.  Can you open up a terminal (Applications>Accessories>Terminal) and type in the following:

```

cd Desktop
tar xvzf TileRacer0.6.tar.gz
cd TileRacer
./TileRacer.sh

```

i got the file open though, there is like 18 files in it i can choose from

---

### Post by chamberlain2006 on 2007-11-12
Those errors just say that the file isn't where I thought it would be... did it download to your desktop?  Did you click "Save to disk" or "Open With"?

---

### Post by Maestro23 on 2007-11-12
> **dylondadank said:**
> nope didnt work

dylan@chaos:~$ cd Desktop
dylan@chaos:~/Desktop$ tar xvzf TileRacer0.6.tar.gz
tar: TileRacer0.6.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
dylan@chaos:~/Desktop$ cd TileRacer
bash: cd: TileRacer: No such file or directory
dylan@chaos:~/Desktop$ ./TileRacer.sh
bash: ./TileRacer.sh: No such file or directory

Did you download the .tar file or the installer from the download page?

---

### Post by chamberlain2006 on 2007-11-12
Ok, scratch that... you probably just clicked open with... can you click extract to, and select your home directory, and then open up a terminal, and type:

cd TileRacer
./TileRacer

---

### Post by dylondadank on 2007-11-12
> **chamberlain2006 said:**
> Those errors just say that the file isn't where I thought it would be... did it download to your desktop?  Did you click "Save to disk" or "Open With"?

i clicked open with

---

### Post by dylondadank on 2007-11-12
> **chamberlain2006 said:**
> Ok, scratch that... you probably just clicked open with... can you click extract to, and select your home directory, and then open up a terminal, and type:

cd TileRacer
./TileRacer

dylan@chaos:~$ cd TileRacer
dylan@chaos:~/TileRacer$

thats what happens

---

### Post by Maestro23 on 2007-11-12
> **dylondadank said:**
> dylan@chaos:~$ cd TileRacer
dylan@chaos:~/TileRacer$

thats what happens

In the folder, is there a README/INSTALL document?

---

### Post by chamberlain2006 on 2007-11-12
Yupp.  Now type the second part, "./TileRacer" (without quotes)

---

### Post by dylondadank on 2007-11-12
> **Maestro23 said:**
> In the folder, is there a README/INSTALL document?

nope, no readme or install, or anything

---

### Post by dylondadank on 2007-11-12
> **chamberlain2006 said:**
> Yupp.  Now type the second part, "./TileRacer" (without quotes)

dylan@chaos:~$ cd TileRacer
dylan@chaos:~/TileRacer$ ./TileRacer
bash: ./TileRacer: No such file or directory
dylan@chaos:~/TileRacer$ 


nothing

---

### Post by chamberlain2006 on 2007-11-12
Sorry about that, that should be "./TileRacer.sh" (without quotes)

---

### Post by dylondadank on 2007-11-12
> **chamberlain2006 said:**
> Sorry about that, that should be "./TileRacer.sh" (without quotes)

it did a bunch of stuff that looked like it probably should have, but now what?
how do i play it?

---

### Post by chlorinekid on 2007-11-12
go to the download page and click the installer instead of the .tar file. the installer is the *.sh file. save it to the desktop. don't open it.

once it's sitting on your desktop, open a terminal and navigate to your desktop directory:

```
cd Desktop
```

then run the file:

```
sudo bash TileRacer0.6_Setup.sh
```

the installer will start :)

---

### Post by chlorinekid on 2007-11-12
> **dylondadank said:**
> it did a bunch of stuff that looked like it probably should have, but now what?
how do i play it?

try looking in applications > games. it might have created a shortcut.

---

### Post by chamberlain2006 on 2007-11-12
Does anything appear on the screen?

---

### Post by chamberlain2006 on 2007-11-12
Its marked as SOLVED, did it work?

---

### Post by dylondadank on 2007-11-12
> **chlorinekid said:**
> go to the download page and click the installer instead of the .tar file. the installer is the *.sh file. save it to the desktop. don't open it.

once it's sitting on your desktop, open a terminal and navigate to your desktop directory:

```
cd Desktop
```

then run the file:

```
sudo bash TileRacer0.6_Setup.sh
```

the installer will start :)

alright, so it took me forever to get the game, and it lags like ****, its so gay

---

### Post by chlorinekid on 2007-11-12
to be honest it wouldn't even start on my machine, but i figured it was because i'm using the laptop so i ain't the best for gaming :/

---

### Post by chamberlain2006 on 2007-11-14
I got it to run, but my desktop will run pretty much anything, but I'll tell you, you really weren't missing out on much.

---

