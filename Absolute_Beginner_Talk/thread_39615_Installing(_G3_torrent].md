---
title: "Installing( G3 torrent]"
date: 2005-06-05
forum: Absolute Beginner Talk
---

### Post by KINGKWESI on 2005-06-05
Hey what up, i'm a hard core windows user but i'm trying to get into linux, but 
i have trouble using the terminal which i am getting the trying to get the hang off and i little  idea on how to install  programs. 

i have downloaded g3torrent-v1.10-ubuntu and unziped it butevery time i run 

python g3torrent.py 

------------------------- this is the out put i get?

Traceback (most recent call last):
  File "g3torrent.py", line 15, in ?
    import wx
ImportError: No module named wx

can  anyone help me out ???

---

### Post by ow50 on 2005-06-05
at the terminal:
sudo apt-get install libwxgtk2.5.3-python

---

### Post by KINGKWESI on 2005-06-05
what does this do
 ?

---

### Post by KINGKWESI on 2005-06-05
when i input the   code i get this 

wxgtk2.5.3-python
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libwxgtk2.5.3-python

---

### Post by tread on 2005-06-05
It's basically a dependency, you need to install the required package. The exact name may be different, I suggest starting synaptic and searching for the package.

---

### Post by KINGKWESI on 2005-06-05
and how do i do that ? hence i'm using kubuntu 64bit

---

### Post by meat on 2005-06-05
Go to The top left pull down Systems->Administration->Synaptic Package Manager.

---

### Post by bored2k on 2005-06-05
and just why g3torrent ? why not official bittorrent package or azureus for amd64?

---

### Post by KINGKWESI on 2005-06-05
lol,  i  mostly use G3 in Windows, Bit Torrent some Times. thats y i was tryin to install in kubuntu

---

### Post by bored2k on 2005-06-05
[QUOTE=KINGKWESI]lol,  i  mostly use G3 in Windows, Bit Torrent some Times. thats y i was tryin to install in kubuntu[/QUOTE]
 I dont think it even has the new 4.0.+ features the new BT has.. [http://g3torrent.sourceforge.net/](http://g3torrent.sourceforge.net/) (decentralized tracker, etc).

There's an ubuntu package for g3torrent though: [http://www.ubuntuforums.org/showthread.php?t=18369&highlight=g3torrent](http://www.ubuntuforums.org/showthread.php?t=18369&highlight=g3torrent) . I have not tried this method but it supposedly works.

P.S. - I don't understand the poll :s.

---

### Post by KINGKWESI on 2005-06-05
does ubuntu support xvid,dvix and mkv and Ac3 ?

---

### Post by bored2k on 2005-06-05
[QUOTE=KINGKWESI]does ubuntu support xvid,dvix and mkv and Ac3 ?[/QUOTE]
 The question is: can you handle them ? :-P
Yeah they do. What ? you think linux users are a bunch of boring hermits ? We are! but we watch movies! [lol]

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)
Keep that link close to you.

---

### Post by KINGKWESI on 2005-06-05
lol, joka, i didnt mean that  lol anyway thanks for link, 
i just gotta try and get ma head around this. its a total different enviroment form windows. i need to adapt

---

### Post by bored2k on 2005-06-05
It's like a 12 step program. Don't try to do everything on one day or you'll crash and go back to the perjudicial old-you ;).

---

### Post by KINGKWESI on 2005-06-05
lol, yeah, i guess so, hence i need to learn how use the termal i cant use it to well cos i always get mixed up with DOS

---

