---
title: "DVD Playback Nightmare"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by Ciwan on 2007-10-16
Hi all

I'm a Ubuntu newbie, but I know how to put codes into a terminal !

I've been trying all day to play a BBC DVD [ Life in the Under Growth ]. But I can't !!!

I want to be able to play it in Totem

Can someone please help me fix this problem :(

---

### Post by Dr Small on 2007-10-16
I forget what you need for it to work in totem, but if you have VLC player, it will work automatically because it accepts those file types. But. it can be done in Totem!

Dr Small

---

### Post by Ciwan on 2007-10-16
the reason I want it to work in Totem is because earlier today I downloaded VLC like 20 times and it still didn't work !!

So I want to stick with Totem and concentrate on making it work on there

Help please :(

---

### Post by Dr Small on 2007-10-16
> **Ciwan said:**
> the reason I want it to work in Totem is because earlier today I downloaded VLC like 20 times and it still didn't work !!

So I want to stick with Totem and concentrate on making it work on there

Help please :(
Did you try [this](http://ubuntuforums.org/showpost.php?p=3541079&postcount=6) and [this](http://ubuntuforums.org/showpost.php?p=3546026&postcount=7) ?

Dr Small

---

### Post by Ciwan on 2007-10-16
yep tried them and still same....I can't play the DVD it shows that error message again :(

---

### Post by Ciwan on 2007-10-16
I just googled this and tried everything on there...but still no luck :cry:

[http://ubuntuforums.org/showthread.php?p=3535566](http://ubuntuforums.org/showthread.php?p=3535566)

I'm getting real fed up ](*,)

---

### Post by AMDBuntu on 2007-10-16
I think there are two different plugin packages that can be used for Totem. Gstreamer and Xine. I prefer the Xine because it doesn't jump the DVD menus. I'm not sure if this is everything but it should be.

totem-xine

libdvdcss2 & w32codecs

And the one your probably pulling you hair out over.

libxine1-ffmpeg (this is the one I was always missing)

PS. VLC should be in the synaptic package manager which installs it perfectly?

---

### Post by Ciwan on 2007-10-16
what do I do to get them three ?

And If I already have them, would it be OK if I reinstall them ? :(

---

### Post by AMDBuntu on 2007-10-16
I'm jumping over to my Ubuntu computer to look where they came from. One moment while it boots...

---

### Post by Ciwan on 2007-10-16
alright, thanks

---

### Post by W1lleyCoy0te on 2007-10-16
I'm a complete noob too, only been using Linux for about a week now. I found this which worked for me.  DVD's playing great now.

sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo apt-get install totem-xine
sudo apt-get install libdvdcss2
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg libxine1-ffmpeg libdvdread3

W1lley

---

### Post by AMDBuntu on 2007-10-16
Okay... Have some info for you. I'm on my wifes Ubuntu Laptop and she doesn't have the repository entered that I need. Anyways, I can get you part of the way there... To add a repository go to, System->Administration->software sources, Third party software Tab, Add button and enter this:


Add only one line at a time. That will get you everything except the w32codec. 

deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main

deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main

Disregard the underlines: It's the VLC repository....

Your Synaptic Package manager will update and you'll fine the plug ins there.
System-->Administration->Synaptic Package Manager, then search for what you need.
For can find that on the web and download it. If you download it to your desktop, I think it will install by just double clicking on it. I

---

### Post by Ciwan on 2007-10-16
W1lley I just went through all them codes you gave me and sitll got no result

AMDBuntu one of them lines gave me an error while the thing updated, I think it said it wasn't in use anymore or something like that.

what plugins will I find in System > Administration > Synaptic Package Manager

I think I'll leave Ubuntu tomroow IF I don't get DVDs to work ! It is a shame I really like it too :(

---

### Post by AMDBuntu on 2007-10-16
I got the codes from here. 


[http://www.videolan.org/vlc/download-debian.html](http://www.videolan.org/vlc/download-debian.html)

They work as I just put them on my wife's computer. I think the other fellows codes don't work becasue you don't have the repository installed - software sources. 

The best software source is the medibuntu repository. It's a little tricky as it has key... The key just ensures that your getting authenic (wrong word) from the repository. Not meant to keep anyone out.

---

### Post by AMDBuntu on 2007-10-16
The medibuntu repository information.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Ciwan on 2007-10-16
so where do I go from here ?? I added them two lines you sent me earlier to the (Software Sources) but I got an error.

What do I do now ?

---

### Post by W1lleyCoy0te on 2007-10-16
try:

sudo gedit /etc/apt/sources.list

Enter your password and a text file should appear.

search down it and find the 2 lines:

#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
#deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

remove the # at the beginning of each line.  Save the file and exit.

do:

sudo apt-get update

sudo apt-get upgrade

wait for it to finish and then try the lines I gave earlier, one at a time.

Best of luck

W1lley

---

### Post by AMDBuntu on 2007-10-16
Are you running Feisty?

---

### Post by Ciwan on 2007-10-16
It says I haven't put in a key, but I can't see a place where to put a key and I don't even know what the key is !!!

---

### Post by Ciwan on 2007-10-16
no I'm running Gutsy Version 7.10

---

### Post by wesley_of_course on 2007-10-16
I too had  " Issues "   with codecs  but the following link sure helped me .

              [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

    Give it a try before giving up .  This forum is  'Da Bomb !

            Happy Ubuntuing !

---

### Post by bromix on 2007-10-16
Go to add/remove  enable all availabe on the drop down on the right.   Then search for restricted...install "ubuntu restricted extras"    Also search for gstreamer .   and install good, bad, and ugly packages.  That should work for you.   If I insert a dvd, Totem pops up and plays it.

I have
           Ubuntu Restricted Extras
           Gstreamer Extra Plugins
           Gstreamer ffmpeg video plugin 
           GStreamer, plugins for mms, wavpack, quictime, musepack,    
           GStreamer plugins for aac, xvid, mpeg2, faad

---

### Post by AMDBuntu on 2007-10-16
From:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

The commands to install the medibuntu library with the stuff you need.


sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

---

### Post by strabes on 2007-10-17
Run the exact two commands from AMDBuntu's last post and then run this command:```
sudo apt-get install w32codecs libdvdcss2
```This process is very common and should not have been as difficult as it has been for you. I apologize.

---

### Post by Ciwan on 2007-10-17
Good Morning

today is the day...If by the end of today I still can't get Ubuntu to play DVDs...then I'm gonna have to uninstall it and go back to Windows.

I just tried AMDBuntu's codes (sent in the previous post of his) followed by the code sent by strabs and I still can't play DVDs

I still get same error

---

### Post by Ciwan on 2007-10-17
OK this is getting even more annoying

I just got a DVD from my sister's room [ Main in Manhattan ] and that worked straight away with no problems.

How come my precious DVDs don't work ?? yet crappy girly films DVDs wrok.

The DVD I'm trying to watch is [ Life in the Under growth By: David Attenbourgh ]

Before you ask the DVD is in top condition, not a single scratch and I can play it with no problems at all on our downstairs PC (OS Win XP).

Someone please help ](*,)

---

### Post by Circus-Killer on 2007-10-17
what is the region of your sisters dvds?
what is the region of your dvds?

if both are the same....then it could be that the ones that did play fine are not encrypted with css (most commercial dvds are).

if this is the case, you do not have libdvdcss2 installed.
first do this: 
```
sudo apt-get install libdvdread3
```

then run the following command: 
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

if totem still does not play your dvds after this, then try install gxine and see if your dvds will play in gxine.

---

### Post by Ciwan on 2007-10-17
OK 

Life in the Under growth..............Region 2+4 Colour PAL UK

Maid In Manhattan........................Region PAL UK also 2 FACT also VPRC Also D2-32711-UK-S

I'm gonna do them two codes now and let you know what happens

---

### Post by Ciwan on 2007-10-17
OK I put them codes in. I tried it and got the same error with totem

I then went and installed Gxine and again exact same error

](*,)](*,)](*,)](*,):cry::cry:

---

### Post by amlucent23 on 2007-10-17
> **Ciwan said:**
> OK 

Life in the Under growth..............Region 2+4 Colour PAL UK

Maid In Manhattan........................Region PAL UK also 2 FACT also VPRC Also D2-32711-UK-S

I'm gonna do them two codes now and let you know what happens

hey Ciwan,

I see that your problem still isnt fixed.. but if you can play the commercial version of Maid in Manhattan then you can play DVDs. So .. try other dvds laying around your house.. its just that one it wont play? 

BTW- I have never heard of this. if your regons and PAL/NTSC match then you should be good to go. Does that DVD play of your dvd player connected to your tv?

---

### Post by LowSky on 2007-10-17
first off your using Gutsy which doesn't have much support yet, I  toocant get DVD to work in Totem but VLC works fine... I havent felt like fixing it because I use VLC for everything

you also say that the DVD works in a Windows machine downstairs, using what Media Player? Which doesn't play DVD's natively either, somewhere you had to get the codec before it just worked.

does it play in a DVD player?

---

### Post by Ciwan on 2007-10-17
Yes it does !!

It doesn't matter now though, I installed windows again :( 

I wish I hadn't but I had no choice, The only DVDs that I like watching are thoes by Sir David Attenborough, and If I can't play them...then to me! I can't play DVDs

Another thing was, I couldn't use the features on my expensive Logitech G15 Keyboard :(

I wish I could have stayed with Ubuntu, cause for the two days I had it (although were very annoying at times) I love it :(

---

