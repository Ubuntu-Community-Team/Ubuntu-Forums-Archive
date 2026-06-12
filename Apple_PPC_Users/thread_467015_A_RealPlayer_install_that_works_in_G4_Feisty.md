---
title: "A RealPlayer install that works in G4 Feisty"
date: 2007-06-07
forum: Apple PPC Users
---

### Post by thedarky on 2007-06-07
Howdy,
After a lot of dead ends looking for an install package for RealPlayer, so that it will work as a Firefox helper and plugin, I've had success - with much help from stmiller.

Here's what works and in newbie steps:

There is no official package for RealPlayer, you have to go and get a package from the open source Helix community, add a package of dependant things that you can get via Aptitude, follow the manual install steps from the official support documentation and the player will work on a 1.25 eMac (USB 2.0).

First, here's the official documentation link:
[https://wiki.ubuntu.com/PowerPCFAQ#head-4c512dc1fe442052d2bb368afeb4f8add9f83d71](https://wiki.ubuntu.com/PowerPCFAQ#head-4c512dc1fe442052d2bb368afeb4f8add9f83d71)

The basic steps are good, except that before you run the RealPlayer installer, you have to get a dependant package from the official repository, which you do with the following code:
```
sudo apt-get install libstdc++5 libstdc++5-3.3-dev
```

and there is an error in the chmod code line - there shouldn't be a space between "+" and "x".  Another way of making the RealPlayer installer executable is to use the GUI, context click the installer and change the permissions in the 'properties' menu item. 

And you have to put the full name (ends in .bin) of the RealPlayer file whenever you are including it in commands.

For the final step, accepting the default means just hit enter without typing anything.

That gave me a working RealPlayer in Feisty today, and I'm listening to a stream from the BBC as I write this.

Good luck beginners.  And here's to someone getting a community "official" package with the extra dependent files up soon.

---

### Post by stmiller on 2007-06-07
Okay that you for your help! I'll edit the wiki with the corrections.

---

### Post by ubuntubrian on 2007-06-07
Great How-To!
I followed the instructions and tried to watch a C-Span video in Firefox. I can't get the url for it but I did add the /opt/RealPlayer/realply.bin to my Firefox config. I click the link and Real Player pops up! 
I get an error that the player can't play the file as it needs the "sipr" component. I checked the codecs in /opt/RealPlayer and there is a sipr.so. Any ideas? I can play the stream with xine or xfmedia without video which I was hoping to get with RealPlayer.
Thanks

---

### Post by ubuntubrian on 2007-06-07
Another ? How did you configure Firefox to use your newly installed Real Player?
I went to BBC and no go.
Thanks

---

### Post by stmiller on 2007-06-07
> **ubuntubrian said:**
> Great How-To!
I followed the instructions and tried to watch a C-Span video in Firefox. I can't get the url for it but I did add the /opt/RealPlayer/realply.bin to my Firefox config. I click the link and Real Player pops up! 
I get an error that the player can't play the file as it needs the "sipr" component. I checked the codecs in /opt/RealPlayer and there is a sipr.so. Any ideas? I can play the stream with xine or xfmedia without video which I was hoping to get with RealPlayer.
Thanks

Hi, you should not need to do anything in Firefox. And that's not the correct realplayer executable.

When RealPlayer installs, it automatically puts the correct plugin in the correct location for Firefox.

Try to run the installer again, but first do this in a terminal:

$ sudo mkdir /opt

[ I might have to add that step to the FAQs. ]

And run the installer again as in the FAQs.

---

### Post by Adam590 on 2007-06-08
On running the install command, I get:

./realplay-10.0.4.750-linux-2.2-libc6-gcc32-powerpc.bin: 1: Syntax error: "(" unexpected

(I get the same thing with both files mentioned in the wiki - the 10.0.4 version and the 10.0.5)

---

### Post by ubuntubrian on 2007-06-08
I've got a /opt directory as you see in the command. I added the RealPlayer directory during installation for some reason that I can't recall.
Unfortunately I have RealPlayer installs from the past and I hoped that by installing into /opt that I could use this install in an isolated manner without trying to track down all those other installs and their files. I currently am using RealPlayer8 codecs to at least get audio in Xine. 
I had added the Firefox extension Mediaconnectivity in an effort to get some better functions and that can be setup to use the RealPlayer as long as I add the correct command. Why doesn't /opt/RealPlayer/realplay.bin work? I can start the player from the command line with that command.
Sorry to make this complex but as I have tried for 3 years to get connected with various players my system is sort of "unique".
Thanks

---

### Post by ubuntubrian on 2007-06-08
Sorry, I had a typo in my command:
/opt/RealPlayer/realplay.bin
I didn't realize it on my last post but I do have it correctly in my Firefox config.
Interestingly, RealPlayer8 launches and plays audio streams in Mozilla Browser

---

### Post by stmiller on 2007-06-08
> **ubuntubrian said:**
> Sorry, I had a typo in my command:
/opt/RealPlayer/realplay.bin
I didn't realize it on my last post but I do have it correctly in my Firefox config.
Interestingly, RealPlayer8 launches and plays audio streams in Mozilla Browser

Sort of OT, but It is not so good to link directly to a program directory to that file. The executable is in

/usr/bin

or 

/usr/local/bin

like

/usr/bin/gedit

In this case, it's

/usr/bin/realplay

----------------

But: you should not have to do this at all. You don't need to specify anything in Firefox.

> I had added the Firefox extension Mediaconnectivity

The realplayer from helix listed on the PPCFAQs includes a proper Firefox plugin when you install the program. This media-thing could possibly cause more trouble that it's worth. B/c you will have two different plugins fighting over the same type of content.

---

### Post by Adam590 on 2007-06-08
Hate to bang on about this, but I started from scratch and I'm still getting the same

...Syntax error: "(" unexpected

when I run the install command.  Any ideas?



*Possibly off-topic disclaimer*
Alternatively, would it be easier to enable either Windows Media or Quicktime, say, in the next hour and thirty minutes? I really want to watch the space shuttle launch. :)
Using Firefox on Ubuntu 7.04

Thanks.

---

### Post by Auria on 2007-06-08
> **Adam590 said:**
> 
Alternatively, would it be easier to enable either Windows Media or Quicktime, say, in the next hour and thirty minutes? I really want to watch the space shuttle launch. :)
Thanks.

Since neither windows media nor quicktime run on linux and wine doesant run on ppc, i don't how you can even think it's possible ;)

---

### Post by ubuntubrian on 2007-06-08
I'll disable MediaConnectivity and see what happens. It's been a great help though because I have been able to watch windows media with mplayer in Firefox and couldn't before. Of course I installed all the plugins I could find.
I can also just change the command to /usr/bin/realplay and avoid conflicts.
BTW, mplayer has plugins to play both wmv and mov files so it is possible to play those in Linux ppc. Xine plays quicktime also as does VLC.

---

### Post by ubuntubrian on 2007-06-08
I would be happy to move this part to another thread if anyone wants a general discussion on media in Ubuntu PPC. I'm watching a re-run of the shuttle launch now on VLC using MediaPlayerConnectivity. I saw the last couple minutes as the shuttle separated from the main tank-cool.

regarding RealPlayer- it launches but won't play the file.

---

### Post by stmiller on 2007-06-08
> **Auria said:**
> Since neither windows media nor quicktime run on linux and wine doesant run on ppc, i don't how you can even think it's possible ;)

As Ubuntubrian just said, you can watch quicktime and windows media streams in Linux. VLC will do the job for most all streams out there. I watch dl.tv's live windows media stream in VLC in PPC Linux.

---

### Post by ubuntubrian on 2007-06-08
Start another thread?
stmiller, you sound like you have valuable experience if you're willing to share.:)

---

### Post by stmiller on 2007-06-09
> **ubuntubrian said:**
> Start another thread?
stmiller, you sound like you have valuable experience if you're willing to share.:)

Ha! Well, it's thanks due to developments in ffmpeg, actually. The recent ffmpeg releases can play back flash video, among other popular codecs. This was incorporated into the recent VLC release, and we now have support for every codec under the sun in PowerPC Linux, x86_64 Linux, OS X and Windows.

---

### Post by thedarky on 2007-06-10
The Firefox add-on helps with pulling out the urls from text playlist files that can't be parsed by the Firefox plugins.

It's worth having, just to do that, in my opinion - - I tried to follow instructions on opening a playlist file in a text editor to find the urls inside it and got very giddy indeed!
My reading tells me there's no Real media codecs yet to give ppcs streaming real video, but real audio should work for all public radio streams.

A sticky thread for unsupported media would be a good idea.  I second Ubuntubrian's motion.

---

### Post by ubuntubrian on 2007-06-10
Sticky thread a good idea! I just reinstalled Gnash as per:
 [http://ubuntuforums.org/showthread.php?t=460198](http://ubuntuforums.org/showthread.php?t=460198)
and I can watch YouTube videos in Firefox. It took a bit of work but I got it.
what version of VLC, Ffmpeg are you referring to Stmiller? In the repositories or from source?

---

### Post by stmiller on 2007-06-10
> **ubuntubrian said:**
> Sticky thread a good idea! I just reinstalled Gnash as per:
 [http://ubuntuforums.org/showthread.php?t=460198](http://ubuntuforums.org/showthread.php?t=460198)
and I can watch YouTube videos in Firefox. It took a bit of work but I got it.
what version of VLC, Ffmpeg are you referring to Stmiller? In the repositories or from source?

Well the VLC now in Feisty has the nice ffmpeg inside. So everything plays back now. Past releases of Ubuntu did not have this new VLC in the repos.

---

### Post by ubuntubrian on 2007-06-10
hmm...I'm still running Dapper so I've been trying to build VLC from source and don't want to get too far without getting everything right. Any experience with this would be helpful.

---

