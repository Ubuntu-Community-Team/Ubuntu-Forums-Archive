---
title: "codec"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by saurabhgupta on 2008-03-23
not able to open any exe files on ubuntu.Do suggest me what to do?
 any installables required?

---

### Post by jan quark on 2008-03-23
exe files are **only** executable in windows
 to run it you will need to install Wine

---

### Post by Perfect Storm on 2008-03-23
First what are you trying to do?

If you may not be aware that Linux do not use .exe files it's a windows format.

---

### Post by linuxtoindia on 2008-03-23
go to ur synaptic and type ''wine'' in search there..
it is worth 39 mb..
install it

after that just right click any .exe file ,, you will be able to install it!

i use tally and condition zero on ubuntu!

---

### Post by bhavi on 2008-03-23
Hello...

To execute .exe programs in linux you need wine(windows emulator)!

This program is supposed to run your windows Applications on linux !

you can easily download it / install it in a single command in your terminal !

to do that follow those steps:
open your terminal by clicking applications -> Accessories -> Terminal

then when your terminal opens, type in :

sudo apt-get install wine

it should ask for your password, type it in . Notice that it won't show the '*' while you type, but just type in normally ! this is how it works to avoid people from looking over your shoulder !:-)

after the apt gets your program and installs it, you can close the terminal either by typing exit, or clicking the X button !

now it's time to run your Wine !

click on applications -> accessories -> winefile

This will show you something like the old "winfile" !

simply browse to your setup.exe for your program !:-), and do everything like you did it on windows !

More Info on wine:

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

But prior to installing wine you need to enable extra repositories..

To do the same please refer:

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by N1N31NCHN41L5 on 2008-03-23
The title of your post is CODEC, if you are just looking for codecs to play mp3 etc go to synaptic manager and search for ubuntu-restricted-extras, then apply those. That will give you all the codecs you need.

---

### Post by fela on 2008-03-23
> **N1N31NCHN41L5 said:**
> The title of your post is CODEC, if you are just looking for codecs to play mp3 etc go to synaptic manager and search for ubuntu-restricted-extras, then apply those. That will give you all the codecs you need.

you don't even need to do that, just try playing a song/video, then it'll ask you to look for a suitable codec. then you can automatically install the codec. :)

---

### Post by N1N31NCHN41L5 on 2008-03-23
> **fela said:**
> you don't even need to do that, just try playing a song/video, then it'll ask you to look for a suitable codec. then you can automatically install the codec. :)

my sugestion was simply to retrieve and apply ALL available codecs at one time. I use firefox to play my sirius satelite radio and it gave me 4 things needing install. it would only let me do 1, now everytime it says more are needed but gives me NO options. Was trying to suggest a way this wouldnt happen if he needed more than one.

---

### Post by fela on 2008-03-23
> **N1N31NCHN41L5 said:**
> my sugestion was simply to retrieve and apply ALL available codecs at one time. I use firefox to play my sirius satelite radio and it gave me 4 things needing install. it would only let me do 1, now everytime it says more are needed but gives me NO options. Was trying to suggest a way this wouldnt happen if he needed more than one.

i guess you can do it like that, but my strategy is just to simply install 'em when i need 'em. The hardest one was libdvdcss (which you need to watch encrypted DVDs), i had to compile that from source to enable playing of my dvds.

---

