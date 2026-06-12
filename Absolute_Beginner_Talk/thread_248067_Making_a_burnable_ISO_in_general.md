---
title: "Making a burnable ISO in general"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2006-08-31
First, let me apologize because I know that this subject has come up before. I did a search on how I might be able to make back up copies of my DVD's, and A LOT of things came up, but two things prevent me from being successful. One, since there are so many threads, it's difficult to find a to the point answer. And secondly, for the same reason, it's hard to find anything specific to my query. 

I installed DVD::Rip but that program seems a bit cryptic, and I don't really see any options to make an ISO. I then installed K9 copy, which seems pretty easy to use, and does have an iSO option, but I haven't been successful with it yet. 

Lastly, after I mount a DVD, there's an option presented when I right click on the drive/movie, that basically lets me rip to ISO. Is this part of K9's program ? Because I never tried to do this before installing either one of the programs I mentioned above. Anyway, I was able to make an ISO this way, but the size of it is 1 gig larger than a blank DVD will support. It came out as 5.7 gigs, rather than 4.7. Not sure of why either. 

It seems like I'm on the right track, but am still missing something here. I would much rather not install Wine, though it's looking like a plausable option if I can't get anything else working. Though I believe that I should be able to, no ? So at this point, any help with K9 or the second method I mentioned (right clicking on device) would be greatly appreciated. 

Doug

Edit: I think I just realized, that even if I am able to make an iso with K9, it too, will be about 6.7 gigs in size. How is it possible to make this burnable to a single layer DVD ?

---

### Post by orb9220 on 2006-08-31
Was to hard to get all the different programs to do what I needed. I have been ripping my dvd library for two years now in windows and linux apps are still not up to the job. I have run in the same problem of dvd being ripped down to 4.7 why beats me since the image HAS TO BE! 4.38 GB to fit on a dvd.

So for me since I always used dvdshrink in windows I now use it in linux works great and gives me alot more control over final product. 
Reauthor just for movie or burn to Hd as ts video folder which is great if your burning to a fat32 partition. Or my fast way is to burn as iso so I can just right click in gnome and burn iso image. I also set preferences  to custom size the defualt is 4464mb which is a tad high for some brand types so I chose 4456mb and never have had problems with burns.

[https://help.ubuntu.com/community/DVDShrink](https://help.ubuntu.com/community/DVDShrink)
[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)

---

### Post by Sweet Spot on 2006-08-31
Thanks for the reply. Are you serious though about not being able to find something native to Ubuntu/Linux that can do the job ? There HAS to be something that does it besides an emulator ! I mean, everyone here hails Ubuntu as being so desktop ready and such, but (and this isn't meant as a bash) there are some really basic things that I just can't seem to get working in Ubuntu, which would make me say "yeah, it surely IS desktop ready".

I understand that there are laws which prevent Ubuntu from having certain things installed in the base package, like Mp3 decoders/encoders and such, but all these things are bypassed by installing them afterwards. So I find it a bit hard to swallow, that there's not one single **simple** program which has been made to rip a proper DVD iso ? 

After all, I've just installed K3b, which seems like a very (even though I'm using Gnome) able burner, which works with ISO's. So someone please tell me (not being sarcastic, because I don't know) what the use is of a program creating an iso file which is too large to fit on a standard DVD ? 

And for clarification also please, when I right click on the iso file on my desktop, and am given the option to burn that iso, is that a stand alone feature native to Gnome, or is that part of K9copy or a different program ? 

Lastly, someone PLEASE tell me, that there's a program/way (easy) to make a burnable movie/DVD iso ! ?  Otherwise, I'm left to boot into Windows and use DVD shrink. I REALLY don't feel like hassling with Wine. It's bad enough that there are so many redundant programs sitting on my menu. I'd love to have just ONE program for each task, ala Zenwalk. Now THAT, is a good concept. (Too bad they just don't have all the necessary programs and only have a small a** repository list)

Doug

---

### Post by Toxicity999 on 2006-08-31
To be fair DVD ripping and A/V Encoding isn't 'basic' really ;)

Also a slight nitpick... Wine Is Not an Emulator... (Wine... funny how that works out aye?)

Second... Any app that is made for windows that works fine in Wine to ME is part of the Ubuntu arsenal. They aren't Microsoft they're provate developers. It's not much different than someone releasing something in an RPM only you need to do a touch of work to convert it to deb or install manually. (I know you can use some tools to install it regularely... don't get me started!.) My point is... if it works in ubuntu... it is part of ubuntu in many ways. Maybe it's not native but so what. if it works it works! And you aren't on windows to do it... I ronically you're using a free implementation of windows to native linux apis =O

---

### Post by orb9220 on 2006-08-31
right-click feature is gnome related and built-in. Wine is not an emulator  in fact it works faster than the window version.

The weak link in the linux apps are gui burning apps are pretty new to the linux scene. And compression options seem imature from an gui perspective.

When I used k3b it took 75mins to rip then another 7mins to burn iso to Hardrive. DVDshrink took 53mins to rip then right click burn iso took 8mins.

I have tried k3b,acid:rip,gnomebaker,k9,and bonfire which is promising but still an infant. 

Good Luck but shrink under wine works as fast or faster than running in windows. And again it is not an emulator.

---

### Post by Sweet Spot on 2006-08-31
Ok, fair enough. It's not an emulator. I understand now. It's more like a catylist which gets programs working rather than a noob like me having to compile or install a package in some (foreign) fashion. Pretty much sum it up ?

Now, as for Wine in general, is it pretty lite on the system resources, or is it going to be a hog which prevents me from multi-tasking ? To be honest, I'd love to just uninstall all the stuff that I tried, and just use DVDshrink and right click burn if that works well. 

What do you guys use for burning data CD's in general then ? Well, data and Music (mp3; wav; audio stuff) too ?

Thanks for the help, 

Doug

---

### Post by orb9220 on 2006-08-31
Noob ripp movies while chatting in gaim and browsing in firefox with amarok playing music.

All on a 1.3ghz 640mbram system.

---

### Post by Sweet Spot on 2006-08-31
Good enough for me then ! Thanks man. By the way, I like your avatar, but it creeps me out a tad. :tongue:

---

