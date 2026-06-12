---
title: "itunes for Ubuntu."
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by GeorgiaBoot on 2007-11-16
I would Like to install itunes on my ubuntu PC. I have tried Amarok, rythmbox and I hate them. Both Freeze get extremely garbled and I really don't like the layout, I am just not impressed. Sorry guys just my opinion, but I feel whatever suites each individual person is what matters so someone might like amarok or whatever and one person might not. 

So since I use itunes on my PC I would Like to know how to get it on my Ubuntu?

Please Consider that I am completely new to Ubuntu so I need very detailed instructions. I am pretty sure I need Wine but really don't have a clue on what to do and where to put things. Thanks

---

### Post by hyper_ch on 2007-11-16
[http://appdb.winehq.org/appview.php?iAppId=1347](http://appdb.winehq.org/appview.php?iAppId=1347)

---

### Post by diskotek on 2007-11-16
however hyper_ch gave the solution what you wanted... i would like to recommend you listen and exaile also. they are not so different much from amarok but worth to try.
[http://www.exaile.org/](http://www.exaile.org/)
[http://www.listen-project.org/](http://www.listen-project.org/)

---

### Post by AndyCooll on 2007-11-16
> **GeorgiaBoot said:**
> I would Like to install itunes on my ubuntu PC. I have tried Amarok, rythmbox and I hate them. Both Freeze get extremely garbled and I really don't like the layout, I am just not impressed. Sorry guys just my opinion, but I feel whatever suites each individual person is what matters so someone might like amarok or whatever and one person might not. 

Fair enough ...that's my opinion regarding iTunes. Anyway, opinions aside, have you tried Songbird?
I believe (though I cannot confirm) that it's designed as a full mimic of iTunes.

:cool:

---

### Post by SunnyRabbiera on 2007-11-16
I dunno I feel amarok is much superior to itunes in many ways.
Exaile is pretty decent though

---

### Post by GeorgiaBoot on 2007-11-16
Thanks guys, Hyper I checked the site out and the only thing I could find was to download an older itunes version which I need but I don't know how to install it. I can't install an exe file. I know I need wine but I don't know how to get it and when I do get it I don't know how to install everything, so if you could give me some directions that would be great.


I already  looked at the other music players and I really don't like them. The only one I would be interested in was Songbird, but when I looked on the site all they had for download was a beta, do they have any stable releases?

Thanks for the help.

---

### Post by Inxsible on 2007-11-16
Ever since the release iTunes 7.0, its been a memory hog. I guess because they added fancy stuff like album covers and different viewing modes and such.

I like Amarok and Rhythmbox. Amarok doesnt go well with the Ubuntu theme (considering its a KDE app) but its nice.

---

### Post by monte48lowes on 2007-11-16
Install wine:

```
sudo apt-get install wine
```

or

```
sudo aptitude install wine
```

Mike

Once wine is installed the exe for iTunes can be installed from nautilus.

---

### Post by SunnyRabbiera on 2007-11-16
> **GeorgiaBoot said:**
> Thanks guys, Hyper I checked the site out and the only thing I could find was to download an older itunes version which I need but I don't know how to install it. I can't install an exe file. I know I need wine but I don't know how to get it and when I do get it I don't know how to install everything, so if you could give me some directions that would be great.


I already  looked at the other music players and I really don't like them. The only one I would be interested in was Songbird, but when I looked on the site all they had for download was a beta, do they have any stable releases?

Thanks for the help.

wine will suit you for exe files...
but honestly what is it about the linux alternatives to itunes you dont like?
after all would you rather use something that integrates well within the system and doesnt need all kinds of nonsense to work, or use an application that gives little to no support to your system.
personally I will take applications like amorok and exaile anyday over itunes on a linux system, until A:
a better player is developed
or b: apple finally gets a clue and makes an itunes for linux.
the latter is most likely never to happen

---

### Post by Inxsible on 2007-11-16
> **SunnyRabbiera said:**
> or b: apple finally gets a clue and makes an itunes for linux.
[COLOR=Red] the latter is most likely never to happen[/COLOR]
F'ing A !!!

They won't provide software without getting paid for it and they know that it will be difficult to get enough revenue in the Linux market since there are so many alternatives.

---

### Post by coolbrook on 2007-11-16
I'm anxious to try banshee again now that I've got my sound issues sorted out. :guitar:

---

### Post by GeorgiaBoot on 2007-11-16
I understand that fully but so far these integrated lovely music players are not very good, amarok glitches the whole system I can't do anything else while listening to music, every time I want to move the window it basically smears the whole screen. Same as Rythmbox. 

Now I am interested in Song Bird, how is that one?

---

### Post by Inxsible on 2007-11-16
> **GeorgiaBoot said:**
> I understand that fully but so far these integrated lovely music players are not very good, amarok glitches the whole system I can't do anything else while listening to music, every time I want to move the window it basically smears the whole screen. Same as Rythmbox. 

Now I am interested in Song Bird, how is that one?I dont know if it matters, but Songbird is not open source. its free tho :)

I, personally, didnt quite like the songbird interface. but like you said in your first post, individual opinions differ for every person.

---

### Post by LowSky on 2007-11-16
[COLOR="Red"]Warning:[/COLOR]
I got iTunes (older version before appleTV, i think 7.2?) running on my Ubuntu machine, but it was very very slow and buggy. Now if I want music I buy it from Amazon.com, as its cheaper and DRM free, and run banshee as my default music player. Also uninstalling it was a pain.

---

### Post by GeorgiaBoot on 2007-11-16
True everyone differs. I don't mind if songbird is not open source. 

Well I did install itunes and it is a little bit better but thats not saying much. Now if songbird works how would I uninstall itunes? Ha I know...


Also I am not able to remove amarok, how do I do that? Remember I am new to Ubuntu so I need instructions.

Thanks and sorry for causing the music player war! :)

---

### Post by xinix on 2007-11-16
My experience with with itunes through wine was that it was very painful.  It would stutter a lot especially whenever you did anything other than sit and look at the itunes window.

Inxsible:  Songbird claims to be open source and they do make the source code available.  What makes you say it isn't?

[http://www.songbirdnest.com/support/#10](http://www.songbirdnest.com/support/#10)

---

### Post by Inxsible on 2007-11-16
> **GeorgiaBoot said:**
> Also I am not able to remove amarok, how do I do that? Remember I am new to Ubuntu so I need instructions.
```
sudo aptitude remove amarok
```should do the trick

---

### Post by Inxsible on 2007-11-16
> **xinix said:**
> Inxsible:  Songbird claims to be open source and they do make the source code available.  What makes you say it isn't?

[http://www.songbirdnest.com/support/#10](http://www.songbirdnest.com/support/#10)
Hmm. I stand corrected then.

Sorry, maybe I confused it with some other software.

---

### Post by SunnyRabbiera on 2007-11-16
to uninstall amorok go to "settings" then to "administration" and select "synaptic package manager"
after you type in your password click on the "search" button and type in "amorok"
after this is done you click on amorok and select "completely remove package"
I am assuming you used the add/remove applet, its fine but synaptic can get you to more places

---

### Post by GeorgiaBoot on 2007-11-16
Thanks you very much for that line, it removed it without a hiccup. Now I downloaded SongBird and I like it allot better. Now how do I go about removing itunes? Ha as soon as I install I want to uninstall :)

Thanks so much for the help.

---

### Post by AndyCooll on 2007-11-16
Open up Nautilus (Places > Home Folder), press CTRL+H to reveal your hidden folders, and  find the .wine folder. Have a look in there for your iTunes folder, you can delete it by removing the folder itself.

Or from the command line, deleting the .wine folder with the following should do the trick:
```
rm -R ~/.wine
```

:cool:

---

### Post by Sims2789 on 2007-11-16
> **GeorgiaBoot said:**
> I would Like to install itunes on my ubuntu PC. I have tried Amarok, rythmbox and I hate them. Both Freeze get extremely garbled and I really don't like the layout, I am just not impressed. Sorry guys just my opinion, but I feel whatever suites each individual person is what matters so someone might like amarok or whatever and one person might not. 

So since I use itunes on my PC I would Like to know how to get it on my Ubuntu?

Please Consider that I am completely new to Ubuntu so I need very detailed instructions. I am pretty sure I need Wine but really don't have a clue on what to do and where to put things. Thanks

If iTunes doesn't work in Ubuntu you can always decrypt your iTunes music in Windows before transferring your songs to Ubuntu:

[http://www.hymn-project.org/download.php](http://www.hymn-project.org/download.php)

I suggest the myFairTunes one, since the Qt one uses .Net.

---

### Post by DarinB on 2007-11-16
I gotta say i am sick of trying to find a player that will do what itunes does, it sucks
i use gpodder for my video podcasts, rhythmbox for music, and gtkpod for playlist management.
i think SteveJ at apple is really messing up. i read canonical says 6 million downloads of gutsy. 
You would think that is quite a bit of new ipods.
i am holding on to my old gen 3 40GB for as long as possible.
i am beginning to feel towards stevej as i do towards billg.
Its sad since apple is like our cousin as far as the unix core kernel.
i wish there was a way to get the message to stevej that he can only gain by getting linux users to go itunes, many of users will buy music and will definitely buy ipods. 
those that will torrent or p2p download will never stop, no matter what.
So i say SteveJ look out you will be sucking up to us one day and that day will be soon.
We will eventually gain a decent market share and then mr J you will be kissing our umm well you know.

---

### Post by jkzubu on 2007-11-16
Give Songbird a try.  It is not in the repository but you can find it here:  [http://www.songbirdnest.com/](http://www.songbirdnest.com/)

It is nice and seems to work ok. I just started testing it.  I wish you could change the background, but you can add plugins and extensions.

JK

---

### Post by DarinB on 2007-11-17
thanks i installed songbird last night but can't dock (mount) my ipod there are add ons or plug ins for 3.0 that help ipod device management
Can i upgrade in debian to songbird 3.0 in feisty??????
How????

---

### Post by DarinB on 2007-11-17
hey  jkzubu
what songbird di you install because version .25 doesn't have add ons and i can;t plugin my ipod to is 
so what are you using .25 or.31??

---

### Post by doctorbighands on 2007-12-31
I'm growing increasingly frustrated with ubuntu music players, also. I hate Apple as much as the next guy (and I'm getting more sick of Apple users with each passing day), but damn it, iTunes is still the best player out there, and for one simple reason: IT DOES EVERYTHING. I could get over iTunes immediately if I could find just one program that performs all of the following:

*Full iPod integration (that means music AND playlists AND pictures AND video!!)
*Full compatibility with any type of common music file
*Simple importation of music files from HDD, selectable as either an entire folder or just one file
*Simple importing and encoding of music from CDs
*Ability to burn audio CDs
*Ability to burn data discs

iTunes is the one and only media player program that can handle all of the functions above BY ITSELF. No application available in ubuntu can make that claim, and that's the source of many people's frustration, including my own. Having to use a combination of [Exaile/Banshee/Amarok/whatever]+Sound Juicer+gtkpod+Serpentine to do what just one simple program can do is ludicrous and absurd all at the same time.

No offense to anyone, I swear. I feel better now that I've vented. I have been and shall continue to be a VERY happy Ubuntu user. I just wish I could have iTunes back!

EDIT:

I should say that I do recognize that several apps do come close, but they still fall short. If I could custom-build my own app (someday I may have the skills to do just that, but I digress...), it would have the wide functionality of Amarok, the user-friendliness and integration of iTunes, and the look and feel of Exaile. THAT would be a killer program!!

---

### Post by mmb1 on 2007-12-31
I've heard that Amarok does a great job managing ipods, but rhythmbox and banshee are also options.

---

### Post by forestpixie on 2007-12-31
I use an iPod to make sure my car stays still while I have the front jacked up - then I don't have to worry about being tied to iTunes

---

### Post by cellarmation on 2007-12-31
I have been using songbird for about a month now, and it looks like it will be really good. Currently using the 0.4 release, and find it limited and buggy. Its getting better all the time, and they seem to be working on it at a good pace. In the mean time probably best to rely on something more stable.

---

### Post by cframes1 on 2008-01-04
OK, so here is my problem with open source I-tunes clones.  THEY NEVER SUPPORT I-TUNES PHONES!!!!  I have been trying to get my Motorola SLVR L7 to work with LINUX for 3 months to no avail.  This sucks, I finally shell out for a nice phone right before I switch to Ubuntu (which I love by the way) and now I can't use the i-tunes feature.  I just wish one of these super genius hackers could step up to the plate for me because I suck at computers.

---

### Post by CCBalla10 on 2008-01-05
I'm currently using songbird 0.4 also and it works flawlessly with my 2gig ipod nano.  I use it all the time

---

