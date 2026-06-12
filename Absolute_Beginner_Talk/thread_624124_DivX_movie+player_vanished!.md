---
title: "DivX movie+player vanished!"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by dimis80 on 2007-11-26
Good evening to all of you. I just have two days the ubuntu installed and i am really happy on getting to know this OS.

It's the start though and i have some small problems...
I have installed the ubuntu 7.10 in my laptop (Compaq 6720s). I am trying to install the right codecs and packages in order to have it in a good shape.

I've tried to open a divx movie after the totem, mplayer vlc etc and when the window appears after some seconds it goes in the background and disappears... why is that? did i do anything stupid?
any help on this??? 
also i have a problem on watching a .mov 

I tried to find the win32 codecs from add/remove but nothing found...

---

### Post by jfinkels on 2007-11-27
Open the terminal ("Applications > Accessories > Terminal") and start vlc from there by typing:```
vlc
```then play your file, and post any error output in the terminal here.

To get w32codecs, you need to add the Medibuntu repository to your list of sources. 

Type the following in the terminal to add the Medibuntu repository to your list of sources:```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
Then, add the GPG Key for the Medibuntu repository by typing the following in the terminal:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Then install the codecs by typing:```
sudo aptitude install w32codecs
```

---

### Post by dimis80 on 2007-11-27
I will proceed now that i am in front of my laptop and I will post if everything goes OK.

Thanks for the help!:):)

---

### Post by dimis80 on 2007-11-27
OK this is the message that i get in the terminal:

** (.:6434): CRITICAL **: clearlooks_style_draw_focus: assertion `height >= -1' failed
[00000341] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
No accelerated IMDCT transform found
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85


I am looking for the decoders...

---

### Post by jfinkels on 2007-11-27
What file are you playing? Have you tried playing this file after having disabled compiz (aka "Desktop Effects")?

---

### Post by dimis80 on 2007-11-28
I' ve gone in the preferences in Mplayer & totem. I selected in video X11 output and it finally worked.

I had some crashes though in the movie but after deselected compiz everything played OK.

:)

---

### Post by dimis80 on 2007-11-28
I' ve gone in the preferences in Mplayer & totem. I selected in video X11 output and it finally worked.

I had some crashes though in the movie but after deselected compiz everything played OK.

:)

---

