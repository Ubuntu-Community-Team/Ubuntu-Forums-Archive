---
title: "download sopcast in linux"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by fooligan on 2007-10-27
im trying to follow jbodell's instructions to dowmload sopcast for linux

ive been to [http://linuxtoy.org/archives/gtk_sopcast.html](http://linuxtoy.org/archives/gtk_sopcast.html) and downloaded

- Download SopCast 1.0.2 for linux

it is now an icon on my desktop

but now im stuck

im not a pc literate person, so probably shouldnt be using linux but i love the philosophy

can anyone explain in laymans terms what steps i need to take next

ta

eric

---

### Post by n3tfury on 2007-10-27
try [[COLOR="SandyBrown"]here[/COLOR]]("http://translate.google.com/translate?hl=en&sl=zh-TW&u=http://changturtle.blogspot.com/2007/10/install-qsopcast-linux-sopcast-to.html&sa=X&oi=translate&resnum=8&ct=result&prev=/search%3Fq%3Dsopcast%2Binstall%2Bubuntu%26hl%3Den%26safe%3Doff%26sa%3DG") and [[COLOR="SandyBrown"]here[/COLOR]]("http://my.opera.com/leeyee/blog/gsopcast-installation-on")

---

### Post by fooligan on 2007-10-27
thanks

ive had a look but its all meaninless to me. 

its like trying to read chinese when i only read english

its such a shame but im going to have to install windows again because im not computer literate enough to use linux

oh well at least i gave it a go

cheers

eric

---

### Post by n3tfury on 2007-10-27
you need to start the program apparently from the terminal.  Accessories>Terminal and type **gsopcast**

note that this is either an obscure program or a bit old.  you rarely have to do something like that for a program to run (unless you want to) in ubuntu.  honestly, i don't think you have it installed at all.  it sounds like you just have the file(s) necessary to do so.  again, this is far and few between with software on ubuntu.  the second link shows exactly what to copy/paste in your terminal to install gsopcast.

---

### Post by fooligan on 2007-10-27
tried typing into terminal but says command not recognised

so can you explain to me what this instruction means from that second link you sent





First of all, you need to install sopcast command line version. Precisely, **it is only a executable script in the tar bal**l. You can download it here: [http://download.sopcast.com/download/sp-sc.tgz](http://download.sopcast.com/download/sp-sc.tgz) and **uncompress it into either ~/bin or /usr/local/bin:**
[B]
tar zvfx sp-sc.tgz
sudo mv sp-sc/sp-sc /usr/local/bin[/B]


like i say im computer iliterate, so i need it in laymans terms ;0)


ta 

eric

---

### Post by n3tfury on 2007-10-27
i found this on their home webpage:

Command line Version:

[B][http://download.sopcast.com/download/sp-auth.tgz](http://download.sopcast.com/download/sp-auth.tgz)
Please read the Readme file in this package, about the usage and library dependency.

If you need the stdc++5 library, download it here:
[http://www.sopcast.com/download/libstdcpp5.tgz](http://www.sopcast.com/download/libstdcpp5.tgz)
Note: No need to download the libstdcpp5.tgz if you can run sp-sc.
[/B]
someone will probably come along and assist further as that's probably out of my league.

---

### Post by srt4play on 2007-10-27
The sopcast website seems a bit slow right now, I've attached sp-sc.tgz to this post.  Save it to your desktop and right-click it and choose 'extract here.'   

On your keyboard do 'Alt-F2' type in 'gksudo nautilus' , hit enter, put in your password, then a file browser will open.  Navigate to /usr/local/bin.  

Open the sp-sc folder that is now on your desktop, select sp-sc and sp-so, then copy and paste them into the window where you navigated to /usr/local/bin.

I use a custom script to launch sopcast because I've never been able to copy/paste a sopcast address into gsopcast, it always crashes.

---

### Post by srt4play on 2007-10-27
[QUOTE=fooligan]thank you ive done all this below, down to pasting into the window where you navigated to /usr/local/bin




what do i do to launch it? what is custom launch?

thanks again because your instructions were plain and simple and easy to understand[/QUOTE]

Open Synaptic (system menu -> administration -> synaptic package manager), click on the search button, change the 'look in' drop down to just 'name', type 'mplayer' in the search field and hit enter.  

On the package 'mplayer' if the check box is empty, click on it and then click 'mark for installation.' If 'Mark additional changes' dialog comes up, click 'mark.' Then click the apply button at the top. If the check box was already green then it's installed and you can move on.  Repeat the process for package 'zenity.'

Download the file sopcast.sh that is attached to this post to your desktop.  Right-click the file, click properties, click on the permissions tab, check the box for 'allow executing file as program.'

At this point you can double-click the sopcast.sh, it willl ask you for the sopcast URL. Copy and paste the URL into it and click OK and it will give a message that mplayer should start shortly.  If the URL is active, mplayer should start playing the channel.

---

### Post by fooligan on 2007-10-28
cheers :)


i have done all of that and thanks because it was so easy to follow.

however when i paste the url in it says itll start in a few minues but it never does.  ive tried a few times too.

heres the site im trying to play a match from, am i doing something wrong?

[http://4.livefooty.doctor-serv.com/sun28.10/Myanmar_China2.html](http://4.livefooty.doctor-serv.com/sun28.10/Myanmar_China2.html)


ta

eric

---

### Post by srt4play on 2007-10-28
Maybe the channel isn't active right now?  I'll try and play it and post back.

EDIT:  I don't see any valid URLs to copy/paste on the page you linked to.  I only watch american football but I get links from [here]("http://www.myp2p.eu"). I think you're trying to watch soccer, not sure but maybe you could find a link to the game you want on the page I linked to.

---

### Post by fooligan on 2007-10-28
ive tried that link. got a bit further than normal, got to the DIB web player looking like it was loading, but thats as far as it went ;0(


thanks for your help so far though, ive been able to follow your instructions very easily

cheers

eric

---

### Post by srt4play on 2007-10-28
I'm not sure what the DIB web player is.  

On the myp2p.eu website the links are separated into columns for the different types of online TV.  

Choose one in the sopcast column, right-click it then click OK on the pop-up that comes up about the myp2p copyright stuff, then click 'copy link location.'  Then paste that into the sopcast.sh prompt window.

---

### Post by fooligan on 2007-10-28
yep tried that link and there is some football on it, but still no joy. either says doesnt recognise link to sop, ot if i click the here button it loads a page but its all lines and never actually shows a picture saying i need to load VTTV Version 1.0.1

can you point me to a url link that you use, then ill copy and paste that url and if it works ill know sopcast is loaded on my pc and therefore know its the sites im trying to visit thats the problem

ta

eric

---

### Post by srt4play on 2007-10-28
sop://broker.sopcast.com:3912/35023

---

### Post by blehman419 on 2007-10-28
Hey sorry to jump in, but I am folowing along with you guys, and I seem to be as stuck as fooligan.  I tried the link you posted srt, but to no avail.  I really want to see the rest of the  Lions game, if you can think of any reason mplayer wouldnt open after caching, please let me know!!

---

### Post by srt4play on 2007-10-28
Run sopcast.sh from a terminal and you can find out why.

Applications menu -> accessories -> terminal.

```

cd Desktop  (or wherever you saved the sopcast.sh file)

./sopcast.sh
```

The Lions game works fine, the address is:

sop://broker.sopcast.com:3912/34643

---

### Post by blehman419 on 2007-10-28
MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) XP 2200+ (Family: 6, Model: 8, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [http://localhost:8800](http://localhost:8800).
Resolving localhost for AF_INET6...
Couldn't resolve name for AF_INET6: localhost
Resolving localhost for AF_INET...
Connecting to server localhost[127.0.0.1]: 8800...
connect error: Connection refused
STREAM_ASF, URL: [http://localhost:8800](http://localhost:8800)
Resolving localhost for AF_INET6...
Couldn't resolve name for AF_INET6: localhost
Resolving localhost for AF_INET...
Connecting to server localhost[127.0.0.1]: 8800...
connect error: Connection refused
Failed, exiting.
Resolving localhost for AF_INET6...
Couldn't resolve name for AF_INET6: localhost
Resolving localhost for AF_INET...
Connecting to server localhost[127.0.0.1]: 8800...
connect error: Connection refused
File not found: 'localhost:8800'
Failed to open [http://localhost:8800](http://localhost:8800).


Exiting... (End of file)
sp-sc: no process killed

---

### Post by srt4play on 2007-10-28
Looks like sp-sc isn't being run at all.

Do you have sp-sc in /usr/local/bin?

What is output of:

```
which sp-sc
```

---

### Post by blehman419 on 2007-10-28
not getting anything when i type "which sp-sc"  but when i only type "sp-sc" in the terminal ii get this:
brandon@VDSL-151-118-163-14:~$ which sp-sc
brandon@VDSL-151-118-163-14:~$ sudo which sp-sc
[sudo] password for brandon:
brandon@VDSL-151-118-163-14:~$ sp-sc
Command 'sp-sc' is available in '/usr/local/bin/sp-sc'
bash: sp-sc: command not found
brandon@VDSL-151-118-163-14:~$

---

### Post by srt4play on 2007-10-28
In the first step, after extracting the downloaded sp-sc.tar.gz you copied the whole sp-sc FOLDER to /usr/local/bin, you need to just have the FILES sp-sc and sp-so in /usr/local/bin.

---

### Post by blehman419 on 2007-10-28
Thanks dude, I got it to work.  I had the sp-sc folder in usr/local/bin.  Took it out of the folder and placed it in the bin folder by itself.  Much thanks, now I can drink a beer and finish watching the Lions stomp the Bears!!

---

### Post by blehman419 on 2007-10-28
now can you get me better picture quality?  j/k

---

### Post by srt4play on 2007-10-28
HAHA I tell ya man it's cool sitting here in my Brandon Jacobs jersey watching the giants continue their winning streak and helping fellow ubuntu users at the same time.

---

### Post by blehman419 on 2007-10-28
Giants are tough this year, but they will have a battle for first place with Dallas.  I can't believe though that my Lions will actually be playing meaningful football in November. I'm usually iching for the NBA to start so I can see a Detroit team win.

---

### Post by blehman419 on 2007-10-28
If you are still around, do you have another listing for sopcast channels?  I'm gonna get my google on, but if you have one that you use more than another, I'd like to hear about it.  Thanks again.

---

### Post by srt4play on 2007-10-28
Hey yeah I was a little worried with the poor start this season (worst defense in the league) but they've turned it around pretty good.

[www.myp2p.eu](www.myp2p.eu) is the only site I know about for sopcast links. If you find more, let us know.

---

### Post by fooligan on 2007-10-28
> **srt4play said:**
> sop://broker.sopcast.com:3912/35023


copied that link in and it works, which means i have got sopcast loaded on my pc , so its obvoiusly the fottball site im trying to play from thats giving me problems for some reason

so now i need to find a footy site i can play ;0)


cheers again for your help, its been a godsend

ta

eric

---

### Post by fooligan on 2007-10-28
currently watching buf vs nyj

much as i appreciate your help, i cant say im a fan, the game stops and starts too much for me.

who are the lions?

---

### Post by fooligan on 2007-10-28
ah just read this line from my footy site

[http://livefooty.doctor-serv.com/](http://livefooty.doctor-serv.com/)

Notes: You MUST use Microsoft Internet Explorer to use these streams.
They do NOT work on Firefox or Opera currently.


so thatll be the reason



although i cant get the "soccer" links to work on the site you use either

[http://www.myp2p.eu/Matches/Match13.htm](http://www.myp2p.eu/Matches/Match13.htm)


finally is it possible to download internet explorer or is that just a microsoft program.....i know its probably heresy, but the football is that important to me ;0)


failing that a link to any manchester united games ;0)


ta

thats it for tonight

---

### Post by srt4play on 2007-10-28
It's not going to be even good quality and there will be interruptions in the broadcast. But it's peer to peer TV, you can't expect too much. If it gets stuck for a long while just kill it and restart it. 

The lions are an NFL team out of Detroit.

You can run internet explorer in Ubuntu but it won't help because your "livefooty" site relies on Windows sopcast software that won't work in Ubuntu.

Just found this site that gives sopcast URLs for soccer, you want the actual link (sop://xxxxxxx) so you can paste it into the sopcast.sh:

[http://www.engfootball.com/](http://www.engfootball.com/)

I searched in google for 'manchester united sopcast links.'

---

### Post by fooligan on 2007-10-28
:lolflag:

thats how low on common sense i am.

ive been searching for live footy broadcasts


thanks for the link

---

### Post by tramir on 2007-11-05
If you guys want a site listing sopcast links for pretty much all the sports (football from both sides of the pond, basketball and so on), you can check this:

[http://livetv.ru/en/]("http://livetv.ru/en/")

Happy foot-ing :lolflag:
Mircea

---

### Post by ubunter1 on 2007-11-06
i dont quite understand how to go about this and install this---  SopCast client version 1.0.2 library dependency
If you don't have stdc++ 5 in your system, please download the libstdcpp5.tgz from
[www.sopcast.com](www.sopcast.com), and copy the
libstdc++.so.5
libstdc++.so.5.0.1
to /usr/lib/

The copy command must be:
cp -a libstdc++.so.5* /usr/lib
With '-a' parameter, and you must login as root.

1. sp-sc-auth

A simple example of sp-sc command line.
./sp-sc-auth sop://broker.sopcast.com:3912/6098 3908 8908 > /dev/null &
Start to transfer channel 6098, and you can play it on 8908 with VLC or mplayer
by open the url: [http://localhost:8908/tv.asf](http://localhost:8908/tv.asf)

2. sp-so-auth

you must install VLC compiled by SopCast and use sp-so-auth to broadcast a channel

2.1 install VLC
login with root
cp /the/package/vlc-install-utf8-pid-getport.tgz /
tar zxvf vlc-install-utf8-pid-getport.tgz

2.2 sp-so-auth
./sp-so-auth -r mmsh://192.168.1.1:8080  -u "user@youremail.com:passwd" -i 6050 broker.sopcast.com 3912 3909 'channel name' 127.0.0.1:3940 3941 >/dev/null & 

 just how do i navigate the terminal to put the files in usr/lib.  ive read some of the threads and tutorials about navigating the terminal but i cant get this yet. i have the files sitting on my desktop(spsc and usr).

---

### Post by srt4play on 2007-11-06
You can install libstdc++5 through Synaptic (system menu -> administration -> synaptic package manager). Follow this thread step by step and it will work.

---

### Post by ubunter1 on 2007-11-06
thanks,i will try now,i already had the lib, it seems installed.ive tried the links and find those a bit confusing but will give another go.

---

### Post by ubunter1 on 2007-11-06
so ive dled it from the site using the deb file and can watch stuff but i have 2 questions. how do i enter a stream channel not in the list? just put it in the channel header in the top bar? sometimes i get the addresses of boxing fights and need to know how to watch them if i have the address. the second is that is vlc player better to use? if so how do i install it  and its dependencies to use in gsopcast?. thanks for your help.

---

### Post by srt4play on 2007-11-07
Sorry dude but if you read this entire thread you would see the comment about gsopcast not being able to play channels that aren't in it's list.  Hence why I jumped in to help with the script I wrote to play those channels, using mplayer, sp-sc, and zenity.

---

### Post by ubunter1 on 2007-11-07
> **srt4play said:**
> Sorry dude but if you read this entire thread you would see the comment about gsopcast not being able to play channels that aren't in it's list.  Hence why I jumped in to help with the script I wrote to play those channels, using mplayer, sp-sc, and zenity.

ok,but i may be able to play it with mplayer?,if not oh well.thanks.

---

### Post by arwa on 2007-11-09
hello

plz any one can help here
[http://ubuntuforums.org/showthread.php?t=608175](http://ubuntuforums.org/showthread.php?t=608175)

---

### Post by rogerp1 on 2007-11-10
Excellent scipt.....many thanks!!!!

---

### Post by hq197 on 2008-01-17
srt4play -- life saver! thanks for attaching sp-sc.tar.gz here. i did this a while ago & now i get a 404 on that page.. you r so kind to help fools like me and fooligan ;)

---

### Post by khughitt on 2008-01-22
Thanks for the guide srt4play :)

I got qsopcast installed and running now, and have been able to download the channel list.
The problem i'm having now is that I'm not seeing any video. If i select a channel and hit "launch" it
will connect to the channel and begin streaming. Then hitting "player" I can hear audio for the stream, but don't see any video. Any thoughts? mplayer is installed already.

Thanks :)

---

### Post by khughitt on 2008-01-23
Okay, got it working. I switched from using **mplayer** to **totem** and that did the trick :)

---

### Post by coffinsupply on 2008-01-25
can anyone help me install vlc on centos?

---

### Post by Dasani on 2008-02-03
thanks for posting your script srt4play! saves the rest of a lot of trouble...
You should publish it on some site!

I guess a little help goes a long way

---

### Post by thecityofgold2006 on 2008-02-23
Thanks to all who've posted useful advice on this thread.

Thanks to you I've now got my eee PC running Sopcast better than it runs on my desktop Windows PC.. A portable all football watching TV!

---

### Post by ryukent on 2008-02-23
To run sopcast sop:// links straight from firefox, please see:

[http://ubuntuforums.org/showthread.php?t=703409]("http://ubuntuforums.org/showthread.php?t=703409")

---

