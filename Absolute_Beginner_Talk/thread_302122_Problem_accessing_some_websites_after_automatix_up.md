---
title: "Problem accessing some websites after automatix update &amp; other issues!"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by Felix Jay on 2006-11-18
Hi there, 

Just used automatix for the first time (wow!) and now for some reason I can't access some websites - torrentspy and redissue among them. Anybody have an inkling as to why that should be the case? 

ALso on playing vids from the web in VLC it flickers! Again any reason? 

I've also just popped a DVD in that has some mpegs etc saved on it and I was told that: 

**You do not have the permissions necessary to view the contents of "cdrom0".**

I'm on Dapper 6.06 - any help appreciated!

---

### Post by Felix Jay on 2006-11-18
bumpty bump!:mrgreen:

---

### Post by Felix Jay on 2006-11-18
Just noticed that the picture in Mplayer flickers as well and I can't get sound! This on a normal DVD.......

Is it something to do with JAVA as Automatix didn't install this...

---

### Post by Felix Jay on 2006-11-18
Just noticed that the picture in Mplayer flickers as well and I can't get sound! This on a normal DVD.......

Is it something to do with JAVA as Automatix didn't install this...](*,)

---

### Post by nickpaton on 2006-11-18
Hi again Felix!!

Fire up Automatix2

You will note the warnings about not being able to use w32, libdvdcss2 and other non-free codecs if you live in the USA, or to be aware that if you live there, of that proviso.  Say no more..

As a minimum ' package' set you need to have the following loaded via Automatix2:

_File Sharing_: None

_Internet_: Sun Java 1.5JRE; Thunderbird (great email package)

_Miscellaneous_:  Extra fonts; Nautlilus Scripts (maybe this is an option!)

_Multimedia_: Aud-Dvd codecs; Flash player; Mplayer and FF plugin; Media Players; Multimedia Codecs; Real Player.

_Office_:  Acrobat reader

I tend to load them a section at a time.

Exit Automatix2.

Ffox not accessing some sites:

Start Firfox.

In address bar (where it says [http://www.whatever_your_search_engine_is.com](http://www.whatever_your_search_engine_is.com))

type in instead:

```
about:config
```

and hit enter.  This gets you into Firefox configuration files.

Scroll down until you find the line starting with:

```
network.dns.ipv6disable 
```
and ending with "false"

click on the line and "false" will change to "true"

Close down all open firefox browsers (no need to save anything etc), and restart firefox again.

Hopefully that will cure that problem.  If not there are more tweaks but that's the main one.

Not sure about your flickering display, but we'll deal with that one if still not cured after the Automatix2 updates.

Good luck again M8 - always a pleasure doing "business" with you - LOL:)

---

### Post by Felix Jay on 2006-11-18
Hey Nick, 

I tell ya I fired up Automatix and pretty much downloaded everything! Awesome application. 

The weird thing is since then I've had no sound! Before all the downloads I heard the drums but since then nothing! Pretty strange.. 

Believe it or not I knew about the firefox & ipv6! It's my one bit of knowledge.. so I'm not sure why I can't access some sites. And when ever I try and stream something I  have no sound and (esp in VLC) the picture is flickery - dead weird......... 

As ever any advice much appreciated!

---

### Post by xpod on 2006-11-18
Im not sure if it`s the same issue but when i first had dapper with all the usual`s from Automatix i could`nt get sound on flash sites like google video and youtube.....but all the system sounds were fine.

There is a simple fix i was given but i dont want to go giving you code`s to type in that might not be relevant......

If it is then you could try this
```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
ln -s /tmp/.esd-1000 /tmp/.esd
```


Thats all i had to do to get my sound up and running.Had to reboot too if i recall correctly.

Of course there are any number of ways sound seems to get messed up at times.There`s a "multimedia audio selector" in dapper thats good for doing sound checks and changing what type gets used,Sometimes it needs enabled via the "alacarte menu editor" buts it`s a handy wee app.

You can also check the "alsamixer" by right clicking your volume icon or typing "alsamixer" in the terminal.

Hope something there helps you

---

### Post by Felix Jay on 2006-11-18
Cheers Xpod I'll try that! 

I had a look in alsamixer and everything is up high so a bit baffled to be fair!

---

### Post by nickpaton on 2006-11-18
Jerky DVD - you may need to enable DMA, so closely follow the steps in:

[https://help.ubuntu.com/community/DMA]("https://help.ubuntu.com/community/DMA")

I too will have a think - any ideas Xpod?

EDIT:  reread your post and you are not referring to DVD's but to streaming....I'll think about this, but may be tomorrow before I get back.

---

### Post by Felix Jay on 2006-11-18
Cheers to you both - I'm okay on DMA - all enabled but still no sound :confused: 

No worries on the time scale I'm being told off as I write so gotta skip!

---

### Post by nickpaton on 2006-11-18
I believe your problem could be that Automatix2 installs flash 7 when you want flash 9 beta.

So go into Automatix and uninstall Flash.

Then go to this link and follow the instructions:

[http://ubuntuforums.org/showthread.php?t=279990]("http://ubuntuforums.org/showthread.php?t=279990")

To help you a little - extracting from the above post:

You can now install via a deb package, thanks to trevino for this.

```
flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb
```(Firefox Plugin)

Once it's downloaded, go into your Home folder and double click it and using the installer, allow it to be automatically installed.

I believe that should be it.

The other thing that has occurred to me is that you are not using Totem.xine, but totem.gstreamer, which does not work in Dapper.

Synaptic package manager can be found in System > Administration > Synaptic

Go into synaptic, and in search type: totem

If you see that totem-gstreamer is installed (green square), and totem-xine  isn't, then you need to uninstall gstreamer, and then install xine version.  Right click on square against each package and click uninstall / install).
I would suggest doing the uninstall and then the install second time round.

No sound:

In the toolbar at the top, just to confirm that you have a loudspeaker icon and that it's not got a cross through it (sound turned off), or isn't even there.
If it's there - just to confirm one more time - double click on it to bring up alsa mixer, and make sure nought is turned off or disabled.

Next thing.

Carry out the following in the Terminal:

[http://ubuntuforums.org/showthread.php?t=227217]("http://ubuntuforums.org/showthread.php?t=227217")

---

### Post by Felix Jay on 2006-11-18
Hey Nick, 

Funnily enough I don't have G-streamer installed - it's telling me I have Xine as a player so to speak but I then installed the firefox plug in so I'll see if that makes any difference...... 

This will sound so dumb but I went into automatix but couldn't find flash (doh) - what am  Ilooking for as I'm ready to install 9 beta! 

Many thanks again.........

---

### Post by Felix Jay on 2006-11-18
I'm an idiot again! I did have gstreamer! I don't any more!

---

### Post by ciscosurfer on 2006-11-18
Are you using Automatix or Automatix2?

---

### Post by nickpaton on 2006-11-18
Get rid of -gstreamer and put on -xine.

And you may find that you have already installed flash, and it will be under the "uninstall" list under "multimedia".

---

### Post by Felix Jay on 2006-11-18
Jeez - I went there and must have just missed it - cheers Nick and thanks for asking Cisco! (automatix 2). It's now gone!

---

### Post by xpod on 2006-11-18
> I too will have a think - any ideas Xpod?

Errrrrrrrmmm.:-k ](*,) :confused: [-( 

Ask nick.:mrgreen:

EDIT:good luck with Flash 9.0

---

### Post by nickpaton on 2006-11-18
> **xpod said:**
> Errrrrrrrmmm.:-k ](*,) :confused: [-( 

Is this one of your X-rated comments then??

> **xpod said:**
> Ask nick.:mrgreen:

WOT - are you trying to say I'm a type of poison LOL!!!

---

### Post by Felix Jay on 2006-11-19
Cheers chaps - the thing hung like forever but i think I've installed it as I can now access Red Issue & hotmail! Happy days.......

Still no sound though! 

Oh & Nick I've assigned a static IP as per the other thread but I was having a problem that ever time I used ubuntu it would change my DNS server settings - do I need not worry about thtan ow as I have this static one???? 

As ever confused! :mrgreen:

---

### Post by Felix Jay on 2006-11-19
Knew it was too good to be true! Have just got a notice saying "an error occured - "unknowen error: 'exceptions.sytemerror" (E: the package flashplugin-nonfree needs to be reinstalled, but I can't find an archive for it". 

What does that mean?!

---

### Post by nickpaton on 2006-11-19
Feliz - This can happen when you first start with Ubuntu (or anything new I guess), but it looks like it's starting to fall apart.
I know there's a real danger of you throwing your PC at me, but I would suggest a complete reinstall.
You've learnt a whole lot about how to install, and you're getting Azureus going, but it looks to me like it's going to be easier at this early stage to simply bung your install disc in again and install over your existing distro.

Sorry M8 - been there....done that...](*,)

---

### Post by nickpaton on 2006-11-19
One other thing - I may have given you wrong advise about removing Flash 7 b4 installing 9 beta - read somewhere that you DONT do that, and I cannot remember what I did.

Even so I think you are at the reinstall stage -shouldn't take too long LOL!!

---

### Post by Felix Jay on 2006-11-19
Ahhh your kidding me!! I'm not sure I could bear that heartbreak! 

The really weird thing is that I then tried reisnstalling teh package again about 20 mins and it's still going! Bit strange.....

Is there no other way out there?

---

### Post by Felix Jay on 2006-11-19
Or if I start again should I upgrade to edgy??

---

### Post by nickpaton on 2006-11-19
Are you man or penguin??!!!
When I first started I messed things up so often that I was reinstalling what felt like a dozen times a day.

Looking at what's happening to you:

Your sound has gone off for some reason when you installed Automatix, but we had been playing around with stuff before then.
Flash has been on and off like nobodies business.

I would go for it - look at it as a "Learning Experience".

100% sympathy etc, but it's not going to take too long is it?

Get your GF to minister to you in the way she knows best...

EDIT: Edgy - It's up to you, either works for me, but you'll need the same type of package as with Dapper.  Hey why not it's only a download and try it.

---

### Post by Felix Jay on 2006-11-19
What the hell - I'll upgrade! Im also on an AMD 64 so perhaps I should really get the proper package!! Here goes nothing!

---

### Post by nickpaton on 2006-11-19
NO DONT GO FOR A 64BIT PACKAGE - I didn't realise you were on that.

Use the 32bit version which works far far better - will fill you in later.

---

### Post by Felix Jay on 2006-11-19
Okay dokey - one last stupid question - when I upgrade will it save my router settings? I presume I'll have to reinstall azareus etc?

---

### Post by nickpaton on 2006-11-19
Router settings are stored in the router's firmware (like a small computer chip in the router).

You will lose your PC network settings in Network Manager, but make a note of them all.

I have been thinking...if you go for Edgy there are a lot of useful programs that are not available to you in Dapper, like Firefox V2, and possibly Flash 9 (could be wrong about that one though), but I did find that things loaded really nicely in Edgy.
Finally..the latest version of Bittornado is available which IMHO is easier and simpler to use than Azureus.

I'll keep an eye open for ya during the evening.

Would you mind sending me a PM when you are up and running?  Click on my name and "send a private message to this person" - it's easier than searching throu posts.

---

### Post by Felix Jay on 2006-11-19
Cheers for that Nick - It's an update I'll do probably later tonight or early next week! I will certainly PM you - I'm gonna need all the advice I can get!

---

### Post by nickpaton on 2006-11-19
I've just sent you a PM with instructions as to how to set yours up in case you dont know.

---

### Post by nickpaton on 2006-11-19
Felix - you need to read my PM about setting up PM's.  Your current settings do not allow me to send to you M8

EDIT:

Just below your name on any page, click on red "private Messages".

In new page LHS, Edit options

New page, scroll down to private messaging section, and put tick in "Enabling Private Messaging"

Option, but worth it, tick "Show private message notification pop up"

Down to bottom of page and "Save Changes"

Click on red Private Messages at to of page, if you're not already returned to this page.

You get back to the forums by clicking on top LH Ubuntu forums........Beginners etc

---

### Post by Felix Jay on 2006-11-20
Hey Nick 

You have mail!

---

### Post by nickpaton on 2006-11-20
> **Felix Jay said:**
> Hey Nick 

You have mail!

Hey Felix

I don't!!!

And still can't send one to you - bizarre

Same error message saying that you are not allowing people to send you PM's....You sure you've set everything up right?

Do you have a hotmail address or something?
If you are actually on line we can v quickly swap them and then delete them off the public forums and do it that way.
I'll await your reply, note yours, and then quickly send mine.

---

### Post by Felix Jay on 2006-11-20
hey Nick ,

No worries and yup everything is set up right as I ticked everything!

---

### Post by Felix Jay on 2006-11-20
The weird thing is it's telling me I have received a mail and sent one! Weird.......

---

### Post by nickpaton on 2006-11-20
Hi Felix

Now get rid of your hotmail address - I'#ve got it!



I'll send one to you now at hotmail.

Can you confirm receipt & I'll remove mine off the forums.

Since we're both in the UK, would it help for you to have my telephone number - I can hotmail it to you.  I get free calls in UK

---

### Post by Felix Jay on 2006-11-20
Cheers Nick! Email received! I'll send you a note of what my problem was last night.. Tel number might be useful!!

---

### Post by nickpaton on 2006-11-20
Hotmail sent!

---

