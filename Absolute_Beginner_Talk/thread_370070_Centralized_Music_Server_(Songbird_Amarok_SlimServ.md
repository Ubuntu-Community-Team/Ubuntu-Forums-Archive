---
title: "Centralized Music Server (Songbird? Amarok? SlimServer?)"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by thornomad on 2007-02-25
Hi,

I am working on a home file server running Ubuntu; will use it to mount drives via NFS/SSH to securely and speedily have all my files in a centralized location (easy backup and redundancy).  I run Macs/Ubuntu machines and share them with my girlfriend.

I am looking for a centralized music experience!  I want access to my tunes & playlists from any machine (Mac or Ubuntu) and, possibly, from a forthcoming Squeezebox.  Would like to consolidate my girlfriend's and my music and have it stored together so we both have access to everything -- however, would like to be able to fashion our own personal playlists.  I don't want to duplicate files, would like FLAC support, and would also like to be able to sync to my iPod (on one machine -- not all of them). 

I have looked at SlimServer and SongBird and Amarok ... was hoping to use the same software from computer to computer ... haven't found anything that lets me quite do it all in one package.

Was wondering what other people used and if anyone has a good system of centralized music  file storage ... ?

Thanks

---

### Post by quicktime1 on 2007-02-25
Im not sure about a program for centralized music storage but I like songbird a lot. I have about 50 gb of music, and when I tried Amarok it froze every time to add media to the library. Songbird did it just fine and much faster too. Songbird though, doesnt have ipod support yet and I think Amarok does. But you can still use gtkpod to add songs into your ipod. Rhythmbox works too, but eh. Right now im satisfied with xmms, I just click the random button and let it roll all day.
I think that as long as you mount your other machines properly you will be able to access the music from whichever program.

There's others out there too:
[http://www.osalt.com/itunes](http://www.osalt.com/itunes)

---

### Post by thornomad on 2007-02-25
I guess with songbird I would need another program responsible for the ripping and tagging of my CDs ... I have a lot done already but am considering going back over them with a higher quality MP3 rip or in FLAC.

Anyway: seems like songbird would "view" and play the songs without a problem ...what about the ripping and tagging ? I use Mac and Ubuntu ...

D

---

### Post by rggavubt on 2007-02-25
From the posts I've seen, Music Player Daemon..MPD is the best.  Search MPD on the forums.  See this How To...it is a bear to set up but apparently the best :

[http://www.ubuntuforums.org/showthread.php?t=320469&highlight=mpd](http://www.ubuntuforums.org/showthread.php?t=320469&highlight=mpd)

Good Luck

---

### Post by thornomad on 2007-02-25
Thanks for that link; I will check it out.  I have never heard of the MPD -- but it sounds interesting.  

Also am seeing it possible to use ABCDE or something like that to rip and organize my files and then just use a seperate player to scan and make available those files.  As long as it doesn't move them all around and cause problems should be fine.

---

### Post by Jose Catre-Vandis on 2007-02-25
I use a combination of xmms (local) and gnump3d (http interface from the server) and (local)

---

### Post by GrammatonCleric on 2007-02-25
I actually store all my media (music and video) on my MythTV box.   This allows me to play my music  via my entertainment center stereo equipment as well as stream media throughout my house.  For backup I run and rsync job to usb drive connected to my house file server.  Actually I have two drives and I swap them out weekly, one drive is stored offsite.   My collection is over 160gigs and it would really suck if I lost all my music.  

For audio playback from my workstation or laptop I use [**Banshee**]("http://banshee-project.org/Main_Page").  I've found that Banshee also handles copying music to and from my ipod the best.  For ripping I use [**Soundjuicer**]("http://burtonini.com/blog/computers/sound-juicer"),  I've edited the output settings for High Quaity VBR MP3, FLAC, and OGG.   For audio conversion [**SoundConverter  **]("http://soundconverter.berlios.de/")is my tool of choice.   For ID3 tag **[EasyTag ]("http://easytag.sourceforge.net/")**is powerful.  Last but not least I'm able to stream my music collection from anywhere, using any player, and share it with friends using [B][mp3act]("http://www.mp3act.net/").

[/B]-GC

---

### Post by rggavubt on 2007-02-26
> **thornomad said:**
> Thanks for that link; I will check it out.  I have never heard of the MPD -- but it sounds interesting.  

Also am seeing it possible to use ABCDE or something like that to rip and organize my files and then just use a seperate player to scan and make available those files.  As long as it doesn't move them all around and cause problems should be fine.

I read an article in Linux Journal mag about a music, video home distribution system using MPD and GMPC using a Gentoo Linux server and controlling each distrubution Linux PC wirelessly using a Nokia 770.  They built a $320 music box for each room using a mini ITX motherboard  with no harddrive with no fans.  Gentoo linux was embedded on a flash drive for each distribution PC.  I have the Nokia 770 being delivered today.

---

### Post by slayerboy on 2007-02-26
I'm extremely interested in the outcomes of all this, as I am looking to get a multimedia server up and running soon (next year or two).  I'd like to have a thin client or minimal system in the main area of the house where the TV is, then I'd like to have my main desktop be a server of sorts, and also have a laptop with wifi.  I'm definitely looking into going with system76's koala and one of their laptops in the next year.

I'll be keeping a close eye on this.  Right now the setup I have is akin to duct tape covering a car door where the window would be.  It works, but it has quirks.:lolflag:

---

### Post by rggavubt on 2007-02-26
> **slayerboy said:**
> I'm extremely interested in the outcomes of all this, as I am looking to get a multimedia server up and running soon (next year or two).  I'd like to have a thin client or minimal system in the main area of the house where the TV is, then I'd like to have my main desktop be a server of sorts, and also have a laptop with wifi.  I'm definitely looking into going with system76's koala and one of their laptops in the next year.

I'll be keeping a close eye on this.  Right now the setup I have is akin to duct tape covering a car door where the window would be.  It works, but it has quirks.:lolflag:

The article I read used a casetronic case and ASUS mini itx board from the following :

[http://www.logicsupply.com/?referrer=googleAd&gclid=CJOJ5tX5y4oCFRZrNAodmzlkgA](http://www.logicsupply.com/?referrer=googleAd&gclid=CJOJ5tX5y4oCFRZrNAodmzlkgA)

---

### Post by lamego on 2007-02-26
MPD seems to be what you are looking for.
It has Linux and Mac clients:
[http://www.musicpd.org/clients.shtml](http://www.musicpd.org/clients.shtml)

---

### Post by slayerboy on 2007-02-26
Yes, I will definitely have to take a look at MPD.  I tried SlimServer a while ago, but had problems accessing it from work, but everyone else could.  I'm sure MPD will be the same way, but I'll look into it more.  Thanks!

---

### Post by Spr0k3t on 2007-02-26
I'm going to throw out my suggestion for Ex Falso when it comes to managing loads of ID3 tags.  You can do entire collections with a few clicks if you have it set up properly.

---

### Post by mcduck on 2007-02-26
MPD is very nice indeed, but not that kind of solution the OOP wanted. MPD's idea is that all music is played on the computer running MPD, and other machines are only able to controll it.

If you want to actually play the music on remote machines it's not a good option. Instead you could try Edna, which is very nice  music server with web interface that is able to stream music to remote machines (where you can play it with any player that can listen to web radios: [http://edna.sourceforge.net/]("http://edna.sourceforge.net/")

---

### Post by thornomad on 2007-02-26
I am leaning towards just relying on my NFS/SSH mounted drives in terms of music playback; that is, pointing my music clients to the NFS:/music folder and letting each client on each machine access it this way; then the server is only really serving files.

My only real concern with this is whether or not programs like iTunes and Amarok and SongBird either a) change the files and directory structure to their liking (I know you can disable this in iTunes) or b) will have problems with different computers accessing the files at the same time (I tend to doubt it because, as I understand it, I think the file gets transferred locally while it is being played since it isn't really "streaming").

Hopefully this will work okay (locally and remotely).

D

---

### Post by Bubbel on 2007-03-02
Another approach is Ampache. It&#347; a HTTP front-end to index and stream your music to any browser (even has a Flash mp3 player in it)

It&#347; not in the repositories, but a breeze to set up. All you need is a web server with running PHP and MySQL.

See: [http://www.ampache.org/]("http://www.ampache.org/")

---

### Post by TehMark on 2007-03-02
check out jinzora.com

looks sweet

Works on linux and windows

can stream music from anywhere

I just have to figure out how to install it.  tryin to remotely setup apache and I believe that its mad that I'm not acutally at the machine

yay for being bored at work

---

### Post by stokedfish on 2007-03-02
Jinzora is my fav...love it!! <3

---

### Post by stokedfish on 2007-03-02
Sorry for the double post but here's 3 shots of my Jinzy installation...

It's pretty easy to set up, I've even written a small how-to, but it's in German:

[http://www.dachboden-wg.de/portal/index.php?option=com_smf&Itemid=104&topic=19372.msg226365#msg226365](http://www.dachboden-wg.de/portal/index.php?option=com_smf&Itemid=104&topic=19372.msg226365#msg226365)  :)

---

### Post by TehMark on 2007-03-02
Jinzora does seem to be the easiest and most feature packed one i've seen so far

---

### Post by stokedfish on 2007-03-02
Well, it's fantastic, but it does have a few bugs and the devs are rare.

Also, your collection needs to be 100% tagged. Otherwise I'd use the directory-based mode, but then, of course, a lot of the features (like the advanced search and more) won't be usable anymore.

For me it's no problem as my collection is fully and perfectly tagged anyway. Once it's set up, get a dyndns account, configure your apache.conf and you music will be streamale from everywhere with a webbrowser...actually, I often listen to mine at my parent's on the WLAN on my Palm TX! :D

---

### Post by handdog on 2007-03-06
Actually you don't lose any functionality by using a directory-based import. It's preferred at this point if your collection is organized. We also just released 2.7.5 yesterday to hopefully crush a few more bugs..


Ben

---

### Post by stokedfish on 2007-03-13
Why is it preferred? This is confusing...

---

### Post by Senilix on 2007-06-06
Here's my thoughts: [http://blogg.s9.no/post/3037868]("http://blogg.s9.no/post/3037868").

In summary, I use RipIT for ripping, FLAC for encoding, Picard for tagging, NFS for sharing and SlimServer, MPD, Rhythmbox and mplayer for search and playback.

---

### Post by paulg on 2007-06-07
I came across this problem a year a go when my wife got a MacBook. 

Our specific problem was getting music from a desktop system that dual boots linux (Ubuntu) and Windows, to a MacBook. The tricky part is making it appear seamless on the MacBook without requiring my wife know which system I was booting thus not requiring port setting changes, IP server changes etc.

Slimserver was the first part of my solution since I can run it in Linux and Windows and access the same collection on the same drive.

The second part was [http://www.fs-driver.org/](http://www.fs-driver.org/) which allows access of ext2 (and therefore ext3) formatted drives so my music is visible in Windows for Slimserver to gain access to the collection.

The last part is Hamachi ([hamachi.cc](http://www.hamachi.cc)) which also has Windows, Linux and Mac clients. This little program, as a most basic description, allows you to nearly effortlessly build a VPN. I use the same key and ID for Hamachi in Windows and Linux so now my wife can connect to my desktop system from any other network no matter what OS I am running without changing IP addresses or configuring different ports. It's just like being on our home LAN all the time. Hamachi takes care of all the tunnelling.

A year on I'm still happy with the setup. I would like to one day add a SqueezeBox to the mix. What is it the fanboys say? (you know who you are... =) it just works... 

well, most of the time :p Occasionally Hamachi on the MacBook needs a kick-start after being put to sleep several dozen times without a reboot - I think the client just gets confused. Could probably write a cron job to overcome this but it happens very infrequently and I've been told often enough not to mess with the MacBook...

Hope someone finds this useful.

~pAul.

---

### Post by pheckel on 2007-06-29
I am in love with my Subsonic server: [http://subsonic.sourceforge.net/](http://subsonic.sourceforge.net/)

Runs as a Tomcat webapp, easy to deploy, very nice interface, provides user accounts, browser based tagging, and streams video as well.  I travel for business every week and it's nice to stream my 100GB collection from my living room to wherever in the world I may be at the time.

Hope this helps.

---

