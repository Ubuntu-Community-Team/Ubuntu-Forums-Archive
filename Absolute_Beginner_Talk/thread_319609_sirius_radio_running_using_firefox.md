---
title: "sirius radio running using firefox"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by broekskw on 2006-12-15
any one out there running sirius radio on firefox. after loging into sirius and trying to select a station i get and error message by firefox saying missing plugin,click get plugin and another  window comes up saying unknow plugin (application/x-oleobject)

thanks:mrgreen:

---

### Post by PurplePenguin on 2006-12-15
Hi, my gut feeling was that it might be a problem with flash, so I went to siriuscanada.ca and signed up for a free 3 day trial membership. :)

I've got flash 9 installed in firefox, by the way.  

Anyway, as soon as you choose the station you want, firefox does bring up that bar saying "missing plugin".  When I click on that, it comes up with the same error that you mentioned (application/x-oleobject).  But, if you let it (your station, that is) load for 10 seconds or so, it'll start playing anyway.

I'm listening to Spill the Wine on Sirius right now, as a matter of fact! :)

So, in other words, make sure you've got Flash 9 installed and just forget about the missing plugin warning. :D  I think that the plugin is minor... maybe a scrolling track list or something.

---

### Post by PurplePenguin on 2006-12-16
I did just try listening to a comedy station and it refused to load.  I've tried three different classic rock stations and one top 40 station and they load no problem (aside from complaining about a missing plugin).

---

### Post by broekskw on 2006-12-16
thanks man will install flash 9, and next time i will think before i post.totally not a question for this site to ask (firefox forum i should have asked,will go and reg at there site) 

again thanks for your reply:D :D

---

### Post by PurplePenguin on 2006-12-16
Hey, don't worry about it! :)  If I helped you out at all, it's all good, right? 

And who knows?  Maybe somebody else will be in the same position and will find your post here in this forum!

---

### Post by broekskw on 2006-12-16
thanks again .installed flash beta 9 but still nothing happened. will try a reboot first:D

---

### Post by PurplePenguin on 2006-12-17
Let me know if it worked or not.  I don't think I installed anything else that could make a difference... I'm pretty sure that it all relies on flash.

Best of luck!

---

### Post by broekskw on 2006-12-17
so got flash 9 installed but missing plugin keeps coming up and if i exit that error then it looks like the station is playing but with no sound control or title display.installed ie6 and same thing happens,not sound and no display of the song playing.must be missing something:D

---

### Post by broekskw on 2006-12-17
here is a screen shot showing plugin missing.and then if i click the x button then the screen looks like it should play the station 9 the pulse but nothing working

---

### Post by PurplePenguin on 2006-12-17
> **broekskw said:**
> here is a screen shot showing plugin missing.and then if i click the x button then the screen looks like it should play the station 9 the pulse but nothing working

That's exactly what I get, minus the STANDARD / PREMIUM part - mine's blank in that area (I assumed that that's where the missing plugin is supposed to be).

I just loaded up the site again to see exactly what happens for me.  Anyway, I get the exact same bar (re: missing plugin) along the top.  I clicked on it, it looked for the plugin, said that it couldn't find it, then I clicked Finish.  By that time, the stream had finished loading and the music started playing. :)

Some stations won't load up at all - I've had this problem just with a couple Talk stations.  I click on the name, it loads the station, and Firefox just says "Done" on the status bar.  Otherwise, I know for sure that a station works if my status bar shows that it's looking for a stream, and then that the stream is transferring (that is, "Transferring from 65.XX.XX.XX", some IP address).  I've attached a screenshot to show what it looks like as a stream is loading.

It doesn't look pretty, but during while taking the screenshot I'm listening to music... and it's still playing while I'm typing this.

It's strange... We're both running gnome, both running ubuntu (although I had a bit of fun with one of the "Make your ubuntu look like a Mac" threads!!), Firefox, on the same website... it works for me, not for you.  [COLOR="Red"]Maybe I was wrong about Flash being the (only) culprit... do you have all of the different non-free multimedia codecs installed?[/COLOR]

---

### Post by broekskw on 2006-12-17
thanks man for all your help in trying to get this going for me,how do i check to see what free" do you have all of the different non-free multimedia codecs installed?"
thanks:mrgreen:

---

### Post by Pobega on 2006-12-17
Try Sipie. 

[http://eli.criffield.net/sipie/](http://eli.criffield.net/sipie/)

---

### Post by broekskw on 2006-12-17
thanks will check that out and see if that works,looks like it should:D hope the instructions are not to detailed :D

---

### Post by PurplePenguin on 2006-12-17
> **broekskw said:**
> thanks will check that out and see if that works,looks like it should:D hope the instructions are not to detailed :D

Check out the [readme]("http://eli.criffield.net/sipie/sipie_README") in the link that he sent, it's in python, so it looks like it should be easy enough to get going (especially if you've installed python programs before and have all the dependencies installed already!).

About the "non-free" codecs I mentioned, those are the ones that aren't allowed to be distributed with Ubuntu.  That would be stuff like mp3 and so on.  You probably used [Automatix 2]("http://www.getautomatix.com") or one of the Beginner's How-To's in order to get mp3s and everything going back when you first installed Ubuntu, right?

---

### Post by broekskw on 2006-12-17
ok thanks.did go to the read me and downloaded [www.mplayerhq.hu](www.mplayerhq.hu). also downloaded [http://www.crummy.com/software/BeautifulSoup/](http://www.crummy.com/software/BeautifulSoup/) and also installed apt-get install python-beautifulsoup also got and installed 
 
If you have python-setuptools, just run easy_install BeautifulSoup (not sure if i did so i just ran the apt-get install python-setuptools command

If you don't have python-setuptools get it, On debian or ubuntu run
apt-get install python-setuptools, or on rpm based distros run
so did not have python-setuptools,installed but now i am stuck at the following section

To run just copy sipie somewhere in your path 
cp sipie ~/bin/sipie
 what path and how do i do that.

thanks:mrgreen:

---

### Post by Pobega on 2006-12-17
So did you get it to work? I'm confused.

---

### Post by broekskw on 2006-12-17
your are confused, boy trying to follow instructions for this is to much for me.sometimes i just don't know if this old guy should have switched to linux](*,)  will keep reading .

---

### Post by wilderness wanderer on 2006-12-17
if you are interested in a simple command line solution you can run in a terminal, check out sipie.  Installation instructions in [this]("http://ubuntuforums.org/showthread.php?t=284893&highlight=sipie") thread

Oops, only read the first page of the thread.](*,)   Some of you folks are already trying to use sipie.  I have updated my instructions given in another thread to make them easier to cut and paste into the terminal.  [**Easy how-to for sipie is here**]("http://ubuntuforums.org/showpost.php?p=1789365&postcount=4").:-D

---

### Post by broekskw on 2006-12-18
great post grade a+++++:D 
got 2 computer running linux ubuntu and have been trying for days to get 1 of them going ,so went to the other one and used your guide to a tee and now have sirius up and running:mrgreen: 

thanks

---

### Post by kd7swh on 2006-12-18
sirius does the same thing to me. I have flash 9 but I don't think I am going to keep it . its too buggy.

---

### Post by DeVelaine on 2006-12-18
> **PurplePenguin said:**
> I did just try listening to a comedy station and it refused to load.  I've tried three different classic rock stations and one top 40 station and they load no problem (aside from complaining about a missing plugin).

I can answer this one from experience. The music stations consist of content and programming directly from their studios, or they have a "free rebroadcast" agreement with the content provider. The vast majority of the talk channels aren't produced internally, and last I checked, they did not have permission to pipe through the internet.

---

### Post by broekskw on 2006-12-18
just follow post #18 and you will get it going in not time from a terminal window instead of firefox.works great for me on both computers.sirius rock on again8)

---

### Post by broekskw on 2007-01-14
Ok had to reformat one computer. followed the guide on post 18 but entered the wrong user  name and password, so now every time i enter the caption it just logs me out to the the first terminal window. so how do i get the logon terminal window to come up again so i can correct my mistake:cool:

---

### Post by wilderness wanderer on 2007-01-17
> **broekskw said:**
> Ok had to reformat one computer. followed the guide on post 18 but entered the wrong user  name and password, so now every time i enter the caption it just logs me out to the the first terminal window. so how do i get the logon terminal window to come up again so i can correct my mistake:cool:

Are you sure you entered the wrong user name and password?  If you reach the Sirius stream daily login limit Sipie will exit with no error message indicating what happened.  Then you must wait 24 hours to login.

To change your username and password, just delete the config file and rerun the program.  It will prompt you for the information.

```
rm ~/.sipie/config
```

---

### Post by AndrewB on 2007-01-17
Thank you....OH THANK YOU post #18   

Jam-On!!!!!        :)

---

### Post by wilderness wanderer on 2007-01-17
Glad you got it working. :D

---

### Post by drascus on 2007-01-19
Ok Keeping it simple there is a bit on an easier way to fix this. in synaptic download the VLC media player and the codecs that allow WMV audio. Then for firefox install a little Extension called media player connectivity. When you run firefox next it will walk you through the set up. When you then log into sirius and pick the channel you want to listen to just click the little icon that appears in the player window and the stream will open via the VLC player. 
I hope this helps anyone else who is still stuck. 
~Mike~

---

### Post by Nevis on 2007-04-29
> **drascus said:**
> Ok Keeping it simple there is a bit on an easier way to fix this. in synaptic download the VLC media player and the codecs that allow WMV audio. Then for firefox install a little Extension called media player connectivity. When you run firefox next it will walk you through the set up. When you then log into sirius and pick the channel you want to listen to just click the little icon that appears in the player window and the stream will open via the VLC player. 
I hope this helps anyone else who is still stuck. 
~Mike~

Excellent, thanks Mike. I have tried sipie and the SiriusPlayer Firefox plugin, for some reason neither worked for me. However, this got it done. It's not exactly what I want but it's a foot in the door.

Thanks again.

---

### Post by amisima on 2007-07-09
I am new to linux and so far am loving every minute of it! 

I believe I have followed your instructions to installing sipie and pre-requisites correctly however when I run it using the /usr/bin/sipie command I get the following error

/usr/bin/sipie: line 1: syntax error near unexpected token `newline'
/usr/bin/sipie: line 1: `<meta HTTP-EQUIV="REFRESH" content="10; url=http://sipie.sourceforge.net/">'

I looks like there is a bug in the code to me but you guys would know better than I would for sure :confused:

---

### Post by sugarland2k on 2007-07-09
I use Last.fm and it has an official Ubuntu download.  I love the music!  :guitar:

Friends do not let friends run Vista!

---

