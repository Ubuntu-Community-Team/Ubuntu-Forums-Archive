---
title: "How do I get video inside Firefox?"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by pbb on 2006-01-06
Hi, I am using Firefox 1.5 and Totem-xine (Totem-gstreamer didn't play many of my videos).

I now have to download every video and then play it by running it through Totem. I would like to play the online videos inside Firefox. How do I go about doing that?

Thanks, Peter

---

### Post by diggs on 2006-01-06
Install automatix, then run it. it makes life a lot easier, as well as installing lots of programs and what not, as well as all your codecs to watch vids in firefox.

[http://www.ubuntuforums.org/showthread.php?t=66563&highlight=Automatix](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=Automatix)

---

### Post by frodon on 2006-01-06
Just install the media player connectivity extension of firefox, it will launch the embedded video stream with the player of your choice each time you will open a video stream.
Look in the firefox tabs there is a field called extensions ...

---

### Post by pbb on 2006-01-06
[QUOTE=diggs]Install automatix, then run it. it makes life a lot easier, as well as installing lots of programs and what not, as well as all your codecs to watch vids in firefox.[/QUOTE]

Okay, I installed Automatix and I ran it. And then???

I've checked and installed "Mplayer with plugin" and "Media Players". Then I restarted Firefox, and there is **no change**. What should I do?

---

### Post by pbb on 2006-01-06
[QUOTE=frodon]Just install the media player connectivity extension of firefox, it will launch the embedded video stream with the player of your choice each time you will open a video stream.
Look in the firefox tabs there is a field called extensions ...[/QUOTE]

Thanks, I've installed the MediaPlayerConnectivity extension. But still, all inline video's get downloaded first, and then played...

Is it not possible under Linux to play streaming video from within a webpage?

---

### Post by meborc on 2006-01-06
i suggest you uninstall firefox before running automatix and then from automatix install it again with all the plugins... there might be a small mix-up in which version of firexox is installed... and where did the plugins go... and what are you running by clicking the icon... :rolleyes: it is always a good idea to make a clean start> 
Thanks, I've installed the MediaPlayerConnectivity extension. But still, all inline video's get downloaded first, and then played...

Is it not possible under Linux to play streaming video from within a webpage?it is possible, i do it all the time... just get your firefox mess cleared up :)

---

### Post by patrick295767 on 2006-01-06
I installed mplayer 
and [http://mplayerplug-in.sourceforge.net/download.php](http://mplayerplug-in.sourceforge.net/download.php)
with apt-get install ... 
 
To make it...
 
Greetz

---

### Post by frodon on 2006-01-06
[QUOTE=pbb]Thanks, I've installed the MediaPlayerConnectivity extension. But still, all inline video's get downloaded first, and then played...

Is it not possible under Linux to play streaming video from within a webpage?[/QUOTE]Are you sure ? 
because this plugin don't download the videos by itself, you can indeed download the video but it's not an automatic behaviour. You know most of video streams need to be buffered a little bit before starting and the time you have to wait depends on your internet connection and the size of the video.

---

### Post by Deaf_Head on 2006-01-06
I'd also like to know how to do this .. sometimes stuff works inside firefox .. often times it does not. I've got totem-xine and teh plugin installed. I've also got VLC .. 

and automatix is a good idea .. but personally I don't want it. I'd like to know what i'm installing and how to install it .. if I wanted people installing things for me I'd get on windows and visit shady websites.

---

### Post by Zerlinna on 2006-01-06
When you say:

[QUOTE=pbb]Thanks, I've installed the MediaPlayerConnectivity extension. But still, all inline video's get downloaded first, and then played...
[/QUOTE]

Do you mean the videos are still played with totem, or are they played with mplayer but in a new window? 

If it's still with totem, check your plugins. 
1) As URL you type into firefox:  about: plugins
(withouth space before the "p")
There you can see which programs are associated to the file types. 
2) Check your plugin directory (usually: /usr/lib/mozilla-firefox/plugins/): is there still the totem plugin? If yes, remove it! (requires root privileges).

If you want to play *.rpm files it's better to install Reaplayer.

Z.

---

### Post by patrick295767 on 2006-01-06
[QUOTE=Zerlinna]When you say:



Do you mean the videos are still played with totem, or are they played with mplayer but in a new window? 

If it's still with totem, check your plugins. 
1) As URL you type into firefox:  about: plugins
(withouth space before the "p")
There you can see which programs are associated to the file types. 
2) Check your plugin directory (usually: /usr/lib/mozilla-firefox/plugins/): is there still the totem plugin? If yes, remove it! (requires root privileges).

If you want to play *.rpm files it's better to install Reaplayer.

Z.[/QUOTE]
  
Btw, if you managed to install realplayer... 
Let us also know how ...
apt-get -f install realplayer
  ask you to downlaod stgh, then do apt-get -f install realplayer... 
not so easy life ... 

thank you

---

### Post by pbb on 2006-01-06
[QUOTE=frodon]Are you sure ? 
because this plugin don't download the videos by itself, you can indeed download the video but it's not an automatic behaviour. You know most of video streams need to be buffered a little bit before starting and the time you have to wait depends on your internet connection and the size of the video.[/QUOTE]

Yes. But trying out a bit more, I see the situation gets complicated.

After installing MediaPlayerConnectivity, when I come to a page with an embedded video (mostly WMV), I see that the video-area is replaced by a black area with a small gray video-icon in the middle.
Automatically at the same time, a "You have choosen to open..." dialog pops up. This is the standard download-dialog of Firefox. It suggests to open the file with Totem. When I do that, the complete file starts downloading in the standard Firefox way, and after downloading the file is opened in Totem. Thus, no streaming.
However, I also noticed now that if I cancel the download-dialog, and click on the black square, MPlayer is started with an error dialog "Couldn't resolve name for AF_INET6". When I click this dialog away, my video does start streamed playing.

So, now I am left with three new questions.
* How can I get the video to automatically start streamed playback instead of opening the download dialog?
* How do I prevent this error that MPlayer shows?
* Is MPlayer the only player that supports streamed playback? I would prefer using Totem if possible, is has a much better interface. Of course, if MPlayer is technically superior then I should use that.

That's Linux for you... Getting an answer to what seemed a simple question, makes you come up with three new questions... ;)

---

### Post by pbb on 2006-01-06
[QUOTE=meborc]i suggest you uninstall firefox before running automatix and then from automatix install it again with all the plugins...[/QUOTE]

I understand the idea that Automatix contains all elements optimized for usage together, but I really don't like the idea of these automatic installers.

I already have a non-functional Opera icon now, thanks to Automatix, and the menu-item "Install Firefox 1.5 with **all extensions**" gives me goosebumbs. (There must be many hundreds of extensions available for firefox, and even if it were only a selection of extensions that gets installed, I would really like to choose them myself.)

---

### Post by frodon on 2006-01-06
[QUOTE=pbb]So, now I am left with three new questions.
* How can I get the video to automatically start streamed playback instead of opening the download dialog?
* How do I prevent this error that MPlayer shows?
* Is MPlayer the only player that supports streamed playback? I would prefer using Totem if possible, is has a much better interface. Of course, if MPlayer is technically superior then I should use that.

That's Linux for you... Getting an answer to what seemed a simple question, makes you come up with three new questions... ;)[/QUOTE]

In the same tab where you found the "extension" field you will find a field for media player connectivity configuration, so you will be able to choose the player you want for each format.
I don't know if it's possible to open the stream automaticaly, in my case i have a "play" icon in the middle of the black box and all i have to do is to click on this icon to open the stream, it's not such a pain ;)

So go in the configuration window of media player connectivity and you may find what you're looking for.

---

### Post by pbb on 2006-01-06
[QUOTE=Deaf_Head]I'd also like to know how to do this .. sometimes stuff works inside firefox .. often times it does not. I've got totem-xine and teh plugin installed. I've also got VLC .. 

and automatix is a good idea .. but personally I don't want it. I'd like to know what i'm installing and how to install it .. if I wanted people installing things for me I'd get on windows and visit shady websites.[/QUOTE]

You speak about "the plugin", do you mean MediaPlayerConnectivity, or a Totem-plugin?

I totally agree with your point on Automatix. If I'd want to use those one-click installers, I wouldn't have Firefox 1.5 now because Synaptic only offers 1.0.7. And for installing Automatix you need to use apt-get, so after that you already know how to install applications "the hard way". I'd much rather see a list of locations for all those packages and instructions on how to install them...

---

### Post by deNoobius on 2006-01-06
You have to use the mplayer plugin with FF 1.5 to get in-line videos.  I don't think totem-xine will work, and in fact, I believe you're supposed to remove it and use mplayer if you want in-line videos.  That's what I did, and it works well.  

See this:


[http://www.ubuntuforums.org/showthread.php?t=76946&highlight=firefox+1.5](http://www.ubuntuforums.org/showthread.php?t=76946&highlight=firefox+1.5)

---

### Post by Zerlinna on 2006-01-06
[QUOTE=patrick295767]Btw, if you managed to install realplayer... 
Let us also know how ...
apt-get -f install realplayer
  ask you to downlaod stgh, then do apt-get -f install realplayer... 
not so easy life ... 

thank you[/QUOTE]

I didn't install realplayer with apt-get. 

I've downloaded the .bin file from [here]("http://www.real.com/linux?pcode=rn&src=freeplayer_partner&opage=freeplayer_partner"). 
Then: 
chmod 777 RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin

And if you have mplayer associated to the rpm-files (check with: about: plugins), do also: 

cd /usr/lib/mozilla-firefox/plugins
sudo mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla-firefox/components
sudo mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup

cd /usr/lib/mozilla/plugins
sudo mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla/components
sudo mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup

(You can find the whole setup-guide for firefox in my blog [here]("http://zerlinna.blogspot.com/2005/10/setting-up-firefox-i-iii.html") and [here]("http://zerlinna.blogspot.com/2005/10/setting-up-firefox-iv-and-v.html"))

---

### Post by patrick295767 on 2006-01-06
[QUOTE=Zerlinna]I didn't install realplayer with apt-get. 

I've downloaded the .bin file from [here]("http://www.real.com/linux?pcode=rn&src=freeplayer_partner&opage=freeplayer_partner"). 
Then: 
chmod 777 RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin

And if you have mplayer associated to the rpm-files (check with: about: plugins), do also: 

cd /usr/lib/mozilla-firefox/plugins
sudo mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla-firefox/components
sudo mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup

cd /usr/lib/mozilla/plugins
sudo mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla/components
sudo mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup

(You can find the whole setup-guide for firefox in my blog [here]("http://zerlinna.blogspot.com/2005/10/setting-up-firefox-i-iii.html") and [here]("http://zerlinna.blogspot.com/2005/10/setting-up-firefox-iv-and-v.html"))[/QUOTE]
  
Thank a lot a lot !! I'll try tonight !
  
Concerning the wmv, with w32codecs installed, the code :
```
apt-get -f install mplayerplug-in
```
gives the possibility of streaming some media player web site... 
(I guess)
not the mms://... 
(I am not expert).
  
That helped me to watch my TV news program every day :-) in mozilla-frfx !
On other hand, the full screen is not workign (mplayer) :-(

.. 
Greetz

---

### Post by Zerlinna on 2006-01-06
[QUOTE=patrick295767]Thank a lot a lot !! I'll try tonight ![/QUOTE]

You're welcome! :-)
  

[QUOTE=patrick295767]
That helped me to watch my TV news program every day :-) in mozilla-frfx !
On other hand, the full screen is not workign (mplayer) :-(
Greetz[/QUOTE]

Hihi.. I have also a howto for mplayer-plugin if you want to try it out (codecs with apt-get, mplayer-plugin from sourceforge) -- full screen works like a charm :-)

---

### Post by pbb on 2006-01-06
[QUOTE=frodon]In the same tab where you found the "extension" field you will find a field for media player connectivity configuration, so you will be able to choose the player you want for each format.
I don't know if it's possible to open the stream automaticaly, in my case i have a "play" icon in the middle of the black box and all i have to do is to click on this icon to open the stream, it's not such a pain ;)

So go in the configuration window of media player connectivity and you may find what you're looking for.[/QUOTE]

I don't know which "extension field" you are talking about here, but I found the configuration for MediaPlayerConnectivity, and I changed the setting for Windows Media from "/usr/bin/X11/gmplayer" to "/usr/bin/X11/totem". However, when I click the "play" icon now, Totem opens up but without any video! Can I make it load the video clicked?

Also, I noticed that when I start up Totem by itself, and then go Movie > Open Location, and enter the URL of the WMV file, nothing happens at all.

Which brings back the question, is Totem able to play streaming WMV at all? It's the only program I found that is able to play WMV from harddisk without heavy jerking (especially MPlayer does that).

And do you have any ideas about the Download- and Error-dialogs I get in the process?

---

### Post by frodon on 2006-01-06
I also like totem but like you it doesn't work with media player connectivity however i have no problem using xine (xine-ui package), my setting is : "/usr/bin/X11/xine"
In all the cases you will need w32codecs installed to play wmv files.

No idea about the Download- and Error-dialogs you get in the process, sorry i can't help you more on this point.

---

### Post by pbb on 2006-01-06
I've got the w32codecs installed.

Now I notice that on some other sites, the WMVs stream fine in Totem together with MediaPlayerConnect.

Getting very tired of non-constant problems. Time to focus on other problems again, else I will go crazy...

---

### Post by Mustard on 2006-01-06
Doesn't the mozplugger package embed totem into firefox?

```
mustard@slave:/var/log$ apt-cache show mozplugger
Package: mozplugger
Priority: optional
Section: universe/web
Installed-Size: 192
Maintainer: Bernard Blackham <bernard@blackham.com.au>
Architecture: i386
Version: 1.7.1-1
Replaces: plugger (<= 4.1)
Depends: m4, libc6 (>= 2.3.4-1), libx11-6 | xlibs (>> 4.1.0)
Recommends: mozilla-browser | mozilla-browser-snapshot | mozilla-browser-cvs | mozilla-firefox
Conflicts: plugger (<= 4.1)
Filename: pool/universe/m/mozplugger/mozplugger_1.7.1-1_i386.deb
Size: 45354
MD5sum: 8981b404c7aa8953de7ae5ca57f465f3
Description: Plugin allowing external viewers to be launched inside Mozilla
 mozplugger allows you to seamlessly integrate external applications
 to view files downloaded from the web that Mozilla can not normally
 handle. The application is embedded within a Mozilla window as to act
 like and feel like a true plugin.
 .
 This allows to you view PDFs, Postscript files, animations and
 movies, amongst other file types all from within Mozilla (with
 supporting applications).
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

I'm on dialup so I don't actually do a lot of streaming on the internet, so i could be wrong. :)

---

### Post by patrick295767 on 2006-01-07
For this website : [http://www.reality.be/webcam/](http://www.reality.be/webcam/)
  
Is it possible to make realplayer working ??
  
I try to start realplayer ok, and copy the link location real into realplayer, and nothg happen ... 
  
Concerning the windows media player, nothg is working either ...
  
Please could someone help me ?
  
Thank you !
  
Pat'

---

### Post by patrick295767 on 2006-01-07
Additional problem: 
  
In bbc online, u can watch news and so on:
I have into mozilla firefox the realplayer started into it , but nothing happen 
u can select normal, medium and full size of the window , but no movie visible ...
Nothing happen 

Help !

---

### Post by Zerlinna on 2006-01-07
After posting my reply (see below) I noticed that according to your profile, you're using Ubuntu Hoary. If you don't use Breezy [my guide]("http://zerlinna.blogspot.com/2005/10/setting-up-firefox-iv-and-v.html") probably won't help you, sorry. But at least you can check if your realplayer / mplayer is generally not working, or if it's only on some sites. 

[QUOTE=patrick295767]Additional problem: 
In bbc online, u can watch news and so on:
I have into mozilla firefox the realplayer started into it , but nothing happen 
u can select normal, medium and full size of the window , but no movie visible ...
Nothing happen 
Help ![/QUOTE]

Can you watch this video: [http://news.bbc.co.uk/nolavconsole/ifs_news/hi/nb_wm_fs.stm?nbram=1&news=1&nbwm=1&bbwm=1&bbram=1&nol_storyid=4589954](http://news.bbc.co.uk/nolavconsole/ifs_news/hi/nb_wm_fs.stm?nbram=1&news=1&nbwm=1&bbwm=1&bbram=1&nol_storyid=4589954) ?
You need to wait some minutes (I suppose you have a fast internet connection)
What about that one:
[http://jt.france2.fr/8h/](http://jt.france2.fr/8h/)

Those work fine for me. The site you've given ([http://www.reality.be/webcam/](http://www.reality.be/webcam/)) doesn't work for me neither (nor does it for my bf using fedora, but I know that my and his realplayer are working fine). Is your realplayer working generally and is it only the 'reality' site which is not working?  
You can check this simply here: [http://www.cinemovies.fr/fiche_multimedia.php?IDfilm=1348](http://www.cinemovies.fr/fiche_multimedia.php?IDfilm=1348)  - choose "real basse res." - for me this video works fine. 

So.. is it just on that 'reality' site that you have problems or is your mplayer /realplayer not working in general? 

How did you install mplayer/realplayer?

Z.

---

### Post by patrick295767 on 2006-01-07
(I am with hoary on 2 pc's)
I checked, and you were right :
[QUOTE=Zerlinna]
Can you watch this video: [http://news.bbc.co.uk/nolavconsole/ifs_news/hi/nb_wm_fs.stm?nbram=1&news=1&nbwm=1&bbwm=1&bbram=1&nol_storyid=4589954](http://news.bbc.co.uk/nolavconsole/ifs_news/hi/nb_wm_fs.stm?nbram=1&news=1&nbwm=1&bbwm=1&bbram=1&nol_storyid=4589954) ?
You need to wait some minutes (I suppose you have a fast internet connection)
What about that one:
[http://jt.france2.fr/8h/](http://jt.france2.fr/8h/)
[/QUOTE] are working great ! :-)
(they are mms:// ... based )

the realplayer is working with videos. For remote location (copy paste from firefox), in realplayer external of firefox, it's not working.
For the site [  ]("http://beelinetv.com/"), the polish 3 links are not working for instance. 
   
> [http://www.cinemovies.fr/fiche_multimedia.php?IDfilm=1348](http://www.cinemovies.fr/fiche_multimedia.php?IDfilm=1348)  - choose "real basse res." - for me this video works fine. 
  
> ```
Those work fine for me. The site you've given ([http://www.reality.be/webcam/](http://www.reality.be/webcam/)) doesn't work for me neither (nor does it for my bf using fedora, but I know that my and his realplayer are working fine). Is your realplayer working generally and is it only the 'reality' site which is not working?  
```  is also working fine for me !! :-) 



So.. is it just on that 'reality' site that you have problems or is your mplayer /realplayer not working in general? 

How did you install mplayer/realplayer?

  I installed mplayer with : 
```
apt-get -f install mplayer-i386
apt-get -f install mplayerplug-in
```

and for the realplayer, I used: 
```
##chmod 777 /home/nfs_work/RealPlayer10GOLD.bin
##sudo ./RealPlayer10GOLD.bin

##And if you have mplayer associated to the rpm-files (check with: about: plugins), do also:

cd /usr/lib/mozilla-firefox/plugins
sudo mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla-firefox/components
sudo mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup

cd /usr/lib/mozilla/plugins
sudo mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla/components
sudo mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup
```
  
  
What's pitty is that for instance, pages like this one : 
  [http://beelinetv.com/]("http://beelinetv.com/")
Is not working
    
 [http://www.radiofrance.fr/chaines/france-info/accueil/]("http://www.radiofrance.fr/chaines/france-info/accueil/")
try this one: "ecouter le direct"
It works for you ?
  
U know if with breezy, it'll be better for our troubles ?
  
Thank you very much,

Patrick

---

### Post by patrick295767 on 2006-01-07
Funny, this one [http://www.radiofrance.fr/chaines/france-info/accueil/](http://www.radiofrance.fr/chaines/france-info/accueil/)
("ecouter le direct") works with mozilla but not mozilla-firefox (if  realplayer is installed).
  
Very strange anyhow
  
I'll try now there with mozilla:
no changes, this page: [http://beelinetv.com/](http://beelinetv.com/)
is not working with mms media or real... 
shitty, isnt it
  
Greetz

---

### Post by patrick295767 on 2006-01-07
I did : 
```
apt-get -f install totem-xine
apt-get -f install mozplugger
```
  
Results are pretty good , very  improved !! 
But the polish are still not working ... :-(

---

### Post by Zerlinna on 2006-01-07
I really don't like totem so I can't help you for that one, sorry. 

For the [http://beelinetv.com/](http://beelinetv.com/) site: I can watch every http stream (realplay AND mediaplayer) - but NOT the rtsp: and the mms: - then my firefox still tries to open totem (grmpf). Maybe one could change this with about:config but I can't figure out how to get it working... 
"ecouter le direct" from france info works fine (though the connection is very lame) - but it has nothing to do with your reaplayer (on my firefoy mplayerplugin is opening the stream, not reaplayer!). 

If  france info worked with mozilla but not with mozilla-firefox you should have a look into the plugin folders: is the content of: /usr/lib/mozilla-firefox/plugins and  /usr/lib/mozilla/plugins exactly the same? It should! If you have different plugins there it will cause you very (not so) funny problems.

> U know if with breezy, it'll be better for our troubles ?

I know that when I had hoary I managed get things to work, too. I think I did with the [ubuntuguide]("http://www.ubuntuguide.org/#mplayer") but I'm not quite sure - I remember I had problems, too.
With breezy the whole plugin-thing is still painfull, but I got almost everything working (except the rtsp / mms thing - but this doesn't seem to be a ubuntu specific problem) and you could try Automatix - if it's not working you could still try out [my guide]("http://zerlinna.blogspot.com/2005/10/setting-up-firefox-iv-and-v.html") ;-) 
For the rest I really enjoy breezy and I'm already looking forward to Dapper.. because every release is just really better than the older one.

Z.

---

### Post by Zerlinna on 2006-01-07
Heehee... I got a solution for the mms: problem we had e.g. on [http://beelinetv.com/](http://beelinetv.com/).

Ok, it's not a REAL solution. Meaning: I didn't find a way to make the videos work inside firefox. And I only got one for the mms: files (not for the rtsp:)


But if you want to watch the videos, you just rightclick on the link, let's say on "NTD TV, China Media" and you copy the link. Then open your konsole and type: >  mplayer mms:restofurl (in this case it would be: mplayer mms://online.ntdtvcast.com/Stream-Live ). 
The rtsp should work the same way with realplayer, but I only get sound and no picture. Hm. 

**UPDATE:** I've found a better solution. It still won't play inside firefox, but it's a way to get the mms: working with mplayer (I've read that totem can't handle them) without the konsole. 

> Type as url into firefox: about:config
Then rightclick --> new --> string --> type : network.protocol-handler.app.mms 
then type: mplayer
Again rightlick --> new --> boolean --> type: network.protocol-handler.external.mms --> true

Restart your firefox. Now firefox will give you a popup: open with mplayer. Click yes, wait some seconds (it takes longer than you'll expect), and you'll have a nice little mplayer window with your stream :-)

I hope this helps you a bit, Z.

---

### Post by patrick295767 on 2006-01-07
I installed : 
```
apt-get -f install totem-xine
apt-get -f install mozplugger
```
=> improvemnt for this [http://beelinetv.com/](http://beelinetv.com/)
  
[http://beelinetv.com/](http://beelinetv.com/)
I tried all posbilities for the  polish tv online... 
mplayer mms://stuffs... 
 not working
I really have no idea now to make it work this polish tv's ... 
Would you eventually know ?
  
(totem-xine installation helped me for usa tv )
  
Thank you very much for progressing & investigating in the same direction 

Greetz, 

Pat'

---

### Post by Zerlinna on 2006-01-07
Hmmm, I don't know, did you do the following? I'm trying to be more clear on this one because I'm not sure if my post was clear enough. 
( I took the examples from the [http://beelinetv.com/](http://beelinetv.com/) site)

As far as we stated
[I]
The firefox-plugins work for[/I]
http: (e.g. usa 10TV Newsbreak)
[I]
The firefox-plugins seem not to work for[/I]
mms: (e.g. NTD TV, China) 
rtsp: (e.g. NJTV-2, China)
[B]
How can we make mms: and rtsp: work? [/B]
Not with totem! But:
[B]
mms: [/B]
If you have mplayer installed (not the firefox plugin, but the program itself:sudo apt-get install mplayer) do the following.
Open firefox.
Set as url: about:config
Rightclick in the main window --> new --> string --> network.protocol-handler.app.mms --> mplayer
Rightclick in the main window --> new --> boolean --> network.protocol-handler.external.mms --> true
Close and restart firefox. 
[B]
rtsp: [/B]
You have to have Realplayer installed for that (again not the plugin). 
Open firefox.
Set as url: about:config
Rightclick in the main window -->new --> string --> network.protocol-handler.app.rtsp --> /usr/bin/X11/realplay
Rightclick in the main window --> new --> boolean --> network.protocol-handler.external.rtsp --> true
Close and restart firefox.

For me, mms works fine now, but with rtsp I get only sound no pictures, but I think it could be a specific problem with my realplayer. (For rtsp see also: [https://bugzilla.mozilla.org/show_bug.cgi?id=202715](https://bugzilla.mozilla.org/show_bug.cgi?id=202715)) 

So.. enough for today, I'm off to bed.. 

Good night,

Z.

---

### Post by patrick295767 on 2006-01-09
Thnak you very much,
 
I'll try tonight !

 Greetings, 

Patrick

---

