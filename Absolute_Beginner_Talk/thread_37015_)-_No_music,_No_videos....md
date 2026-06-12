---
title: ")-: No music, No videos..."
date: 2005-05-25
forum: Absolute Beginner Talk
---

### Post by shaynaynay on 2005-05-25
HEEEELP!
I'm newbie to Linux and Ubuntu.
I cant play mp3's, avi's, mpg's etc on my Ubuntu.
I read ubuntuguide.org, tried to download some codecs, and got some errors.
Found on the net some good codecs, extraced them to /usr/lib/codecs but still, it does not work.
I have here Totem player.

Have no idea what to do.

Your help is needed.
Thank you very very much!
 ](*,)

---

### Post by jkndrkn on 2005-05-25
Following the steps in ubuntuguide is your best bet. If you have errors downloading using apt-get or synaptic, you have bigger problems than faulty multimedia codecs.

---

### Post by clb137 on 2005-05-25
[QUOTE=shaynaynay]HEEEELP!
I'm newbie to Linux and Ubuntu.
I cant play mp3's, avi's, mpg's etc on my Ubuntu.
I read ubuntuguide.org, tried to download some codecs, and got some errors.
Found on the net some good codecs, extraced them to /usr/lib/codecs but still, it does not work.
I have here Totem player.




Have no idea what to do.

Your help is needed.
Thank you very very much!
 ](*,)[/QUOTE]

Hi,

Can you tell me what errors you had following the guide???/

You should not have had any,  are you using KDE???

---

### Post by shaynaynay on 2005-05-26
[QUOTE=clb137]Hi,

Can you tell me what errors you had following the guide???/

You should not have had any,  are you using KDE???[/QUOTE]

Tried this in Gnome and in KDE.
The first thing (downloading the .deb file) was good.
The second thing: "sudo apt-get install gstreamer0.8-plugins" return an error:
> 
Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.8-plugins has no installation candidate

Every other command gives error like this...
for ex:
> 
E: Couldn't find package w32codecs

after running the third command.....
 ](*,)  ](*,)  ](*,)

---

### Post by drummer on 2005-05-26
[QUOTE=shaynaynay]Tried this in Gnome and in KDE.
The first thing (downloading the .deb file) was good.
The second thing: "sudo apt-get install gstreamer0.8-plugins" return an error:

Every other command gives error like this...
for ex:

after running the third command.....
 ](*,)  ](*,)  ](*,)[/QUOTE]
Have you added the marillat repositories and extra hoary repositories? looks like you might not have, so read 'Adding extra repositories' at the top of the guide and this should allow you to install the codecs through apt-get.

[http://www.ubuntuguide.org/#extrarepositories]("http://www.ubuntuguide.org/#extrarepositories")

Also, if you've downloaded a .deb file you need to use 'sudo dpkg -i *.deb' to install it rather than apt-get. apt-get is for installing packages that are in package repositories (remote servers with thousands of packages on them), it does the downloading for you so you don't have to look for .deb files yourself and also satisfies all package dependencies while it's at it. Very intuitive program.

Once the extra repositories have beed added, all the packages needed for mp3 and video can be installed through apt-get.

---

### Post by eldrich_rebello on 2005-05-26
if synaptic fails,download the packages manually and install them yourself.i doubt there are many dependency issues to resolve

---

### Post by poofyhairguy on 2005-05-27
Here. Try this:

[http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)

---

### Post by jobezone on 2005-05-27
[QUOTE=shaynaynay]HEEEELP!
I'm newbie to Linux and Ubuntu.
I cant play mp3's, avi's, mpg's etc on my Ubuntu.
I read ubuntuguide.org, tried to download some codecs, and got some errors.
Found on the net some good codecs, extraced them to /usr/lib/codecs but still, it does not work.
I have here Totem player.

Have no idea what to do.

Your help is needed.
Thank you very very much!
 ](*,)[/QUOTE]
 In the ubuntu guide, add the "backports" repository. I'm not sure if you'll need the Universe and Multiverse repositories, but try now to install, using synaptic or the ```
sudo apt-get install <package>
``` command in a terminal:

gstreamer0.8-lame
gstreamer0.8-plugins
w32codecs
liblame0

Then run in a terminal
```
gst-register-0.8
```

---

### Post by shaynaynay on 2005-05-28
Thank you all, it really was repositories problem.
fixed it. (-:

Now I just got little problem with some avi and mpg files, and of course wma/wmv files...
But that is for other time.

Also, I have a question: I mounted my C drive, but there are no folders and files that contaions Hebrew characters in their name... Not in KDE (with I changed to Hebrew)..
I could never get Hebrew files mounted, right?

---

### Post by jkndrkn on 2005-05-29
It is generally not recommended to mount system drives unless you have them set to read only. Create a separate partition to hold your media files and mount that instead.

As far as the Hebrew characters, I've not looked into that so I can't offer comment.

---

### Post by pravit on 2005-05-29
I have gotten all gstreamer0.8 stuff and w32codecs, basically followed the instructions of ubuntuguide for "get multimedia codecs", yet I still can't play avi files. Totem movie player gives me audio but no video and XMMS doesn't play it at all(instead it opens up some dialog asking me what I want to play).

---

### Post by jobezone on 2005-05-29
[QUOTE=pravit]I have gotten all gstreamer0.8 stuff and w32codecs, basically followed the instructions of ubuntuguide for "get multimedia codecs", yet I still can't play avi files. Totem movie player gives me audio but no video and XMMS doesn't play it at all(instead it opens up some dialog asking me what I want to play).[/QUOTE]
 For video, install either gxine or xine . Totem-gstreamer is still a little flaky .

---

### Post by clb137 on 2005-05-30
[QUOTE=pravit]I have gotten all gstreamer0.8 stuff and w32codecs, basically followed the instructions of ubuntuguide for "get multimedia codecs", yet I still can't play avi files. Totem movie player gives me audio but no video and XMMS doesn't play it at all(instead it opens up some dialog asking me what I want to play).[/QUOTE]


Hi,

I also agrre with the last thread install xine,  not all formats will work in lunux

clinton

---

### Post by jobezone on 2005-05-30
pravit, did you execute gst-register-0.8 like explained in [http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs) ?

clb137, Well, the codecs pravit installed (w32codecs) will give him acess to all (or at least the most popular) of the multimedia "formats". These codecs should be acessible by the various linux multimedia applications, like totem+gstreamer, xine, and mplayer. But perhaps since gstreamer isn't yet a 1.0 version, it has a few problems running some codecs.
In my system I have totem open all of my multimedia files, except for wmv's for which I use gxine.

---

### Post by clb137 on 2005-05-30
[QUOTE=jobezone]pravit, did you execute gst-register-0.8 like explained in [http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs) ?

clb137, Well, the codecs pravit installed (w32codecs) will give him acess to all (or at least the most popular) of the multimedia "formats". These codecs should be acessible by the various linux multimedia applications, like totem+gstreamer, xine, and mplayer. But perhaps since gstreamer isn't yet a 1.0 version, it has a few problems running some codecs.
In my system I have totem open all of my multimedia files, except for wmv's for which I use gxine.[/QUOTE]

HI there,

 thanks for the info,  so far I have foiund that xine plays more foramts with less hassle, it seems everybody has a different way of getting there video formats played.


I think the bigest problem is when folks are trying to run streaming video on the net.  We will have to what for the boy in the programing world to do there stuff.

thanks again

clinton

---

### Post by bored2k on 2005-05-30
[QUOTE=clb137]I think the bigest problem is when folks are trying to run streaming video on the net.  We will have to what for the boy in the programing world to do there stuff.[/QUOTE]
[https://addons.mozilla.org/extensions/moreinfo.php?application=firefox&category=Entertainment&numpg=10&id=446](https://addons.mozilla.org/extensions/moreinfo.php?application=firefox&category=Entertainment&numpg=10&id=446)
THat worked for me and xine :D

---

