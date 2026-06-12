---
title: "MP3/iPod help for Dapper needed"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by Beastmouth on 2006-08-09
Okay, I have been trying to get this to work for about a week, and I haven't.  

First, I don't really need my comp to do much.  Surf the web, IM, some minor office stuff, and the only apparent biggie, actually play music and, w/ luck, get along w/ my iPod.

I installed Ubuntu for the first time about a week ago (basically my first Linux experience, even).  Hadn't used a CLI in about a decade, it took a bit of getting used to but I've got decent hang of it now.  Anyway, I wanted to listen to my music.  I popped in a CD, Sound Juicer (SJ) came up.  It played the CD just fine.  Then, I tried to rip it.  I set SJ up to rip into MP3, using the gstreamer pipeline given in the help menu, audio/x-raw-int,rate=44100,channels=2
Ripped the cd in about eight minutes, which is fast enough.  Then I tried playing it.  Blammo, rhythmbox can't recognize the MIME of these files.  
So I spent a few days d/l'ing various things, I tried amaroK on Gnome Ubuntu, it acted like it wanted to play my MP3s, only it told me they were either half a second or half a week long.  
So I decided to try ripping to Ogg Vorbis, since rhythmbox is supposed to like it.  Well, I could only rip to Ogg at about 0.2 speed, and I can't spend five hours to rip one CD; I'd sooner buy a new copy of Vista or w/e (!).  
Then I decided to try Kubuntu, amaroK being part of the deal there.  Well, no such luck; all I got was more of the same.  
So yesterday and today (took *for*ev*er) I d/l'ed Automatix and installed damn near everything.  I sit down to try out all my new media players and guess what happens?  All my MP3's are 3 days long again.  :cry:  And Ogg still takes a year.  

I'll probably just reinstall to get rid of all the automatix, it seems to do me absolutely no good at all.


Anyway, can anyone help me out here?  What should I do to get Ubuntu to play files that my iPod likes?  MP3'd be great, m4p/aac/mp4 (sorry I forget th extension used and I'm not booting up the windows machine at midnight unless it's abs necessary), the format the thing's made for would be great.


Also, I haven't got around to trying GNUpod or GKTpod or w/e g**pod is listed on Synaptic, as all this other stuff's taken so long.  Ideally, is there a program that will work with my iPod set to factory spex, and if I'm lucky, can it take the music from my iPod too so there's that much less to rip?

Thanks in advance, y'all!  :)




PS It'd be super ridawesoculous if there's a program that runs under Ubuntu that'll turn vinyl input into MP3's.  Thankx!

---

### Post by MrHorus on 2006-08-10
> **Beastmouth said:**
> 
Also, I haven't got around to trying GNUpod or GKTpod or w/e g**pod is listed on Synaptic, as all this other stuff's taken so long.  Ideally, is there a program that will work with my iPod set to factory spex, and if I'm lucky, can it take the music from my iPod too so there's that much less to rip?

Yes - gtkpod :)

Personally I prefer flashing the firmware with the free Rockbox so that the iPod can playback Ogg and FLAC but it's a little hairy to set up initially.

If you are having difficulties getting music to play, have you installed the appropriate codecs?

Linux doesn't ship with these by default due to patent/liscencing restrictions so you will have to enable the universe and multiverse repositories for apt/Synaptic... there should be a guide lying around on the forums somewhere if you are not sure how to do this.

---

### Post by Kobalt on 2006-08-10
Maybe Rhythmbox can't read the files you ripped because of the Pipeline you used... Here is what I use as a Pipeline : ```

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc quality=0 preset=1001
```
With this I can play files on my iPod mini or in rhythmbox. I just need to edit the tags properly, Sound Juicer does not apparently, with Cowbell (a tag editor - it's in the repos). 
To transfer files to your iPod you should use gtkpod, it works like a charm. 

And one more little hint : you don't need to install Kubuntu to get amaroK, you can install it from Synpatic in Ubuntu just as any other software. 

Cheers ! :rolleyes:

---

### Post by Beastmouth on 2006-08-10
In the repos?  What tags do I edit, something on each song file?  Cowbell, I can find this with Synaptic?  (atm I'm running sudo apt-get upgrade so I can't use synaptic).


I did know I didn't *need* to install Kubuntu for amaroK, I was just hoping it'd be more co-operative.  Plus, I got to find out for sure that I prefer regular Ubuntu to that version, so chalk that one up to experience, I guess.  

Merci!

---

### Post by Kobalt on 2006-08-10
The number and the name of the songs will be done well, it's just the artist and the album name that didn't appear. You can select all files at one and apply the names to all in once. It's really easy and fast... 
Yes cowbell can be installed from Synaptic, just like amarok :rolleyes:

De rien !

---

### Post by Beastmouth on 2006-08-12
Okay, I'm getting somewhere.

I installed grip and am using it to rip CDs.  I installed lame and can convert .wav to .mp3 just fine.  Rhythmbox opens my files just fine and recognizes my iPod.  I installed audio_conv.py from [http://seismic.ocean.dal.ca/~leblanc/pwp_wiki/static/AudioFormatConversion.html](http://seismic.ocean.dal.ca/~leblanc/pwp_wiki/static/AudioFormatConversion.html) and am trying to figure it out.  

I gather from the above site that I need to move the file to my paths, such as /usr/bin (this is correct?  Still quite a noob).  I tried copy/paste from the GUI but got nowhere since I'm not root there.  I tried to move it via the terminal but kept getting
[quote=error]$ sudo mv ./audio_conv.py ./usr/bin/audio_conv.py
mv: cannot move `./audio_conv.py' to `./usr/bin/audio_conv.py': No such file or directory[/quote]

and

[quote=error]$ sudo mv ./audio_conv.py ./usr/bin/audio_conv.py
mv: cannot move `./audio_conv.py' to `./usr/bin/audio_conv.py': No such file or directory[/quote]

I'm not even sure what 'cannot stat' means, but I know something's wrong.  :/

Can someone pls help? 

My plan is to rip some CD's, then use this script while I'm afk to encode each .wav file for me, as I rip .wav so fast and the encoding takes a good while.  If this is not a sound plan, could someone offer something better?  

Many thanks!

---

