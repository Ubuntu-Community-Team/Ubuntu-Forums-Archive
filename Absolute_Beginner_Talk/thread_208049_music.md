---
title: "music"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by ckonrad on 2006-07-02
anyone know how to play music in ubuntu? I like to listen to somafm.com how do i get that to work, i have tried like 5 programs so far that came with ubuntu but none of them play it.

thanks

---

### Post by aysiu on 2006-07-02
[Enable MP3 playback.](https://help.ubuntu.com/community/RestrictedFormats#head-e18f2d510b1efe975368b818b5aa3ae2b2eee5c8)

Then click the MP3 link on somafm.com.
When I did that, it opened in Rhythmbox as a radio station.

---

### Post by ckonrad on 2006-07-02
i dont really u nderstand what you are talking about, how do i enable that. I looked at the link you provided but its pretty much over my head. How do i install those packages. I am used to just installing rpm's and compiling things from source. I also dont know what dapper drake is. Where do i find  gstreamer0.10-plugins-ugly? Sorry for all the questions, i usually use suse 10 on my laptop and everything just works great all the time. 


[QUOTE=aysiu][Enable MP3 playback.](https://help.ubuntu.com/community/RestrictedFormats#head-e18f2d510b1efe975368b818b5aa3ae2b2eee5c8)

Then click the MP3 link on somafm.com.
When I did that, it opened in Rhythmbox as a radio station.[/QUOTE]

---

### Post by aysiu on 2006-07-02
This link explains how to install stuff in Ubuntu (all four major ways):
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

To get the right repositories, go here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then, you can just do ```
sudo aptitude update
sudo aptitude install gstreamer0.10-plugins-ugly
```

---

### Post by ckonrad on 2006-07-02
I got as far as putting the information in my source list but it tells me i cant save it. Not surprisingly taking into account that i dont even know what a repository is.



[QUOTE=aysiu]This link explains how to install stuff in Ubuntu (all four major ways):
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

To get the right repositories, go here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then, you can just do ```
sudo aptitude update
sudo aptitude install gstreamer0.10-plugins-ugly
```[/QUOTE]

---

### Post by aysiu on 2006-07-02
That's why you should read the link about installing software.

If you follow the instructions exactly as written, you'll notice that the command to edit /etc/apt/sources.list as administrator has a special parameter in front of it: ```
kdesu
``` or ```
gksudo
```

Please read the first link I gave you about installing software--it explains a bit about repositories.

---

### Post by ckonrad on 2006-07-02
here is the error i get,

GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.




[QUOTE=aysiu]This link explains how to install stuff in Ubuntu (all four major ways):
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

To get the right repositories, go here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then, you can just do ```
sudo aptitude update
sudo aptitude install gstreamer0.10-plugins-ugly
```[/QUOTE]

---

### Post by ckonrad on 2006-07-02
i didnt see that written anywhere in that link on the 4 ways to install things in ubuntu.



[QUOTE=aysiu]That's why you should read the link about installing software.

If you follow the instructions exactly as written, you'll notice that the command to edit /etc/apt/sources.list as administrator has a special parameter in front of it: ```
kdesu
``` or ```
gksudo
```

Please read the first link I gave you about installing software--it explains a bit about repositories.[/QUOTE]

---

### Post by ckonrad on 2006-07-02
yeah that doesnt work either i just get the same error again. 

GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


[QUOTE=ckonrad]i didnt see that written anywhere in that link on the 4 ways to install things in ubuntu.[/QUOTE]

---

### Post by aysiu on 2006-07-02
Explains repositories:> All Debian-based distros having something called aptitude which allows you to draw from a set of online repositories (stored in the /etc/apt/sources.list file) that house packages (i.e., programs/software). You can enable extra Ubuntu repositories by following **these instructions**--extra repositories means more software available to install. The aptitude command does several things at once--it downloads the appropriate files, downloads all their dependencies, and installs all of them. **these instructions** links to this:

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

which says: > Open up a terminal and type in

If you're using Ubuntu (Gnome):
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
**gksudo** gedit /etc/apt/sources.list

If you're using Kubuntu (KDE):
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
**kdesu** kwrite /etc/apt/sources.list

If you're using Xubuntu (XFCE):
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
**gksudo** mousepad /etc/apt/sources.list 

---

### Post by aysiu on 2006-07-02
[QUOTE=ckonrad]yeah that doesnt work either i just get the same error again. 

GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/QUOTE] That "error" is fine--just trust me.

If you don't trust me, read more here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by ckonrad on 2006-07-02
Yes i know and this 

If you're using Ubuntu (Gnome):
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list

doesnt work i get the error i posted in my last message.

thanks for helping though.





[QUOTE=aysiu]Explains repositories: **these instructions** links to this:

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

which says:[/QUOTE]

---

### Post by ckonrad on 2006-07-02
its not that i dont believe you, its that it doesnt work, it wont let me save the source.list i typed in exactly what was listed on the link you provided.


[QUOTE=aysiu]That "error" is fine--just trust me.

If you don't trust me, read more here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)[/QUOTE]

---

### Post by aysiu on 2006-07-02
Hm. That's weird.

Can you do this instead, then? ```
sudo nano /etc/apt/sources.list
``` To save when you're done, press Control-X, Y, then Enter--in that order.

---

### Post by ckonrad on 2006-07-02
I think that worked, but at the top of the page it says copy and paste it OVER the original source.list do i have to delete the other one first or will it just copy over it. Then at the bottom of the page it seems to give different instructions to delete everything afterwards? Why would i do that?


[QUOTE=aysiu]Hm. That's weird.

Can you do this instead, then? ```
sudo nano /etc/apt/sources.list
``` To save when you're done, press Control-X, Y, then Enter--in that order.[/QUOTE]

---

### Post by ckonrad on 2006-07-02
[QUOTE=aysiu]Hm. That's weird.

Can you do this instead, then? ```
sudo nano /etc/apt/sources.list
``` To save when you're done, press Control-X, Y, then Enter--in that order.[/QUOTE]

Well i did this stuff after copying and pasting that repository info or whatever it was all i know is that i am pasting things all over the place.

sudo aptitude update
sudo aptitude install gstreamer0.10-plugins-ugly

and the music still doesnt work, any suggestions?

---

### Post by ckonrad on 2006-07-03
[QUOTE=ckonrad]I think that worked, but at the top of the page it says copy and paste it OVER the original source.list do i have to delete the other one first or will it just copy over it. Then at the bottom of the page it seems to give different instructions to delete everything afterwards? Why would i do that?[/QUOTE]

i get a "stream error, unexpected end of stream" which is what i got before i did this update with this new file.

---

### Post by ckonrad on 2006-07-03
[QUOTE=ckonrad]i get a "stream error, unexpected end of stream" which is what i got before i did this update with this new file.[/QUOTE]


anyone else out there able to help out with this problem?

---

### Post by aysiu on 2006-07-03
Let me try to explain as best I can.

The instructions you have been copying and pasting do this:

1. Make a backup copy of your old sources.list, which lists all your online repositories that have software in them.

2. Change your sources.list to one I know has the proper repositories that will give you MP3 playback. The reason you paste them *over* your old sources.list is you'd otherwise have duplicate sources, which won't work. Since you have a backup copy, it doesn't matter if you erase your old one.

3. Install the MP3 playback codecs. So it should work now, but you're getting some strange error about the stream ending unexpectedly. [Unfortunately, it doesn't appear to be a very common problem](http://www.google.com/search?hl=en&q=stream+error%2C+unexpected+end+of+stream+site%3Aubuntuforums.org&btnG=Google+Search).

I wish I could help with this more. I usually am able to help people either because I've solved problems on my own or because I can find the error through a Google search.

---

