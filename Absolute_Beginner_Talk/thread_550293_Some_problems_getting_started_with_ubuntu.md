---
title: "Some problems getting started with ubuntu"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by ROJIRU on 2007-09-13
Ever since I loaded Windows XP on my computer, I have had nothing but problems. In trying to solve them I have become disillusioned with microsoft and their greed.
My son in law, gave me a copy of ubuntu. I tried to load it onto my PC but experienced problems. Until I formatted the Hard drive. After this Ubunto loaded easily.
Had I used ubuntu 20years ago I doubt if I would have missed windows.
Where I am missing it is in the running of programmes that I have bought.
The most notable being Photoshop by Adobe. And use of the Windows Media Player. 
That said my son in law had already given me a copy of Videolan, but it would not download onto ubuntu. so...
I downloaded a copy for ubuntu and transfered it from my computer with xp on it, to my spare computer with ubuntu. 
The packages  appear on my desk top but I haven'worked out how to make them work.
That said I've just read the article on using Synaptic, so I'm off to try it.
The other problem I have is that I receive the Internet Wirelessly. How do I get to receive Ubuntu Wirelessly?

---

### Post by overdrank on 2007-09-13
> **ROJIRU said:**
> Ever since I loaded Windows XP on my computer, I have had nothing but problems. In trying to solve them I have become disillusioned with microsoft and their greed.
My son in law, gave me a copy of ubuntu. I tried to load it onto my PC but experienced problems. Until I formatted the Hard drive. After this Ubunto loaded easily.
Had I used ubuntu 20years ago I doubt if I would have missed windows.
Where I am missing it is in the running of programmes that I have bought.
The most notable being Photoshop by Adobe. And use of the Windows Media Player. 
That said my son in law had already given me a copy of Videolan, but it would not download onto ubuntu. so...
I downloaded a copy for ubuntu and transfered it from my computer with xp on it, to my spare computer with ubuntu. 
The packages  appear on my desk top but I haven'worked out how to make them work.
That said I've just read the article on using Synaptic, so I'm off to try it.
The other problem I have is that I receive the Internet Wirelessly. How do I get to receive Ubuntu Wirelessly?

Hi and welcome, As for the wireless if you could post the out put of the command in the terminal
```
lspci
``` 
located under applications, accessories terminal, Then we can tell which wireless card you have then maybe help. You can get VLC in synaptic manager located under system, administration, synaptic manager. Just do a search for VLC.

---

### Post by skymera on 2007-09-13
so, you got rid of windows entirely?

i personally wouldnt have done :(
i still use for photoshop, gaming.

reinstall?

---

### Post by Tyke91 on 2007-09-13
for photoshop, many people have found that GIMP is a good substitute... you can find it in your applications>graphics menu

as for Windows Media player... that thing is disgusting... 

instead use amaroK for music and VLC for videos.

to get amaroK, much like getting anything else on ubuntu, go into a terminal and type

```
sudo aptitude install amaroK
```

similarly, to get VLC type

```
sudo aptitude install vlc
```

**sudo **lets you use administrative powers

**aptitude **is a cool package management program that will download files from a large ubuntu repository... when people say that something is "on the repos" they mean that you can get it using aptitude

**install** tells aptitude to install the program that you downloaded
[B]
amaroK[/B] is the name of the media player and **vlc **is the name of the movie player


EDIT: if you are unsure on how to open a terminal or what a terminal is, go to your Applications>accessories menu. it will be in there.  Note that it is also called a "shell" 

EDIT2: if you need help with shells, see my sig

---

### Post by ROJIRU on 2007-09-14
> **skymera said:**
> so, you got rid of windows entirely?

i personally wouldnt have done :(
i still use for photoshop, gaming.

reinstall?Thanks for the reply, I've got a second computer that I mess around with. So yes I removed XP from that but still use XP on the othe. But I like what I see with Ubutu, so My aim is to see If I can develop Ubuntu to the point whereby I can get rid of Microsoft.

---

### Post by Dai Bando on 2007-09-14
I got rid of winedos over five years ago and I must say I never missed it.

---

### Post by armandh on 2007-09-14
3 machines running Ubuntu
so far only 2 issues prevent me from dumping windows totally
a great dds-32 printer running in xp with win2k beta drivers [no linux]
4 companies running on QB pro 2007 
but I have not purchased a MS OS since discovering Ubuntu 
and a legal XP pro copy I bought previously, I gave away 
[to my son the gamer for his new box]
My wifes lap top came with vista-sucks [NEXT PROJECT]

---

### Post by ROJIRU on 2007-09-22
> **Tyke91 said:**
> for photoshop, many people have found that GIMP is a good substitute... you can find it in your applications>graphics menu

as for Windows Media player... that thing is disgusting... 

instead use amaroK for music and VLC for videos.

to get amaroK, much like getting anything else on ubuntu, go into a terminal and type

```
sudo aptitude install amaroK
```

similarly, to get VLC type

```
sudo aptitude install vlc
```

**sudo **lets you use administrative powers

**aptitude **is a cool package management program that will download files from a large ubuntu repository... when people say that something is "on the repos" they mean that you can get it using aptitude

**install** tells aptitude to install the program that you downloaded
[B]
amaroK[/B] is the name of the media player and **vlc **is the name of the movie player


EDIT: if you are unsure on how to open a terminal or what a terminal is, go to your Applications>accessories menu. it will be in there.  Note that it is also called a "shell" 

EDIT2: if you need help with shells, see my sig
Thanks Tyke 91, tried it but it didn't quite work.
1st. I put in the what would you call it ? code ....sudo etc. it appeared to work but said something about it being successful when the package was unwrapped. But nothing happened.
2nd. I tried it a second time, it asked for my password, but the computer would not let me type in the letters. So any attempts to programme the instalation fail.
3rd. I tried to download Amorok. Went into their web site, followed the instructions to download and was sent to a second page, where I was offered a choice of about 8. eg. suzze,  debian etc. I went for debian because the file system looked familiar, but all it did was refer me back to the first page. Can you help Rojiru. many thanks.

---

### Post by forestpixie on 2007-09-22
you need to get the Kubuntu version - 1.4.7

are you sure that it hasn't installed though try this

```
whereis amarok
```

similarly check for vlc the same way

if it shows up it should be installed, it goes in the sounds menu

when you're in a terminal and it asks for your password, the cursor doesn't move - a security thing, but it is doing it :)

Edit - if once you've got amarok and it doesn't play mp3 - I use this codec for it

```
sudo apt-get install libxine-extracodecs
```

---

### Post by moredhel on 2007-09-22
it doesn't show when you type your password. just type it and press enter.

You can always use add/remove programs or synaptic instead of aptitude.

They are gui programs as opposed to command line programs.

---

### Post by bobczar on 2007-09-25
> **skymera said:**
> so, you got rid of windows entirely?

i personally wouldnt have done :(
i still use for photoshop, gaming.

reinstall?

You don't have to do a reinstall. There is a program called Partition Recovery that works really well. Goes back as far as 8 partitions I believe.

---

