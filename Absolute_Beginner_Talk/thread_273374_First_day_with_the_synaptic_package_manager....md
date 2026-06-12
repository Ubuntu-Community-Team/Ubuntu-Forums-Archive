---
title: "First day with the synaptic package manager..."
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-07
This is my first day on Linux/Xubuntu and so far I'm pretty confused. I like the feel of the OS so far, but I don't really know if I'm adding packages correctly. I've tried to add wine, so I can use utorrent and filezilla which I'm used too and like, and everytime I install wine form the synaptic manager or the add+ on the wine download page, I can't figure out why it's not installing. Is it because I have xfce xubuntu, and not ubuntu?

I also installed some games and they didn't show up in my games area, and some did.

Also, when I've downloaded from Firefox's download manager to a file,/home/me/Download Manager/..., I'm not being able to open files like icons for my xfce desktop. and I've also had trouble with the plug-ins for java and flash.

I've read a few manuals and I think I need some sort of other instructions or maybe a good beginner page for software packages and instructions for how to load them and explanations of the regular procedure. And I've been a little nervous about trying terminal for the first time, any suggestions?

I'm going to read the forums here some more and a few more wiki pages and whatever else I can find to help me learn.

Also, should I have the gnome desktop to run certain programs? ...And does the ubuntu "edgy eft" and "dapper" come with media support ready plug ins for videos and music files of different types. I already down loaded these plug-ins from the synaptic manager for xfce:

gstreamer0.10-plugins-ugly 
gstreamer0.10-ffmpeg 
gstreamer0.10-gl 
gstreamer0.10-plugins-base 
gstreamer0.10-plugins-good 
gstreamer0.10-plugins-ugly-multiverse 
libxine-extracodecs 
ffmpeg 
lame 
faad 
sox 
mjpegtools 
libxine-main1

and I'm wondering if there was another page like in the xubuntu desk top guide that has a list of what is needed to start a new linux xubuntu xfce user off.

Last question, is xubuntu to bare bones for a novice, would regular gnome ubuntu be easier to learn on?

---

### Post by jordanmthomas on 2006-10-07
Any commands you come across should, for the most part, work without trouble on your xfce install.  

1.  Some games don't get installed in the menu.  Search Synaptic for a package called 'menu'  This will give you a Debian option in the Applications menu that gets a lot more of the games than usual

2.  I'm not sure about your Firefox problem.  Maybe you should set Firefox to save to your Desktop by default?  The java and flash plugins won't just install like in Windows.  Look at [http://www.ubuntuguide.org](http://www.ubuntuguide.org) for how to get them going.

3.  Don't be nervous about the terminal.  Just use a couple of copy and paste places (like ubuntuguide) and take note of what's going on.  You'll catch on in no time.

4.  Edgy Eft doesn't come with any more media support than Dapper Drake.

5.  Xubuntu should be plenty easy to learn on.  The only trouble you may have is some of the guides will tell you to click certain places, and you'll have to translate that over to xfce clicks...not really difficult.

Have fun!

---

### Post by crimesaucer on 2006-10-07
Thank you, and I'll read that link. 

Does anyone have a list of comparable packages like media players and FTP clients that are popular?

And also, I read that bit torrent is really slow on ubuntu/xubuntu, would wine and utorrent make it as fast as I have it on windows, or would using my utorrent on my dual booted XP just be better cause I have all of my preferences set perfectly and it is pretty fast. Could I get equal download rates on xubuntu?

thanks again,
-c.

---

### Post by jordanmthomas on 2006-10-07
torrents on my ubuntu are plenty fast.  (when I'm at home at least, they won't work at school :( )

I don't have a list handy for you, but I can say that the most popular media players are
```
amarok
xmms
beep media player (bmp)
Rhythmbox
Banshee
Listen
and it's not popular, but nice:  Exaile!

```

The only FTP client I know is GFTP, but I don't ever use any anyway.  Look around, there are such lists.

Also, you asked about installing software:  Here is something else you may want to read if you have the time
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

**edit** amarok is god

---

### Post by b_martinez on 2006-10-07
> **crimesaucer said:**
> This is my first day on Linux/Xubuntu and so far I'm pretty confused. I like the feel of the OS so far, but I don't really know if I'm adding packages correctly. I've tried to add wine, so I can use utorrent and filezilla which I'm used too and like, and everytime I install wine form the synaptic manager or the add+ on the wine download page, I can't figure out why it's not installing. Is it because I have xfce xubuntu, and not ubuntu?

I also installed some games and they didn't show up in my games area, and some did.

Also, when I've downloaded from Firefox's download manager to a file,/home/me/Download Manager/..., I'm not being able to open files like icons for my xfce desktop. and I've also had trouble with the plug-ins for java and flash.

I've read a few manuals and I think I need some sort of other instructions or maybe a good beginner page for software packages and instructions for how to load them and explanations of the regular procedure. And I've been a little nervous about trying terminal for the first time, any suggestions?

I'm going to read the forums here some more and a few more wiki pages and whatever else I can find to help me learn.

Also, should I have the gnome desktop to run certain programs? ...And does the ubuntu "edgy eft" and "dapper" come with media support ready plug ins for videos and music files of different types. I already down loaded these plug-ins from the synaptic manager for xfce:

gstreamer0.10-plugins-ugly 
gstreamer0.10-ffmpeg 
gstreamer0.10-gl 
gstreamer0.10-plugins-base 
gstreamer0.10-plugins-good 
gstreamer0.10-plugins-ugly-multiverse 
libxine-extracodecs 
ffmpeg 
lame 
faad 
sox 
mjpegtools 
libxine-main1

and I'm wondering if there was another page like in the xubuntu desk top guide that has a list of what is needed to start a new linux xubuntu xfce user off.

Last question, is xubuntu to bare bones for a novice, would regular gnome ubuntu be easier to learn on?



From what I have read so far, I personally think you should install Ubuntu desktop. Open a terminal and type in 

sudo aptitude install ubuntu desktop 
[enter your user password when you see the password prompt]

To open a terminal in XFCE just right click on an open area of the screen and select terminal.
This will stop you from having to install all over again. 
As to your questions, yes, Xubuntu is a very minimal desktop, best suited to low end systems and experienced users. Notice I wrote ..."and experienced users." 
 Dapper drake does not come with pre-installed codecs, I don't think any of them do.
 Open 'file manager' in XFCE to see your files. Downloaded and system istalled.
The games may need to be opened in a terminal to run. Or you may just need to open a terminal and 

sudo updatedb
[password]

to update data base and let the system 'see' the changes.
  If you do not mind the frustration of stumbling in the dark, XFCE is a wonderful desktop. BUT, you are now trying to learn a new operating system AND a new way of using it, on top of a new desktop's way of doing things.
  If you have a computer that has at least a 500MHz processor, and 256Mb ram, go to Ubuntu, or Kubuntu, because they are more point-and-click and thus, easier to get used to.
As far as a learners manual, I haven't looked for one, but you may get an answer to that if you wait for a bit.
Bill

---

### Post by crimesaucer on 2006-10-08
Thanks again,

I have a new question:

I seem to have no volume and mute right now, also I have no wifi antenna connection but I haven't tried to find out how to install that yet...so is there a page for all of the regular questions like that, cause I'm sure every new user goes through the same thing.

Thanks and I'll check those links you posted,
-c.

A question to Bill's post above: So, If I download the ubuntu desk top, then I'll have both of the desk tops, to choose from, and all of the plugins from the ubuntu, or will the xubuntu OS just turn into ubuntu OS?

Thanks again for all of the responses

---

### Post by Ogre_Army on 2007-04-14
Alright! I am new to ubuntu as well but i have spent the last 3 weeks fixing and breaking things haha. I think i know the basics you need to do for your wireless card. get the information about your wireless card. All of the information. Then i reccomend wifi radar. but with all of that search in google and you should find a how to. just type <wireless card info> <ubuntu edition> how to help. and that should find you a nice little tutorial.

---

### Post by an4rew on 2007-04-14
you need to get online via a wired connection get wpa supplicant and network manager-gnome in synaptic.

---

### Post by crimesaucer on 2007-04-15
All of these issues were fixed back in October 2006. This was one of my first posts from my first day on xubuntu. Thanks anyway.

And I do recommend wifi radar for wifi, and Audacious for a simple media player that uses skins.

---

### Post by jeduan on 2007-04-16
Just in case, filezilla is in the repos

---

### Post by hyper_ch on 2007-04-16
Oh well, I don't consider Xfce as easy or as difficult as Gnome or KDE... each one is specific on your own and Xfce is tailored towars lower end machines than Gnome or KDE.
I could run Gnome or KDE without problems but too many things are added there that I really don't need.

If you have a lot of questions about *ubuntu then it's probably a good idea to use IRC and ask directly there.

IRC Server:  irc.freenode.org
Channles:  #xubuntu and/or #ubuntu and/or #kubuntu

---

### Post by crimesaucer on 2007-04-16
Thanks to the many people on this forum and their help for beginners, I had solved all of my "newb" first-day-issues back in October when I had started this thread. 

But it is nice to hear about Filezilla finally being in the repos. 

I used to love that app, but had switched to FireFTP since moving to xubuntu a little over 6 months ago.

I might install Filezilla now because it seems a little better then FireFTP, all though FireFTP does work ok.

Thanks, but for me this thread has been done for a while. I've basically learned everything I needed to know about terminal, and how to install what I needed from the wiki page. I also stayed with xubuntu and learned Linux using XFCE, and even though it was a little more difficult then learning on ubuntu, I would still recommend it because of how fast it is, and for how easy it is to customize your OS. I found out that the xfce-engine is really easy to write a custom gtkrc for.

This is my original gtkrc that I wrote called Xfce-rusty_charcoal_b. You can find my gtkrc in the ubuntu gallery, along with 5 others that I wrote. The Emerald theme is also my original theme and a couple of variations of it can be found on the Beryl site. Audacious is in our repos, or at least the older version is, and the Ecowlizer Mooamp skin is on the xmms skin page. My Thunderbird and Firefox are themed in the default mode to use my gtkrc theme, and if you want to use my gtkrc themes, then you will need the package called gtk2-engines-xfce. (I also substituted the Cylence:Obsidian icons into the Firefox Classic Skin that is default)

This is my current desktop:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-18-8.png[/IMG]

---

### Post by crimesaucer on 2007-04-16
I also wanted to comment that XFCE works really nicely on new machines too. It's a lot faster then ubuntu edgy was for me, and I think it shouldn't always be considered to be "only for older slower computers".

I plan on using XFCE for any distro and for any computer because it has been so lightning fast on my hp pavillion dv4230us. I also like the fact that once I got to know it, it's Thunar file system is very simple. Plus the new final release of XFCE4.4 looks like it should have improved on the XFCE4.3.99.1 (XFCE Beta2) that I have been using.

I have been waiting for the xubuntu 7.04 RC or the stable final version to upgrade.

---

