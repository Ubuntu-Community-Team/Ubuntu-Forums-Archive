---
title: "Seemingly out of options with music players."
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by fullmetalgerbil on 2008-01-07
I was using Amarok, but took it out as it seemed to be causing random restarts and shutdowns ( I thought it might be a hardware issue but the restarts have ceased since I removed the program). I've tried out every other player in the add/remove list and none of them have what I want-which isn't much, just the capability to hold a music library I can choose songs or albums from as I dont even use playlists. Rythmbox does this, however I dont particularly care for it all too much. But if it comes down to being the only choice I have I'll just bite the bullet and use it.
Any suggestions on a music player that I can just load my music folder into and pick songs/albums to play from? I have a few hundred albums and I really dont want to have to organize each one as a separate playlist.
Also, I dont know how to install .tar files so if anybody knows of any players that I could download as  .deb files that would be cool beans.
Thanks much!

---

### Post by spiderbatdad on 2008-01-07
what's wrong with totem gstreamer? works great for me. you create a library with the add + button, lower right, and put what ever you want into a folder you then add. Of course that eliminates xine, but it's a trade off i can live with. P.S. you need all the codecs for gstreamer.

---

### Post by Xavieran on 2008-01-07
I think XMMS could do what you want...
I myself wrote a little music player ,you simply point it at a directory full of music (and only music,I haven't put error handling in it yet) and it will play the songs back in alphabetical order...
XMMS should be in the repositories (Search synaptic) and if you are *really* interested in my music playing script it's on cli-apps.org...

:)

---

### Post by p_quarles on 2008-01-07
You didn't say what you've tried, exactly, so I don't know if this has already been checked off on the list: Exaile. It's very similar to Amarok, but designed specifically for Gnome, and will get along better with the default Ubuntu environment.

---

### Post by JoshuaRL on 2008-01-07
I understand what you're saying about Amarok.  I think it's because it is KDE based.  So it may have weird issues with Gnome.  I suggest Exaile, it's the Gnome version of Amarok.  The only thing is that it's a little behind, so you'll have to put up with that.  I've also heard good things about Muine.  Try this article, it's a multi-page one:

[http://www.pcworld.com/article/id,128636-c,linux/article.html](http://www.pcworld.com/article/id,128636-c,linux/article.html)

---

### Post by browndruid on 2008-01-07
I can't really help with the music player problem, but I can tell you about .tar files.

When you download a file, if it ends with .tar.gz, then you'll want to open terminal, navigate to the folder containing that file, and type in, 
```
tar -xzvf *file*
``` 

If it ends with just .tar, then do the same, but enter
```
tar -xf
```

After that, enter *ls* into the terminal to find the new file that was created. Navigate to the folder. Again, view the contents with *ls*. There will normally be a file that is called README or INSTALL. Enter 

```
less *file*
``` to view the contents, using the arrow keys to scroll. The file will tell you the rest!

Good luck!

---

### Post by jordanmthomas on 2008-01-07
mpd + sonata sounds exactly like something you'd like.
If you don't like sonata there's a bunch of other clients for mpd that can basically do the same.

Usually, I just put all my music in a huge playlist and play on shuffle, but sonata is pretty good for picking any files from your library as well.

---

### Post by fullmetalgerbil on 2008-01-07
I've actually tried Exaile before but it kind of throws the whole library into one big list and doesn't sort by album welll. Thanks though for the suggestion. With Sonata, do I have to first install MPD?

---

### Post by jordanmthomas on 2008-01-07
> **fullmetalgerbil said:**
> I've actually tried Exaile before but it kind of throws the whole library into one big list and doesn't sort by album welll. Thanks though for the suggestion. With Sonata, do I have to first install MPD?

Yes, you have to install and set up MPD first (and it must be running to use sonata).  It's not really that difficult, and it's just a one-time deal.

---

### Post by fullmetalgerbil on 2008-01-08
Ok, so I went and got the mpd .tar.gz file-its on my desktop-however, eventhough I have the instructions to install the file once I navigate to the folder in terminal...I cant seem to navigate to the folder. I tried the cd command thinking it would take me to the desktop, but when I tried the installation it wouldn't go-all it said was: tar: file: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
david@david-desktop:~$

---

### Post by jordanmthomas on 2008-01-08
1.  Why not use mpd from the repositories (you will need universe repository enabled)?
```
sudo apt-get install mpd
```
2.  here's how to extract a tarball on your desktop:
```
cd ~/Desktop
tar -xzf file.tar.gz
```
Then, you can cd into the folder it makes


edit
just typing cd takes you to your home directory, not your desktop

---

### Post by PurposeOfReason on 2008-01-08
Note, if you use mpd read the wiki or how to. It is probably the smoothest ride once you get it set up though and easily the lightest. The best part is you don't even have to have a graphical interface to use it.

---

### Post by antisocialist on 2008-01-08
if you like a GUI then open .tar.XX with archive manager, click the folder and click extract, navigate to desktop and click save, after a few seconds there will be a new folder on your desktop.

now open terminal and type the following cmd's, ignore anything between < and >
cd ~/Desktop/newfoldername
sudo aptitude install checkinstall
y
<checkinstall will be installed after a min or so>
./configure
<when configure is done, type>
sudo checkinstall -D
<make sure that D is a capital D not a lower case D>
<wait a min or so>
<if it asks to install, type y and hit enter>
<you have now installed your new program, keep in mind that some files may need to be installed differently, read the readme if ./configure or sudo checkinstall -D dont work>

now for a breakdown of the cmd's
cd ~/Desktop/newfoldername - you know this, change dir to specified
sudo aptitude install - you know this, aptitude is essentially the same as apt-get, i just prefer aptitude
checkinstall - nifty program that converts tarball sourcecode archives into .deb packages
y - it will ask if you want to install it, y stands for yes
./configure - configuration file for the tarball sourcecode archive, it makes it possible to install the program from source
sudo - you know this part
checkinstall -D run checkinstall, create and install .deb package

rest is just my comments, lol
if you want to run everything as fast as possible use below, where a linebreak is a pause waiting for a new prompt

cd ~/Desktop/newfoldername
sudo aptitude install checkinstall

y

./configure

sudo checkinstall -D

and your done, wasnt that easy

---

