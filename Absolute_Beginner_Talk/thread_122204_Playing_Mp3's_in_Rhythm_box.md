---
title: "Playing Mp3's in Rhythm box"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by booyang on 2006-01-27
Okay, Im very new to Ubuntu, and linux in general..

 I purchased a new PC, so I decided to put Ubuntu on my old win98 setup.

 Installation went well,I cant get it to auto detect my dialup modem,but at the moment its not my major concern as I plan on giving away this tower to a friend who only wants it for playing music,and managing photos.. I was very suprised to see how well it recognized my USB devices, something that was always a problem on 98.

 Anyways - my problem is Rhythm box says its an MP3 player, yet it wont play my MP3's.. None of them.. it keeps saying something about not a recognized audio stream .

 Im positive they are Mp3's, and not unprotected, Rhythm box, nor Totem for that matter will play them.. I searched on Rhythm box's home, but didnt see any problems such as this..

 What makes it difficult is I have to unhook this computer tower to switch to the Ubuntu one (that cant get on the net ) so its alot of fussing around with wires, finding a problem there, unhooking that tower for this one, searching the net, unhooking the tower again, ect.

 Im going to download that autoupdate thing to a cd, maybe that XMM thing that is like winamp, try those, but it just seems like Im missing something obvious to get the Mp3s to play in Rhythm box . I mean the MP3 files I put on there are showing up as an Mp3 file, but Rhythm box keeps telling me it cant play that audio stream.. ?

---

### Post by moephan on 2006-01-27
Perhaps you haven't installed the unfree codecs yet?

Check here: [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

Also, I haven't tried it myself, but it seems that many people are having great success with Automatix: [http://ubuntuforums.org/showthread.php?t=114251](http://ubuntuforums.org/showthread.php?t=114251)

You should probably try that first.

Enjoy.

Cheers, Rick

---

### Post by Sutekh on 2006-01-27
mp3s are a restricted format.  In order to sidestep illegalities Ubuntu doesn't officially support mp3 codecs. You'll have to read here to work this one out

[Ubuntu Wiki - Restricted Formats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by booyang on 2006-01-27
If it doesnt support it, then why does it include it as an MP3 player ??

 Im going to get that automatix, but like most things i need, Ill have to download it on this PC, burn it to a cd, transfer it to the Linux one.. Also I have to copy and paste any instructions and tips that you guys give me to a note pad, put on the cd, so I can read it on the Linux one..

---

### Post by Sutekh on 2006-01-27
[QUOTE=booyang]If it doesnt support it, then why does it include it as an MP3 player ??

 Im going to get that automatix, but like most things i need, Ill have to download it on this PC, burn it to a cd, transfer it to the Linux one.. Also I have to copy and paste any instructions and tips that you guys give me to a note pad, put on the cd, so I can read it on the Linux one..[/QUOTE]

It doesn't support the use of non free codecs such as mp3.  The fact that Rhythmbox *can* play mp3s is not Ubuntu's issue.  Rhythmbox will play free codecs such as .ogg and FLAC and is a good player hence its inclusion in Ubuntu.  Its pie to install restricted formats but its illegal for ubuntu to distribute them in many countries

---

### Post by booyang on 2006-01-27
So if its an Ubuntu issue, does that also mean that installing another Mp3 player will still give me this problem until I install the restricted formats in Ubuntu itself ?

---

### Post by Sutekh on 2006-01-27
[QUOTE=booyang]So if its an Ubuntu issue, does that also mean that installing another Mp3 player will still give me this problem until I install the restricted formats in Ubuntu itself ?[/QUOTE]
Yes that's correct.  The players themselves have the capability to play mp3s, *provided* the OS using them has the codecs installed.  Think trying to play some kinds of video in Windows.  That needs you to download the appropirate codecs.  

Ubuntu could support mp3 codecs but would have to pay for that *right*. In turn we would have to pay to use Ubuntu.

---

### Post by booyang on 2006-01-27
Im getting the impression that Im stuck without having an internet connection on the Linux tower. It appears that adding repositories basicly tells the computer to download a certain file from a website,and install it. 

 Thats the way I understand it, from what I read. I didnt see how I could download it as a file on one computer, and move it to another.

 Sorry if I understand wrong, this is all pretty new to me. Copy and pasting the lines seems simple, but it appears I "need" to have internet access on that computer to "get" the file... As oppossed to the windows way of doing things where I could just download a file(or codec in this case), and drag it into the proper directory,and install it..

---

### Post by Sutekh on 2006-01-27
[QUOTE=booyang]Im getting the impression that Im stuck without having an internet connection on the Linux tower. It appears that adding repositories basicly tells the computer to download a certain file from a website,and install it. 
[/QUOTE]
Yes thats right

[QUOTE=booyang]
 Thats the way I understand it, from what I read. I didnt see how I could download it as a file on one computer, and move it to another.

 Sorry if I understand wrong, this is all pretty new to me. Copy and pasting the lines seems simple, but it appears I "need" to have internet access on that computer to "get" the file... As oppossed to the windows way of doing things where I could just download a file(or codec in this case), and drag it into the proper directory,and install it..[/QUOTE]
Well you can copy the files over to your linux PC and install them from there.

This is a link to the Ubuntu Packages website ([packages.ubuntu.com]("http://packages.ubuntu.com/")).  Here you can download any package available to Ubuntu users through repositories and Synaptic.

Here is the link to the gstreamer0.8-mad which decodes mp3s
[Ubuntu Packages - gstreamer0.8-mad]("http://packages.ubuntu.com/breezy/libs/gstreamer0.8-mad")
Copy this to your Ubuntu PC and install it using the command
```
sudo dpkg -i gstreamer0.8-mad.deb
```

---

### Post by Sutekh on 2006-01-27
Oops forgot one thing.  Installing the gstreamer0.8-mad package also has dependant packages that must be installed prior.

They are;
libc6
libglib2.0-0
libgstreamer0.8-0
libid3tag0
libmad0 
libxml2
zlib1g

Best to use Synaptic to make sure that these are installed (use a search for them) and where possible use Synaptic to install them, as they might be on the installation CD.  If not then unfortunately you will need to download them individually.  Laborious I know, that's why Synaptic is so good (if you have a net connection)

---

### Post by booyang on 2006-01-27
big thanks..Ill try it in the morning.. All this shuffling computers around has worn me out for the night. Obviously installing things are a little different than what Im used to.

Its not that it appears difficult, just making sure I understand how it works.This is a good learning step for me,as Im sure Ill need to use it many more times in the future..

 Again, thank you.

---

### Post by aysiu on 2006-01-27
[QUOTE=booyang]Im getting the impression that Im stuck without having an internet connection on the Linux tower. It appears that adding repositories basicly tells the computer to download a certain file from a website,and install it.[/QUOTE] Yes, before you worry about MP3 playback, setting up email, Firefox, some random game, or whatever...

The number one thing to get working in Ubuntu (or most Linux distributions) is your internet connection, even if it's dial-up. Most Linux distributions, but especially single-CD ones, are repository and internet dependent for software installation.

There isn't a .exe that you can just download from another computer and copy over.

---

### Post by booyang on 2006-01-27
The internet connection wasnt a priority (least thats what i initially thought)

 I read up on how to make a network connection with dialup (searched these forums) got as far as the auto-detect modem, which failed, so I took the lazy way out, and opted to focus mostly on getting the MP3 playback to work.

 Like I said tho, this computer will be given away, and the guy using it will just be using it for Music and photos. I'd like to have the connection working, but again shuffling computers around is starting to wear on me.. Then again it is almost 3am,and Ive been searching, reading, moving computers around, trying various things since 6pm.Information overload, and the thing I figured would be quickest and easiest to fix(the music) has just about done me in for 1 night.

---

