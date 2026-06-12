---
title: "Novice needs help installing codecs"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by shaftesburyiv on 2007-08-29
I'm trying to use Rhythmbox or a similarly library-like media player, but it won't add the files to the library... probably because I don't have the codecs for them.  I have gone to this page:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

as well as the top half of this:

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

and so now I have added the restricted formats as well as all four g-steamers from synaptic and macromedia.  What I need to do next is add the win32codecs, but for the life of me I can't figure it out.  I found the command line and opened the /etc/apt area, I added the four lines of text, but then what?  When I try to close it, it asks me if I want to save the file and I said yes, then it says I lack the permission.  Could someone walk me through getting the win32codecs at a really, really beginner level?

---

### Post by FuturePilot on 2007-08-29
```
gksudo gedit /etc/apt/sources.list
```
Then add
```
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
```
And then save.
In a terminal do
```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```
And finally do```
sudo apt-get update
```
Then to install```
sudo apt-get install w32codecs
```

---

### Post by rsambuca on 2007-08-29
You don't need to add the '$' sign in front of those commands.  Thus you want to enter```
gksudo gedit /etc/apt/sources.list
```

EDIT:  FuturePilot beat me to it!

---

### Post by arpan on 2007-08-29
prepend 'sudo' to your command for opening /etc/apt file.

e.g. if you tried vim /etc/apt/sources.list then make it sudo vim /etc/apt/sources.list.

add those lines and save it. this should work. btw, same info is listed on the second link you posted here..!!! 

Prepending 'sudo' to command will ask you for your password and will give you priviledges required when given correct password.

---

### Post by shaftesburyiv on 2007-08-29
it will only let me do a "save as" not save ... save isn't highlighted in the file menu.  probably because i am not signed in as an administrator somehow?

---

### Post by FuturePilot on 2007-08-29
> **shaftesburyiv said:**
> it will only let me do a "save as" not save ... save isn't highlighted in the file menu.  probably because i am not signed in as an administrator somehow?

You need to use this command ```
gksudo gedit /etc/apt/sources.list
```
Then follow the directions in my other post above.

---

### Post by rsambuca on 2007-08-29
What happens when you type in ```
gksudo gedit /etc/apt/sources.list
```, make a change and try to save it?

EDIT:  Man FuturePilot types fast!

---

### Post by FuturePilot on 2007-08-29
> **rsambuca said:**
> 
EDIT:  Man FuturePilot types fast!

Lol. I keep beating you. Sorry:lolflag:

---

### Post by shaftesburyiv on 2007-08-29
thanks ... you guys are brilliant.  it was that dollar sign thing.

now the only problem is getting rhythmbox to use those codecs!  when i try to play the files, it shows that red sign with the white line through it - it says, you do not have a decoder installed, you might need to install the necessary plugins.  any advice?

---

### Post by s26c.sayan on 2007-08-29
What is the format of the media file you are trying to play?
e.g mp3, etc

---

### Post by shaftesburyiv on 2007-08-29
mostly wma, with a few mp3 and a few aac

---

### Post by shaftesburyiv on 2007-08-29
solved: just had to restart it ... although lossless wma don't work, hm.

---

