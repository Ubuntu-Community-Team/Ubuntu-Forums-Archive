---
title: "DVD Rip Programs - Easy to use?"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by discmaster on 2007-05-30
I have used all the "big names" in windows; Shrink/DVDD/Ri4M, etc.

I have been trying to use k9copy with no luck; dvd:rip seems to be above my level of understanding, being new to linux. Is there something out there that does work for dvd backups?

Also,  any tutorials (step by step). I couldn't really find much to address the issues I have experienced with k9copy, for example.

I don't mind trying to learn a new program, but if there are no good guides avail. for it, I don't really want to spend 2 weeks "muddling" around trying to sort things out on my own.

Being a newbie to this OS, that is what I have done before, & always end up "breaking" things, having to re-install, etc.

Any & all suggestions welcome.

Thank You :)

---

### Post by ryanVickers on 2007-05-30
I would recommend K3B for all your cd/dvd needs - it's a KDE app, but it works fine on gnome.

---

### Post by stalker145 on 2007-05-30
Personally, I like AcidRip to copy DVD's to avi's and let the kids play with those on a 700MB disk instead of the original DVD... works for me, anyway.

---

### Post by orb9220 on 2007-05-30
I use dvdshrink and dvdecrypter in wine.
[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)
[https://help.ubuntu.com/community/DVDShrink](https://help.ubuntu.com/community/DVDShrink)

---

### Post by discmaster on 2007-05-30
Hi Guys,

Thanks for the replies;

Acidrip - I tried - I'm too dumb to use it :(

K3B - I am considering that; trying to get away from command line, if possible...

> I use dvdshrink and dvdecrypter in wine. Thought of that too; I have read several "nightmare" threads on wine, but at least I know how to use shrink & dvdd...

More suggestions - tutorials & guides?
:)

---

### Post by discmaster on 2007-05-30
> 
K3B - I am considering that; trying to get away from command line, if possible I just checked this one out - nice GUI; however; "cannot copy encrypted DVDs"...

---

### Post by discmaster on 2007-05-30
*sigh* 

Guess I will have to wait until I gain more knowledge for this to occur...I tried the wine method using Mr.bass's instruction; DVDD says, no dvd readers found, I can't select any drives with the dropdown arrow.

Then I got lost with all this...
>  cd ~/.wine/dosdevices
rm d:
ln -s /media/cdrom d:

Later versions of wine, like the one shipped in Dapper Drake (0.9.9) ignore settings in ~/.wine/config
You have to use the "winecfg" program to set windows version to NT 4.0 (thanks to Phil B. July 2006)

gedit ~/.wine/config
[Version]
"Windows"="win98"
change to
"Windows"="nt40

maybe someday...:confused:

---

### Post by orb9220 on 2007-05-30
Did you alt-F2 and enter winecfg and add it to wine and then click on drives tab and click on autodetect?

---

### Post by discmaster on 2007-05-30
when I press Alt + F2 wine doesn't show up there. I did install wine, or so I thought; how can I check on it?

---

### Post by ryanVickers on 2007-05-30
> I just checked this one out - nice GUI; however; "cannot copy encrypted DVDs"...
well, yes, it's not software designed for this kind of thing, but for anything else it's good.  But like people have said, acidrip would be good for coping DVDs to mivie files

---

### Post by daimaru on 2007-05-30
> **orb9220 said:**
> I use dvdshrink and dvdecrypter in wine.
[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)
[https://help.ubuntu.com/community/DVDShrink](https://help.ubuntu.com/community/DVDShrink)

why dont u just use DVDshrink for ubuntu instead of all the wine crap ?
get urself automatix install it .. thats it or use terminal which ever u prefer

---

### Post by Foxmike on 2007-05-30
> **daimaru said:**
> why don't u just use DVDshrink for Ubuntu instead of all the wine crap ?
get yourself Automatix install it .. thats it or use terminal which ever u prefer


Why use Automatix when you can easily copy/paste in the terminal? Here is a [nice How-to]("http://doc.gwos.org/index.php/Xdvdshrink").  Has been made for Breezy but I don't see any reason it wouldn't work under Feisty.

Besides, you can give dvd95 a try.  You can install it from Synaptic.

As for the problems you had with k9copy, what were they?  Maybe someone can give a hand!  As for me, I just built the latest version and it works like a charm!  Here is the [how-to]("http://doc.gwos.org/index.php/K9copy") if you don't mind building a package from source.  Basically, all you have to do is to follow the steps and copy/paste commands in the terminal. 

Good luck!:)

---

### Post by discmaster on 2007-05-30
Hi Foxmike,

I will have a look-see at the info./links that you posted!

---

### Post by discmaster on 2007-05-30
> Did you alt-F2 and enter winecfg and add it to wine and then click on drives tab and click on autodetect?I was able to do that & get the "Run Application" box. I put winecfg in the dropdown arrow box at the top &  click run?


After that, I....wait a minute...I got it going! 

GEEZ, I'll never be able to do that again, not in a million years! I'm not even sure what I did to make it work! Well, one hurdle jumped, now on to DVD Shrink!

Is that one easier?!?!

---

### Post by discmaster on 2007-05-30
I am almost there; I am so close, I can feel it! :lolflag:

Using this [tut.,]("https://help.ubuntu.com/community/DVDShrink") , I followed the steps to setup shrink & dvdd in wine, autodetect drives, etc.;

> To start DVD Shrink type the following command in a terminal:

wine "C:\Program Files\DVD Shrink\DVD Shrink 3.2.exe"


I can't get that to happen; little help?

I get this in the term. window...
> tr@tr-desktop:~$ C:\Program Files\DVD Shrink\DVD Shrink 3.2.exe
bash: C:Program: command not found
tr@tr-desktop:~$ 


---

### Post by shirilover on 2007-05-31
You could try either of the following:
```

wine "~/.wine/drive_c/Program Files/DVD Shrink/DVD Shrink 3.2.exe"

```
or
```

env WINEPREFIX="/home/yourusername/.wine" wine "C:\Program Files\DVD Shrink\DVD Shrink 3.2.exe"

```

---

### Post by ghandi69_ on 2007-05-31
I have no idea how or wjy 

But k3b has been able to handle every DVD I have thrown at it so far. (Again, not entirely new movies... but Family Guy Movie, Sin City, Good the Bad and the Ugly collectors editoin etc etc...)

I make sure to check "ignore errors" and I always use "copy .iso only", because I prefer not to have any kind of compression.  Maybe I'm getting lucky.

---

### Post by techno-mole on 2007-05-31
i used k3b last night to burn 3 full length films to dvd (granted i had decoded them first with dvd fab under windows) but k3b seems to do the job, they play in a dvd player and thats good enough for me :D 
i didnt know they did a dvd shrink for linux/ubuntu so i bookmarked the how to, cheers for that.
cheers

---

### Post by discmaster on 2007-05-31
EDIT: Seems I missed a step - D'OH!!!

> Download dll.zip 1.1MB to your desktop (contains riched20, quartz and mfc42 dlls)
unzip Desktop/dll.zip -d ~/.wine/fake_windows/Windows/System/

But now, when I try to do that, the term. responds with -
> tr@tr-desktop:~$ unzip Desktop/dll.zip -d ~/.wine/fake_windows/Windows/System/
checkdir:  cannot create extraction directory: /home/tr/.wine/fake_windows/Windows/System
tr@tr-desktop:~$ 

 So, how do I create the extraction directory?

---

### Post by discmaster on 2007-05-31
ok, maybe making a bit of progress. I created  the extraction directory manually - I thought it would be auto-created, as in windows...

After that, I try to install shrink again, & now I get an error box;
"An error occured while trying to replace the existing file"
Delete file failed code 32
Sharing Violation
click retry,ignore,abort.

Only ignore or abort works, then I go to end of install, click finish, which is supposed to launch shrink. which it doesn't.

Need some assistance from this point, I don't really know what else to do.

I am following mr.bass tutorials on this - I did get dvdd installed, but shrink - no way, no how! ](*,)

---

### Post by discmaster on 2007-05-31
Does anyone have any ideas how to get past this problem? I don't mind doing research to find out on my own, but since I am a newb. to linux, I don't know what else to try. 

Any ideas? Is maybe part of the problem that I tried to install shrink first before I had the dlls installed? :?

---

### Post by discmaster on 2007-05-31
well how about this? If I can't fix it, how do I get shrink completely off the hard drive so I can try to reinstall it again from scratch?

I did throw everything away that I saw relating to shrink, but I must not have got everything, otherwise I wouldn't receive this message when I try to reinstall it.

> "An error occured while trying to replace the existing file"
Delete file failed code 32
Sharing Violation
click retry,ignore,abort.

---

### Post by notwen on 2007-05-31
Not sure, but it seems like I recall VLC having the ability to actually save a DVD to .avi.  You may want to install VLC and search some of it's options. Hope this helps.

---

### Post by discmaster on 2007-05-31
I have VLC, but I don't believe it will do what I need, as far as running shrink & dvdd in tandem to rip/compress/burn a movie.

---

### Post by eeried on 2007-07-26
Only wondering why to a question about an easy-to-use VDVD rip app some people here starts talking about wine and all that. 

Why not use what's in the repos, what's designed for Ubuntu and what's free like freedom (rather than free beer, though I wouldn't mind a pint of beer this evening).

I've used k9copy on Xubuntu but it doesn't seem to accept the option to remove the menus: I get an error after a while.

I've also used dvd95 on Xubuntu: it's light and okay if you don't want to include the bonus -- as I don't get how you select more than one video file in the main panel.

I choose not to burn anything directly as it's rather wiser to check what the iso file looks like: you can play it directly in VLC (no need to mount it, just open it in VLC).

At the moment I'm trying not to include the menu as I've chosen one audio language and one subtitle. I've found that VLC offers a list of subtitle in its menu so you can choose to enable the subtitle which seems disabled by default (menu video > subtitle).

Okay, it seems I've been able to remove the DVD menu, that is the picture with the DVD menus to set up, languages, bonus, etc. Some DVDs have very nice  menus, and it may be worth keeping them even if you have ripped out some audio and subtitles, and therefore have rendered the DVD menu useless.

My 2 cents, :guitar:
cheers

---

### Post by mcduck on 2007-07-26
If you want nice and _really_ easy DVD ripper try Thoggen. It's hard to make a program simpler than that. The only downside is that it only rips into .ogg Theora video.

---

### Post by eeried on 2007-07-26
Yes Thoggen is great precisely because it encodes into OGG. :)

The only drawback seems to be the time it takes to rip a DVD. I have a PIII on which both DVD95 et K9copy work fine.

Any idea how to speed up Thoggen?

The configuration doesn't look very simple. I'm not sure how to increase the quality or remove subtitles and audio tracks (unwanted languages).

---

### Post by mcduck on 2007-07-27
> **eeried said:**
> Yes Thoggen is great precisely because it encodes into OGG. :)

The only drawback seems to be the time it takes to rip a DVD. I have a PIII on which both DVD95 et K9copy work fine.

Any idea how to speed up Thoggen?

The configuration doesn't look very simple. I'm not sure how to increase the quality or remove subtitles and audio tracks (unwanted languages).

To increase quality just use either the 'Make video certain quality' or 'Make video a certain size' and set quality/size higher.

Then select the language you want and all other languages are removed. I'm not sure if Thoggen even supports ripping subtitles so there should be no problem getting rid of tem ;)

---

### Post by phenest on 2007-12-17
> **eeried said:**
> Yes Thoggen is great precisely because it encodes into OGG. :)

The only drawback seems to be the time it takes to rip a DVD. I have a PIII on which both DVD95 et K9copy work fine.

Any idea how to speed up Thoggen?

The configuration doesn't look very simple. I'm not sure how to increase the quality or remove subtitles and audio tracks (unwanted languages).

I would like to support free codecs like ogg vorbis/theora, but Thoggen IS slow. Is Thoggen still in development? The current version in the repos is 0.6.0 which was released on 16th October 2006, over a year ago! Is there another way to decrypt a DVD and encode to theora with decent quality in both video and sound? Otherwise, I might have a look at Thoggen's code myself and have a play with it.

---

### Post by tor528 on 2007-12-22
To copy DVDs using K3B, you first need to get libdvdcss2. 

```
sudo apt-get install libdvdread3
```

then

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by omega_user on 2007-12-23
yeah, I have Thoggen and it is ridiculously slow, slower then the actual movie by almost double the time.  What's better?

---

