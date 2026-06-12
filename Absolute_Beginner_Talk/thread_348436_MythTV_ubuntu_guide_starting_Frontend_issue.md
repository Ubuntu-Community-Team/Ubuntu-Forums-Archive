---
title: "MythTV ubuntu guide starting Frontend issue"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by lawson23 on 2007-01-28
[Guide]("https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend#head-efc7a1a32622b1ba4359ea774469c0a5fc97ee74")

[mythtvtalk post]("http://www.mythtvtalk.com/forum/viewtopic.php?p=18826#18826")

Myth Install -Step 12 in Guide
Says:
> Right click the desktop and log out of the openbox session. At the gdm screen, switch the session to Mythtv. Login. When asked if you want mythtv as the default, hit yes. Now, when restarting your machine, mythtv should come right up.

But this is what I get:
MENU: Openbox 3
Option: Terminal emulator - runs terminal emulator
Option: Web browser
Option: Desktops 1,2,3,4 - really no options here
Option: Obconf - does nothing?
Option: Reconfigure - does nothing?
Option: Restart - does nothing?
Option: Exit - exits this little menu and you can't get it back. Desktop is then locked and I can't seem to do anything else.

So I guess I was wondering if there is a config file (since I can't figure out gui) I could edit and then do a server restart?

---

### Post by lawson23 on 2007-01-29
This "[post]("http://www.ubuntuforums.org/showthread.php?t=320071")" is exactly the same thing I'm experiencing.

Will something like this command help me out?
```
sudo dpkg-reconfigure gdm
```

---

### Post by lawson23 on 2007-02-01
Ok I figured out how to get around this ISSUE.

To see the answer please see this [post]("http://www.mythtvtalk.com/forum/viewtopic.php?p=19066") at the Mythtvtalk forums.

I describe what I did and how I got around this.

---

### Post by Patrick Dixon on 2007-02-06
I assume that to switch user to mythtv you also need to have set a password for mythtv???

---

### Post by lawson23 on 2007-02-06
This isn't about the user as it is about logging out of openbox.

You already have the user setup (and you can't use mythtv) with login and password.  Also you have the system set to automatically log this user into the system.

Are you having this issue or giving suggestions?  I'm confused and if you could be more descriptive I may be able to help.

---

### Post by Patrick Dixon on 2007-02-07
Yes I had exactly this issue.

But AFAIKT, even when you get the switch user option (through your trick, or by hitting the power button and getting the switch/shuttdown menu as I did), you still need to re-log in as mythtv, and to do that you need a mythtv password to have already been set - or am I missing something?  My understanding is that you have to switch to the mythtv account and then select the mythtv account to be the one that gets automatically booted in to.

I found the instructions to be completely incomprehensible at this point in the guide and since I had other problems too, I just ditched the whole thing and did a full desktop install per the parker guide [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

Unfotunately I still have the problem, which is that I'm getting picture/sound breakup which isn't there when I just stream from the card with mplayer.

So I'm about to ditch the whole mythtv thing, because it seems to be far too painful to install, and I have concerns about on-going reliability.  I haven't had to hard-boot a PC so many times for a very long time, and I'm currently on my 3rd ubuntu/mythtv install ...

---

### Post by lawson23 on 2007-02-07
The second to the last bullet of the "install base" section says:
```
Choose a Username and password. Be sure not to use the username mythtv, as it will be generated automatically later.

```

This is the username and password you would use for:  (you should not use mythtv)
Part 6 and 7 of the "Install Mythtv" Section

This is also the same username and password you would use for the manual login that I describe in my instructions.

I found this guide besides 2 issues (one has already been updated) to be very effective.  The last issue I figured out finally myself, got lucky.

As far as some other things these are linux and Mythtv configuration issues.

I myself don't have:
my remote working yet
my audio working yet
video is choppy

I hope to have these worked out someday but either way these issues have nothing to do with the guide.

---

### Post by superm1 on 2007-02-08
> **lawson23 said:**
> The second to the last bullet of the "install base" section says:
```
Choose a Username and password. Be sure not to use the username mythtv, as it will be generated automatically later.

```This is the username and password you would use for:  (you should not use mythtv)
Part 6 and 7 of the "Install Mythtv" Section

This is also the same username and password you would use for the manual login that I describe in my instructions.

I found this guide besides 2 issues (one has already been updated) to be very effective.  The last issue I figured out finally myself, got lucky.

As far as some other things these are linux and Mythtv configuration issues.

I myself don't have:
my remote working yet
my audio working yet
video is choppy

I hope to have these worked out someday but either way these issues have nothing to do with the guide.
You hit the nail on the head with what I was going to chime in.  Things can be achieved with the username that you first use being "mythtv", but you are asking for more trouble then its worth.

---

### Post by Patrick Dixon on 2007-02-08
> **superm1 said:**
> You hit the nail on the head with what I was going to chime in.  Things can be achieved with the username that you first use being "mythtv", but you are asking for more trouble then its worth.

Yes, I understood that.  However,

[Quote=Guide]
12 Right click the desktop and log out of the openbox session. At the gdm screen, switch the session to Mythtv. Login. When asked if you want mythtv as the default, hit yes. Now, when restarting your machine, mythtv should come right up.[/quote]

So asssuming that you can 'log out of the openbox' and get to the 'gdm screen', you then need to 'switch the session to Mythtv'.  Does this mean the mythtv user, or the mythfrontend application?  If it means the mythtv user, it seemed to me that I couldn't switch users to mythtv without giving the mythtv username and a mythtv password (which wasn't set) - hence my complete confusion over this step.

I'm none the wiser about what is supposed to be happening at this step (and presumably it's fairly crucial - or you won't get myth to run automatically), and I don't understand what you need to click, enter and select to achieve it.  Sorry for being thick.

---

### Post by Patrick Dixon on 2007-02-08
> **lawson23 said:**
> 

As far as some other things these are linux and Mythtv configuration issues.

I myself don't have:
my remote working yet
my audio working yet
video is choppy

I hope to have these worked out someday but either way these issues have nothing to do with the guide.I recommend the parker guide for an ir remote at least.  Make sure you do the 'Make the LIRC Device Static' bit when you install it though, as it will save some messing around later.

---

### Post by lawson23 on 2007-02-08
> So asssuming that you can 'log out of the openbox' and get to the 'gdm screen', you then need to 'switch the session to Mythtv'. Does this mean the mythtv user, or the mythfrontend application? 
NOT USER - I wish I had a print screen to show but I'm not that advanced in linux.
FROM MY EXPLAINATION WITH A BIT MORE DETAIL:
--Then I would have enough time to go to the right corner and hit options. Switch Session select mythtv (NOT USER, This is avail for selection because what was done in Part 2,3 and 4 of the "Install Mythtv" Section ). Then I clicked Ok or something closing that window.--

I understand that the above is not described very well I had to document this all from memory because as I was doing it I wasn't sure it was going to help me until it was finished.

THEN:
After making the above change you LOGIN with the username and password set in the second to the last bullet of the "install base" section.

You will then upon login get a box that will ask you if you always want to use MYTHTV to start automatically.

> 
If it means the mythtv user, it seemed to me that I couldn't switch users to mythtv without giving the mythtv username and a mythtv password (which wasn't set) - hence my complete confusion over this step.

The actual "mythtv" account is NEVER used by you.  It is only used by the MYTHTV application behind the scenes.  I think the app uses this ID to access mySQL.  So as long as you act like this ID does not exist you will be all set.

---

### Post by superm1 on 2007-02-08
> **Patrick Dixon said:**
> Yes, I understood that.  However,



So asssuming that you can 'log out of the openbox' and get to the 'gdm screen', you then need to 'switch the session to Mythtv'.  Does this mean the mythtv user, or the mythfrontend application?  If it means the mythtv user, it seemed to me that I couldn't switch users to mythtv without giving the mythtv username and a mythtv password (which wasn't set) - hence my complete confusion over this step.

I'm none the wiser about what is supposed to be happening at this step (and presumably it's fairly crucial - or you won't get myth to run automatically), and I don't understand what you need to click, enter and select to achieve it.  Sorry for being thick.
Switching the session to Mythtv means clicking the session button picking the mythtv option.  I see your confusion over this step now though since the mythtv password isn't set, but the catch here is that you dont log in as the user mythtv.  You log in as the regular user that you created.  You put yourself into the "mythtv" group instead.

---

### Post by superm1 on 2007-02-08
> **lawson23 said:**
> 
The actual "mythtv" account is NEVER used by you.  It is only used by the MYTHTV application behind the scenes.  I think the app uses this ID to access mySQL.  So as long as you act like this ID does not exist you will be all set.
Exactly, this is what I was trying to get at.  The "mythtv" username is only used for the backend process.  The "mythtv" group is used by anyone that wants to use the frontend.  

The "mythtv" user can also be used as the frontend, but then you have to assign it a password, and put it in all the groups you would have normally been using it as.  At this point, why not just use the regular account and save the trouble?

---

### Post by lawson23 on 2007-02-08
superm1,

Are you the document creator?

I believe you are.  Do you have any information as to why a handful of users are running into this log out issue with openbox???

---

### Post by Patrick Dixon on 2007-02-08
> **superm1 said:**
> Switching the session to Mythtv means clicking the session button picking the mythtv option.  I see your confusion over this step now though since the mythtv password isn't set, but the catch here is that you dont log in as the user mythtv.  You log in as the regular user that you created.  You put yourself into the "mythtv" group instead.

Right.  So you are actually switching to the mythfrontend session then?  Maybe I didn't have mythfrontend running at that stage or something, because I never got an option to switch to it, and I ran in to the same issues as the others here.  The only switch button I could get was the switch users, and so I assumed that switching to mythtv meant switching users to mythtv ... but that didn't seem to make much sense either.

---

### Post by Dubstar_04 on 2007-02-11
I can only get mythtv to work if i log in as mythtv, but then I experience the same choppy playback that other people have mentioned.

Anyone solved this yet?? I believe its a rights issue with the mythtv user but i'm pretty new to linux so its a wild guess!!!

I did use mythdora for a while but had major sound problems using a dvb-t cx-88 card, in ubuntu the sound is fine just the video is terribily jumpy, jerky and choppy!!

Once this is solved i maybe able to move on and one day move away from my windows mce machine and media portal which untill the new release of mythtv reigns supreme in the HTPC arena. plus i can set media portal up in less than 20 minutes on xp pro!!

[http://www.team-mediaportal.com/](http://www.team-mediaportal.com/)

If anyone can recommend a solution to my choppy video i would be very grateful!!

Cheers,

Dubstar_04

---

### Post by superm1 on 2007-02-11
> **Dubstar_04 said:**
> I can only get mythtv to work if i log in as mythtv, but then I experience the same choppy playback that other people have mentioned.

Anyone solved this yet?? I believe its a rights issue with the mythtv user but i'm pretty new to linux so its a wild guess!!!

I did use mythdora for a while but had major sound problems using a dvb-t cx-88 card, in ubuntu the sound is fine just the video is terribily jumpy, jerky and choppy!!

Once this is solved i maybe able to move on and one day move away from my windows mce machine and media portal which untill the new release of mythtv reigns supreme in the HTPC arena. plus i can set media portal up in less than 20 minutes on xp pro!!

[http://www.team-mediaportal.com/](http://www.team-mediaportal.com/)

If anyone can recommend a solution to my choppy video i would be very grateful!!

Cheers,

Dubstar_04
Well first thing, install proprietary drivers if you don't already have them on.  Next, check SD content first if you are only doing HD.  Test with other media players to rule out if this is myth exclusive.  Check CPU usage.

---

### Post by Dubstar_04 on 2007-02-12
ok cpu usage is 100% even when i move an open window!! The crazy thing is mythdora works fine!! I really don't understand?!?! My hard ware is upto the task but i can't get an ubuntu-myth install to work. I've tried 5 times now and the last 3 i have managed to install mythtv and every thing but video works!! 

Any suggestions welcome.

---

### Post by superm1 on 2007-02-13
> **Dubstar_04 said:**
> ok cpu usage is 100% even when i move an open window!! The crazy thing is mythdora works fine!! I really don't understand?!?! My hard ware is upto the task but i can't get an ubuntu-myth install to work. I've tried 5 times now and the last 3 i have managed to install mythtv and every thing but video works!! 

Any suggestions welcome.
This really sounds like no proprietary (accelerated) drivers installed.  Have you installed them?

---

### Post by Patrick Dixon on 2007-02-13
> **Dubstar_04 said:**
> ok cpu usage is 100% even when i move an open window!! The crazy thing is mythdora works fine!! I really don't understand?!?! My hard ware is upto the task but i can't get an ubuntu-myth install to work. I've tried 5 times now and the last 3 i have managed to install mythtv and every thing but video works!! 

Any suggestions welcome.

I've tried 5 times now too and have just chucked in the towel.

The first install worked absolutely fine with no tweaking or driver issues at all, but unfortunately I had to temporarily install Windows to sort out a motherboard sound hardware issue, and haven't been able to get back there, even by doing exactly the same install.

I've come to the conclusion that something in the ubuntu depositories has changed over the past two weeks and is causing the problem, because I simply can't think of anything else it could be.    I only get about 60% cpu usage, but video is choppy and sound glitches, and it's totally unwatchable :-(

---

### Post by Dubstar_04 on 2007-02-13
> **superm1 said:**
> This really sounds like no proprietary (accelerated) drivers installed.  Have you installed them?

I have been using the on board video, which after doing a 'sudo dpkg-reconfigure xserver-xorg' works fine. I do believe that it is a problem with video drivers!! I might have to put another install off for a while and order a new motherboard because the AGP slot in mine is dead!! and i have a nvidia fx 5200 card boxed up and waiting to go in to a myth system!!  

I might even put it off until the new version of ubuntu is released in the hope that more hardware will be supported.  

Has anyone recently installed mythtv from the repositories and can confirm that the mythtv verion there is ok??  as almost every post about mythtv is a failed install or jerky video!!

Fingers crossed ubuntu and mythtv will become easier and quicker to install with time then more people will be able to use both together. I don't mind giving it weeks between install atempts as i have a windows htpc in the lounge running media portal which is excellent and very easy to install (10 minutes) for all those people who are truely fed up with mythtv installs going wrong. But i like to play with mythtv especially with a new release looming!!

---

### Post by Titus A Duxass on 2007-02-13
I installed myth on a new box about 2 weeks ago, using the community documents as a starting point.
I did not follow every step of the How-To because of issues, but it does work.

The system is an old amd 900, mx440 graphic, 512mb ram and a 300gb hdd.

---

### Post by Dubstar_04 on 2007-02-15
Ok so i have spent the last two hours plodding throught the achieves in the mythtv gossamer threads jobbie and it seems choppy videos is almost always caused by bad video drivers.

Now my main issue is that i have an nvidia 5200 boxed ontop of my pc and i cant use it due to my main ubuntu machines agp slot being damaged and not working and my other ubuntu machine doesn't have an agp slot!!!

I now have the task of ordering a new motherboard and would like a few recommendations as i have experienced problems with ubuntu on msi motherboards.

My first point is which processor should i use? I have the choice of either;

A AMD xp 1700+ or,
A Intel Pentium P4 1700

so both are pretty much the same.


Then I need a MATX motherboard to go with the choosen processor. plus I will probably order some new ram as I only have 300+MB of ram spare. 

This will be my main desktop pc and will run mythtv front and back ends + 1 or 2 tuners. However I have a dedicated HTPC so unless the new release of mythtv is exceptional it will remain a play machine!!

---

### Post by Dubstar_04 on 2007-02-19
I managed to sort out the choppy video. I just used the ENVY driver installer!! WOW its so simple to do and now i can watch tv and videos smooth as ever!!

Still got on problem with the mythtv internal video player being weird and i can't get lirc to work with xine.

also not a mythtv problem but my sound output changes priority when i reboot!!

---

### Post by superm1 on 2007-02-19
> **Dubstar_04 said:**
> I managed to sort out the choppy video. I just used the ENVY driver installer!! WOW its so simple to do and now i can watch tv and videos smooth as ever!!

Still got on problem with the mythtv internal video player being weird and i can't get lirc to work with xine.

also not a mythtv problem but my sound output changes priority when i reboot!!
ENVY driver?  Whats this?

---

### Post by gerick on 2007-02-19
> **superm1 said:**
> ENVY driver?  Whats this?

I am guessing that he meant tseliot's "Envy" scripts to load the nvidia drivers.
[http://www.ubuntuforums.org/showthread.php?t=301499]("http://www.ubuntuforums.org/showthread.php?t=301499")

---

### Post by Dubstar_04 on 2007-02-19
Yeah I mean 'Envy' The driver install. It worked great. I really like mythtv almost more than media portal on my main htpc, if i can get it working and 0.21 brings a fresh gui and faster dvb channel changes i might actually scrap windows!!

---

### Post by superm1 on 2007-02-19
> **Dubstar_04 said:**
> Yeah I mean 'Envy' The driver install. It worked great. I really like mythtv almost more than media portal on my main htpc, if i can get it working and 0.21 brings a fresh gui and faster dvb channel changes i might actually scrap windows!!
Ah envy looks pretty neat.  I haven't been following the mailing list religiously, but it looks like 0.21 is still a ways off.  91 active tickets for the 0.21 milestone....

---

### Post by Dubstar_04 on 2007-02-19
> **superm1 said:**
> Ah envy looks pretty neat.  I haven't been following the mailing list religiously, but it looks like 0.21 is still a ways off.  91 active tickets for the 0.21 milestone....

0.21 may well be a way off yet but in the mean time there will be a new ubuntu release and extra time for me to get use to using ubuntu!!  

I've been using linux since october 06 and it has taken me until now to be able to watch tv with out it jumping and freezing, and I still have problems that need ironing out, for example:

Can't get mythtv transcode to work in 'Good' mode. Perfect and iso work fine but there is no output from 'Good'

I can't get lirc to work with Xine, works ok with mythtv (mceusb2)

The sound device changes its name with every reboot (udev related?)

Can't get mythtv archive to output a dvd

mythtv 'internal' player is jumpy (xine is excellent)

I think thats it so not far now, I'm gonna do a fresh install at the weekend and see where that gets me. I will make notes and hopefully post them for people to read.

---

