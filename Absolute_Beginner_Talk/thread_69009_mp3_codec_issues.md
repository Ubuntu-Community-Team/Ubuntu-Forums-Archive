---
title: "mp3 codec issues"
date: 2005-09-25
forum: Absolute Beginner Talk
---

### Post by Zarkoth on 2005-09-25
Alright, I've come very far since I've last posted...got myself a dual-boot of WindowsXP(for gaming only I promise  :) ) and Ubuntu, have a wonderful shared fat32 and all kinds of fun things...but now that I've gotten around to getting my mp3's up and running, I've hit all kinds of problems...

Now I did search and found someone who was having the exact same problem, so I decided that following the advice posted there was a wise decision, and I'm sure it was.

But, for some reason or the other, it didn't work....

here's that thread....

[http://ubuntuforums.org/showthread.php?t=63375&highlight=mp3](http://ubuntuforums.org/showthread.php?t=63375&highlight=mp3)

and here's what I get when I type....

> zarkoth@ubuntu:~$ sudo apt-get install w32codecs libdvdcss2 totem-xine gstreamer0.8-misc gstreamer0.8-plugins
Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate


This also happens with the dvd and other such codecs...

Any help is very much appreciated, thanks in advance

 - Zarkoth

---

### Post by Perfect Storm on 2005-09-25
Did you follow this which is also reffered on the link you provided? [http://ubuntuguide.org/#repositories](http://ubuntuguide.org/#repositories)

---

### Post by Mustard on 2005-09-25
[QUOTE=Artificial Intelligence]Did you follow this which is also reffered on the link you provided? [http://ubuntuguide.org/#repositories](http://ubuntuguide.org/#repositories)[/QUOTE]
 win32codecs is not in the ubuntu repositories anymore due to legal issues.

---

### Post by wkh on 2005-09-25
So what the **** are we supposed to do if we want to play our mp3s on Ubuntu?  ](*,)

---

### Post by Mustard on 2005-09-25
[QUOTE=wkh]So what the **** are we supposed to do if we want to play our mp3s on Ubuntu?  ](*,)[/QUOTE]
 I imagine you just download and install them from another source.

---

### Post by Xian on 2005-09-25
[QUOTE=wkh]So what the **** are we supposed to do if we want to play our mp3s on Ubuntu?  ](*,)[/QUOTE]
Geez....
Like we used to of course. 

Download the [Essential Codecs Package](http://www1.mplayerhq.hu/homepage/design7/dload.html) from [Mplayer](http://www1.mplayerhq.hu/homepage/design7/news.html).
Or you can try installing the codecs from [debian-marillat](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/).

---

### Post by TristanMike on 2005-09-25
I was just kindly led onto [this site](http://giannaros.org/tor/bt/) which has the "w32codes" and the "java" pack via torrent. Just download (and seed :)) the appropriate file and a quick little```
sudo dpkg -i <filename>
```Credit goes to "robotgeek" and "apokryhpos" for getting us here.

Please remember to seed :)

---

### Post by Perfect Storm on 2005-09-25
[QUOTE=wkh]So what the **** are we supposed to do if we want to play our mp3s on Ubuntu?  ](*,)[/QUOTE]
Go to the link that Xian provided

cd /where/your/downloaded/file/is
tar -xjf essential-20050412.tar.bz2
sudo mkdir -p /usr/local/lib/codecs
sudo cp essential-20050412/* /usr/local/lib/codecs/

---

### Post by Perfect Storm on 2005-09-25
[QUOTE=TristanMike]I was just kindly led onto [this site](http://giannaros.org/tor/bt/) which has the "w32codes" and the "java" pack via torrent. Just download (and seed :)) the appropriate file and a quick little```
sudo dpkg -i <filename>
```Credit goes to "robotgeek" and "apokryhpos" for getting us here.

Please remember to seed :)[/QUOTE]

Perhaps it should be written into the unofficial ubuntu guide, I guess we'll alot of these post.

---

### Post by bkasterm on 2005-09-26
mp32ogg works for me.

Best,
Bart

---

### Post by tageiru on 2005-09-26
[QUOTE=wkh]So what the **** are we supposed to do if we want to play our mp3s on Ubuntu?  ](*,)[/QUOTE]
Pay for a legal mp3 decoder license.

---

### Post by linkunderscore on 2005-09-27
[QUOTE=tageiru]Pay for a legal mp3 decoder license.[/QUOTE]

why would anyone using linux ( a free open source operating system) PAY to listen to music?

---

### Post by Wolki on 2005-09-27
[QUOTE=wkh]So what the **** are we supposed to do if we want to play our mp3s on Ubuntu?  ](*,)[/QUOTE]

Realize you don't need win32codecs for that, libmad and gstreamer0.8-mad should be enough. :)

More info on codecs: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by tseliot on 2005-09-27
[QUOTE=Artificial Intelligence]Go to the link that Xian provided

cd /where/your/downloaded/file/is
tar -xjf essential-20050412.tar.bz2
sudo mkdir -p /usr/local/lib/codecs
sudo cp essential-20050412/* /usr/local/lib/codecs/[/QUOTE]
I'v always put the codecs into /usr/lib/win32 (and it worked)

Do you think it makes any difference? (I'm asking because I really don't know)

---

### Post by TristanMike on 2005-09-27
[QUOTE=Wolki]Realize you don't need win32codecs for that, libmad and gstreamer0.8-mad should be enough. :)

More info on codecs: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)[/QUOTE]Funny....the wiki still tells us to install the w32codecs......

---

### Post by Wolki on 2005-09-27
[QUOTE=TristanMike]Funny....the wiki still tells us to install the w32codecs......[/QUOTE]

Of course, if you want the w32codecs functionality. You don't need it for mp3 though, that's - as I said - in libmad and the gstreamer plugin.

w32codecs supplies, according to the package itself:
[QUOTE=w32codecs] ATI VCR-2 video codec.
 Cinepak video codec
 DivX ;-) video codec, ver. 3.11
 DivX ;-) video codec, ver. 4.x
 Indeo Video 3.2/4.1/5.0/4.1 quick/5.0 quick codecs.
 Intel 263 video codec.
 Microsoft MPEG-4 video codec, beta version 3.0.0.2700
 Morgan Multimedia Motion JPEG video codec.
 QuickTime
 RealAudio
 RealVideo 8
 RealVideo 9
 Windows Media Video 9[/QUOTE]

---

### Post by 23meg on 2005-09-27
here's a direct link to w32codecs in the Marillat repository; it doesn't have any dependencies, so you can install it straight away with sudo dpkg -i :

[ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb)

---

### Post by TristanMike on 2005-09-27
[QUOTE=Wolki]Of course, if you want the w32codecs functionality. You don't need it for mp3 though, that's - as I said - in libmad and the gstreamer plugin.

w32codecs supplies, according to the package itself:[/QUOTE]Wow, thanx for clearing that up, and providing that list, pretty sweet, but now I understand what you meant. Much appreciated.

---

### Post by Zarkoth on 2005-10-01
Yeah, I really would've followed all those suggestions, but these forums were down for a bit, and during that time I managed to fix the problem, lol
I suppose I owe it all to Easy Ubuntu:
[http://ubuntuforums.org/showthread.php?t=64629]("http://ubuntuforums.org/showthread.php?t=64629")
Great little program :)
Thanks for the suggestions and whatnot.
You gotta love that Linux community, thanks all!

-Zarkoth

---

### Post by thort on 2005-10-03
[QUOTE=Artificial Intelligence]Go to the link that Xian provided
cd /where/your/downloaded/file/is
tar -xjf essential-20050412.tar.bz2
sudo mkdir -p /usr/local/lib/codecs
sudo cp essential-20050412/* /usr/local/lib/codecs/[/QUOTE]Hi !
Is this all that is needed? Just copy the codecs files to **/usr/local/lib/codecs**. I have done this, but no mp3 sound in Totem. It says: [COLOR="Sienna"]"There were no decoders found to handle the stream, you might need to install the corresponding plugins."[/COLOR]
Have I missed something? I thought Totem automatically search for codecs in **/usr/local/lib/codecs**. Is there something more to do to make Totem play mp3?

---

### Post by Wolki on 2005-10-03
[QUOTE=thort]Have I missed something? I thought Totem automatically search for codecs in **/usr/local/lib/codecs**. Is there something more to do to make Totem play mp3?[/QUOTE]

w32codecs doesn't help with mp3. look above for a list of what's in w32codecs.

If you're using hoary, the default totem can't even use them. For mp3 support in default totem, install gstreamer0.8-mad from synaptic, or gstreamer0.8-codecs for a variety of codecs.

---

### Post by thort on 2005-10-03
Thanks Wolkl for Your reply ![QUOTE=Wolki]w32codecs doesn't help with mp3. look above for a list of what's in w32codecs.
If you're using hoary, the default totem can't even use them. For mp3 support in default totem, install gstreamer0.8-mad from synaptic, or gstreamer0.8-codecs for a variety of codecs.[/QUOTE]Sorry, but what is **hoary**? I'm a newbie.

I can't find neither **gstreamer0.8-mad** nor **gstreamer0.8-codecs** in the list of available packages in Synaptic. So, if they are necessary, from where do I install them?

How can I make Totem play mp3? And wma would be nice to.

---

### Post by Mustard on 2005-10-03
Hoary Hedgehog is the name given to the 5.04 version of Ubuntu.

The newer 5.10 version will be known as Breezy Badger.

If you can't find the packages when you search in Synaptic, I would be inclined to think that there are other repositories that are not yet activated on your system.

Try going to your Settings > Repository section of Synaptic and playing around with what repositories are enabled.

---

### Post by Wolki on 2005-10-03
[QUOTE=thort]I can't find either **gstreamer0.8-mad** or **gstreamer0.8-codecs** in the list of available packages in Synaptic. So, if they are necessary, from where do I install them?[/quote]

I'm sorry, it's called gstreamer0.8-plugins instead of -codecs.
You need to point synaptic to additional software lists to get these files. In synaptic, go Settings -> Repositories, Add, and check universe and multiverse.

---

### Post by thort on 2005-10-04
Thanks Wolki ![QUOTE=Wolki]You need to point synaptic to additional software lists to get these files. In synaptic, go Settings -> Repositories, Add, and check universe and multiverse.[/QUOTE]Neither **gstreamer0.8-mad** nor **gstreamer0.8-plugins** appear in the Synaptic list of not installed packages to install. A package named **gstreamer0.8-plugins-apps** turn up. Is this the same as **gstreamer0.8-plugins**?
How do I get these packages installed?

---

### Post by Wolki on 2005-10-04
[QUOTE=thort]Thanks Wolki !Neither **gstreamer0.8-mad** nor **gstreamer0.8-plugins** appear in the Synaptic list of not installed packages to install. A package named **gstreamer0.8-plugins-apps** turn up. Is this the same as **gstreamer0.8-plugins**?
How do I get these packages installed?[/QUOTE]

No, plugins-apps is a different package. Make sure that in Settings -> Repositories, you have universe and multiverse enabled. If you do, press update. You should be able to find both pavkages now.

If you cant, there's something wrong. Post the contents of the /etc/apt/sources.list file.

---

### Post by thort on 2005-10-05
Thanks Wolki !

I give up the attempt to get mp3 and wma support in Totem. At least for now.

I have sucessfully managed to install the XMMS and Mplayer musicplayers. I did this using the Synaptic Package Manager. I had to add a new repository in Synaptic to be able to download all files needed for Mplayer.

Now my XMMS plays mp3, and the Mplayer both mp3 and wma.

I am satisfied for now!

:) :) :)

---

### Post by poofyhairguy on 2005-10-05
[ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/w/w32codecs/w32codecs_20050412-0unofficialubuntu2_i386.deb](ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/w/w32codecs/w32codecs_20050412-0unofficialubuntu2_i386.deb)

There is the codecs you desire.

---

