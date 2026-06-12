---
title: "[SOLVED] installing games"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by k33bz on 2007-05-17
ok i found two games i want to install, i already downloaded them, and they are not .deb packages. I know I have seen it somewhere, but recently cant find it about installing applications that are not .rpm or deb. packages.

how would i go about installing these two games.
1.ufoai-2.1.1-linux_hotfix2.run
2. ufo2000-0.7.1071-sources.tar.bz2

---

### Post by smithman89 on 2007-05-17
This guide helped me through my first weeks of Ubuntu, it was a godsend for me:  [http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")
Hope this helps :D

---

### Post by k33bz on 2007-05-17
its a great guide, and i appreciate it, it will come in use in the future i know. but didnt see one for that .run file game

---

### Post by Pollywoggy on 2007-05-17
> **k33bz said:**
> ok i found two games i want to install, i already downloaded them, and they are not .deb packages. I know I have seen it somewhere, but recently cant find it about installing applications that are not .rpm or deb. packages.

how would i go about installing these two games.
1.ufoai-2.1.1-linux_hotfix2.run
2. ufo2000-0.7.1071-sources.tar.bz2

I am guessing that number one is a shell script.
Try 'less ufoai-2.1.1-linux_hotfix2.run' to be sure.
If you see '#!/bin/sh' or '#!/bin/bash' at the top of the file it is a BASH script
and you can run 'sh ufoai-2.1.1-linux_hotfix2.run' (you might have to be root, but try as ordinary user first).

For #2

put the file in a temporary (empty) directory and run 'tar jxvf ufo2000-0.7.1071-sources.tar.bz2'
There is probably a file called INSTALL or README in the resulting directory that explains how to install.

---

### Post by k33bz on 2007-05-17
> **Pollywoggy said:**
> I am guessing that number one is a shell script.
Try 'less ufoai-2.1.1-linux_hotfix2.run' to be sure.
If you see '#!/bin/sh' or '#!/bin/bash' at the top of the file it is a BASH script
and you can run 'sh ufoai-2.1.1-linux_hotfix2.run' (you might have to be root, but try as ordinary user first).

For #2

put the file in a temporary (empty) directory and run 'tar jxvf ufo2000-0.7.1071-sources.tar.bz2'
There is probably a file called INSTALL or README in the resulting directory that explains how to install.

well i have tried the first one, and yes, confirmed it is a shell script, so i used sh ufoai-2.1.1-linux_hotfix2.run and got this.
```
k33bz@xxxxx:~$ sh ufoai-2.1.1-linux_hotfix2.run
sh: Can't open ufoai-2.1.1-linux_hotfix2.run
k33bz@xxx:~$ sudo sh ufoai-2.1.1-linux_hotfix2.run
Password:
sh: Can't open ufoai-2.1.1-linux_hotfix2.run
k33bz@txxxxx:~$ 

```

i will be tryin the second one here momentarily

---

### Post by Bachstelze on 2007-05-17
w00t, UFO is a great game for sure !

Back on topic, here did you save the RUN file on your system.

---

### Post by k33bz on 2007-05-17
currently it is on my desktop. should i put it somewhere else

---

### Post by Bachstelze on 2007-05-17
No, but it you're searching for it in your home folder when it's on your desktop, no wonder you can't find it ;)

```

cd ~/Desktop
sudo chmod +x ufoai-2.1.1-linux_hotfix2.run
sudo ./ufoai-2.1.1-linux_hotfix2.run
```

---

### Post by k33bz on 2007-05-17
> **HymnToLife said:**
> No, but it you're searching for it in your home folder when it's on your desktop, no wonder you can't find it ;)

```

cd ~/Desktop
sudo chmod +x ufoai-2.1.1-linux_hotfix2.run
sudo ./ufoai-2.1.1-linux_hotfix2.run
```

ya i already had changed to my desktop before i did that, oh wait, maybe i didnt, hold on, lol

yep thats what it was, lol.........sorry

---

### Post by k33bz on 2007-05-17
ok what am i doin wrong, and i know i have plenty of space left, i checked a few hours ago
[IMG]http://img.photobucket.com/albums/v471/houstonkeebler/Screenshot-UFOAlienInvasionSetup-1.png[/IMG]

ok, i changed the install directory to home/"my user name"
and i will be able to install it there
but is there a way i can install it with root so i can put it in its default location?

---

### Post by k33bz on 2007-05-17
anyone?[-o<

---

### Post by Bachstelze on 2007-05-17
Could you please tell me where you got it from so I can look into it ?

---

### Post by k33bz on 2007-05-17
if i remember correctly i got it from here, [http://gnomefiles.org/]("http://gnomefiles.org/")
but as i said, i am now able to install it into my home directory, but was wondering if there is someway to install it  to where it wants to be installed.

install path 
hat/usr/local/games/ufoai

binary path /usr/local/bin

---

### Post by Bachstelze on 2007-05-17
That's weird, it works just fine here... Are you sure you ran it with sudo ?

---

### Post by k33bz on 2007-05-17
ya this time i am sure i ran it with sudo, i entered my pw and everything. just when the gui loads up, it tells me i dotn have enough space, and i figured out it is because of permissions, so i tried my home folder, and i am able to install it there.

---

### Post by Bachstelze on 2007-05-17
Yeah, that's what I find weird 'cause if you run it with sudo, you should have permission to install in /usr/locel...

---

### Post by k33bz on 2007-05-17
ya i know thats wierd, what do you think it could be

im goin to go try again, and see what happens

---

### Post by k33bz on 2007-05-17
uhhh, well it worked this time, only thing i did different was use the other command you gave me before installing
sudo chmod +x ufoai-2.1.1-linux_hotfix2.run

Thanks Hymn, now off to go get my other game done

---

### Post by mattva01 on 2007-05-17
You should generally do that every time you download a script like that. It sets the script as executable.

---

### Post by k33bz on 2007-05-17
> **mattva01 said:**
> You should generally do that every time you download a script like that. It sets the script as executable.

alright, cool, i didnt know that, thanks

---

### Post by mattva01 on 2007-05-17
The easiest way to tell is to use ls in a terminal. Scripts set as executable are marked in green.

---

### Post by k33bz on 2007-05-17
o ok, i didnt knwo what each color stood for, i knew it meant something, lol

what do the other colors mean

---

### Post by mattva01 on 2007-05-17
Some of the basic ones 
Blue: directory
Red:archive
light blue: shortcut
purple: multimedia
light green: script

---

### Post by k33bz on 2007-05-17
cool, thanks again

---

### Post by Bachstelze on 2007-05-17
Purple goes for videos too, and there's also another shade of blue for audio files.

---

### Post by mattva01 on 2007-05-17
Oh forgot about that 
I'm pretty sure audio is purple by default as well.

---

### Post by k33bz on 2007-05-17
> **mattva01 said:**
> Oh forgot about that 
I'm pretty sure audio is purple by default as well.
my guess is probable what kind of audio file, no?

---

### Post by mattva01 on 2007-05-17
> **k33bz said:**
> my guess is probable what kind of audio file, no?
Possibly but all my audio is purple(Flac and mp3)

---

### Post by Bachstelze on 2007-05-17
It's blue here and I don't think I changed the defaults :p

---

### Post by k33bz on 2007-05-17
then its only ogg files that are :)

so it just depends on what type of audio file it is

---

### Post by mattva01 on 2007-05-17
Hmm ogg files on mine default to purple as well.
It doesnt really matter it just makes me curious.

---

### Post by k33bz on 2007-05-17
makes me curious as well, i dotn have any ogg files, so i wouldnt even know :(

---

### Post by Bachstelze on 2007-05-17
I guess it's just [Pat](http://en.wikipedia.org/wiki/Patrick_Volkerding) playing around with the settings, then ;)

---

### Post by mattva01 on 2007-05-17
Here's a test, there are some on the John Williams page on WIkipedia. Like this one:[http://upload.wikimedia.org/wikipedia/en/6/6a/John_Williams_Theme_from_Jaws.ogg](http://upload.wikimedia.org/wikipedia/en/6/6a/John_Williams_Theme_from_Jaws.ogg)

---

### Post by mattva01 on 2007-05-18
> **HymnToLife said:**
> I guess it's just [Pat](http://en.wikipedia.org/wiki/Patrick_Volkerding) playing around with the settings, then ;)
Could be, that's the Slax difference®

---

### Post by m404 on 2007-05-18
terminal colours are _definitely_ distro-dependent.
there are distros who won't even feature any colours at all.
there are some that will use the common standard (set by debian, if i recall correctly).
and there are some that will have colours, but different patterns.

so you really can't compare one distro to the other when it comes to that.

---

### Post by k33bz on 2007-05-18
> **m404 said:**
> terminal colours are _definitely_ distro-dependent.
there are distros who won't even feature any colours at all.
there are some that will use the common standard (set by debian, if i recall correctly).
and there are some that will have colours, but different patterns.

so you really can't compare one distro to the other when it comes to that.

figured as much

---

### Post by mattva01 on 2007-05-18
> **m404 said:**
> terminal colours are _definitely_ distro-dependent.
there are distros who won't even feature any colours at all.
there are some that will use the common standard (set by debian, if i recall correctly).
and there are some that will have colours, but different patterns.

so you really can't compare one distro to the other when it comes to that.

I knew that, but I thought he was using kubuntu :)

---

### Post by Pollywoggy on 2007-05-18
I must try this game, I did not know of its existence.

---

### Post by k33bz on 2007-05-18
> **Pollywoggy said:**
> I must try this game, I did not know of its existence.

its  a good game, i loved it, got caught up in playin it all nite, lol

---

