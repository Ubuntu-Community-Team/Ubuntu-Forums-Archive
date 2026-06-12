---
title: "Setting up my multimedia"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by Kanephan on 2005-11-20
Well I'm pretty new to Ubuntu, but I'm willing to learn. I don't mind command line stuff and all.

I've got a series of things that need to be dealt with.

1. My sound card isn't detected. As a result, I have no audio at all. I'm not sure what kind I have, I'll have to check later, but I have no idea how to help Ubuntu find it.

2. I need help with codecs. I'm not sure what formats Ubuntu can handle out of the proverbial box, but I'm gonna need support for basic video and audio formats like avi and mp3.

3. I plan to keep all my multimedia on a seperate partition, but I don't know how to reach it in Ubuntu. I did it once before months ago, but I forgot how. I think I have to "mount" it right? Whatever that means.. =/ 

Uh..I guess that covers the most prudent problems. I'd appreciate any help. Thanks in advance.

---

### Post by aysiu on 2005-11-21
[QUOTE=Kanephan]
2. I need help with codecs. I'm not sure what formats Ubuntu can handle out of the proverbial box, but I'm gonna need support for basic video and audio formats like avi and mp3.[/quote] Read this: [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)

> 
3. I plan to keep all my multimedia on a seperate partition, but I don't know how to reach it in Ubuntu. I did it once before months ago, but I forgot how. I think I have to "mount" it right? Whatever that means.. =/  [http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by Kanephan on 2005-11-21
I tried one of the steps in the site you gave me, but I get this error:

john@ubuntu:~$ sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg
[B]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/B]


?!?

---

### Post by 23meg on 2005-11-21
Make sure you don't have Synaptic running as you issue the apt-get command.

---

### Post by Kanephan on 2005-11-21
ahhh =]

---

### Post by Kanephan on 2005-11-21
Problem. Even though I'm doing this:
[I]
The Codecs

"The Codecs" support playing MPEG-1, -2 & -4, DivX, Quicktime, Real Media 8 & 9, Windows Media Video 9 and many other formats.

If you live in a country where it is legal to use the codecs, use your web browser to download the file [WWW] w32codecs_20050412-0.0_i386.deb to your Desktop, and, in a terminal, type:

cd ~/Desktop
sudo dpkg -i w32codecs_20050412-0.0_i386.deb[/I]

I still get this error in Totem

*There were no decoders found to handle the stream, you might need to install the corresponding plugins*


Even though I got no errors in the terminal. everything seemed to go smoothly:

[I]john@ubuntu:~$ cd ~/Desktop
john@ubuntu:~/Desktop$ sudo dpkg -i w32codecs_20050412-0.0_i386.deb
(Reading database ... 65470 files and directories currently installed.)
Preparing to replace w32codecs 1:20050412-0.0 (using w32codecs_20050412-0.0_i386.deb) ...
Unpacking replacement w32codecs ...
Setting up w32codecs (20050412-0.0) ...
john@ubuntu:~/Desktop$[/I]

Tips?

---

### Post by Kanephan on 2005-11-21
I also tried downloading a 20 second mp3 file and playing it in rythembox and totem but neither worked.

This is after supposedly downloading all the codecs.

---

### Post by aysiu on 2005-11-21
Do you have all the codecs here?
[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

And did you type gst-register-0.8 afterwards?

---

### Post by Kanephan on 2005-11-21
That seems to be working.

How come this always happens?:

[I]After unpacking 3486kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.[/I]

am I doing something wrong?

---

### Post by aysiu on 2005-11-21
I don't know. I've never had that happen. Anyone else who can help out here?

---

### Post by arnieboy on 2005-11-21
[QUOTE=Kanephan]That seems to be working.

How come this always happens?:

[I]After unpacking 3486kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.[/I]

am I doing something wrong?[/QUOTE]
try pressing "Y" in caps minus the quotes instead of "y".

---

### Post by aysiu on 2005-11-21
[QUOTE=arnieboy]try pressing "Y" in caps minus the quotes instead of "y".[/QUOTE] It shouldn't make a difference, but it's worth a try. A lower-case *y* always works for me.

---

### Post by Kanephan on 2005-11-21
no luck with capital Y

---

### Post by arnieboy on 2005-11-21
[QUOTE=aysiu]It shouldn't make a difference, but it's worth a try. A lower-case *y* always works for me.[/QUOTE]
i wudnt be too surprised if its just a case binding issue.

---

### Post by arnieboy on 2005-11-21
[QUOTE=Kanephan]no luck with capital Y[/QUOTE]
too bad.

---

### Post by aysiu on 2005-11-21
That's weird. I did a search, and [you're not alone](http://ubuntuforums.org/showpost.php?p=402042&postcount=8)--unfortunately, I couldn't find the solution, though.

---

### Post by arnieboy on 2005-11-21
[QUOTE=aysiu]That's weird. I did a search, and [you're not alone](http://ubuntuforums.org/showpost.php?p=402042&postcount=8)--unfortunately, I couldn't find the solution, though.[/QUOTE]
this is really interesting... it definitely is a key binding issue.. and apt-get seems to think y is not y... lol. lemme look into this. I will get back if I find something.

---

### Post by Kanephan on 2005-11-21
[QUOTE=arnieboy]this is really interesting... it definitely is a key binding issue.. and apt-get seems to think y is not y... lol. lemme look into this. I will get back if I find something.[/QUOTE]


Thanks. I look forward to hearing if you found something. I wouldn't know where to start :???:

---

### Post by schdefan on 2005-11-21
I thought that the upper case letter is the default option so in case y doesn't work it's just pressing enter.
> After unpacking 3486kB of additional disk space will be used.
Do you want to continue [Y/n]? <ENTER>

To see if your soundcard is detetected by ubuntu type
> lspci | grep audio
or
> cat /proc/asound/cards
schdefan

---

### Post by Kanephan on 2005-11-24
[QUOTE=schdefan]I thought that the upper case letter is the default option so in case y doesn't work it's just pressing enter.


To see if your soundcard is detetected by ubuntu type

or

schdefan[/QUOTE]

I got this:

[I]john@ubuntu:~$  lspci | grep audio
0000:00:0e.0 Multimedia audio controller: Rockwell International: Unknown device 4310
[/I]

and this

[I]john@ubuntu:~$  cat /proc/asound/cards
cat: /proc/asound/cards: No such file or directory
[/I]


And the Y/n problem still exists. I tried pressing just "enter" and that worked for the Gstreamer plugins but it won't work for some other things. The installation still aborts.

i'd like to get to the bottom of this... =[

---

### Post by schdefan on 2005-11-25
Your soundcard is not detected properly. I think this means
[LIST]If it is not an onboard card open your case and check if the pci card is stuck tight on the motherboard[/LIST]
[LIST]there is no driver for your soundcard available[/LIST]

Found some links that maybe helps you
[http://www.linuxant.com/drivers/riptide/index.php]("http://www.linuxant.com/drivers/riptide/index.php")
[http://www.linuxquestions.org/questions/archive/63/2005/06/2/324273]("http://www.linuxquestions.org/questions/archive/63/2005/06/2/324273")

schdefan

---

