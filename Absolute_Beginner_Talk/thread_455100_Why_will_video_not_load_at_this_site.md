---
title: "Why will video not load at this site ?"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2007-05-26
Why will the video not load and play on my home computer Feisty/firefox installation like it does on my work XP/IE computer at this site ?  

What software is required to play this video that I do not have loaded on my Feisty installation and yes, I do have both FlashPlayer & RealPlayer installed.

[http://abc.go.com/primetime/nationalbingonight/](http://abc.go.com/primetime/nationalbingonight/)

Thanks.

---

### Post by Dzenhax on 2007-05-26
I know you have to have gstreamer to play a lot of video and audio files in protected formats.  If you can already play DVDs and MP3 files then you probably have it loaded.  If not, that could be part of the problem.

Does'nt play on mine either, but I don't have flash player.

---

### Post by wpshooter on 2007-05-26
When I search gstreamer in Synaptic, I see that there are a few of the gstreamer programs that were apparently installed by default during the O/S install (because I know I did not install them) BUT there are a large number of programs that begin with gstreamer that are NOT marked as being installed.

How do I know if any of those unchecked programs are supposed to/need to be installed ?

Thanks.

---

### Post by Dzenhax on 2007-05-26
K

Here is the safe list.  It's long.  I will exclude what Ubuntu loads on it's own, so don' uncheck any of those.

gstreamer0.10-ffmpeg
gstreamer0.10-g1
gstreamer0.10-pitfdll
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.8-dv
gstreamer0.8-dvd
gstreamer0.8-faac
gstreamer0.8-faad
gstreamer0.8-flac
gstreamer0.8-lame
gstreamer0.8-mad
gstreamer0.8-misc
gstreamer0.8-mpeg2dec
gstreamer0.8-musepack
gstreamer0.8-speex
gstreamer0.8-swfdec
gstreamer0.8-vorbis
gstreamer0.8-xvid

I do not claim to have spelled all these correctly.  If I'm a letter or two off sorry.  Lousy typer.  
Disclaimer:  I got this list from Ubuntu Linux Bible (William von Hagen) just to cover my plagery insurance.

Ya gotta have the restricted, multiverse repositories enabled in synaptic.

---

### Post by wpshooter on 2007-05-26
You say SAFE list.

Does that imply that there are some that it is NOT safe to install ???

Thanks.

---

### Post by Dzenhax on 2007-05-26
Nah,

     What that means is that this is more packages than you probably need.  But you if you use this list, then you won't be back here later when something else doesn't work, cause you'll already have the package installed.

---

### Post by wpshooter on 2007-05-26
Thanks.

---

### Post by Dzenhax on 2007-05-26
Please let me know if this fixes it.  I'm curious it that's the problem or not.

and you're welcome.

---

### Post by srt4play on 2007-05-26
It doesn't play on my machine either.  I don't think you're going to have much luck getting it to play.

---

### Post by wpshooter on 2007-05-26
I installed all of the gstreamer files and that did NOT make it work !!!

Any other suggestions ?

---

### Post by Dzenhax on 2007-05-26
If you can find out what format the video on the page is using (maybe use view source in your browser) then you can research how to view that format.  What I gave you should work for most formats.  Sorry I couldn't help more.  In any case you should be set for most multimedia with the packages you did install, so won't have to worry about that later.

---

### Post by Dzenhax on 2007-05-26
New idea,

try installing the windows codecs

wget -c -P /tmp/ [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb)

should all be on one line.

got that from here:

[http://www.cs.cornell.edu/~djm/ubuntu/#multimedia](http://www.cs.cornell.edu/~djm/ubuntu/#multimedia)

Looks like alot of great stuff.

---

### Post by ronmarley1 on 2007-05-26
It's a Flash video.  I have Flash installed, but it does not play for me either.

---

### Post by H.E. Pennypacker on 2007-05-26
Same here.  I have Flash installed, but video won't play.  No ABC owned websites work for me (that includes ABC News).

---

### Post by wormser on 2007-05-26
Has anybody gotten it to work?  I think ABC has a new plugin that is only available for Mac and Windows.  If you have one of those systems check to see if a new plugin is required  to view.  I know to watch there TV episodes you have to download a plugin from [MoveNetworks]("http://www.movenetworks.com/").

---

### Post by Dzenhax on 2007-05-26
Someone posted and said this fixed it for him.

[http://ubuntuos.wordpress.com/2006/08/01/howto-play-windows-media-video-wmv-in-ubuntu/](http://ubuntuos.wordpress.com/2006/08/01/howto-play-windows-media-video-wmv-in-ubuntu/)

Let us all know.  I am really curious now.

---

### Post by Happy_Man on 2007-05-26
Mine worked out of the box. This may or may not be due to me using Konq to play it though.....

And besides, dzenhax, it's a .flv.

---

### Post by Dzenhax on 2007-05-26
Weird.

     I can play .flv s.  I took a look at the source to see if I could find where the vid comes from but I'm not an html or java script guy.

   Youtube uses .flv and they come out fine too.

I give up.  If anybody figures it out....

---

### Post by mgmiller on 2007-05-26
I also found none of abc videos play any more.  They appear to be flash, but with some proprietary twist that won't work in Linux.  I went to here:  [http://abc.go.com/fsp/index.html?channel=UglyBetty&clip=119634]("http://abc.go.com/fsp/index.html?channel=UglyBetty&clip=119634")
and then clicked where it said click here to watch a full episode.  You will get an "Oops, you have the wrong browser/OS message.  on the lower right is a Feedback button.  I clicked that and gave them a piece of my mind.  You should too.  Keep it clean and to the point.  I mentioned that fox.com still allows non windows/mac people to view from their site.  I also mentioned Dell now selling new ubuntu comps and none of these new customers will be able to view their site either.  I also mentioned that there are more Linux users than Mac users.  Feel free to add whatever else you can think of, but keep it factual.  Flaming them won't get us anywhere.  Remember, you can catch more flies with honey than with vinegar.

---

### Post by matchstich on 2007-05-27
mgmiller, i just went there. i have flash installed and the site is asking me to install flash.

i've noticed that i can't view videos in msn, and  yahoo anymore.

they both changed something on thier sites

---

### Post by wpshooter on 2007-05-27
If someone finds the correct solution to this, would appreciate it if you would post the answer on this thread.

Thanks.

---

### Post by jimbob on 2007-05-27
Country music site cmt.com is the same way.  They have at least two filters you must get past.
First they check your OS and if it is Linux give you some gobblygook about being sorry but DRM won't let them play on Linux.  If I use UserAgentSwitcher and set it to ex pee with IE I get by that filter but then they check some location they think is in IE for Flash and don't find it - telling you you need to download and install Flash 8.  I have Flash 9 installed but they don't know where to look for it in Linux.
What a lot of crap!
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by wpshooter on 2007-05-27
Is this a conspiracy or does Linux just need to let the people that are doing this programming, that these sites, etc. are not working for people that are using Linux workstations ?  

OR is this a case wherein that the programs that are being used by Linux computer, i.e. Firefox, etc. or the entire O/Ss need to be conformed to the way that these programs are being written ?

Thanks.

---

### Post by Detonate on 2007-05-27
I wrote an email to one of the local TV stations here about being unable to see the videos posted on the site.  I mentioned that I could see all of the videos on all of the other local stations fine.  They wrote me back that they were sorry, but their web page was not "optimized" for linux.:p

There are some people out there who are feverishly working on Greasemonkey Scripts that will help with some of these problems.  Thanks to them I can watch the videos on Foxnews.com and Yahoo.  Maybe one of them will get around to ABC soon.

---

### Post by Dzenhax on 2007-05-27
> **wpshooter said:**
> Is this a conspiracy or does Linux just need to let the people that are doing this programming, that these sites, etc. are not working for people that are using Linux workstations ?  

OR is this a case wherein that the programs that are being used by Linux computer, i.e. Firefox, etc. or the entire O/Ss need to be conformed to the way that these programs are being written ?

Thanks.

Yup, it's a conspiracy.  What Jimbob wrote figures.  Ya can't steal videos, music, pix in Linux any easier than in any other OS.  There are plenty of Win tools to do that.  But our communtiy is the one that gets blamed.  Open source remains a threat to the bottom line and we are punished for that.  The DRM guys don't like us much.

So....

We switch the whole world to Linux and then they have to build it for us too. :D

---

### Post by lupin492 on 2007-05-29
:-(

---

### Post by Shukymeyer on 2007-11-26
my feedback to ABC's Mentallity on their site


I dont think that it is fair for your Linux Customers not to be able to watch our favorite shows online.

I have a Dell which i purchased with Ubuntu and I cannot view your Streaming Videos... I did some research and learned that this has to do with the move networks plugin not being compatible with Linux, and I hope that those of you over at ABC see that this is ridiculous (all platforms should be supported) I cant remember ever buying one type of TV and being told "sorry your TV is not supported by ABC go watch you TV elsewhere."

This is something that should be addressed immediately or you will lose alot of customers (more people use Linux that Mac).

---

### Post by perce on 2007-11-26
Have you tried to report a broken webpage to the Mozilla foundation?

> **Shukymeyer said:**
> (more people use Linux that Mac).

Where did you get this information? I wish it was true, but my personal experience is completely, and by far, the opposite.

---

