---
title: "Issue with iTunes music in Ubuntu"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by theknave on 2006-09-29
Okay, so I followed the directions to transfer all of my iTunes music over to Ubuntu, and I downloaded amaroK to play them (so I could edit the tags), but it won't play any of them! It just tells me it's playing and the little marker goes through the length of the song in a couple seconds, but it won't let me hear it! Any reason why?

---

### Post by theknave on 2006-09-29
Please? Anyone?

---

### Post by hoagie on 2006-09-29
Em do you have the codecs?

---

### Post by theknave on 2006-09-29
Probably not, sir. I have no clue what I'm doing with this ubuntu thing. How would I get said codecs?

---

### Post by slibuntu on 2006-09-29
I had the exact same problem, like exactly! I posted it on this forum here: [http://ubuntuforums.org/showthread.php?t=244061]("http://ubuntuforums.org/showthread.php?t=244061")

---

### Post by theknave on 2006-09-29
I can't even find any of those things they mention in your thread in the package manager. ](*,)

---

### Post by slibuntu on 2006-09-29
Interesting, thats strange, check that you have all the repositories enabled

---

### Post by theknave on 2006-09-29
I didn't, but now I do and I still can't find it in the list.

---

### Post by ewl1217 on 2006-09-29
Did you reload the software list? You need to do that after editing your sources.list.

---

### Post by theknave on 2006-09-29
> **ewl1217 said:**
> Did you reload the software list? You need to do that after editing your sources.list.

Yeah, I wouldn't have known to but it told me.

---

### Post by slibuntu on 2006-09-29
You have to go to the terminal and type " sudo apt-get update " for it to take account of the new repositories
EDIT:
Sorry just saw that new post. Weird. I'm all out of ideas i'm afraid, beyond a good old fashioned reboot! Anyone else care to have a shot?!

---

### Post by theknave on 2006-09-29
I'm looking at it right now and I cannot locate libxine-extracodecs (which is what I need). Any ideas?

---

### Post by paulyche on 2006-09-29
Can you post your repository list?

Open the terminal and type

```
cat /etc/apt/sources.list
```

P.S. Hope you don't mind using the terminal. It's just that it's quicker for trouble shooting purposes.

---

### Post by slibuntu on 2006-09-29
tou actually need to use sudo to get that to worl, and since gedit is the pre installed text editor, this would be better, 
sudo gedit /etc/apt/sources.list

---

### Post by paulyche on 2006-09-29
> **slibuntu said:**
> tou actually need to use sudo to get that to worl, and since gedit is the pre installed text editor, this would be better, 
sudo gedit /etc/apt/sources.list

Not sure that's true, since the permissions allow all users to read sources.list but not to write to it. At least on my system

---

### Post by theknave on 2006-09-29
Okay that "cat" command gave me this:

```
brett@Brett:~$ sudo gedit /etc/apt/source.list
Password:
brett@Brett:~$ cat /etc/apt/sources.lits
cat: /etc/apt/sources.lits: No such file or directory
brett@Brett:~$ cat /etc/apt/sources.list

deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
brett@Brett:~$

```

And the sudo gedit command opened an empty file.

And I don't mind using the terminal, I just don't know what I'm doing with it.

---

### Post by theknave on 2006-09-29
On try two the sudo gedit command opened a file with the same contents as I posted. I must have made a typo.

---

### Post by paulyche on 2006-09-29
Okay, so what happens when you type:

```
sudo apt-get update
```
```
sudo apt-get install libxine-extracodecs
```

and check that xine is selected in amarok:

settings > configure amarok > engines > sound system

---

### Post by slibuntu on 2006-09-29
Sorry, forgot that you weren't trying to edit it! yeah aal users do have permission to read it, i can't see anything wrong with that list,you paulyche?

---

### Post by theknave on 2006-09-29
```
brett@Brett:~$ sudo apt-get update
Get:1 http://ca.archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://ca.archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:3 http://ca.archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://ca.archive.ubuntu.com dapper Release
Hit http://ca.archive.ubuntu.com dapper-updates Release
Get:4 http://security.ubuntu.com dapper-security Release.gpg [189B]
Hit http://ca.archive.ubuntu.com dapper-backports Release
Hit http://security.ubuntu.com dapper-security Release
Hit http://ca.archive.ubuntu.com dapper/main Packages
Hit http://ca.archive.ubuntu.com dapper/restricted Packages
Hit http://ca.archive.ubuntu.com dapper/main Sources
Hit http://ca.archive.ubuntu.com dapper/restricted Sources
Hit http://ca.archive.ubuntu.com dapper/universe Packages
Hit http://ca.archive.ubuntu.com dapper/universe Sources
Hit http://ca.archive.ubuntu.com dapper-updates/main Packages
Get:5 http://ca.archive.ubuntu.com dapper-updates/restricted Packages [14B]
Hit http://ca.archive.ubuntu.com dapper-updates/main Sources
Get:6 http://ca.archive.ubuntu.com dapper-updates/restricted Sources [14B]
Hit http://ca.archive.ubuntu.com dapper-backports/main Packages
Get:7 http://ca.archive.ubuntu.com dapper-backports/restricted Packages [14B]
Hit http://ca.archive.ubuntu.com dapper-backports/universe Packages
Hit http://ca.archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://ca.archive.ubuntu.com dapper-backports/main Sources
Get:8 http://ca.archive.ubuntu.com dapper-backports/restricted Sources [14B]
Hit http://ca.archive.ubuntu.com dapper-backports/universe Sources
Hit http://ca.archive.ubuntu.com dapper-backports/multiverse Sources
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Fetched 60B in 1s (36B/s)
Reading package lists... Done
brett@Brett:~$ sudo apt-get install libxine-extracodecs
Reading package lists... Done
Building dependency tree... Done
Package libxine-extracodecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libxine-extracodecs has no installation candidate

```

---

### Post by paulyche on 2006-09-29
Okay. Now try 
```
sudo apt-get install aptitude
```
```
sudo aptitude install libxine-extracodecs
```

The package is in the repo.

---

### Post by theknave on 2006-09-29
I didn't mention: What I posted was the result of apt-get install, etc.

Also, the soundsystem thing IS xine.

---

### Post by theknave on 2006-09-29
> **paulyche said:**
> Okay. Now try 
```
sudo apt-get install aptitude
```
```
sudo aptitude install libxine-extracodecs
```

The package is in the repo.

That looked like it installed it, but the music still won't play. Do I need to reboot?

---

### Post by paulyche on 2006-09-29
OK hold on, I'll do some googling.

By the way, is your itunes music mp3 or aac format? I hope it's not itunes music store music!

---

### Post by slibuntu on 2006-09-29
YES! i was tearing my hair out cos it wouldn't play and then after a simple reboot, it worked, give it a go!

---

### Post by paulyche on 2006-09-29
> **slibuntu said:**
> YES! i was tearing my hair out cos it wouldn't play and then after a simple reboot, it worked, give it a go!

Yeah give it a go. It certainly won't hurt! :-)

---

### Post by Old Pink on 2006-09-29
.m4p is iTunes encrypted music store format, and will **never** play on ubuntu, unless Apple create [iTunes for Linux](http://matt.moved.in/?p=10).

There are ways of converting iTunes music store formats (.m4p) to .mp3 or .aac, but they aren't entirely legal, so I won't post them here.

---

### Post by theknave on 2006-09-29
It's all MP3.

Reboot solved nothing. :(

---

### Post by Old Pink on 2006-09-29
Terminal:
```
sudo apt-get install xmms
```

Try that?

---

### Post by theknave on 2006-09-29
I installed XMMS, but it's too "winamp" and not enough "iTunes".

I liked it when I could browse things by artist in columns. :(

---

### Post by slibuntu on 2006-09-29
Yeah good idea, XMMS is basically the Linux version of WinAmp, and will play your mp3's straight away, it doesn't have all of amaroks functionality though

---

### Post by theknave on 2006-09-29
> **slibuntu said:**
> Yeah good idea, XMMS is basically the Linux version of WinAmp, and will play your mp3's straight away, it doesn't have all of amaroks functionality though

Yeah, it's way too winamp for me, though. I'm not a fan of winamp.

---

### Post by slibuntu on 2006-09-29
I had a feeling that might be a problem, try looking at this site, it might possibly help [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by theknave on 2006-09-29
I already read that part on MP3s :(

Ah well, I'm sure I can learn to put up with this new program, so long as I can rename songs.

I CAN rename songs, right?

---

### Post by Old Pink on 2006-09-29
Try JuK.

You'll like that, I'm sure. :) 

That's more iTunes, less Win Amp. :P

---

