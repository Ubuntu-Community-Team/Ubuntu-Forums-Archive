---
title: "Steem"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by j002 on 2006-12-11
I can't get any sound on the STEEM (Atari ST) emulator.

It says that if sound is "bad" (in fact, it is non-existent), you should try installing it in root.

You do install in root graphically (i.e. without "sudo") ?
It'd be a real hassle de-compacting from the CLI because its got all these tars and gzip things on it and you have to use exactly the right command.

---

### Post by troymcdavis on 2007-01-06
Yes, you do have to use exactly the right command, it's "tar". First change to whatever directory you downloaded it to with "cd" (this will be easiest if you download it to your home directory) and then extract them with "tar". It should look something like this:

```
snakes@plane:~$ cd ~
```

If you downloaded to the home directory, or 

```
snakes@plane:~$ cd ~/Dekstop
```

if you downloaded to your Desktop. Then, to unzip:

```
snakes@plane:~$ sudo tar -xf ARCHIVENAME.tar.gz
```

For [the version of STEem I downloaded from this website]("http://downloads.vnunet.com/download/games/steem+linux+3.1/_1934.html"), mine would look like this:

```
snakes@plane:~/Desktop$ sudo tar -xf xsteem_v3_2-i486.tar.gz 
```

Then it will ask for your password. This is really the only step in the "installation". Maybe they intend for you to run the actual program as root? In which case, they explain how to do that in the README:

> If you want to be able to run Steem by typing "steem"
into any terminal, we suggest you put a shell script
called "steem" in /usr/bin/ (or any standard path in
the PATH variable) containing something like:

#!/bin/bash

/(Steem's directory)/steem

Don't forget to make the script executable.

In this case, you would just do "sudo steem".

Don't fear the CLI. It is by far the easiest (though maybe not the simplest) way to get things done. Plus it is possibly the only consistent interface two users will share, thus making it much easier to give and receive help.

Feel free to ask any follow-ups; I'm glad to help. :D

---

