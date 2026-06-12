---
title: "wmv playback"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by meney on 2006-07-30
I have been attempting to play a wmv file in totem. I have the w32codecs installed. When I click on the file to open, it opens up and begins to play the sound... But there is no video. Where the video should be, there is that screen saver type animation. I'm not sure if this is just a setting or I have to do something else? Does anybody know?

Thanks in advance!

Alex

---

### Post by croak77 on 2006-07-30
Totem with gstreamer doesn't play all wmv's. You will need another program like totem-xine, gxine or mplayer.

---

### Post by Skia_42 on 2006-07-30
Gxine will solve your problem.

---

### Post by Fac51 on 2006-07-30
i have no idea how many times i have posted this, but here it goes again....

```
wget ftp://mplayerhq.hu/MPlayer/releases/codecs/all-20060611.tar.bz2

tar xvjf all-20060611.tar.bz2

cd all-20060611

sudo mkdir /usr/lib/win32

sudo cp * /usr/lib/win32
```

---

### Post by IrishGangsta on 2006-07-30
sudo mkdir /usr/lib/win32


all the commands work but that one comes up as 

mike@Finnegan:~/all-20060611$ sudo mkdir /usr/lib/win32
mkdir: cannot create directory `/usr/lib/win32': File exists

then i did sudo cp* /usr/lib/win32 anyway and nothing happened... im guessing it worked what ever it did.

But what should i do about that one command with the file already existing?

Or does it not matter

---

### Post by Hg80 on 2006-07-30
done this but still cant play WMV v9

---

### Post by Oreo on 2006-08-01
Fac51, I hope you will respond to the correction someone offered. I also have trouble with the mkdir line.

I can play only a few WMVs. I get an error that says I need WVP2 codecs.

How can I get that?
Why aren't there any posts about this?

Oreo

---

### Post by RudolfMDLT on 2006-08-01
Hi! I had some troubles with WMA but if you install XINE, and the and all the Xine add-on's for Totem, amarok ect... Also install Mplayer and the Mplayer PlugIns for Mozilla. Mplayer played files that I could not play in Totem. All the above are easy to find in Synaptic.

As for the mkdir error, it's not an error. Try making any directory anywhere where the same directory already exists and you will get this message. IT's just saying that the directory is already created. I think Fac51's method was when you start from scratch with a fresh install.

EDIT: Isn't wmv 9 the latest version? in that case, won't it create a problem using the default generic linux drivers which (I think) where based on older wmv formats?

Oreo: - There are a LOAD of posts on WMA and WMV problems, you just have to search trough the results :D 

On WVP2:
[http://www.wmplugins.com/ItemDetail.aspx?codec=WVP2](http://www.wmplugins.com/ItemDetail.aspx?codec=WVP2)

It seams like it's a pure Microsoft thing... If any of the older linux dogs are browseing this post some help would be apreciated;)

---

### Post by gils0040 on 2006-08-01
simplest and imho best way is to use mplayer
sudo apt-get install w32codecs mplayer-686
works perfect for me

---

### Post by RudolfMDLT on 2006-08-01
mplayer-686 - Just double check if your running 686 or 386 kernel? I don't know whether it will make a diffrence. Give it a shot though! Afterall, it is a one liner!

I would still like it if an old hat linux users could comment on the compatibility of new WMV codecs VS the linux one's. 

Hg80 - What file can't you play. If you could, send me an URL and if possible I could maybe see if I can view it. Atleast then we'll be on the same playing field!

---

### Post by Oreo on 2006-08-02
Thanks for your help so far!

On the one-liner:  sudo apt-get install w32codecs mplayer-686
I can't get that to work! It says the library is unavailable.
Tried substituting 386, which I should use, and that didn't work.
I do have mplayer installed, probably a manual install some time back, but it doesn't work!

But I have nearly every other player out there installed. The Xine and Gxine players work to play some WMVs.

The problem one that brings up the WVP2 error message in Totem will act like it is playing on the two above players. But there is no video. That video doesn't have sound, so I don't know if they would play with sound.

I went to Rudolph's link, 
         On WVP2:
          [http://www.wmplugins.com/ItemDetail.aspx?codec=WVP2](http://www.wmplugins.com/ItemDetail.aspx?codec=WVP2)
But that takes me to the Microsoft site. If I download a Windows version of the codecs, probably in EXE format, I would assume that I would install it with Wine. But would that help me in playing the files using Ubuntu?

The video that I have that is causing the problem is one I made myself using Microsoft MovieMaker. That's the problem.

Oreo

---

### Post by IrishGangsta on 2006-08-02
i read a little bit and it says that my wmv file is encrypted and can not be played.

I read about it and found that i think i just cant play it. unless i pay for something taht would like cross over it idk

I just dont think i can play it

---

### Post by RudolfMDLT on 2006-08-03
[I]On the one-liner:  sudo apt-get install w32codecs mplayer-686
I can't get that to work! It says the library is unavailable.
Tried substituting 386, which I should use, and that didn't work.
I do have mplayer installed, probably a manual install some time back, but it doesn't work![/I]

OKay, try Synaptic: System => Administration => Synapric packedge manager
Search here for mplayer. Please install mplayer and verything that looks like drivers and codecs! :)

If you can't find either mplayer or the w32codecs than you may need to edit your sources list:

/home/YOURUSER/conf/sources.list

opening it through the GUI will only open it in READ ONLY mode, so in the terminal: sudo gedit /home/rudolf/conf/sources.list
replacing rudolf with your username.

In here make sure that atleast one of every pair of URL's is UN-commented(no #). Save the file, and try again.

[I]I went to Rudolph's link, 
         On WVP2:
          [http://www.wmplugins.com/ItemDetail.aspx?codec=WVP2](http://www.wmplugins.com/ItemDetail.aspx?codec=WVP2)
But that takes me to the Microsoft site. If I download a Windows version of the codecs, probably in EXE format, I would assume that I would install it with Wine. But would that help me in playing the files using Ubuntu[/I]?

I only sent you there to see what the codec was. No, as far as I know wine can handle some MS apps but drivers and codecs are something very different. 

*The video that I have that is causing the problem is one I made myself using Microsoft MovieMaker. That's the problem.* 

I've just done the same though and it did play. I am using an old MS codec to do so though, I take it that you are using a new version. Are you doing anything weird in the video like menus or something? Try encoding the video in another formar or simpler WMV format. If that doesn't work, try encoding as DVI or Mpeg.


and lastly

*i read a little bit and it says that my wmv file is encrypted and can not be played.*

WMV codecs support certification and encryption access control. This means that for example a website will let you download a video for free and then when you try to play it you need to download a Certificate to de-encrypt the file for playing and thats where you pay, for the certificate! Its a way to earn cash for some sites.

Hope this helps!

---

### Post by Oreo on 2006-08-03
Thanks, Rudolf!
Oreo

---

