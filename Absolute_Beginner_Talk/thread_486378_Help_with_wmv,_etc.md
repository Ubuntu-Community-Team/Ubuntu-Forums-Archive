---
title: "Help with wmv, etc?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-06-27
I have a feeling this is going to be one of those "depends on what you are doing things", but since I am new I'm going to ask anyway:

I have a cheap Gateway laptop and when I access emails, etc., that have .wmv files, a player starts up and shows a black window while the sound is heard.  Is there an easy way to fix this?  And as long as I am asking, what is the easiest way to get dvd playback?  I haven't tried it yet but from what I've read on this forum it sounds like it might be tricky.

---

### Post by starcraft.man on 2007-06-27
> **anewguy said:**
> I have a feeling this is going to be one of those "depends on what you are doing things", but since I am new I'm going to ask anyway:

I have a cheap Gateway laptop and when I access emails, etc., that have .wmv files, a player starts up and shows a black window while the sound is heard.  Is there an easy way to fix this?  And as long as I am asking, what is the easiest way to get dvd playback?  I haven't tried it yet but from what I've read on this forum it sounds like it might be tricky.

[Link!]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs")

Install all of those codecs and you should be able to play anything (including WMV) back in Feisty (except maybe stupid Real format... I hate that format). The section right under it will tell you how to get DVD playback, I believe it works well enough... I don't play dvds on my computer, can't vouch. I just use VLC for most of my movies, I like it better, you can search further down and find how to install VLC.

Oh and if your a bit uncomfortable with the Terminal/CLI, [linux command]("http://www.linuxcommand.org/") is good place to start learning. Just putting it out there.

Any questions, of course feel free to post again here.

---

### Post by anewguy on 2007-06-27
:KSThank you!  I will try all of that out tonight and tomorrow and see what happens.

---

### Post by starcraft.man on 2007-06-27
> **anewguy said:**
> :KSThank you!  I will try all of that out tonight and tomorrow and see what happens.

Your welcome. Btw, nice name, plan on being new forever? :p

---

### Post by anewguy on 2007-06-28
I think I must be doing something wrong so I'm posting a copy of the terminal window when I tried the things on the page.  Please let me know what I'm doing wrong, as I really am completely new at this.  Thank you.
dave@dave-ubuntu:~$ sudo apt-get install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras
dave@dave-ubuntu:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
dave@dave-ubuntu:~$

---

### Post by starcraft.man on 2007-06-28
Hehe, don't forget to read the little notes right under the title of the tut...

>  How to install Multimedia Codecs
    * Read #General Notes
    * Read #How to add extra repositories 

To save you the trouble, I assume its just you forgot to add all the extra repositories. Follow this guide before, then paste in the commands again, w32 and a few other restricted packages are in medibuntu I believe.

[Link!]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

That should do it, enjoy :).

---

### Post by anewguy on 2007-06-28
Thanks again!  It seems to be working now.:KS

Even if you're an old fart like me, I like to THINK I'm a new guy!!;)  I suppose someday I really should change that, kinda hard being a "new guy" at 52!:D

---

### Post by starcraft.man on 2007-06-28
> **anewguy said:**
> Thanks again!  It seems to be working now.:KS

Even if you're an old fart like me, I like to THINK I'm a new guy!!;)  I suppose someday I really should change that, kinda hard being a "new guy" at 52!:D

LOL! Wow... well, uh, no comment. Just knowing I started my computer times on DOS 4.x when was younger makes me feel old... and I still remember em.

---

### Post by anewguy on 2007-06-28
Heck, I started with computers in the pre-CP/M days - a lot has changed, eh?;)

I do have another dumb question in regards to the problem I posted here:

When I retried the w32codecs line it failed again.  When I check in my mail and try to play a movie clip (I guess it was wmv?) it still just goes into movie player and show a blank window with sound.

My guess??  I'm still quite stupid!!  Any ideas what I did wrong this time?  If it helps, the "source" I enabled was the  ubuntu restricted one - am I supposed to enable more?;)

Thanks for being so patient!!:)

---

### Post by starcraft.man on 2007-06-28
> **anewguy said:**
> 
I do have another dumb question in regards to the problem I posted here:

When I retried the w32codecs line it failed again.  When I check in my mail and try to play a movie clip (I guess it was wmv?) it still just goes into movie player and show a blank window with sound.

My guess??  I'm still quite stupid!!  Any ideas what I did wrong this time?  If it helps, the "source" I enabled was the  ubuntu restricted one - am I supposed to enable more?;)

Thanks for being so patient!!:)

After pasting in the new sources list you remember to import the gpg key (used for authentication) and then update right?

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

```
sudo apt-get update
```

Run those two concurrently in terminal (after I assume you pasted in the new sources list from guide). After that try:

```
sudo aptitude install w32codecs
```

That should do it I think. And its never a dumb question, everyone learns somewhere :).

> Heck, I started with computers in the pre-CP/M days - a lot has changed, eh?;)

*shudders in fright at how old that is.....*

---

### Post by anewguy on 2007-06-28
:popcorn:Well, I must have messed up again.  I'm including the terminal window when I did these.  Is it possible that the w32codecs have been removed?  The how-to said something about them being copywrite protected or something?

Sorry it's taking so long - I promise I'll get better as I try to understand this Linux thing!;)

---

### Post by anewguy on 2007-06-28
Oops-------- I pulled a Homer -> forgot to include the terminal window!!  Here it is:

dave@dave-ubuntu:~$  sudo wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -
OK
dave@dave-ubuntu:~$ sudo apt-get update
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Translation-en_US     
Get:1 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release.gpg [191B]     
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                                    
Ign [http://download.skype.com](http://download.skype.com) stable Release                         
Hit [http://download.skype.com](http://download.skype.com) stable/non-free Packages               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                              
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Sources
Fetched 194B in 2s (96B/s)
Reading package lists... Done
dave@dave-ubuntu:~$ sudo aptitude install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No candidate version found for w32codecs
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
dave@dave-ubuntu:~$

---

### Post by starcraft.man on 2007-06-28
w32codecs is most certainly still there, I just checked. Problem is medibuntu isn't in your sources.list.

Open terminal and paste in:

```
gksudo gedit /etc/apt/sources.list
```

This opens up your sources list with the gedit program, gksudo authorizes the application with root powers to edit (its normally a protected file, its important).

Scroll to the bottom of list and paste this in:

```
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://packages.medibuntu.org/ feisty free non-free
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main
```

Save, then do:

```
sudo apt-get update
```

If it asks for a missing key, reimport the medibuntu key with the above command.

Then run:

```
sudo aptitude install w32codecs
```

Oh and one more thing, while your at it... give VLC a try. You might like it better for watching wmvs.

```
sudo aptitude install vlc
```

I hope that does it, I'm almost off to bed...

---

### Post by anewguy on 2007-06-28
I think I'm going to need to do some reading of the page you pointed me to and what else I might find.  The .wmv file has been saved from the email to my desktop, where the preview shows a picture from the clip.  If I open it with VLC I still get a video window that is blank but the sound plays.


I REALLY appreciate what you've done tonight to help an old "new" guy along!:D  I hope all the help on this forum is as good and patient as you are!  Everything went in exactly as you said it would so that part of things worked great!

THANKS SO MUCH!!:KS

---

### Post by starcraft.man on 2007-06-28
> **anewguy said:**
> I think I'm going to need to do some reading of the page you pointed me to and what else I might find.  The .wmv file has been saved from the email to my desktop, where the preview shows a picture from the clip.  If I open it with VLC I still get a video window that is blank but the sound plays.


Thats odd, VLC plays WMV natively without any codecs... you sure you opened it in VLC? Maybe its a corrupt WMV. Only other thing I can think of is it requires the Windows DRM scheme to play? Anyway, I dunno >.>.
> 
I REALLY appreciate what you've done tonight to help an old "new" guy along!:D  I hope all the help on this forum is as good and patient as you are!  Everything went in exactly as you said it would so that part of things worked great!

THANKS SO MUCH!!:KS

No problemo, heres a bunch of other links to help ya along....

[Ubuntuguide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") site and [psychocats]("http://www.psychocats.net/ubuntu/") for General basics. [LinuxCommand]("http://www.linuxcommand.org/") for learning the CLI/Terminal. [Ubuntu Wiki]("https://wiki.ubuntu.com/") for advanced and specific questions (also forums of course) [Linux app finder]("http://linuxappfinder.com/") for finding programs and applications that suit you.

Oh and ya, I'm pretty damn patient... I mean I been with Bell Sympatico all these years, that takes a real amount of patience. Anyway, best of luck with that. Any more trouble, just post back and someone else will probably get to ya, I think I'm likely off to sleep.

---

### Post by tarek on 2007-06-28
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by FDavid on 2007-06-29
I have a similar but opposite problem. 

After installing the packages the movie viewer requested  to play .wmv files, I was able to get picture but no audio playing back .wmv files.

Any suggestions?

---

### Post by anewguy on 2007-06-29
I'd be interested in any more help as well.  I followed the link provide by tarek, with the first 2 steps being the same result as before.  Once it gets into the other players and media types, I get lost - I just don't know that stuff!;)  Thanks for all the help from everyone, and please let me know if you have any other ideas for an old duffer like me.:p

---

### Post by tarek on 2007-06-29
> **anewguy said:**
> I'd be interested in any more help as well.  I followed the link provide by tarek, with the first 2 steps being the same result as before.  Once it gets into the other players and media types, I get lost - I just don't know that stuff!;)  Thanks for all the help from everyone, and please let me know if you have any other ideas for an old duffer like me.:p

Even though I have 7.04 I still use the command for 6.10 and it worked to play all movies, try this:
```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
```

Now for the DVD, enter the following command:
```
sudo apt-get install libdvdread3 libxine1-ffmpeg
```

Now try playing a DVD and a .wmv.

tk

---

### Post by anewguy on 2007-06-29
Thanks for the help.  The first step went okay, the second said nothing was done because I already had the newest versions.  I tried opening the wmv in mplayer, same result.  I tried opening the the wmv in VLC with the same result.  I still have sound, but no video.

I am a real novice at any of this and not that smart about computers, so I'm probably doing something stupid again:p  

Thanks again for the help, everyone!;)

---

### Post by tarek on 2007-06-29
How about the DVD? does it play now?

---

### Post by anewguy on 2007-06-29
Hello, again.  I tried a DVD with Movie Player and with VLC and still the same result - sound but no video.

Thanks again for not giving up on me!!:KS

---

### Post by anewguy on 2007-06-29
bump

---

### Post by tarek on 2007-06-29
Sorry anewguy, I don't know why it's doing that. My last shot, are you using beryl/compiz?

---

### Post by anewguy on 2007-06-29
I installed those but I don't think they work, and I have no idea how to uninstall them.  Could they be the problem?:D

Thanks again!!;)

---

### Post by tarek on 2007-06-29
I had some video issues when I had beryl but since you're not using beryl/compiz I don't think they're the problem. :( sorry!

---

### Post by rodami on 2007-06-29
I have a similar problem, but its mosotly a weird bug, i get the black screen with sound, but if i move the window or wobble it, i get video, but if i open anther window of anything else and move it on top, i lose the videoo and have to shake the player screen again.

---

### Post by tarek on 2007-06-29
> **rodami said:**
> I have a similar problem, but its mosotly a weird bug, i get the black screen with sound, but if i move the window or wobble it, i get video, but if i open anther window of anything else and move it on top, i lose the videoo and have to shake the player screen again.

Yep, that was the problem I had but I found the fix here:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL")

This should fix your problem.

---

### Post by anewguy on 2007-06-29
;)I tried your wobble the window thing, but I still don't see video.  A weird question:  what type of video card/chip are you running?  I know my PC uses a Via S3G Unichrome Pro integrated graphics processor - I wonder if that has something to do with it?  I had to install the driver as detailed in the Unichrome project pages.  Perhaps this is a problem?:D

---

### Post by tarek on 2007-06-29
> **anewguy said:**
> ;)I tried your wobble the window thing, but I still don't see video.  A weird question:  what type of video card/chip are you running?  I know my PC uses a Via S3G Unichrome Pro integrated graphics processor - I wonder if that has something to do with it?  I had to install the driver as detailed in the Unichrome project pages.  Perhaps this is a problem?:D

I just thought of something, can you please play a video in one player and play another video in a different player **while the first one is playing**. Let me know if you can see the video now.

tk

---

### Post by anewguy on 2007-06-29
:Dtarek:  I'm going to take some time this weekend to go through the link you provided.  The driver I installed from Unichrome includes 3D support, so after briefly scanning the document I would bet that is my problem.  It looks a little involved so I will need to take my time with it.  It sounds like that is why I couldn't get Beryl to do anything (by default I don't think the 3D XGL stuff is on).  Also, I remember reading some stuff somewhere that pretty much said you can't even come close to running Beryl on my cheap setup, but I thought what the heck, let's try it.  I think I did something stupid again and got myself in trouble!;)   Slowly but surely I guess I will learn some of this stuff!

---

### Post by anewguy on 2007-06-29
tarek:  Just saw your message on trying 2 players at once.  Guess what?  It DOES show video in the second player, and it still shows even after I close the first player!!  Does that mean anything?/:KS

---

### Post by tarek on 2007-06-29
YESSS!! we're getting closer ... it's video overlay, are you connected to a tv or a second screen?

---

### Post by anewguy on 2007-06-29
No second screen or TV - just the LCD in my laptop.  BTW - where the HECK did you learn all this stuff, anyway?:p

---

### Post by anewguy on 2007-06-29
I'm sorry, but I have to leave for a while.  Thanks for your help so far!!;)

---

### Post by tarek on 2007-06-29
I have the same problem with my ATI card, but it only happens when I watch movies on TV. They work fine on my monitor though :)  I have to play two movies and then close one to watch the other on TV.

For some reason the problem disappeared when I installed beryl using the tutorial in the link I posted and that fixed the wobble problem + video overlay + beryl

I created a separate session for beryl, and the problem disappears only there if I use the regular gnome session it comes back. In the tutorial you'll see how the problem is fixed.

3 in 1 solution :D

Here's the url: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL")

Sorry! I should have thought of that before but it just didn't cross my mind at the time.

The tutorial looks long because it gives two examples for kde and gnome but it only takes 5 min to setup.

Let me know it goes for future reference, thanks.

tarek

---

### Post by anewguy on 2007-06-30
;)I've tried the link several times tonight but it just gets kicked back to me as a URL that isn't reachable.  I'm hoping "they" maybe have their servers down for some reason, since it did work earlier.  I want to be sure and let you know the result when I get done.

Thanks again!:D

---

### Post by anewguy on 2007-07-05
tarek:  I wanted to keep you up to date on what's going on.  I have very much appreciated your help.  I messed up some things so I borrowed a 6.10 CD from a friend and installed it instead of 7.04.  I didn't do anything to try to set up beryl, etc., but the video still doesn't show.  I think I may have found out why, however:

I have a VIa S3G UniChrome Pro integrated graphics controller (I think that's what you call them), so I found another post that mentioned this link:

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)


I used it to install the 2D and then the 3D drivers for my video card and didn't have the errors I had before.  I did notice this at the bottom of the post:

#

I do not have any picture when playing videos
This mostly happens when using a laptop and is caused by openChrome not supporting Xv correctly on some models. You can try to change the video driver in Xine to "gl" or "x11" and see if that helps. This problem does not appear when not using the integrated LCD and using an external monitor instead. The OpenChrome ticket for that is located here: [WWW] [http://www.openchrome.org/trac/ticket/40](http://www.openchrome.org/trac/ticket/40)
#


I'm not sure what it all means, particularly the part that says "Xine", but I thought maybe this was my problem.  What do you think?;)

---

### Post by tarek on 2007-07-07
Sorry anewguy, I don't know why either. As I said I solved the problem by playing two videos then closing one of them. Not the best solution but it works.

tarek

---

### Post by anewguy on 2007-07-07
Thanks tarek!  It appears it is indeed a problem with the openchrome driver and the chipset.  I do appreciate so much the help you have been.  :D

---

### Post by anewguy on 2007-07-07
:(To all reading this thread with a similar problem:  I upgraded to 7.04, which of course messed up my "via" driver for xorg.conf, so I went back to the default "vesa" driver until I get time to go through building the driver again.  The end result, is that in 7.04, using the default "vesa" driver in xorg.conf, movies, .wmv, etc., play fine.  I believe this indeed points to the openchrome driver as the root of my problem.

If you have an integrated graphics processor using the k8m800(?) chipset, you will by default get lower resolution but be able to play movies, etc., if you use the default "vesa" driver.

If someone has a way around this please post back to this thread.;)

---

### Post by anewguy on 2007-07-08
tarek - I found this in a post about using compiz - perhaps it can help you (I don't have the drivers installed so I can't do it now anyway).


  #26   Report Post  
Old 2 Weeks Ago
crimesaucer's Avatar 	
crimesaucer crimesaucer is online now
Has an Ubuntu Drip
	  	
Join Date: Jan 2006
Location: Traveler
Beans: 709
Xubuntu 7.04 Feisty Fawn User
Re: Compiz Fusion: A guide with a warning for new users.
I fixed my Xine movie palyer like this: The Settings-->--Set Up-->--Video-->--I changed the driver from "auto" to "xshm" and it worked for playback.

I also fixed the transparent video like this: ccsm-->--General-->--Opacity Settings-->--Window Opacities-->-- then edit the string and take "Unkown" off of the list.
__________________
We are the music-makers, and we are the dreamers of dreams- Willy Wonka.
Reply With Quote

---

### Post by tarek on 2007-07-10
> **anewguy said:**
> tarek - I found this in a post about using compiz - perhaps it can help you (I don't have the drivers installed so I can't do it now anyway).


  #26   Report Post  
Old 2 Weeks Ago
crimesaucer's Avatar 	
crimesaucer crimesaucer is online now
Has an Ubuntu Drip
	  	
Join Date: Jan 2006
Location: Traveler
Beans: 709
Xubuntu 7.04 Feisty Fawn User
Re: Compiz Fusion: A guide with a warning for new users.
I fixed my Xine movie palyer like this: The Settings-->--Set Up-->--Video-->--I changed the driver from "auto" to "xshm" and it worked for playback.

I also fixed the transparent video like this: ccsm-->--General-->--Opacity Settings-->--Window Opacities-->-- then edit the string and take "Unkown" off of the list.
__________________
We are the music-makers, and we are the dreamers of dreams- Willy Wonka.
Reply With Quote


I tried it using mplayer and it worked! Thanks a lot :D

tarek

---

