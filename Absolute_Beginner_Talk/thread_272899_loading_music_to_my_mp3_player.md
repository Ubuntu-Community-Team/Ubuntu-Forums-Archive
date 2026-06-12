---
title: "loading music to my mp3 player"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2006-10-07
Hi to you all. I've been trying, without success, to find a media player that will load my music files onto my mp3 player. about a week ago I happened to notice a thread by Xpod regarding this very thing {while I was trying to get my video app working}, but I can't find her thread again (sob, sob). 
Currently I have to log back onto XP and use WindowsMediaPlayer for this (much sobbing). My mp3 player is a Philips GoGear and I think any generic app will work it, if I could only find one! XMMS doesn't do it, nor Beep, Vlc, Rhythmbox, etc. In fact none of the mp3 apps available in SynPacMan will do it [at least for me].
I scrolled the 'dapper packages' but nothing seemed to fit my need. I haven't had much success in downloading apps from sources outside Ubuntu - they just won't install. Yes, i'm a dummy.
Nevertheless, this is an app I use all the time.
Any ideas? please?](*,)

---

### Post by MiXor on 2006-10-07
Is your MP3 player Creative Labs?
*oops, sorry, had not read carefully enough, it's philips... Don't know how to remove replies from this forum*... I'm a loser :???:

---

### Post by MiXor on 2006-10-07
Have you tried Gnomad 2? Is your MP3 player a MTP device?

---

### Post by RudolfMDLT on 2006-10-07
Amarok should work? Just a question, can you use your mp3player as a USB flash drive? or is it something a bit more advanced, ie dit you need to install drivers in windows?

---

### Post by Marsolin on 2006-10-07
I haven't looked into your player specifically, but [here]("http://linuxappfinder.com/multimedia/portableaudiomanagers") is a list of apps that can be used to manage mp3 players.

---

### Post by carloslosgrande on 2006-10-07
Hi to you, and thanks for your replies. MiXor, I don't know what MTP is.:confused:
RudolfMDLT, yes i can use it as a flash drive and yes it came with its own disc and drive, but it seems to work on Ubuntu for playing music and storing data, whatever, without reinstalling the drive. I thought Amarok was for Kubuntu? Sofar the problem has been that the apps I've tried don't have a function for loading music to it.:-|
Marsolin, thanks for that list, I'll give them a try. I've already tried 'Listen' but it wouldn't run which may be as much about my download/installation skills [zip!]:)
Of course what I was really hoping for was an app already in 'packages' , that would be _so_ easy for me. [Lazy by design].
Thanks again, I shall plug on.:-k

---

### Post by HareBall on 2006-10-07
> **carloslosgrande said:**
> Hi to you all. I've been trying, without success, to find a media player that will load my music files onto my mp3 player. about a week ago I happened to notice a thread by Xpod regarding this very thing {while I was trying to get my video app working}, but I can't find her thread again (sob, sob). 
Currently I have to log back onto XP and use WindowsMediaPlayer for this (much sobbing). My mp3 player is a Philips GoGear and I think any generic app will work it, if I could only find one! XMMS doesn't do it, nor Beep, Vlc, Rhythmbox, etc. In fact none of the mp3 apps available in SynPacMan will do it [at least for me].
I scrolled the 'dapper packages' but nothing seemed to fit my need. I haven't had much success in downloading apps from sources outside Ubuntu - they just won't install. Yes, i'm a dummy.
Nevertheless, this is an app I use all the time.
Any ideas? please?](*,)

I have an RCA mp3 player. When I want to load music, I plug it into the USB port and drag and drop from the file holding the music. Of course I am new to all this, so I don't know any better;) 
Larry

---

### Post by kaplis on 2006-10-07
hey!

a few days ago i bought Sony mp3 player but i had to give it back because of the same problem as you had, as  i understand. i got now Creative mp3 player! no problems- just plug and copy in music and listen;) 

P.s. when in the shop i told to the salesman that this player wouldnt work for me because i have linux (there was included that instalation programm Sonic Stage for music upload..in Windows, of course:evil: ), he for some 10 seconds was looking at  me and saying nothing at all, like i would some ugly monster, because i dont use Windows:mrgreen: :D

---

### Post by carloslosgrande on 2006-10-08
Thanks guys, the trouble is that when I drag n drop music files to the mp3 player all I get is files! no music will play from this.

---

### Post by crispy_420 on 2006-10-08
just a simple google search of mine ... i have no experience with this player ... just a few apps i found:

first one even has .deb files

[http://opengogear.sarovar.org/](http://opengogear.sarovar.org/)

[http://tuxmobil.org/player_linux_survey_philips.html](http://tuxmobil.org/player_linux_survey_philips.html)

---

### Post by carloslosgrande on 2006-10-08
Hey Crispy, thanks! This looks like just the thing!:D

I've been trying to download and install the Deb package and it tells me that 'dependency not satisfied libid3-3.8.3'
So I went to the dapper packages and found 'libid3-3.8.3c2a' which is a later version and is in conflict with the earlier version as I tried to install that from another site. I figure the later version is being used by other apps so i didn't overwrite it. I found 'id3lib' which is, I guess, the same thing with a different name but its a 'so' file, whatever the heck that is and archive manager won't recognise it.:confused:
I also tried the other app you listed but i had even more trouble with that.
I've been following the  'howto'  by Dinerty for installing anything and  it isn't working for me so there is a really basic problem here in that I don't know what it is that I'm doing wrong.:-k
All advice gladly appreciated.

---

### Post by xpod on 2006-10-08
Still at it then????
Dont know what thread o mine would have possibly been of help to anyone...
Most likely broke the pc even more;) 

I got all the codecs and media players out of Automatix and copying mp3 music is just a case of dragging and dropping although im not a 100% sure which app i used as i got that many of them...

When i first posted about it my boy say`s the music was`nt copying over SO i came on here etc etc etc....turns out though it had been working all the time
and my boy was having a father like "DUH" moment..

I`ll go play around with it all if that helps

---

### Post by gn2 on 2006-10-08
[QUOTE=carloslosgrande;1590439] I thought Amarok was for Kubuntu? /QUOTE]

It works perfectly in Ubuntu, and is available via Synaptic.

---

### Post by carloslosgrande on 2006-10-08
Hi Xpod, yes I'm still at it. And that was the thread I had in mind. Apparently my mp3 needs Sqlite indexing to code the files to play on the player.
I don't understand what I'm doing wrong with downloading and installing, I just can't seem to do it!:confused:
Attached is the latest result in the command line.
If an app isn't in the packages then I'm  buggered!
I'm sure it's just something really basically stupid I'm doing.:-k

Thanks GN2, I'm just loading Amarok now and I'll check it out.:)

---

### Post by xpod on 2006-10-08
I cant see what would have been in that thread that would have assisted you in anyway......confused you even more most likely:D 

Just do what i do and install automatix then once you got that check all the boxes that relate to mp3,codecs,mulitimedia,free beer blah blah blah....
And anything i play just seems to work although i do end up on the odd sites that loads the mplayer,do the buffering etc then just play sound with no video.still got to suss that bit out:-k 
Apart from that i aint had no problems.....9 times out of 10 if i post a new thread i always realise my stupidity or stumble across the answer as soon as it`s posted like was they case that time......boys fault[-( ..lol

[http://www.ubuntuforums.org/showthread.php?t=267918](http://www.ubuntuforums.org/showthread.php?t=267918)

EDIT:All the advice those guys gave me about mounting and unmounting did`nt come into the equation...all i had to do was plug in the mp3 and it showed up on desktop then got some tunes from frostwire for him then dragged them over to his mp3.....there was a bit of confusion but we got it done in the end:mrgreen:

---

### Post by carloslosgrande on 2006-10-08
I tried Amarok but it says it can't play mp3 files, so I'm loading Automatix (again) and it also says there is 'no device available' even though it is clearly connected - *[COLOR=Blue]I [/COLOR]*can see it!:o
I've actually run Automatix a few times but there is a message at the end that says about keeping the standard package list or using Automatix's with the added comment that 'you may not want this!' so I save back to the standard because I don't know.
Do I need to keep the Automatix list to make things work????:confused:
See - i really haven't a clue!:-k

---

### Post by xpod on 2006-10-08
If your setting automatix up and want to have it`s sources added to your source list then choose "cancel" at that point
You`ll need it if you want to use automatic

EDIT:choosing "cancel" merely stops it reverting back to your old sources list

EDIT2...Theres a look at mine

## Automatix sources.list
## This is automatically generated by Automatix


####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe restricted main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

# Dapper Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse

# Dapper Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


##############################
### Automatix Repositories ###
##############################

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

## created by automatixrepo3
deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./

---

### Post by carloslosgrande on 2006-10-08
Ok, the automatix thing has finished and amarok still not doing its thing. I'll try again in the morning - reboot may do the trick:rolleyes:
Thank you all for help, I'd be nowhere without it.:)

---

### Post by crispy_420 on 2006-10-10
Just a test:

Try to uninstall libid3-3.8.3c2a and see what it connects to. Don't actually proceed.

Worst case scenario you may have to compile it youself...

---

### Post by Jamhos on 2006-10-10
Amarok is lovely, and will most likely sync with your player. To get Amarok to play mp3's, go to Synaptic and do a search for 'codecs', and it should come up with a few. It's probably a good idea to download them all, as you are likely to use them at some point, but make sure you get the xine audio ones, and then make sure Amarok is using the xine engine. Should work fine then! IMO Amarok is great, I use it all the time, so I would recommend getting it working! :D

---

### Post by carloslosgrande on 2006-10-10
[FONT=Comic Sans MS]Crispy, Hi.
I just did as you said and it wants to also remove ipodslave, python id3lib, python 2.4 id3lib, and ubuntu desktop. So I'll give that a miss.
I thought the .dev files were files that were still in development so I haven't loaded them until last night when I realised that they are for developing the app! I skim over instructions too fast.:-?

Jamhos, thanks for the info. I have already downloaded as many codecs as I can find but my mp3 player is Gogear and it needs libid3 and SQLite [especially] to prep the music files to actually play! I have been shown an app specially written for this player but I'm having enormous trouble installing it, but thats another thread.](*,)
I agree Amarok is a great player.
[/FONT]

---

