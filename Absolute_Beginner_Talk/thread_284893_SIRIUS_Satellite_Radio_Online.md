---
title: "SIRIUS Satellite Radio Online"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by barton.jones on 2006-10-26
I'm looking for some help to get SIRIUS online running on linux

---

### Post by TitusDalwards on 2006-10-26
[http://www.linuxquestions.org/questions/showthread.php?t=403193](http://www.linuxquestions.org/questions/showthread.php?t=403193)

there is a tip for it

---

### Post by barton.jones on 2006-10-26
so I'll download and try wine when I'm finished updating to 6.10

---

### Post by wilderness wanderer on 2006-11-21
I couldn't get the sirius player to work, but I have found a command line player which I actually prefer.

Instructions:

First, install mplayer and python-setuptools:

```
sudo apt-get install mplayer python-setuptools
```

Then, install Beautiful Soup:

```
sudo easy_install BeautifulSoup
```

Next download sipie:

```
wget http://eli.criffield.net/sipie/sipie
```

Make it executable:

```
sudo chmod a+x sipie
```

Move it to /usr/bin

```
sudo mv sipie /usr/bin
```

That's it.  You can run sipie from the command line or create a custom launcher using the attached image as the icon and the following as the "command" line:

```
gnome-terminal -x /usr/bin/sipie
```

You'll have to enter your user id & password the first time you run the program, as well as whether you are a guest or subscriber.  Thereafter you will only have to enter the "captcha" code each time you run the program.  

Press tab tab to show all streams, tab completion of stream names is supported.  You can press CTRL-C to end playing a stream and select another one.

readme is at [http://eli.criffield.net/sipie/sipie_README](http://eli.criffield.net/sipie/sipie_README)

Hope this helps someone.

---

### Post by myname on 2006-12-01
I could get sirius player to work with Dapper Kubuntu, but with Edgy, I cannot.  I installed Ubuntu with KDE, and tried every plug-in and download to play windows media stuff and nothing. 

I can log into my sirius account, pick the genre, and when I go to pick the station I want to listen to, a message pops up saying that I don't have a windows media player/codec installed to play this type of file, do I want to download?  

Any ideas?  I have not tried the command line one yet, but I'm afraid that all this installing of different codecs/players could mugg up my Ubuntu installation.

Has Anyone else got their sirius player to work in Edgy?

--Kevin

---

### Post by wglenncamp on 2006-12-06
> **wilderness wanderer said:**
> I couldn't get the sirius player to work, but I have found a command line player which I actually prefer.

Instructions:

First, install mplayer and python-setuptools with apt or synaptic.

Then, open a terminal and run sudo easy_install BeautifulSoup

download sipie from [http://eli.criffield.net/sipie/sipie](http://eli.criffield.net/sipie/sipie) and put it somewhere in your path.  change permissions to make it executable.

run sipie.

You'll have to enter your user id & password, then it will prompt you to enter the captcha (from the graphic of letters and numbers displayed).

tab tab to show all streams, tab completion supported.

readme is at [http://eli.criffield.net/sipie/sipie_README](http://eli.criffield.net/sipie/sipie_README)

Hope this helps someone.

NICE!  This works great!  Thanks for the tip.

---

### Post by wilderness wanderer on 2006-12-06
I'm glad it worked for you.  The project is in active development, and I see the latest version posted 12/3 adds a now playing list as well as support for classes.  According to the author it shouldn't be hard to add a gtk interface to this.

Any Sirius subscribing GTK developers out there??

Here is the project's [freshmeat page]("http://freshmeat.net/projects/sipie/?branch_id=67224").

---

### Post by rubadub on 2006-12-08
Sipie was working great at first. But now it only plays for a few minutes when I start it then just goes blank. I don't know if its buffering or what, it doesn't say anything in the terminal. Is anyone else having this issue?

---

### Post by wilderness wanderer on 2006-12-08
> **rubadub said:**
> Sipie was working great at first. But now it only plays for a few minutes when I start it then just goes blank. I don't know if its buffering or what, it doesn't say anything in the terminal. Is anyone else having this issue?

I had this problem last night, but I've been streaming all day today with no dropouts.  Perhaps a server side problem at Sirius. 

I have noticed, however, a couple of crashes since upgrading to the latest version with playlist support.  These crashes seem to be related to the playlist functionality, and this can be disabled by changing a line in ~/.sipie/config from True to False:

```
showplaying = False
```

---

### Post by al_sharpe on 2006-12-08
Hello barton.jones

To get Sirius working install gxine and gxineplugin with 
synaptic from ubuntu repository. it will open up in a gxine app and you 
will be able to browse while it is playing.

Thanks goes to Aigars Mahinovs who emailed me how he got it working

Enjoy
Al Sharpe

---

### Post by Pobega on 2006-12-08
Sipie doesn't want to work at all for me, I've installed mplayer, python-setuptools and beautifulwhatever. Everytime I try to execute the file it basically does nothing.

```
pobega@ubuntu:~$ cd /usr/bin 
pobega@ubuntu:/usr/bin$ ./sipie
pobega@ubuntu:/usr/bin$
```

Anyone have any ideas what I might be doing wrong?

**Edit:** Nevermind, after a day of working around some things I finally got it working over the terminal. It's a very nice program, thanks for the easy setup instructions.

---

### Post by boris yeltsin on 2006-12-14
I have Sirius Canada, I assume no way for that to work with Sipie? Because Sipie looks great...

---

### Post by wilderness wanderer on 2006-12-17
> **boris yeltsin said:**
> I have Sirius Canada, I assume no way for that to work with Sipie? Because Sipie looks great...

You might want to check with the project author.  It could be as simple as just changing a url or two in the code. 

Have you tried logging in and/or streaming (from a Windows machine) at the [www.sirius.com](www.sirius.com) address?  If that works then you can probably use sipie as is.

---

### Post by LookTJ on 2006-12-18
Nice program! It works! Too bad my dad's internet radio subscription expired, so I signed up for 3 days(guest service).

This works very well!

EDIT: Forgot to mention that I meant sipie.

---

### Post by myname on 2006-12-21
sipie is the shiznit... This is so much better than going to sirius.com through a browser.  Thanx for the info on how to install it.

--Kevin

---

### Post by jensenhearing on 2006-12-22
@al_sharpe

Was very happy when i manage to install gxine. But alas, after rebooting, ubuntu is now a non-system disk and my pc cannot boot up. Am browsing online via Live CD.

---

### Post by lime4x4 on 2007-01-05
is there a way to have this working on a headless system?
I have a ubuntu box next to my tv tied into my surround sound for playing mp3 remotely
would like to be able to play sirius as well thru the headless box

---

### Post by wilderness wanderer on 2007-01-06
You should be able to log into the headless system via ssh and run sipie on it (assuming it is installed there).  You'd then be able to control it via the terminal on whatever machine you launched the ssh session from.  If you get it working on firefox on that machine, you should be able to start an ssh session with X forwarded (ssh -X) and control it that way.  In either case, audio is not forwarded through an ssh tunnel by default, so it should play on the headless system.

---

### Post by lime4x4 on 2007-01-06
john@john-edgy:~$ ssh -X john@192.168.0.16
john@192.168.0.16's password: 
Linux mythtv 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Fri Jan  5 18:41:52 2007 from 192.168.0.11
/usr/bin/X11/xauth:  creating new authority file /home/john/.Xauthority
john@mythtv:~$ gnome-terminal -x /usr/bin/sipie
Enter the captcha from the popup: CgS98N
 Enter stream: 

I don't get the nice interface like i do on my computer that always my to select which channel i want to listen to

---

### Post by wilderness wanderer on 2007-01-08
> **lime4x4 said:**
> 
I don't get the nice interface like i do on my computer that always my to select which channel i want to listen to

I don't understand, can you clarify? :confused:

What program are you using to listen on your other computer?

---

### Post by lime4x4 on 2007-01-08
here is a pic of the screen shot when i use my main computer to listen to sirius.As u can see i get a nice little drop down box to choose which channel i want to listen to

[http://lime4x4.pointclark.net:8888/coppermine/displayimage.php?album=3&pos=0](http://lime4x4.pointclark.net:8888/coppermine/displayimage.php?album=3&pos=0)

---

### Post by wilderness wanderer on 2007-01-10
> **lime4x4 said:**
> here is a pic of the screen shot when i use my main computer to listen to sirius.As u can see i get a nice little drop down box to choose which channel i want to listen to

[http://lime4x4.pointclark.net:8888/coppermine/displayimage.php?album=3&pos=0](http://lime4x4.pointclark.net:8888/coppermine/displayimage.php?album=3&pos=0)

Ah, that explains why I didn't understand.  The author of sipie has added the gui since I installed the program.  I didn't even realize there was a gui, so thanks for that!  

I just tried it and I see what you mean.  I get the gui when I start sipie on the machine directly, but not when I start it through an ssh session-- even with the -X option.  You might want to check with Sipie's author.

---

### Post by venik212 on 2007-01-12
Very helpful-- THANKS!.  However, I don't know:
1) How do I attach the icon to the sipie file?
2) How do I make that sipie file executable?
I know this is very basic, but my knowledge of Linux is similarly rudamentary.
Thanks again.

---

### Post by Pobega on 2007-01-12
> **venik212 said:**
> Very helpful-- THANKS!.  However, I don't know:
1) How do I attach the icon to the sipie file?
2) How do I make that sipie file executable?
I know this is very basic, but my knowledge of Linux is similarly rudamentary.
Thanks again.

I don't know the answer to your first question, but as for your second;

Assuming you downloaded to your home folder, you can do:

> chmod +x ~/sipie

---

### Post by venik212 on 2007-01-12
OK-- Thanks.

---

### Post by wilderness wanderer on 2007-01-17
> **venik212 said:**
> Very helpful-- THANKS!.  However, I don't know:
1) How do I attach the icon to the sipie file?
2) How do I make that sipie file executable?
I know this is very basic, but my knowledge of Linux is similarly rudamentary.
Thanks again.

Regarding 1, what I did is create a custom launcher on one of my panels.  Assuming you are using Gnome (Ubuntu) and not KDE (Kubuntu):

1.  Right click on a blank area of the panel and choose "Add to panel."
2.  Click the "Custom Application Launcher"
3.  Click on the "no Icon" button and browse to wherever you saved the icon.
4.  Give the launcher a name, for example "Sipie" or "Sirius Radio"
5.  In the "Command" field type the following

```
python /usr/bin/sipie
```

That's it.  You can click on the icon to launch the file.  It seems the author of Sipie has created an icon for the program, you may prefer to use it:

```
wget http://eli.criffield.net/sipie/sipie.png
```

---

### Post by elicriffield on 2007-01-24
> **boris yeltsin said:**
> I have Sirius Canada, I assume no way for that to work with Sipie? Because Sipie looks great...

It has canada support now, its an option in the config.

Eli

---

### Post by elicriffield on 2007-01-24
> **wilderness wanderer said:**
> You should be able to log into the headless system via ssh and run sipie on it (assuming it is installed there).  You'd then be able to control it via the terminal on whatever machine you launched the ssh session from.  If you get it working on firefox on that machine, you should be able to start an ssh session with X forwarded (ssh -X) and control it that way.  In either case, audio is not forwarded through an ssh tunnel by default, so it should play on the headless system.

It will try to run aalib's asciviewer if all else fails to view the captcha in asci art. Sometimes you can even read the letters ..... If your trying via ssh use as small as font as you can and as big of window as you can, and if that doesn't work exit and try again with a diffrent captcha.

Eli Criffield

---

### Post by skoalman88 on 2007-01-29
The Sipie thing is pretty cool. It is small, and a lot less intrusive than the player Sirius.com provides. Thanks for this.

---

### Post by myname on 2007-02-19
I am not receiving the following:

> 
~$ sipie
*Traceback (most recent call last):
*File "/usr/bin/sipie", line 890, in ?
*checkForUpdates()
*File "/usr/bin/sipie", line 800, in checkForUpdates
*hd = sipie.geturl('http://eli.criffield.net/sipie/LATESTIS')
*File "/usr/bin/sipie", line 164, in geturl
*handle = urllib2.urlopen(req)
*File "/usr/lib/python2.4/urllib2.py", line 130, in urlopen
*return _opener.open(url, data)
*File "/usr/lib/python2.4/urllib2.py", line 358, in open
*response = self._open(req, data)
*File "/usr/lib/python2.4/urllib2.py", line 376, in _open
*'_open', req)
*File "/usr/lib/python2.4/urllib2.py", line 337, in _call_chain
*result = func(*args)
*File "/usr/lib/python2.4/urllib2.py", line 1021, in http_open
*return self.do_open(httplib.HTTPConnection, req)
*File "/usr/lib/python2.4/urllib2.py", line 996, in do_open
*raise URLError(err)
*urllib2.URLError: <urlopen error (-3, 'Temporary failure in name resolution')>


I made a post here:

[http://www.ubuntuforums.org/showthread.php?p=2178995#post2178995](http://www.ubuntuforums.org/showthread.php?p=2178995#post2178995)

---

### Post by tomwsmf on 2007-02-19
I got that today as well.

The Url is unreachable and I think that is where its failing. I wonder if we just disabled the check for updates if it will go on. 

I would hate to think the XM<>Sirius merger today had anything to do with it:)-

-tomhiggins

---

### Post by tomwsmf on 2007-02-19
If you comment out the checkForUpdates line in /usr/bin/sipie things will work, at least for the cli version that I use.  

So look for the line that says 

checkForUpdates()

and replace it with

####checkForUpdates()

I made a copy of sipie from /usr/bin/ and place it on my desktop so that I don't frack up the real code. Hopefully we will find out what went wrong with the domain and it will all work out. 

Remember to run the modified sipie and not the untouched one.

-tomhiggins

---

### Post by myname on 2007-02-19
woot!!!!  worked like a charm!  Thanx

---

### Post by myname on 2007-02-19
> **tomwsmf said:**
> I got that today as well.

The Url is unreachable and I think that is where its failing. I wonder if we just disabled the check for updates if it will go on. 

I would hate to think the XM<>Sirius merger today had anything to do with it:)-

-tomhiggins

do you have a link to the latest news on this?  They aren't going to merge???

--Kevin

---

### Post by twisted_steel on 2007-02-19
> **myname said:**
> do you have a link to the latest news on this?  They aren't going to merge???

--Kevin


[http://xmradio.mediaroom.com/index.php?s=press_releases&item=1423](http://xmradio.mediaroom.com/index.php?s=press_releases&item=1423)

The two companies agreed, but it has to be approved by the FCC, SEC, the shareholders, etc.  So there are few steps beforehand.

---

### Post by elicriffield on 2007-02-20
Sorry about that, My website was down and that caused sipie to bomb on startup when it checked for an update.

My website is backup and theres a new version at [http://eli.criffield.net/sipie/sipie](http://eli.criffield.net/sipie/sipie) that doesn't reply on my website to be up.

Eli Criffield

---

### Post by tomwsmf on 2007-02-23
Thanks for the fix Eli, and thanks for the great tool. 

-tom

---

### Post by cometier on 2007-03-05
I'm very new to Ubuntu / Linux so please bear with me...

1) Where is the sipie config file stored?

2) What do I need to edit to enable the Canadian stream?

Thanks

---

### Post by venik212 on 2007-03-07
If you run Krusader (a VERY nice KDE file manager), you can use its LOCATE function and find any file on your system.

---

### Post by noshooz on 2007-03-09
Thanks so much for providing this! It's not the same as having the SIRIUS-provided player's GUI, but it works.

---

### Post by bcmiller on 2007-03-09
> **wilderness wanderer said:**
> I couldn't get the sirius player to work, but I have found a command line player which I actually prefer.

Instructions:

First, install mplayer and python-setuptools:

```
sudo apt-get install mplayer python-setuptools
```

Then, install Beautiful Soup:

```
sudo easy_install BeautifulSoup
```

Next download sipie:

```
wget http://eli.criffield.net/sipie/sipie
```

Make it executable:

```
sudo chmod a+x sipie
```

Move it to /usr/bin

```
sudo mv sipie /usr/bin
```

That's it.  You can run sipie from the command line or create a custom launcher using the attached image as the icon and the following as the "command" line:

```
gnome-terminal -x /usr/bin/sipie
```

You'll have to enter your user id & password the first time you run the program, as well as whether you are a guest or subscriber.  Thereafter you will only have to enter the "captcha" code each time you run the program.  

Press tab tab to show all streams, tab completion of stream names is supported.  You can press CTRL-C to end playing a stream and select another one.

readme is at [http://eli.criffield.net/sipie/sipie_README](http://eli.criffield.net/sipie/sipie_README)

Hope this helps someone.

This is brilliant... very simple and it works

---

### Post by lime4x4 on 2007-04-07
OK i did have this working great.Then i had to do a reinstall.I can play sirius but i no longer get the pop up window to select which channel i want to listen to. I have to manually type in the name of it.

---

### Post by techgeek on 2007-04-09
Well I'm nearly there.  I can get as far as entering a stream, but I get this error:

Traceback (most recent call last):
  File "/usr/bin/sipie", line 964, in ?
    sipie.play(stream)
  File "/usr/bin/sipie", line 405, in play
    asxurl = self.getasxurl(stream)
  File "/usr/bin/sipie", line 371, in getasxurl
    hd = self.geturl(url,post)
  File "/usr/bin/sipie", line 164, in geturl
    handle = urllib2.urlopen(req)
  File "/usr/lib/python2.4/urllib2.py", line 130, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.4/urllib2.py", line 364, in open
    response = meth(req, response)
  File "/usr/lib/python2.4/urllib2.py", line 471, in http_response
    response = self.parent.error(
  File "/usr/lib/python2.4/urllib2.py", line 402, in error
    return self._call_chain(*args)
  File "/usr/lib/python2.4/urllib2.py", line 337, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.4/urllib2.py", line 480, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
urllib2.HTTPError: HTTP Error 403: Forbidden

I have edited my ~/.sipie/config file as I have a Sirius Canada account:

[sipie]
username = techgeek
canada = **True**
playlist = playlist
popups = True
viewer = /usr/bin/eog
trygui = True
player = /usr/bin/mplayer -really-quiet -nojoystick -nolirc -user-agent NSPlayer -nomouseinput -aoesd,alsa,oss -prefer-ipv4 -cache 32 -playlist 
showplaying = True
host =** [www.siriuscanada.ca](www.siriuscanada.ca)**
cryptpass = ## I removed this
login_type = subscriber
cookiefile = cookies.txt
bitrate = low

The items bolded are the entries I have changed.  Apparently it doesn't like the host address?  I have used mp.siriuscanada.ca as well.  Any ideas.  Not that it should make a difference (since it works fine in Windows), but I am logging into my account from Yemen (I work here).  I hope I have provided enough information.  Thanks in advance for any assistance you can provide.

---

### Post by techgeek on 2007-04-09
I don't know if this makes a difference, but when I run:

/usr/bin/sipie

from the terminal window for the first time, it goes through asking me for username, password, account type, then it captures the code.  Of course the first time through it sets me up for a US account not a Canadian account.  I then edit the ~/.sipie/config file as mentioned above.  When I re-run /usr/bin/sipie, it doesn't display the captured code, it goes straight to asking me which stream I would like to listen to.  Is this supposed to happen?  I assumed that everytime I log in it should require the entering of the captured code.  Or am I wrong and it is only supposed to do this the first time?

---

### Post by techgeek on 2007-04-09
Well I was able to get it working nearly correctly without sipie.  I used this link:

[http://forums.megagram.com/comments.php?DiscussionID=6&page=1#Item_7]("http://forums.megagram.com/comments.php?DiscussionID=6&page=1#Item_7")

I installed the mozilla_plugin_vlc and lall it's dependencies.  Now it plays fine from within FIreFox, I just can't what's playing.  All the channel selections work fine.  I still get the missing plugin notification, but it starts to play in about 20 seconds.

Still interested to see if I can get sipie working, but at least I have music now.

---

### Post by elj4176 on 2007-04-10
It doesn't like my account info for some reason. I am a subscriber (have had sirius in my car for over 3 years now) and i can use firefox to listen. Everytime I try to login I get this after entering the code:

Enter username: mycorrectusername here
Enter password:  mycorrectpwhere

Login Type, type guest or subscriber
Enter login type: subscriber
LOGIN FAILED: bad password, invalid account?

I know my login info is right since i can access it through firefox so what is going on?

Thanks!

---

### Post by NICU on 2007-04-10
Hi everyone - there's a much easier way to get Sirius satellite radio to work in Linux.  There is a new Firefox extension which makes a Sirius player in the browser.  Check it out at [https://addons.mozilla.org/en-US/firefox/addon/3546](https://addons.mozilla.org/en-US/firefox/addon/3546)  This works great on both my Ubuntu PCs (Edgy and Feisty).  You may need to install an additional media player like mplayer or vlc, but most installs already have a media player installed.

---

### Post by mossking on 2007-04-24
Very Helpful. Thank you very much.

We run a content filter here at work. Using this method gets around the content filter, so I can listen on-line here at work. Very Cool.


> **wilderness wanderer said:**
> I couldn't get the sirius player to work, but I have found a command line player which I actually prefer.

Instructions:

First, install mplayer and python-setuptools:

```
sudo apt-get install mplayer python-setuptools
```

Then, install Beautiful Soup:

```
sudo easy_install BeautifulSoup
```

Next download sipie:

```
wget http://eli.criffield.net/sipie/sipie
```

Make it executable:

```
sudo chmod a+x sipie
```

Move it to /usr/bin

```
sudo mv sipie /usr/bin
```

That's it.  You can run sipie from the command line or create a custom launcher using the attached image as the icon and the following as the "command" line:

```
gnome-terminal -x /usr/bin/sipie
```

You'll have to enter your user id & password the first time you run the program, as well as whether you are a guest or subscriber.  Thereafter you will only have to enter the "captcha" code each time you run the program.  

Press tab tab to show all streams, tab completion of stream names is supported.  You can press CTRL-C to end playing a stream and select another one.

readme is at [http://eli.criffield.net/sipie/sipie_README](http://eli.criffield.net/sipie/sipie_README)

Hope this helps someone.

---

### Post by venik212 on 2007-05-04
I installed sipie under Feisty, but when I run it I get the error message:
asciiview not found

What do I do now?  This used to work under Edgy.

---

### Post by cryogenic on 2007-05-09
Interesting... I have the xine plugin installed along with the W32 codecs and it works perfectly fine in Konqueror. I just visited the Sirius site and loaded up a stream with no problems at all. Haven't tried it in Firefox but I honestly use Konqueror for most of my browsing needs.

---

### Post by chiefrocca on 2007-05-13
> **wilderness wanderer said:**
> I couldn't get the sirius player to work, but I have found a command line player which I actually prefer.

Instructions:

First, install mplayer and python-setuptools:

```
sudo apt-get install mplayer python-setuptools
```

Then, install Beautiful Soup:

```
sudo easy_install BeautifulSoup
```

Next download sipie:

```
wget http://eli.criffield.net/sipie/sipie
```

Make it executable:

```
sudo chmod a+x sipie
```

Move it to /usr/bin

```
sudo mv sipie /usr/bin
```

That's it.  You can run sipie from the command line or create a custom launcher using the attached image as the icon and the following as the "command" line:

```
gnome-terminal -x /usr/bin/sipie
```

You'll have to enter your user id & password the first time you run the program, as well as whether you are a guest or subscriber.  Thereafter you will only have to enter the "captcha" code each time you run the program.  

Press tab tab to show all streams, tab completion of stream names is supported.  You can press CTRL-C to end playing a stream and select another one.

readme is at [http://eli.criffield.net/sipie/sipie_README](http://eli.criffield.net/sipie/sipie_README)

Hope this helps someone.



I tried to do this and I entered the password incorrectly the first time, so everytime I would try and run the program it would try and log in and just close the command window.

I decided to try and just log on to sirius.com afterwards and I tried to go to AltNation but no music would play as the player window said"stopped".  After that I tried to get Howard Stern 100, and all of sudden it was playing and I heard the sweet voice of one Arthur Lange.  I immediately tried to go back to AltNation and try again, it works!!!  I don't want to close my browser!  

Maybe installing the programs in this series of commands, allows it to play through the regular website!

Why doesn't sirius make their site Linux friendly???  I would think that part of their target market would be linux users....no?

---

### Post by chiefrocca on 2007-05-13
I'll try it out...worth a shot!

---

### Post by Falcorn on 2007-05-29
I have succeeded in getting the Sirius player to open in feisty fawn, however, everytime i go to use it I am given a firefox message that says im missing plugin: application/x-oleobject
This is an active x plugin,  I cant seem to find the correct plugin to use to make sirius work, any suggestions?  I am a linux noob, details please!  thanks

---

### Post by Squid_blk on 2007-05-30
I just started using Linux and Ubuntu within the past month. I have three books on how to do things but some of the material is already dated or not specific to Feisty which I am running.  One of the things I was worried about with going to Linux was that I would not be able to run the Online radio from my home computer.  I thought the issue was a Shockwave player issue and was working on getting IEs for Linux which were easy to install and was trying to workout doing Shockwave.  But learning that is was an Active X thing was like D'oh.

But an answer to one of my posts was to check out Sipie.  It totally worked.  It took less than 10 minutes and now I can listen with my home computer with better speaker package instead of my work laptop (I work from home when I am home) with crappy speakers.  I like the GUI format. It is better than the Internet format.

One question!  I subscribed to the Premium version because it sounds better.  Should I bail on that?  The sound was not too bad using Sipie.

---

### Post by ScottLij on 2007-06-11
I believed I've installed everything properly but when I type:

 gnome-terminal -x /usr/bin/sipie

A window comes up real briefly and then closes and when I type just:

sipie

I  get the error:

/usr/bin/sipie: line 1: syntax error near unexpected token `newline'
/usr/bin/sipie: line 1: `<meta HTTP-EQUIV="REFRESH" content="10; url=http://sipie.sourceforge.net/">'

Am I missing something?

---

### Post by shanerdaner on 2007-06-12
> **ScottLij said:**
> I believed I've installed everything properly but when I type:

 gnome-terminal -x /usr/bin/sipie

A window comes up real briefly and then closes and when I type just:

sipie

I  get the error:

/usr/bin/sipie: line 1: syntax error near unexpected token `newline'
/usr/bin/sipie: line 1: `<meta HTTP-EQUIV="REFRESH" content="10; url=http://sipie.sourceforge.net/">'

Am I missing something?

I am having the same problem and the firefox player isn't producing sounds when I try it either but my speakers are working,  Any ideas?

---

### Post by venik212 on 2007-06-14
Me too-- Sipie worked fine for a while, but then I had to reinstll the desktop, and since the I get similar error messages.  HELP!

---

### Post by deeproot on 2007-06-18
my firefox gives the error msg about missing the plugin but it starts to stream fine.  Its using mplayer plugin. Takes about 10 seconds to start streaming and while its waiting it just looks like its not gonna work but it does.

---

### Post by Sternfan on 2007-06-20
Deeproot - I installed the mplayer plugin - sirius is still not working for me - Ubuntu 7.04 - anything else I can try to get sirius working on firefox?

---

### Post by apureevil1 on 2007-06-20
> **NICU said:**
> Hi everyone - there's a much easier way to get Sirius satellite radio to work in Linux.  There is a new Firefox extension which makes a Sirius player in the browser.  Check it out at [https://addons.mozilla.org/en-US/firefox/addon/3546](https://addons.mozilla.org/en-US/firefox/addon/3546)  This works great on both my Ubuntu PCs (Edgy and Feisty).  You may need to install an additional media player like mplayer or vlc, but most installs already have a media player installed.

This plugin works great on my windoz machine but I cannot get it to function on ubuntu fiesty..mplayer/vlc etc what did you do to get this to work?.

---

### Post by Sternfan on 2007-06-22
I have the firefox plugin, VLC & mplayer - still not working.

Rob

---

### Post by rwallinger on 2007-06-29
Hey, I've got Sipie working and I love the program, but I'm finding one thing that's not working right.  The pop-ups for the name, artist, etc... I've traced it back to being a problem with Beryl/Compiz.  When I have Beryl turned off and have the default Metacity GUI everything works, but when Beryl is active it doesn't work.  Does anyone have a workaround for this?

Thanks
Bob

---

### Post by venik212 on 2007-07-03
Could you please tell us EXACTLY how you installed Sipie?

---

### Post by LasTion on 2007-07-06
I followed those steps exactly as they are and I can't get Sipie to run in the terminal.. It flashes a window for a moment but then goes away. Any thoughts?

---

### Post by padlock.x on 2007-07-12
Sipie has moved to [http://sipie.sourceforge.net](http://sipie.sourceforge.net).  If you open up the file it's just a simple web page, that's why people are getting the line error.  I downloaded this one and it's working great.  They do have install instructions on the above page, but I just downloaded the tar.gz, uncompressed, and it worked.

---

### Post by venik212 on 2007-07-12
I have installed sipie according to the latest instructions, but this is what I get when I type sipie into the Konsol:

(c)Eli Criffield <pyeliATzendoDOTnet> [http://eli.criffield.net/sipie/](http://eli.criffield.net/sipie/)
Licensed under GPLv2 [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Traceback (most recent call last):
  File "/usr/bin/sipie", line 5, in <module>
    pkg_resources.run_script('Sipie==0.1181072404', 'sipie')
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 407, in run_script
    self.require(requires)[0].run_script(script_name, ns)
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 1091, in run_script
    exec script_code in namespace, namespace
  File "/usr/bin/sipie", line 6, in <module>

  File "build/bdist.linux-i686/egg/Sipie/__init__.py", line 8, in <module>
  File "build/bdist.linux-i686/egg/Sipie/Popup.py", line 6, in <module>
ImportError: No module named pynotify

---

### Post by daybreaker on 2007-08-16
When I try to do sudo easy_install sipie  I get a download error when trying to install Beautiful Soup saying "name or service not known"   

Ideas?

---

### Post by Squid_blk on 2007-08-20
I use Feisty and got the Python, Soup and Sipie software up and running in less than 15 minutes and have no problems in the past three or four months.  I use the mediaplugin with mplayer and vlc player for WindowsMedia player files and that works great too.  Only thing I cannot get to get going is the SiriusStudio CD so I can update my Stiletto software.  Said the cd was copy-protected.  Any advice?

---

### Post by rodzroom on 2007-08-20
I´m a semi-newb, using Ubuntu 7.04 Feisty, and I was anxious to get Sirius up and running. I followed a couple of different paths, including a fruitless struggle with Sipie. I guess it was a little over my head. I was finally successful-- here&#347; what I did:

1. Downloaded the MediaPlayerConnectivity plug-in for Firefox, found here: 
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

2. Downloaded M-Player:
[http://www.debianadmin.com/install-mplayer-ubuntu.html](http://www.debianadmin.com/install-mplayer-ubuntu.html)
[Note, I don´t think this was the exact place I downloaded it, but it is easy to find.]

3. Logged into the Sirius player, chose the channel I wanted, and clicked Play in the normal Sirius UI. The MediaPlayerConnectivity graphic appeared in place of the Windows Media Player status, with a play icon. 

[Clicking Play on that MediaPlayerConnectivity graphic didn´t work, though-- missing a required file or some such.]

4. Right-Clicked and copied the URL of the stream.

5. In MPlayer, I chose Open > Play URL, then pasted the URL that I copied in Firefox.

It´s working quite nicely for me-- may be a clunky process, but I usually stick to one station for a while anyway.... Hope this helps someone.

---

### Post by rodzroom on 2007-08-20
> **rodzroom said:**
> It´s working quite nicely for me-- may be a clunky process, but I usually stick to one station for a while anyway.... Hope this helps someone.

I should add that, previously, I downloaded the GStreamer codec package.
[http://gstreamer.freedesktop.org/](http://gstreamer.freedesktop.org/)

I would guess that that was required, too-- but I forgot to add that to my instructions because I did that a while ago...

---

### Post by daybreaker on 2007-08-20
> **rodzroom said:**
> I´m a semi-newb, using Ubuntu 7.04 Feisty, and I was anxious to get Sirius up and running. I followed a couple of different paths, including a fruitless struggle with Sipie. I guess it was a little over my head. I was finally successful-- here&#347; what I did:

1. Downloaded the MediaPlayerConnectivity plug-in for Firefox, found here: 
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

2. Downloaded M-Player:
[http://www.debianadmin.com/install-mplayer-ubuntu.html](http://www.debianadmin.com/install-mplayer-ubuntu.html)
[Note, I don´t think this was the exact place I downloaded it, but it is easy to find.]

3. Logged into the Sirius player, chose the channel I wanted, and clicked Play in the normal Sirius UI. The MediaPlayerConnectivity graphic appeared in place of the Windows Media Player status, with a play icon. 

[Clicking Play on that MediaPlayerConnectivity graphic didn´t work, though-- missing a required file or some such.]

4. Right-Clicked and copied the URL of the stream.

5. In MPlayer, I chose Open > Play URL, then pasted the URL that I copied in Firefox.

It´s working quite nicely for me-- may be a clunky process, but I usually stick to one station for a while anyway.... Hope this helps someone.

Unfortunately, thats what I'm doing right now, too (more or less)... I wish I could have gotten Sipie to work.

---

### Post by northband on 2007-08-21
Hi -

I am trying to install sipie, which seems to go fine (mplayer, beautifulsoup, etc...  However, when I run it I get errors, which almost look like python errors(?)

Can anyone help?  I am using Feisty Fawn 7.04  

Here's what I get (any help appreciated - thanks):


$:/usr/bin$ sipie
(c)Eli Criffield <pyeliATzendoDOTnet> [http://eli.criffield.net/sipie/](http://eli.criffield.net/sipie/)
Licensed under GPLv2 [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Traceback (most recent call last):
  File "/usr/bin/sipie", line 5, in <module>
    pkg_resources.run_script('Sipie==0.1181072404', 'sipie')
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 407, in run_script
    self.require(requires)[0].run_script(script_name, ns)
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 1091, in run_script
    exec script_code in namespace, namespace
  File "/usr/bin/sipie", line 22, in <module>
    
  File "build/bdist.linux-i686/egg/Sipie/cliPlayer.py", line 71, in cliPlayer
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 371, in getStreams
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 220, in auth
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 171, in __grabURL
IOError: [Errno 13] Permission denied: u'img_020.jpg'

---

### Post by northband on 2007-08-22
Grabbed latest SVN - monkeyed around with my setup.  Works like a champ.

-NB

---

### Post by daybreaker on 2007-09-06
> **northband said:**
> Grabbed latest SVN - monkeyed around with my setup.  Works like a champ.

-NB

what did you change? I am getting this error after grabbing the latest SVN

---

### Post by ntwrkguy on 2007-09-07
I don't exactly know what I have done differently, but I tried the online player today in firefox with mplayer and what not installed and it works fine! The online player window has to be active though for sound to come out. It's a step in the right direction!

---

### Post by camada on 2007-09-10
I'm having a similar problem as posted a couple days ago.

I previously had sipie running just fine on my Feisty laptop but wound up reinstalling from scratch after having to install windows xp on a separate partition.

After updating the new installation and following the newest instructions in the sipie distribution, I get the following errors:

$ sipie
(c)Eli Criffield <pyeliATzendoDOTnet> [http://eli.criffield.net/sipie/](http://eli.criffield.net/sipie/)
Licensed under GPLv2 [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)


username and a crypted password will be stored in /home/cdavis/.sipie/config
no plain text passwords are stored
if you want to change your password remove /home/cdavis/.sipie/config
then run sipie and it'll ask you for username and password again

Enter username:
Enter password:

Login Type, type guest or subscriber
Enter login type: subscriber
Are you using Sirius Cananda ([http://siriuscanada.ca](http://siriuscanada.ca))
 True or False: False
Traceback (most recent call last):
  File "/usr/bin/sipie", line 5, in <module>
    pkg_resources.run_script('Sipie==0.1181072404', 'sipie')
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 407, in run_script
    self.require(requires)[0].run_script(script_name, ns)
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 1091, in run_script
    exec script_code in namespace, namespace
  File "/usr/bin/sipie", line 22, in <module>
    
  File "build/bdist.linux-i686/egg/Sipie/cliPlayer.py", line 71, in cliPlayer
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 372, in getStreams
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 303, in tryGetStreams
Sipie.Factory.AuthError
==================================================================

The installation procedure I used was:

$ sudo apt-get install mplayer python-setuptools python-wxgtk2.6

$ sudo easy_install sipie


Any ideas?  I have sirius working w/ vlc in a browser, but I never see a now playing list.  I much prefer cliSipie over anything else.

Thanks!

---

### Post by headshok on 2007-09-11
Hey I'm having trouble getting sipie to work in Ubuntu Feisty

I followed the steps outlined in this thread and also scoured the readme
[http://eli.criffield.net/sipie/sipie_README](http://eli.criffield.net/sipie/sipie_README)

I have all of the prereqs installed as far as I can tell but I receive the following error

Traceback (most recent call last):
  File "/usr/bin/sipie", line 5, in <module>
    pkg_resources.run_script('Sipie==0.1181072404', 'sipie')
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 407, in run_script
    self.require(requires)[0].run_script(script_name, ns)
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 1091, in run_script
    exec script_code in namespace, namespace
  File "/usr/bin/sipie", line 22, in <module>
    
  File "build/bdist.linux-i686/egg/Sipie/cliPlayer.py", line 71, in cliPlayer
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 372, in getStreams
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 303, in tryGetStreams
Sipie.Factory.AuthError


Any help would be appreciated!

---

### Post by yuri_rage on 2007-09-23
Eli's site appears to be down at the moment.  I downloaded a tarball from SourceForge, but it appears to have quite a bit more than just a command line sipie executable.  I have no idea how to go about installing the package.  Anybody have any insight?

EDIT:
Alright, I followed the README as best I could.  Now I get this...just like a few others have posted:

```

Traceback (most recent call last):
  File "/usr/bin/sipie.py", line 5, in <module>
    pkg_resources.run_script('Sipie==0.1190648273', 'sipie.py')
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 448, in run_script
    self.require(requires)[0].run_script(script_name, ns)
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 1173, in run_script
    exec script_code in namespace, namespace
  File "/usr/bin/sipie.py", line 22, in <module>
    
  File "build/bdist.linux-i686/egg/Sipie/cliPlayer.py", line 69, in cliPlayer
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 99, in __init__
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 115, in __setupOpener
  File "/usr/lib/python2.5/urllib2.py", line 467, in build_opener
    opener.add_handler(h)
  File "/usr/lib/python2.5/urllib2.py", line 303, in add_handler
    type(handler))
TypeError: expected BaseHandler instance, got <type 'NoneType'>

```

---

### Post by yuri_rage on 2007-09-25
Bump...anybody have any ideas?  Anybody...?

---

### Post by elicriffield on 2007-10-01
Please try the latest version @ [http://downloads.sourceforge.net/sipie/Sipie-0.1190648273.tar.gz](http://downloads.sourceforge.net/sipie/Sipie-0.1190648273.tar.gz)

Make sure you have version 0.1190648273 and let me know how that works.

I think all the problems are fixed in the latest version. Sirius changed the way there captcha worked and that broke sipie.

Eli Criffield

---

### Post by llamakc on 2007-10-01
Newest version is working for me (on Feisty). Thanks.

---

### Post by headshok on 2007-10-02
Awesome new release works perfect...  For those that used easy_install this is all I did
```

sudo easy_install --upgrade sipie
```

---

### Post by clancymf on 2007-10-03
I did the following:
clancymf@clancypc:~$ sudo easy_install --upgrade sipie
Searching for sipie
Reading [http://cheeseshop.python.org/pypi/sipie/](http://cheeseshop.python.org/pypi/sipie/)
Couldn't find index page for 'sipie' (maybe misspelled?)
Scanning index of all packages (this may take a while)
Reading [http://cheeseshop.python.org/pypi/](http://cheeseshop.python.org/pypi/)
Reading [http://cheeseshop.python.org/pypi/Sipie/0.1179843539](http://cheeseshop.python.org/pypi/Sipie/0.1179843539)
Reading [http://eli.criffield.net/sipie/](http://eli.criffield.net/sipie/)
Best match: Sipie 0.1190648273
Downloading [http://downloads.sourceforge.net/sipie/Sipie-0.1190648273.tar.gz](http://downloads.sourceforge.net/sipie/Sipie-0.1190648273.tar.gz)
Processing Sipie-0.1190648273.tar.gz
Running Sipie-0.1190648273/setup.py -q bdist_egg --dist-dir /tmp/easy_install-jTQsJf/Sipie-0.1190648273/egg-dist-tmp-QJ0jQO
Adding Sipie 0.1190648273 to easy-install.pth file
Installing sipie.py script to /usr/bin
Installing cliSipie script to /usr/bin
Installing gtkSipie script to /usr/bin
Installing wxSipie script to /usr/bin

Installed /usr/lib/python2.5/site-packages/Sipie-0.1190648273-py2.5.egg
Processing dependencies for sipie
clancymf@clancypc:~$ gnome-terminal -x /usr/bin/sipie 
clancymf@clancypc:~$ 

It looks like it worked but when i run the gnome-terminal -x /usr/bin/sipie the screen just flashes and nothing...

Sorry still a major noob when it comes to ubuntu

---

### Post by headshok on 2007-10-03
It appears that you downloaded the latest release so that shouldnt be a problem.  I would try to clear out the ~/.sipie/config

Then, try to run
/usr/bin/cliSipie
in a terminal window
This will give you more detail on what the possible error might be, as it wont just disappear.

---

### Post by llamakc on 2007-10-03
> **clancymf said:**
> I did the following:
clancymf@clancypc:~$ sudo easy_install --upgrade sipie
Searching for sipie
Reading [http://cheeseshop.python.org/pypi/sipie/](http://cheeseshop.python.org/pypi/sipie/)
Couldn't find index page for 'sipie' (maybe misspelled?)
Scanning index of all packages (this may take a while)
Reading [http://cheeseshop.python.org/pypi/](http://cheeseshop.python.org/pypi/)
Reading [http://cheeseshop.python.org/pypi/Sipie/0.1179843539](http://cheeseshop.python.org/pypi/Sipie/0.1179843539)
Reading [http://eli.criffield.net/sipie/](http://eli.criffield.net/sipie/)
Best match: Sipie 0.1190648273
Downloading [http://downloads.sourceforge.net/sipie/Sipie-0.1190648273.tar.gz](http://downloads.sourceforge.net/sipie/Sipie-0.1190648273.tar.gz)
Processing Sipie-0.1190648273.tar.gz
Running Sipie-0.1190648273/setup.py -q bdist_egg --dist-dir /tmp/easy_install-jTQsJf/Sipie-0.1190648273/egg-dist-tmp-QJ0jQO
Adding Sipie 0.1190648273 to easy-install.pth file
Installing sipie.py script to /usr/bin
Installing cliSipie script to /usr/bin
Installing gtkSipie script to /usr/bin
Installing wxSipie script to /usr/bin

Installed /usr/lib/python2.5/site-packages/Sipie-0.1190648273-py2.5.egg
Processing dependencies for sipie
clancymf@clancypc:~$ gnome-terminal -x /usr/bin/sipie 
clancymf@clancypc:~$ 

It looks like it worked but when i run the gnome-terminal -x /usr/bin/sipie the screen just flashes and nothing...

Sorry still a major noob when it comes to ubuntu

It's /usr/bin/sipie.py now.

---

### Post by clancymf on 2007-10-03
If i could hug you i would.

THANKS A MILLION!!!!!

---

### Post by llamakc on 2007-10-03
Send me a virtual beer and all is well. Enjoy your Sirius!

Bababooey!

---

### Post by headshok on 2007-10-03
Ahhh I just noticed that as well...  

Note to all if you have a previous version of sipie installed check the 2 files

```

more /usr/bin/sipie.py 
#!/usr/bin/python
# EASY-INSTALL-SCRIPT: 'Sipie==0.1190648273','sipie.py'
__requires__ = 'Sipie==0.1190648273'
import pkg_resources
pkg_resources.run_script('Sipie==0.1190648273', 'sipie.py')
```

```
more /usr/bin/sipie
#!/usr/bin/python
# EASY-INSTALL-SCRIPT: 'Sipie==0.1181072404','sipie'
__requires__ = 'Sipie==0.1181072404'
import pkg_resources
pkg_resources.run_script('Sipie==0.1181072404', 'sipie')
```

I just deleted /usr/bin/sipie to prevent confusion. 
 It appears that easy_install modified the cliSipie, wxSipie, and gtkSipie, but didnt touch the /usr/bin/sipie file...

I've just been launching cliSipie from my panel with the following command.
gnome-terminal -t "Sirius Radio" -x /usr/bin/cliSipie
wx and gtxSipie disappear after listening for awhile and I have to manually kill the process and then restart if I want to change stations etc...  Anybody else having that problem?  Any other cool solutions/integrations of Sipie into a panel applet or anything?

---

### Post by llamakc on 2007-10-03
A panel applet would be REALLY kick@$$!

---

### Post by rolyat420 on 2007-10-04
Not sure if this is a gutsy thing (i had to try it out before final release, don't know why)

I did have it working on fiesty just fine. Here's what I did

Fetch the latest version
```
 svn co https://sipie.svn.sourceforge.net/svnroot/sipie sipie
```

So I installed the required dependencies
```
sudo apt-get install mplayer python-setuptools python-wxgtk2.6
```

then ran
```
sudo easy_install sipie
```

ran sipie from command put in my name, password, subscriber, false then it crashes here is the output.
```
Traceback (most recent call last):
  File "/usr/bin/sipie.py", line 5, in <module>
    pkg_resources.run_script('Sipie==0.1190648273', 'sipie.py')
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 448, in run_script
    self.require(requires)[0].run_script(script_name, ns)
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 1173, in run_script
    exec script_code in namespace, namespace
  File "/usr/bin/sipie.py", line 22, in <module>

  File "build/bdist.linux-i686/egg/Sipie/cliPlayer.py", line 69, in cliPlayer
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 99, in __init__
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 115, in __setupOpener
  File "/usr/lib/python2.5/urllib2.py", line 467, in build_opener
    opener.add_handler(h)
  File "/usr/lib/python2.5/urllib2.py", line 303, in add_handler
    type(handler))
TypeError: expected BaseHandler instance, got <type 'NoneType'>

```

Anybody experiencing similar or know what could be wrong?

---

### Post by Vanadaar on 2007-10-09
I get the same thing using easy_install on gutsy beta.

---

### Post by clancymf on 2007-10-09
> **Vanadaar said:**
> I get the same thing using easy_install on gutsy beta.

If this is the case I am going to hold off on upgrading for a while.

---

### Post by aggieml on 2007-10-12
Tried all known methods.  Here's what I've found:

1...the sirius add-on for firefox is awesome.  Works great on my PCLinux laptop but for some reason no sound comes out on Kubuntu when I have no other sound-related problems.  The only thing missing in this plugin is "now playing" info with artist and song title.  As of 10/10/07, the author has said that he will have a new release very soon.

2.  For the life of me, I cannot get Sipie to work.  If I type sipie at command line, I get nothing.  If I type cliSipie, I get to enter my sirius credentials and then it crashes with a "expected BaseHandler" error.

3.  I am able to listen in Firefox by using the sirius.com player.  I needed to install the MediaPlayerConnectivity add-on for firefox.  When the sirius player comes up, I get that annoying "missing plugin" error, but then when I click on the player the MediaPlayerConnectivity add-on launches Kaffeine and the stream plays fine.


Mike

---

### Post by llamakc on 2007-10-12
> **llamakc said:**
> Newest version is working for me (on Feisty). Thanks.

No longer working on Gutsy.

```

ken@llamakc 08:32:37:~/src/Sipie-0.1190648273$ sipie.py 
Traceback (most recent call last):
  File "/usr/bin/sipie.py", line 5, in <module>
    pkg_resources.run_script('Sipie==0.1190648273', 'sipie.py')
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 448, in run_script
    self.require(requires)[0].run_script(script_name, ns)
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 1173, in run_script
    exec script_code in namespace, namespace
  File "/usr/bin/sipie.py", line 22, in <module>
    
  File "build/bdist.linux-i686/egg/Sipie/cliPlayer.py", line 69, in cliPlayer
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 99, in __init__
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 115, in __setupOpener
  File "/usr/lib/python2.5/urllib2.py", line 467, in build_opener
    opener.add_handler(h)
  File "/usr/lib/python2.5/urllib2.py", line 303, in add_handler
    type(handler))
TypeError: expected BaseHandler instance, got <type 'NoneType'>

```

---

### Post by Shrav on 2007-10-13
Same error for me after upgrading to Gutsy today :(

---

### Post by rolyat420 on 2007-10-15
Looks like somebody submitted a patch to fix the sipie + gutsy issue.  Check it out here.
[http://sourceforge.net/tracker/index.php?func=detail&aid=1813501&group_id=196723&atid=958597]("http://sourceforge.net/tracker/index.php?func=detail&aid=1813501&group_id=196723&atid=958597")

I am at work right now, but want to try it when I get home.  If anyone can try it right now, please post and let us know how it went

---

### Post by 43moon on 2007-10-15
* edited post

---

### Post by llamakc on 2007-10-15
EDIT: Patch didn't work for me. I had an older sipie.py in my path.

---

### Post by rolyat420 on 2007-10-16
First I went and grabbed the latest svn```
 svn co https://sipie.svn.sourceforge.net/svnroot/sipie sipie
```

Tried the patch, but when I run```
sudo easy_install sipie
``` It goes out and fetches a new tar.gz from sourceforge instead of what i grabed thru svn so it doesn't have the patched code.  Here is what I did to get around that.

First I tried to locate Factory.py on my computer thru ```
locate Factory.py
```

Nothing shows up, Thru a little more research and watching the install process as well as the crash output, I found out that it is really packaged up in this file /usr/lib/python2.5/site-packages/Sipie-0.1184989269-py2.5.egg

So I copied that file to my own directory and extracted using ark. BTW it is a archive zip.

Then I downloaded the patch from 

and copied it to the './Sipie/Sipie' directory of the extracted .egg file

Ran ```
patch -p0 <sipie.patch
``` in konsole

Everything should go fine.

Then i rezipped the folders Sipie & EGG-INFO and named it Sipie-0.1184989269-py2.5.egg

Then I copied it back over to /usr/lib/python2.5/site-packages/ directory as root

Removed the old config in my home directory just in case ```
rm -rf /home/*****/.sipie
```

Then ran sipie. Followed the prompts and I am up in running.

Hope I didn't confuse anyone and not sure if I can but I attached the Sipie-0.1184989269-py2.5.egg file so you can just do the svn checkout, run sudo easy_install sipie then overwrite the file located in /usr/lib/python2.5/site-packages/ with my attached file. And you should be up in running.  Just remember to rename the attachment from a .zip to .egg

I just hope eli updates sipie soon b/c when gutsy rolls out there may be some sipie users who are not aware of this situation.

---

### Post by llamakc on 2007-10-16
That worked perfectly. I'm up and running. Much thanks.

---

### Post by 43moon on 2007-10-16
rolyat420, 

I appreciate all of your hard work; and the fact that you got it running gives me hope, but I am having no luck following your instructions.

---

### Post by llamakc on 2007-10-17
43,

Start in a clean directory and do the svn checkout line:
```

 svn co [https://sipie.svn.sourceforge.net/svnroot/sipie](https://sipie.svn.sourceforge.net/svnroot/sipie) sipie

```

Next do this:

```

sudo easy_install sipie

```

And then download the attachment in rolyat420's post. Rename the file extension from .zip to .egg and next mv the .egg to 

 /usr/lib/python2.5/site-packages/ with sudo.

That should do it for you.

---

### Post by 43moon on 2007-10-17
I finally got it working after some trial and error.  Thanks again rolyat420 for figuring it out and thanks to llamakc for the clarification.

---

### Post by rolyat420 on 2007-10-17
I can't take credit for the patch that fixed it, but glad to see it is working for ya now.

---

### Post by Keith_Burton on 2007-10-17
I wasn't familiar with sipie and just tried it.  Okay it works, but takes my cpu to 100%. Not acceptable, since I already had an alternative:
   sudo apt-get install mplayer mozilla-mplayer
After that, you can use the web-based player from inside Firefox.

---

### Post by rolyat420 on 2007-10-17
So when you run top, sipie is pegged at 100% CPU usage or mplayer? By default sipie uses mplayer for the stream, sipie is merely the frontend, similar to sirius.com online player. On my system mplayer sits around 2% while streaming.

I think the mozilla-mplayer package for firefox to stream sirius thru firefox was mention earlier in this thread. I just like to use a stand alone and not have to fire up firefox, log in and fill in captcha everytime I would like to listen to sirius.  To each their own. That's the beauty of freedom. Choice. Keep rockin.

---

### Post by GMeola on 2007-10-18
rolyat420 kudos on posting a working solution for Gusty... Can't live without Sirius...

---

### Post by daybreaker on 2007-10-18
> **llamakc said:**
> It's /usr/bin/sipie.py now.

Snap! Sipie works! Finally, after like 3 months! I no longer have to use Amarok!

Thanks to headshok for the easy_install --upgrade, and to llamakc for the sipie.py!

---

### Post by Shrav on 2007-10-18
I also got it working following the instructions in this thread. I have to launch it using 

/usr/bin/cliSipie

and then I get the Stream Name prompt. Is this the way this patched version works? I do miss the drop down list that I had under Fiesty instead of typing in the channel name I want to listen to. Did I screw up or is this the way it will work until a new version is released? It isn't the end of the world and I'm thankful that the Ubuntu community works together so well. Thanks to all for their help! :guitar:

---

### Post by llamakc on 2007-10-18
You should also have a /usr/bin/sipie.py which provides that wXwidget (if you have already installed python-wxgtk2.6).

---

### Post by Shrav on 2007-10-18
> **llamakc said:**
> You should also have a /usr/bin/sipie.py which provides that wXwidget (if you have already installed python-wxgtk2.6).

Sweet!!!!!!!!!! All I have to do is launch /usr/bin/sipie.py and it all works as it once did. You guys ROCK!!!!:guitar:

---

### Post by Squid_blk on 2007-10-20
I just upgraded to Gusty from Feisty this afternoon. I had Sipie working with the Gui up until today.   I was launching the Gui application from the Apps menu as it did not have to bring up a terminal window.  No it does not work.  The Gui will not work and when I do a command line I get this

brandon@el-diablo:~$ sipie
(c)Eli Criffield <pyeliATzendoDOTnet> [http://eli.criffield.net/sipie/](http://eli.criffield.net/sipie/)
Licensed under GPLv2 [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)
Traceback (most recent call last):
  File "/usr/bin/sipie", line 922, in <module>
    sipie = Sipie(configItems)
  File "/usr/bin/sipie", line 135, in __init__
    self.setup_opener()
  File "/usr/bin/sipie", line 151, in setup_opener
    opener = urllib2.build_opener(cookie_handler,proxy_handler)
  File "/usr/lib/python2.5/urllib2.py", line 467, in build_opener
    opener.add_handler(h)
  File "/usr/lib/python2.5/urllib2.py", line 303, in add_handler
    type(handler))
TypeError: expected BaseHandler instance, got <type 'NoneType'>

I am a newbie to not only Ubuntu but to Linux and have only been using since May. I have books that helped me learn but I am totally lost here.

I do not know how to get it working.  I downloaded the patch and that zip file but do not know what to do with them. I renamed the Sipie-0.1190648273-py2.5.zip to '.egg but I did the mv command and it did not work. How do you mv with sudo?  I think I have Sipie 2.5 but can someone repost how to fix this Gusty issue because I am completely lost and now annoyed Sipie is not working. Please help. Thanks.

---

### Post by Squid_blk on 2007-10-20
I did a quick yahoo search can found that there is a plugin/addon for Firefox (versions 2 and higher) for the Sirius Radio Player.  It is called Sirius Player 1.1 and is located at:

[https://addons.mozilla.org/en-US/firefox/addon/3546](https://addons.mozilla.org/en-US/firefox/addon/3546)

It seems to work. But I would rather use Sipie.  I have been thinking of getting the full web subscription to get all the channels which is not cheap but I do work from home when I am not traveling and miss some of the channels missing from the free webplayer.  I have a Stiletto 100 which works well in my Scion that has an Aux port.   But when I rent cars without Aux ports I have trouble with the FM modulation because the Stiletto does not go as low as the radios meant for cars go.

The only problem I have had with Sipie is that eventually your login will expire. I found that it if I logged into Sirius through my Windows-based work laptop then Sipie was back in action. The Gui does not really show you how to stay logged in.  But with Sipie you do not have to have a browser open and the nice workspace windows with Ubuntu let one switch screens without minimizing or worrying about too much clutter.  I like Sipie and for those who have it they should consider donating. I know I plan to, but right now it is not working.  So still need a fix. Thanks.

---

### Post by rolyat420 on 2007-10-22
Squid_Blk

The easiest thing to do is completely start fresh.

Remove the files that show up after running
```
locate sipie
```

Then do a new svn checkout
```
svn co https://sipie.svn.sourceforge.net/svnroot/sipie sipie
```

Then install
```
sudo easy_install sipie
```

Download this attachment (its the patched code to allow it to work in gutsy)
```
[http://ubuntuforums.org/attachment.php?attachmentid=46552&d=1192583943]("http://ubuntuforums.org/attachment.php?attachmentid=46552&d=1192583943")
```

Rename the extension from .zip to .egg

Then copy it to /usr/lib/python2.5/site-packages/ with sudo
```
sudo cp Sipie-0.1184989269-py2.5.egg /usr/lib/python2.5/site-packages/
```

Run sipie.py from command line, fill in your stuff and it should be kicking. Good luck

---

### Post by Buckley9477 on 2007-10-24
I upgraded to Gutsy about a week ago and my sipie stopped working. I just did everything you laid out step by step with the exception of the file name for the .egg file being different (Sipie-0.1190648273-py2.5.egg), and I am still getting the same result.

brandon@brandon-desktop:~/Desktop$ sipie.py
Traceback (most recent call last):
  File "/usr/bin/sipie.py", line 5, in <module>
    pkg_resources.run_script('Sipie==0.1184989269', 'sipie.py')
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 448, in run_script
    self.require(requires)[0].run_script(script_name, ns)
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 1173, in run_script
    exec script_code in namespace, namespace
  File "/usr/bin/sipie.py", line 22, in <module>

  File "build/bdist.linux-i686/egg/Sipie/cliPlayer.py", line 69, in cliPlayer
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 99, in __init__
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 115, in __setupOpener
  File "/usr/lib/python2.5/urllib2.py", line 467, in build_opener
    opener.add_handler(h)
  File "/usr/lib/python2.5/urllib2.py", line 303, in add_handler
    type(handler))
TypeError: expected BaseHandler instance, got <type 'NoneType'>

I notice this in the error: " pkg_resources.run_script('Sipie==**0.1184989269**', 'sipie.py')"  shouldn't this read " pkg_resources.run_script('Sipie==**0.1190648273**', 'sipie.py')"

---

### Post by Buckley9477 on 2007-10-24
UPDATE: I changed 0.1184989269 to 0.1190648273 in the /usr/bin/sipie.py file and it worked like a charm!!

---

### Post by crshman on 2007-10-24
Wonderful, that did it for me! Running Gutsy and I have now completed my full migration to linux...this was the last piece of the puzzle =D

---

### Post by Squid_blk on 2007-10-24
I did the Locate and it found the Sipie files and folder. How do I remove the files? Do I need to change into that directory? This sounds stupid but I have not had to do that before.  Also the egg file is not the same one in the download. Did miss something there? It is "Sipie-0.1190648273-py2.5.egg"

Sirius Player plugin for Firefox works but it does that annoying "Are You Still Listening" thing and is not as good as Sipie.

---

### Post by linux4me on 2007-10-24
Sipie worked great for me until I upgraded to Gutsy today.

I think I followed the instructions above correctly:
> 
Remove the files that show up after running
Code:

locate sipie

Then do a new svn checkout
Code:

svn co [https://sipie.svn.sourceforge.net/svnroot/sipie](https://sipie.svn.sourceforge.net/svnroot/sipie) sipie

Then install
Code:

sudo easy_install sipie

Download this attachment (its the patched code to allow it to work in gutsy)
Code:

[http://ubuntuforums.org/attachment.p...2&d=1192583943](http://ubuntuforums.org/attachment.p...2&d=1192583943)

Rename the extension from .zip to .egg

Then copy it to /usr/lib/python2.5/site-packages/ with sudo
Code:

sudo cp Sipie-0.1184989269-py2.5.egg /usr/lib/python2.5/site-packages/

Run sipie.py from command line, fill in your stuff and it should be kicking. Good luck


including altering the file name in sipie.py from 1184989269 to 1190648273; however, when I enter sipie.py at the command line to run it and enter the captcha, I get:
> 
Traceback (most recent call last):
  File "/usr/bin/sipie.py", line 5, in <module>
    pkg_resources.run_script('Sipie==0.1190648273', 'sipie.py')
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 448, in run_script
    self.require(requires)[0].run_script(script_name, ns)
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 1173, in run_script
    exec script_code in namespace, namespace
  File "/usr/bin/sipie.py", line 22, in <module>
    
  File "/home/taylor/Desktop/sipie/Sipie/cliPlayer.py", line 74, in cliPlayer
  File "/home/taylor/Desktop/sipie/Sipie/Factory.py", line 370, in getStreams
  File "/home/taylor/Desktop/sipie/Sipie/Factory.py", line 301, in tryGetStreams
Sipie.Factory.AuthError


There are no "taylor" folders on my machine, so I'm guessing the problem is with where sipie is looking for files. 

How do I fix this?

---

### Post by Squid_blk on 2007-10-25
I cannot delete, move or remove the original Sipie files anymore. Something changed during the upgrade and I lost root permissions. I did not change anything or do anything. When I tried to do the reinstall thinking it would overwrite stuff it created the Sipie new folder in my Home folder for some reason. I tried to delete the two files from the usr folder and it says I do not have permission and I the trash can will not delete the folder from the Home folder. This is crazy but even with the sudo permission enabled in Nautilus via the Terminal it still does not work.  I am hoping I do not have to do a clean install but not sure what happened here.

---

### Post by linux4me on 2007-10-25
Hi Squid,

Have you tried opening a terminal window and trying:
```
locate sipie
```

Then working with that list of files, do the deletions straight from terminal; for example, if locate lists:
> /home/squid/.sipie

You try:
```
sudo rm -rf /home/squid/.sipie
```

It should prompt you for your password and then get rid of all the files.

The -rf means that rm works **r**ecursively and **f**orces the deletions without prompting you for each file. 

I'm no expert, but that worked for me.

---

### Post by thepaulmorris on 2007-10-27
I currently have Sipie running in Gutsy, everything works as it should, the dropdown list, I see track title and artist, but I am hearing no sound whatsoever! I hear sound everywhere else, youtube, break, etc, even if I use mplayer to stream sirius i can hear it, its only with sipie that I hear no sound. Does anyone have any suggestions?

Thanks!

---

### Post by Squid_blk on 2007-10-31
I am having no success. Gusty says I am no longer the root user or the owner of my own system. This means I cannot get rid of the old files, new files do not replace older ones and I cannot change some things. I just may have to do a complete system wipe because this upgrade is not working properly. This was the one thing I was hoping that I would not have to ever do except with a system or hardware failure when I switched to Linux.  I now try to locate sipie and it comes up with nothing yet things are there. Now I do not know what is wrong.  Sipie now gets an error, I cannot get rid of the old files now and I no longer have the gui part either.  Any suggestions?

---

### Post by llamakc on 2007-10-31
> **Squid_blk said:**
> I am having no success. Gusty says I am no longer the root user or the owner of my own system. This means I cannot get rid of the old files, new files do not replace older ones and I cannot change some things. I just may have to do a complete system wipe because this upgrade is not working properly. This was the one thing I was hoping that I would not have to ever do except with a system or hardware failure when I switched to Linux.  I now try to locate sipie and it comes up with nothing yet things are there. Now I do not know what is wrong.  Sipie now gets an error, I cannot get rid of the old files now and I no longer have the gui part either.  Any suggestions?

Sounds like you broke something. Yes it is fixable.

Let's start with the first step: Open a Terminal and type the following. Cut/paste the output back in this thread.

```

cd && ls -lh

```

---

### Post by Squid_blk on 2007-10-31
I have learned how to remove files properly but what has surprised me with Linux is that it does not always overwrite stuff and it is possible to have multiple versions of files and folders which is weird.

I think I have removed all of the old Sipie files.  I removed the old sipie.py from the /usr/bin and the files in the sipie folder.

I did the cd && ls -lh command and came up with:

brandon@el-diablo:~$ cd && ls -lh
total 80K
drwxr-xr-x  2 brandon brandon 4.0K 2007-05-13 16:52 bin
drwxr-xr-x  2 brandon brandon 4.0K 2007-10-20 18:29 Desktop
drwxr-xr-x  3 brandon brandon 4.0K 2007-10-30 10:50 documents
drwxr-xr-x  2 brandon brandon 4.0K 2007-10-26 18:35 downloads
drwxr-xr-x  2 brandon brandon 4.0K 2007-08-30 19:34 ebooks
lrwxrwxrwx  1 brandon brandon   26 2007-05-13 15:07 Examples -> /usr/share/example-content
drwxr-xr-x  8 brandon brandon 4.0K 2007-08-30 12:28 gaming
drwxr-xr-x  4 brandon brandon  16K 2007-08-29 14:05 music
drwxr-xr-x  3 brandon brandon 4.0K 2007-09-28 23:29 ogg
drwxr-xr-x 17 brandon brandon 4.0K 2007-10-20 11:40 pictures
drwxr-xr-x  2 brandon brandon 4.0K 2007-10-20 13:46 Public
drwxr-xr-x  3 brandon brandon 4.0K 2007-09-01 17:54 quicken files
drwxr-xr-x  2 brandon brandon 4.0K 2007-05-13 17:02 sounds
drwxr-xr-x  2 brandon brandon 4.0K 2007-10-20 13:46 Templates
drwxr-xr-x  3 brandon brandon 4.0K 2007-10-30 16:12 VASSAL
drwxr-xr-x  7 brandon brandon 4.0K 2007-10-20 18:45 VASSAL-3.0
drwxr-xr-x  2 brandon brandon 4.0K 2007-05-13 17:07 videos
drwxr-xr-x  3 brandon brandon 4.0K 2007-06-08 18:19 Windows

Other things seem to work. Vassal stopped working and with the older version I had made a documentation folder which I found with 3.0 likes to be there even if it makes no sense. The newer version works a bit different than my previous version but it works nonetheless.

Sipie is the only thing not working in Gusty.  I think I can now at least get the files loaded and get to the error that Buckley9477 noted: 

" pkg_resources.run_script('Sipie==0.1184989269', 'sipie.py')" shouldn't this read " pkg_resources.run_script('Sipie==0.1190648273', 'sipie.py')"

But I do not know how to get permission to edit the .py file.  So I think I am making progress.

---

### Post by Buckley9477 on 2007-10-31
try:    sudo gedit /usr/bin/sipie.py

---

### Post by Squid_blk on 2007-10-31
Ah, sudo. I am starting to get it now.  I have been reading allot but it appears I must be reverting to my old 16-bit Atari days and my Macs I had in the '90s and probably what makes others shy away from Linux is that you cannot do everything in graphical mode. When I clicked on the sipie.py file it did open with the text editor but said no way to any changes.  I have learned that I need to do the sudo from the terminal or sudo with Nautilus to get it to work.  I will get to the bottom of this over the weekend as work will have me out of state for the next few days.  Makes much more sense now.  Thanks for the help so far so I am feeling more confident that it will work soon. Cool beans!

---

### Post by Betelgeuse1 on 2007-11-01
> **al_sharpe said:**
> Hello barton.jones

To get Sirius working install gxine and gxineplugin with 
synaptic from ubuntu repository. it will open up in a gxine app and you 
will be able to browse while it is playing.

Thanks goes to Aigars Mahinovs who emailed me how he got it working

Enjoy
Al Sharpe

Thanks for this tip!! I'm a newbie so there might be an easier way.I got it working by downloading gxine and all the plugins using synaptec. Then I downloaded the firefox unplug plugin (search the extensions page or google it).  The unplug plugin allows the link to a video stream to be saved as a file or url.  I then logged into the sirius player as normal from their website and used unplug to save the stream as a file to the desktop.  In my case the name it saved it as was playasx.jsp. I then simply dragged and dropped the file into gxine and voila!!!

---

### Post by IronSheick67 on 2007-11-02
I got Sirius working.  Now, I am a noob, and after some some trial and error, this is what worked for me(i think):
-install mediaplayerconnectivity firefox addon
-run initial configuration to run all media files in VLC. also automatically turn on VLC when any stream is present.  
-started sirius media player.  Vlc automatically started playing when channel (100) was selected.  

These are probably horrible directions, and truthfully this took me 4 hours to figure out.  I don't know what i did (because i tried everything that a google search came up with). Hopefully this helps someone.

---

### Post by Betelgeuse1 on 2007-11-03
> **IronSheick67 said:**
> I got Sirius working.  Now, I am a noob, and after some some trial and error, this is what worked for me(i think):
-install mediaplayerconnectivity firefox addon
-run initial configuration to run all media files in VLC. also automatically turn on VLC when any stream is present.  
-started sirius media player.  Vlc automatically started playing when channel (100) was selected.  

These are probably horrible directions, and truthfully this took me 4 hours to figure out.  I don't know what i did (because i tried everything that a google search came up with). Hopefully this helps someone.

Wow nice!! I just downloaded the mediaplayconnectivity add on and configured it to use gxine and now it's so much easier to launch sirius.  Thanks a lot!!!  If I only knew that add- on existed I wouldn't have wasted countless hours on the research and trail-and-error. :(    If you want to try gxine instead of vlc download it using synaptic.  The executable will be in /usr/bin.

---

### Post by Squid_blk on 2007-11-05
I reinstalled and edited the .py file but still having errors. I used to be able to just type sipie and the gui would come up. I tried sipie and sipie.py and got the following:

brandon@el-diablo:~$ sipie
/usr/bin/sipie: line 1: syntax error near unexpected token `newline'
/usr/bin/sipie: line 1: `<meta HTTP-EQUIV="REFRESH" content="10; url=http://sipie.sourceforge.net/">'


brandon@el-diablo:~$ sipie.py
Traceback (most recent call last):
  File "/usr/bin/sipie.py", line 5, in <module>
    pkg_resources.run_script('Sipie==0.1190648273', 'sipie.py')
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 448, in run_script
    self.require(requires)[0].run_script(script_name, ns)
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 626, in require
    needed = self.resolve(parse_requirements(requirements))
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 528, in resolve
    raise VersionConflict(dist,req) # XXX put more info here
pkg_resources.VersionConflict: (Sipie 0.1184989269 (/usr/lib/python2.5/site-packages/Sipie-0.1184989269-py2.5.egg), Requirement.parse('Sipie==0.1190648273'))

Any suggestions?

---

### Post by Squid_blk on 2007-11-05
I restored the original sipie.py file so I am back to where I need to do the update of the egg file. But this is where I was stuck the last time and the gui version was not working either.  And to make things worse Sirius did some kind of update to their system over this past weekend. My Firefox Sirius Radio Player Add-on today would not play sound. It worked on my work laptop but it booted me off when I went into my user account and then I had too many login attempts which were supposed to be reset but did not go.  Customer Care was useless and said I needed to download stuff and it may have stopped working due to a firewall issue and popup blocker issue of which neither were an issue last week when I last used it.

---

### Post by Squid_blk on 2007-11-06
Al_sharpe posted in the beginning of this thread to install gxine and gxineplugin with Synaptic from ubuntu repository to get the online Sirius player working. Well it works. It went right into my premium service and sounds pretty well so far.  

Sirius was no help in figuring out why the Sirius Player 1.1 add-on for Firefox is not working but acknowledged that is now has problems since they did their update over the weekend. Hopefully  they will figure it out because it is a neat option.

I am still a few steps away from getting Sipie but looks like you can do this gxine/plugin option, Sipie with Beautiful Soup/Python support and Sirius Player add-on for Firefox (once working again) for online Sirius listening.  That is three options which is pretty cool.  It is my understanding that the lack of Shockwave support in Linux is why we need these options to use this service. Maybe that will be fixed soon.

Still any thoughts on what I am doing wrong with Sipie?

---

### Post by clancymf on 2007-11-06
Squid,

I m not at home right not but I believe that I had the same errors.  Off the top of my head, I think I remebered that you have to get rid off all reference to the Sipie-0.1184989269-py2.5.egg file within the sipie.py code.

Double check that and when I get home tonight I'll post my configutions.  The only remaining problem that I am having is stopping sipie. I usually have to kill it from the command line and sometimes it still plays in the background.

---

### Post by nleach on 2007-11-07
This is a total hack, but I am listening to Sirius on Ubuntu Gutsy Gibbon (7.10).  I thought it was worth posting...

I installed the gxine and gxineplugin packages (actually I already had them installed)...

sudo apt-get install gxine gxineplugin

I launched Firefox and signed into Sirius and went through the process to choose a channel (Stern 100 in my case).  Once that page comes up (and doesn't play), do a page-->view-->source.  Look for a section of code like this...

			<OBJECT ID="SIRIUSPlayer" width="1" height="0"
			standby="Loading Microsoft Windows Media Player components..." 
			type="application/x-oleobject">
			<PARAM NAME="AutoStart" VALUE="true">
			<PARAM NAME="FileName" VALUE="http://www.sirius.com/sirius/mediaplayer/asx/mac/playasx.jsp?streamKey=howardstern100&buttonStatus=low&hashkey=daEdEbABsGWGIkcgh">
			<PARAM NAME="ShowControls" VALUE="False">
			<PARAM NAME="ShowTracker" VALUE="False">
			<PARAM NAME="ShowStatusBar" VALUE="False">

			<PARAM NAME="ShowDisplay" VALUE="False">
			<PARAM NAME="ShowCaptioning" VALUE="False">
			<PARAM NAME="ShowPositionControls" VALUE="False">
			<EMBED type="application/x-mplayer2" 
				pluginspage="http://www.microsoft.com/Windows/MediaPlayer/" 
				SRC="http://www.sirius.com/sirius/mediaplayer/asx/mac/playasx.jsp?streamKey=howardstern100&buttonStatus=low&hashkey=daEdEbAcsGWGIkcgh" 
				name="SIRIUSPlayer" 
				width=1 
				height=0 
				autostart=1
				ShowStatusBar=0
				ShowCaptioning=0 
				showdisplay=0 
				ShowTracker=0 
				showcontrols=0
				showpositioncontrols=0>
			</EMBED>
			</OBJECT>


Copy the SRC or VALUE URL and paste it into the MRL within GXine.  It will play...but keep the Firefox session open.  I hope someone comes up with an easier way, but at least I can listen now!

---

### Post by Squid_blk on 2007-11-07
I am using the gxine and plugin right now. Works fine. But maybe I should note that I have had the MediaConnectivity Plugin for Firefox installed for a while now with VLC player to handle my Windows Media Player needs. I have left Real Media and Quicktime media settings with Totem. This does excellent with videos and streams from terrestrial radio web streams.  It either uses the websites player or opens the selected Linux player. Just close the unneeded window/program.

When I log into the Sirius online launcher I sign in and it opens the channel page.  I get an error box that always says:

"Playlist Error
The playlist 'http://a177.l2280061671.c22800.g.lm.akamaistream.net/D/177/22800/v0001/reflector:61671?aifp=abcd&partner=sirius_online_player&stream=siriusbuzzsaw&auth=daEcccsc3drc.bfcAd8aTa4bMcObHddasb5-bhmEV8-cw-DtISwsxdbak&token=a654f25f5951d4977e79e71f62424df&login_type=subscriber&login=name&campaign=null&bitrate=high&wmcache=0&mswmext=.asx' could not be parsed, it might be damaged."

But I just close it as Totem opens at the same time. Totem then plays the stream which sounds pretty good. At the 90 minute mark you get a chime that alerts you to select on the Sirius channel selector window to keep on going.  So far no problems. It did not beep when I last used it with XP.

Sipie does not have the timeout which is one reason why I really like it and it keeps you logged in longer.

---

### Post by rubadub on 2007-11-09
> **nleach said:**
> This is a total hack, but I am listening to Sirius on Ubuntu Gutsy Gibbon (7.10).  I thought it was worth posting...

I installed the gxine and gxineplugin packages (actually I already had them installed)...

sudo apt-get install gxine gxineplugin

I launched Firefox and signed into Sirius and went through the process to choose a channel (Stern 100 in my case).  Once that page comes up (and doesn't play), do a page-->view-->source.  Look for a section of code like this...

			<OBJECT ID="SIRIUSPlayer" width="1" height="0"
			standby="Loading Microsoft Windows Media Player components..." 
			type="application/x-oleobject">
			<PARAM NAME="AutoStart" VALUE="true">
			<PARAM NAME="FileName" VALUE="http://www.sirius.com/sirius/mediaplayer/asx/mac/playasx.jsp?streamKey=howardstern100&buttonStatus=low&hashkey=daEdEbABsGWGIkcgh">
			<PARAM NAME="ShowControls" VALUE="False">
			<PARAM NAME="ShowTracker" VALUE="False">
			<PARAM NAME="ShowStatusBar" VALUE="False">

			<PARAM NAME="ShowDisplay" VALUE="False">
			<PARAM NAME="ShowCaptioning" VALUE="False">
			<PARAM NAME="ShowPositionControls" VALUE="False">
			<EMBED type="application/x-mplayer2" 
				pluginspage="http://www.microsoft.com/Windows/MediaPlayer/" 
				SRC="http://www.sirius.com/sirius/mediaplayer/asx/mac/playasx.jsp?streamKey=howardstern100&buttonStatus=low&hashkey=daEdEbAcsGWGIkcgh" 
				name="SIRIUSPlayer" 
				width=1 
				height=0 
				autostart=1
				ShowStatusBar=0
				ShowCaptioning=0 
				showdisplay=0 
				ShowTracker=0 
				showcontrols=0
				showpositioncontrols=0>
			</EMBED>
			</OBJECT>


Copy the SRC or VALUE URL and paste it into the MRL within GXine.  It will play...but keep the Firefox session open.  I hope someone comes up with an easier way, but at least I can listen now!

I made a simple script to go along with this hack to make changing channels relatively easy. First thing you have to do is to have firefox open the page source in a text editor, instead of their own web page. Do this by typing about:config into the the address bar in firefox. At the top where it says filter, type in source.  Double click on view_source.editor.external so it says true. Then double click on view_source.editor.path and type in /usr/bin/gedit

So now that the page source opens in a text editor it will be saved in the /tmp folder under MediaPlayer.html  everytime you view it. Make sure you have vlc installed. Do this by sudo apt-get install vlc or you can find it in synaptic. Now create a new file in you home folder named sirius and copy this into it

VLC=$(vlc $(grep 'VALUE="http' /tmp/MediaPlayer.html | cut -d'"' -f4))
$VLC

Next make this file executable by sudo chmod +x sirius, make sure you are in your home folder when you type this. Now everything is ready to go. So you go to sirius.com and and open up their player. Login and click on the channel you want to listen to.  You will see the missing plugin notice up in the top of the window. Now right click and go to view page source. Then you can close this right after it comes up. Now to play it type ./sirius into the command line (again make sure your in your home folder) or create a launcher on the desktop by right clicking  on desktop and then create launder. Name it sirius and the command would be ./sirius. Now this will bring up vlc and it will play the channel, there is alittle pause when it starts so be patient. To change the channel you just close vlc the click on the new channel in the media player and after the missing plugin notice comes up right click-view page source, close it right away and run the ./sipie command.

So until the sirius player starts working again or sipie gets fixed.  I think this is the best alternative.

---

### Post by Kreuger on 2007-11-12
When I run it, I get 
> kreuger@kreuger-desktop:/usr/bin$ ./wxSipie
/home/kreuger/.themes/Human/gtk-2.0/gtkrc:70: error: unexpected identifier `True', expected keyword
Traceback (most recent call last):
  File "./wxSipie", line 8, in <module>
    load_entry_point('Sipie==0.1190648273', 'gui_scripts', 'wxSipie')()
  File "/usr/lib/python2.5/site-packages/Sipie-0.1190648273-py2.5.egg/Sipie/wxPlayer.py", line 254, in wxPlayer
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7757, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7354, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "/usr/lib/python2.5/site-packages/Sipie-0.1190648273-py2.5.egg/Sipie/wxPlayer.py", line 118, in OnInit
  File "/usr/lib/python2.5/site-packages/Sipie-0.1190648273-py2.5.egg/Sipie/wxPlayer.py", line 35, in __init__
  File "/usr/lib/python2.5/site-packages/Sipie-0.1190648273-py2.5.egg/Sipie/Factory.py", line 369, in getStreams
  File "/usr/lib/python2.5/site-packages/Sipie-0.1190648273-py2.5.egg/Sipie/Factory.py", line 217, in auth
  File "/usr/lib/python2.5/site-packages/Sipie-0.1190648273-py2.5.egg/Sipie/Factory.py", line 168, in __grabURL
IOError: [Errno 13] Permission denied: u'img_067.jpg'
so when I run it as root, the captcha comes up and when I put it in, it closes and nothing else. The terminal output shows this:

> Unsuccessful Login. Please check username and password.
Traceback (most recent call last):
  File "./wxSipie", line 8, in <module>
    load_entry_point('Sipie==0.1190648273', 'gui_scripts', 'wxSipie')()
  File "/usr/lib/python2.5/site-packages/Sipie-0.1190648273-py2.5.egg/Sipie/wxPlayer.py", line 254, in wxPlayer
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7757, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7354, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "/usr/lib/python2.5/site-packages/Sipie-0.1190648273-py2.5.egg/Sipie/wxPlayer.py", line 118, in OnInit
  File "/usr/lib/python2.5/site-packages/Sipie-0.1190648273-py2.5.egg/Sipie/wxPlayer.py", line 35, in __init__
  File "/usr/lib/python2.5/site-packages/Sipie-0.1190648273-py2.5.egg/Sipie/Factory.py", line 369, in getStreams
  File "/usr/lib/python2.5/site-packages/Sipie-0.1190648273-py2.5.egg/Sipie/Factory.py", line 258, in auth
Sipie.Factory.LoginError
But my password is right

---

### Post by budman21901 on 2007-11-16
I could not get sipie to work.  I got errors.  I found a very easy way to get sirius to play in mplayer.  

Sign into sirius with your username and password.  
right click on the player, and choose page info.
Then media tab.  
Find the the one link that says embed and right click and choose copy.  
Open up Mplayer, and choose play URL.  
Copy and paste, and it will play.  
You can now close all web pages.  Sirius will continue to play in mplayer.

---

### Post by Scott-271 on 2007-11-16
I've installed sipie according to the most recent instructions, and I can get it to launch but that's it. I get a little 1"x1" box on my desktop, and I can get the playlist; but the playlist seems to be about 1" wide and go from the top to the bottom of the screen with only half of it showing channel choices. On top of that, I have no sound. 

When I start it up, either cli or panel launcher, it maxes out my cpu then drops and does nothing.

What do I need to do to get this working?

Thanks,
Scott

---

### Post by Dr. Feltersnatch on 2007-11-17
Had this working in Gutsy earlier and then I reinstalled the OS.

Now when I follow the instructions I receive this message after the initial setup of sipie.py

There is a captcha file, Please open the file img_010.jpg
And input the leters below
: rt3k
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/Sipie-0.1190648273-py2.5.egg/Sipie/gtkPlayer.py", line 67, in on_Play_clicked
NameError: global name 'stream' is not defined

---

### Post by Drain on 2007-11-18
I was hoping to get Sipie working as well - I got my Sirius connection going through Firefox easily, but since I mainly use Opera and KDE, I thought I'd try and get this working.  :-)

I did the "sudo apt-get install" of the dependencies (mplayer, python-setuptools, beautifulsoup, and python-wxgtk2.6) , and then did "sudo easy_install sipie"  It downloaded and installed "Sipie-0.1190648273.tar.gz" easy enough. It even let me enter my username/password.  But here is where it came up short:

```
$ cliSipie

Traceback (most recent call last):
  File "/usr/bin/cliSipie", line 8, in <module>
    load_entry_point('Sipie==0.1190648273', 'console_scripts', 'cliSipie')()
  File "build/bdist.linux-i686/egg/Sipie/cliPlayer.py", line 69, in cliPlayer
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 99, in __init__
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 115, in __setupOpener
  File "/usr/lib/python2.5/urllib2.py", line 467, in build_opener
    opener.add_handler(h)
  File "/usr/lib/python2.5/urllib2.py", line 303, in add_handler
    type(handler))
TypeError: expected BaseHandler instance, got <type 'NoneType'>


$ wxSipie
Traceback (most recent call last):
  File "/usr/bin/wxSipie", line 8, in <module>
    load_entry_point('Sipie==0.1190648273', 'gui_scripts', 'wxSipie')()
  File "build/bdist.linux-i686/egg/Sipie/wxPlayer.py", line 236, in wxPlayer
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 99, in __init__
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 115, in __setupOpener
  File "/usr/lib/python2.5/urllib2.py", line 467, in build_opener
    opener.add_handler(h)
  File "/usr/lib/python2.5/urllib2.py", line 303, in add_handler
    type(handler))
TypeError: expected BaseHandler instance, got <type 'NoneType'>

```

Anyone have any suggestions?

---

### Post by clancymf on 2007-11-20
> **clancymf said:**
> Squid,

I m not at home right not but I believe that I had the same errors.  Off the top of my head, I think I remebered that you have to get rid off all reference to the Sipie-0.1184989269-py2.5.egg file within the sipie.py code.

Double check that and when I get home tonight I'll post my configutions.  The only remaining problem that I am having is stopping sipie. I usually have to kill it from the command line and sometimes it still plays in the background.

Sorry again for the delay:

Although something must have been updated since I have last played sipie cause now it doesnt work for me either.  I get the gui to pop up and it tells me what song is playing but no sound is coming out.

Here is my output of my sipie.py
```

#!/usr/bin/python
# EASY-INSTALL-SCRIPT: 'Sipie==0.1190648273','sipie.py'
__requires__ = 'Sipie==0.1190648273'
import pkg_resources
pkg_resources.run_script('Sipie==0.1190648273', 'sipie.py')

```

---

### Post by clancymf on 2007-11-20
Also discussed here:

[http://ubuntuforums.org/showthread.php?t=610232&highlight=sipie](http://ubuntuforums.org/showthread.php?t=610232&highlight=sipie)

---

### Post by tachibamaboi on 2007-12-03
well i got my [stilleto 2](http://www.sirius.com/freeradio) then that i purchased last thanksgiving well so far i have no problem with that ... humm they have this [Sportster 4](http://www.sirius.com/freeradio) its nice for the car then... 
well maybe this link well help you [http://www.sirius.com/freeradio](http://www.sirius.com/freeradio) 
hope it will help you..

many thanks!
[IMG]http://i7.tinypic.com/8avgao5.jpg[/IMG]
TaChiBamaBoi

---

### Post by kd7swh on 2007-12-05
Sipie is running, I am just not getting song notifications.

---

### Post by clancymf on 2007-12-05
> **kd7swh said:**
> Sipie is running, I am just not getting song notifications.

So is sipie working for you?  Did you have to do any changes?

---

### Post by clancymf on 2007-12-05
Looks like a solution has been found:

[http://sourceforge.net/forum/forum.php?thread_id=1869165&forum_id=697500](http://sourceforge.net/forum/forum.php?thread_id=1869165&forum_id=697500)

I will try it when I get home.

---

### Post by TheKid965 on 2007-12-05
Just wanted to say that installing the SVN version (referenced in the post immediately above mine) seems to have done the trick!  I was getting the "NoneType" error before, but this took care of it and now I've got Sirius on my Ubuntu desktop.

Many thanks!

---

### Post by kd7swh on 2007-12-06
yeah, svn at source forge works just no notifications

---

### Post by prosonik on 2007-12-10
i've had no luck with the latests SVN As of yesterday)
It might be me, being a Canadian listener, I've tried it under two different gutsy
and a mint guest as well..

if anybody can tell me how to turn on some debugging, I will. I had a quick peek at the code 
yesterday. As a side note, the Sirius-firefox plugging works well.

pro

---

### Post by TheKid965 on 2007-12-12
[deleted]

---

### Post by Squid_blk on 2007-12-19
Can someone post the modified egg file? I tried to edit and still no luck. I am too much of a Linux newbie I guess.  My Firefox plugin still does not work and when I tried the fix that the sipie source website has I got the code downloaded and then all of a sudden the east_install says it cannot work. I have changed nothing on my system and I am pretty much using a stock OS with very few other programs on it.  Gusty is weird in some ways. It wants to shut off my screen on login when Feisty never did and the default logoff sound stopped working when it did the upgrade.  Not sure what is happening.  Thanks.

---

### Post by bdawk36 on 2007-12-24
> **llamakc said:**
> 43,

Start in a clean directory and do the svn checkout line:
```

 svn co [https://sipie.svn.sourceforge.net/svnroot/sipie](https://sipie.svn.sourceforge.net/svnroot/sipie) sipie

```

Next do this:

```

sudo easy_install sipie

```

And then download the attachment in rolyat420's post. Rename the file extension from .zip to .egg and next mv the .egg to 

 /usr/lib/python2.5/site-packages/ with sudo.

That should do it for you.
Awesome, thanks to all of you who replied to this thread.  This finally got my Sirius connection working.

---

### Post by reiley321 on 2007-12-29
Thanks So much !



Deleting and doing a fresh install did it for me.

---

### Post by chica4me on 2008-01-16
I have followed the instructions and sipie launches, displays station, and the current song playing but I get no sound.  Any thoughts.
Thanks.

---

### Post by daybreaker on 2008-01-18
Thanks! It worked! I hadnt had sirius for WEEKS!

---

### Post by z-vap on 2008-01-21
I also have no sound. It displays the popup GUI, but no sound comes out.  I tried running it with Root privileges to see if there were any error messages displaying and I saw this:

```
 08 01|21 11:41 siriushits1: Morning Mash Up!-data by DogstarRadio.com

** (sipie.py:8052): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (sipie.py:8052): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (sipie.py:8052): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (sipie.py:8052): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (sipie.py:8052): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

```
It looks like it redisplays this during every song change...

Any ideas?

---

### Post by morone on 2008-02-13
> **rolyat420 said:**
> Squid_Blk

The easiest thing to do is completely start fresh.

Remove the files that show up after running
```
locate sipie
```

Then do a new svn checkout
```
svn co https://sipie.svn.sourceforge.net/svnroot/sipie sipie
```

Then install
```
sudo easy_install sipie
```

Download this attachment (its the patched code to allow it to work in gutsy)
```
[http://ubuntuforums.org/attachment.php?attachmentid=46552&d=1192583943]("http://ubuntuforums.org/attachment.php?attachmentid=46552&d=1192583943")
```

Rename the extension from .zip to .egg

Then copy it to /usr/lib/python2.5/site-packages/ with sudo
```
sudo cp Sipie-0.1184989269-py2.5.egg /usr/lib/python2.5/site-packages/
```

Run sipie.py from command line, fill in your stuff and it should be kicking. Good luck

Spent quite a bit of time to get my trial membership working - but this post certainly helped me out quite a bit - the package name has changed to a new number since October, but that is to be expected, but something to note for people following along with these steps as time goes on.  

Wanted to make sure that I could get this working before signing up.  Still not seeing the playlists, but will work on that tomorrow.  Great to be able to use the forums here to solve issues - it is nice to have a resource like this to figure out solutions to configuration problems.

---

### Post by myname on 2008-02-19
Thanx, followed your steps, and sipie launches, I select the station and then nothing, no song list, no music.  Any ideas?

Also, is it possible to run sipie straight from the command line?  I used it a year ago, ran it from the terminal window and LOVED that it was straight command line and that I could see the song listing.

--kevin

---

### Post by Squid_blk on 2008-03-08
I finally got this to work but I had to modify the instructions somewhat.

The downloaded zip file is named Sipie-0.1190648273-py2.5.zip. You have to make sure the last command has the correct file name--Sipie-0.1190648273-py2.5.egg after you rename it.  Also make sure that right before you execute the last command that you change directories into the folder where you send your downloads.  Mine goes to my Downloads folder in my Home Folder.  I had changed the file name using Nautilus but could not figure out why the command was still not working. When I entered cd downloads and then ran the command everything worked but I had to modify the command line in this thread from: 
 
sudo cp Sipie-0.1184989269-py2.5.egg /usr/lib/python2.5/site-packages/

To:

sudo cp Sipie-0.1190648273-py2.5.egg /usr/lib/python2.5/site-packages/

Now I will not have to deal with the website's are you still listening every 90 minutes. 

This makes three ways to listen to Sirius.  

The Firefox Sirius plugin may work for some but it failed for me after Sirius did some kind of upgrade to their system and it never worked for me again.

Gxine and gxine plugin with VLC Player via  the Multimedia Connectivity Plugin still works but you have to deal with the alert and have to close uneeded players that pop up during the alert.

So thanks everybody. I just hope this works with Hardy Heron.  I guess we will have to wait and see.  If it does then I plan to donate as Heron will be a LTS.  Cool beans.

---

### Post by QualityPancakes on 2008-03-11
Hi everyone. I have Sipie installed and apparently working, but when it asks for the captcha file I just get this:
```
There is a captcha file, Please open the file img_062.jpg
```

Nothing opens and I have no idea what to do. I am a total beginner so I will likely need very clear instructions.

Thanks

---

### Post by z-vap on 2008-03-15
Well I got mine working today.   I did the easy_install and tried running the .py file and wham.  I have sirius streaming as we speak!!!!

I don't know what specifically I did that worked.  But I'd like to thank many of the people on this thread that posted their assistance and help.  Here are some specific posts that I think did a lot for me:


**wilderness wanderer:** for getting the original install instructions w/ dependencies started
[http://ubuntuforums.org/showpost.php?p=1789365&postcount=4](http://ubuntuforums.org/showpost.php?p=1789365&postcount=4)

**rolyat420:** for assisting with the egg issue. :)
[http://ubuntuforums.org/showpost.php?p=3546960&postcount=99](http://ubuntuforums.org/showpost.php?p=3546960&postcount=99)

**llamakc:** for highlighting to me the easy_install method.
[http://ubuntuforums.org/showpost.php?p=3547883&postcount=102](http://ubuntuforums.org/showpost.php?p=3547883&postcount=102)

**Squid_blk:** for that last bit of information. 
[http://ubuntuforums.org/showpost.php?p=4477165&postcount=161](http://ubuntuforums.org/showpost.php?p=4477165&postcount=161)

and a special thanks goes out to **elicriffield** for starting [Sipie]("http://sipie.sourceforge.net/") to begin with.


Now I'm off to get that icon :)
:guitar:

---

### Post by bueller on 2008-03-17
Talk about frustrating...

Either I'm too ignorant or just damned unlucky, but I can't make any of this work and just don't know enough to explain why.

I've tried Sipie, I've tried the add on for Firefox, I've installed Mplayer (prior to installing Sipie), I've installed the media player connectivity add on. Everything either doesn't work or locks up the system. I have at least 6 hours into this already and I'm just about ready to tell Sirius to shove it for their inability/unwillingness to provide a format that works easily in a linux environment.

Or maybe a linux based operating system is too complex for me. But I've managed to make almost everything work just great in Gutsy.

This has been a real disappointment. Any suggestions? Can someone walk me through this from start to finish?

---

### Post by Wobedraggled on 2008-03-17
This is what I get when trying to run it.

>  sipie
(c)Eli Criffield <pyeliATzendoDOTnet> [http://eli.criffield.net/sipie/](http://eli.criffield.net/sipie/)
Licensed under GPLv2 [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Traceback (most recent call last):
  File "/usr/bin/sipie", line 5, in <module>
    pkg_resources.run_script('Sipie==0.1181072404', 'sipie')
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 448, in run_script
    self.require(requires)[0].run_script(script_name, ns)
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 1173, in run_script
    exec script_code in namespace, namespace
  File "/usr/bin/sipie", line 22, in <module>
    
  File "build/bdist.linux-i686/egg/Sipie/cliPlayer.py", line 66, in cliPlayer
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 102, in __init__
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 118, in __setupOpener
  File "/usr/lib/python2.5/urllib2.py", line 467, in build_opener
    opener.add_handler(h)
  File "/usr/lib/python2.5/urllib2.py", line 303, in add_handler
    type(handler))
TypeError: expected BaseHandler instance, got <type 'NoneType'>


---

### Post by BKonkle on 2008-03-27
I just tried this on a fresh Hardy Beta install, and it worked "out of the box" without the patch file referenced in earlier posts.  When you install python-wxgtk2.6 ahead of time, you get nice popup notifications that tell you the artist and song title.  Here are the steps I took from my home directory in the terminal:

```
sudo apt-get install mplayer python-setuptools python-wxgtk2.6
```

```
locate sipie
```

```
svn co https://sipie.svn.sourceforge.net/svnroot/sipie sipie
```

```
sudo mv sipie /opt/
```

```
cd /opt/sipie
```

```
sudo easy_install sipie
```

```
sipie.py
```

I entered my username and password as instructed, went through the rest of the steps, and then it presented me with the "there is a captcha" message.  I opened the directory that I installed Sipie to - /opt/sipie - and opened the jpeg file that had been saved there.  I entered the letters from the jpeg into the terminal, and bingo!  Instant HardAttack!

---

### Post by lime4x4 on 2008-03-27
It doesn't seem to work on hardy 64 bit

Enter login type: subscriber
Are you using Sirius Cananda ([http://siriuscanada.ca](http://siriuscanada.ca))
 True or False: false
Traceback (most recent call last):
  File "build/bdist.linux-x86_64/egg/Sipie/gtkPlayer.py", line 67, in on_Play_clicked
NameError: global name 'stream' is not defined
Traceback (most recent call last):
  File "build/bdist.linux-x86_64/egg/Sipie/gtkPlayer.py", line 67, in on_Play_clicked
NameError: global name 'stream' is not defined

---

### Post by BKonkle on 2008-03-27
Try removing your ~/.sipie folder.  Then re-run sipie.py and go through the configuration again.  Pay careful attention to capitalization - I noticed you used false instead of False - maybe the configuration script doesn't have a method coded to correct the capitalization?  Just a guess.

---

### Post by BKonkle on 2008-03-27
I forgot to mention that I'm running x86_64 also.

---

### Post by lime4x4 on 2008-03-27
i closed the terminal then opened a new terminal and it works go figure

---

### Post by chperry on 2008-03-27
I am running Ubuntu (Gutsy).  I have sipie installed and working!  Now the problem.  It plays for 5 to 10 minutes (2 to 3 songs) and then simply shuts down.  I restart sipie and it works fine for 5 to 10 minutes.  Any ideas?

Running x86_64

I am completely new to Linux, btw.

Thanks

Charles

---

### Post by z-vap on 2008-03-29
I just moved my setup to a different disk, and knew i'd have to reinstall Sipie from scratch. I worked okay.  :)

---

### Post by Kreuger on 2008-03-30
I can use it from the commandline but the GUI versions keep showing this

> kreuger@kreuger-desktop:~$ /usr/bin/gtkSipie
Traceback (most recent call last):
  File "/usr/bin/gtkSipie", line 8, in <module>
    load_entry_point('Sipie==0.1190648273', 'gui_scripts', 'gtkSipie')()
  File "build/bdist.linux-i686/egg/Sipie/gtkPlayer.py", line 8, in gtkPlayer
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
ImportError: /usr/lib/libcairo.so.2: symbol png_set_expand_gray_1_2_4_to_8, version PNG12_0 not defined in file libpng12.so.0 with link time reference
kreuger@kreuger-desktop:~$ 

---

### Post by gmrishel on 2008-05-11
BKonkle, thank you so very much for the clear and detailed help.  Many posters assume that you even know enough to cd into the proper dirrectory. Those little things left out caused me some long nights when I was starting to change to open source.

Worked great for me...

---

### Post by BKonkle on 2008-05-12
> **gmrishel said:**
> BKonkle, thank you so very much for the clear and detailed help.  Many posters assume that you even know enough to cd into the proper dirrectory. Those little things left out caused me some long nights when I was starting to change to open source.

Worked great for me...

I'm glad to hear I was able to help.  Enjoy!

---

### Post by Bakon Jarser on 2008-05-13
When I run 
sudo easy_install sipie

I get the following error:

```

Searching for sipie
Reading http://pypi.python.org/simple/sipie/
Couldn't find index page for 'sipie' (maybe misspelled?)
Scanning index of all packages (this may take a while)
Reading http://pypi.python.org/simple/
Reading http://pypi.python.org/simple/Sipie/
Reading http://eli.criffield.net/sipie/
Reading http://sipie.sourceforge.net/
Best match: Sipie 0.1196144357
Downloading http://downloads.sourceforge.net/sipie/Sipie-0.1196144357.tar.gz?use_mirror=internap
error: Download error for http://downloads.sourceforge.net/sipie/Sipie-0.1196144357.tar.gz?use_mirror=internap: (110, 'Connection timed out')

```

Any ideas what went wrong?

Edit:  I copied the link it was trying to download from and removed the part about the mirror to get the tarball.  I extracted the files to /usr/bin and it works perfectly.

---

### Post by prosonik on 2008-06-15
Hey everybody,

I have been struggling with Sipie for every, with no audio
playing at all when launching any of the clients. I have tried the tips and tricks posted here with no luck..

That all changed, when I tried an American guest account.. It worked perfectly. Now, i'm wondering if there is not a problem with the Canadian code. Is there a way to turn on logging or something so i can get a better grasp of what's going on?

---

### Post by netjess on 2008-06-19
After mudling my way throug the installs. I am at work and the proxy dosn't allow file downloads through http, only ftp. I can listen to other streaming radios like Jango.
I also have to type out sipie.py to get it to run, not just sipie like it says here, but then I get the following:
 /usr/bin/Sipie/sipie.py
Traceback (most recent call last):
  File "/usr/bin/Sipie/sipie.py", line 22, in <module>
    Sipie.cliPlayer()
  File "/usr/bin/Sipie/Sipie/cliPlayer.py", line 74, in cliPlayer
    completer = Completer(sipie.getStreams())
  File "/usr/bin/Sipie/Sipie/Factory.py", line 374, in getStreams
    streams = self.tryGetStreams()
  File "/usr/bin/Sipie/Sipie/Factory.py", line 279, in tryGetStreams
    hd = self.__getURL(url)
  File "/usr/bin/Sipie/Sipie/Factory.py", line 157, in __getURL
    handle = urllib2.urlopen(req)
  File "/usr/lib/python2.5/urllib2.py", line 124, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.5/urllib2.py", line 381, in open
    response = self._open(req, data)
  File "/usr/lib/python2.5/urllib2.py", line 399, in _open
    '_open', req)
  File "/usr/lib/python2.5/urllib2.py", line 360, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.5/urllib2.py", line 1107, in http_open
    return self.do_open(httplib.HTTPConnection, req)
  File "/usr/lib/python2.5/urllib2.py", line 1082, in do_open
    raise URLError(err)
urllib2.URLError: <urlopen error (111, 'Connection refused')>

 Any ideas?

---

### Post by pimpaulogy on 2008-06-20
Running Ubuntu 8.04 - the Hardy Heron

Installed Sipie yesterday.  Had a couple of install hick-ups, but I think I figured it all out.

The only problem that I am having is:

Launch the gui (sipie.py)
Click Play on already chosen channel, or pick new one.
Start listening.
Then, at some random amount of time, the gui crashes, but Sirius is still playing and I still get notifications about what's currently playing.

The only way to stop the channel from playing is to kill both mplayer processes that are playing.

Has anybody experienced this and if so, did you resolve it?

---

### Post by *Legion* on 2008-07-07
pimpaulogy: The sipie crash (and mplayer keeps playing) situation happens to me too. No resolution yet.

If you launch sipie.py from a console, the app will throw a "Segmentation Fault" when it dies.

I can also say that the segfault crash happens when sipie pops up the little notification window that shows the new track title. But, at least for me, it doesn't happen the FIRST time, but usually after a few title pop-ups.

---

### Post by Kreuger on 2008-07-07
Someone needs to make a damn GTK client or something. I'm tired of this sipie crap.

---

### Post by Dillio187 on 2008-07-08
agreed, an app like Stream_On would be awesome!  It's unfortunate Stream_On is written in .NET :(

---

### Post by Kreuger on 2008-07-09
Since it uses .NET, maybe it can run through mono.

---

### Post by Dillio187 on 2008-07-10
I didn't have any luck getting it to work, it also requires WMP.  It's a great app though, it's so nice seeing what is playing on all of your favorite channels at the same time!

---

### Post by Kreuger on 2008-07-12
I couldn't figure out where to even start haha. I just gave up, I don't listen to it much anyway.

---

### Post by fastazzmustang on 2008-07-13
Although this is my first post, I have been lurking these forums for a couple of years or so.  I have to say thanks to everyone on this board for posting excellent information.  I started using Ubuntu with version 5.04.  I just did a fresh install of 8.04 on my new system.

I have AMD 64 bit processor.  I did what BKonkle said to do on page 17 of this thread and everything works fine.  Thanks BKonkle.:guitar:

I do have one question which no matter how much I search, I cannot find an answer to.  After running the sipie python script for just a few minutes, the application goes to sleep and the song title popups quit displaying and I cant change channels.  How do I stop it from going to sleep?

---

### Post by BKonkle on 2008-07-14
> **fastazzmustang said:**
> After running the sipie python script for just a few minutes, the application goes to sleep and the song title popups quit displaying and I cant change channels.

Glad to hear my post helped!  I've never actually seen Sipie do this before.  Are you minimizing the window, or are you keeping it up on your desktop behind other windows while listening?  I always keep my sipie window up on the desktop and not minimized, and I don't seem to have any problems.

I'm actually learning more about Python because I'm doing a lot of work using Django, my favorite web framework.  It is built on Python so I'm starting to learn a lot more about how to program in Python.  I don't like the wxWidgets approach to UI design, so I'm thinking about taking the base Sipie player that Eli Criffield developed and coming up with a new GUI based on a different library.  If I can figure out how to use GTK in Python, that would probably be my choice.  If I decide to go ahead and pursue this project, I'll reach out to Eli and keep you posted on this thread.

---

### Post by fastazzmustang on 2008-07-15
I keep the window open on the desktop.  I even tried selecting "always on top".  That helped, but then I changed channels and the gui quickly went away.  I still have sound when this happens.  I just don't have the gui and can't change channels or stop it.  When I go to system monitor or "task manager" if you will, it shows python as sleeping and two instances of mplayer sleeping as well.  Nothing I do will get the gui back.  I can kill process and restart or log out and log back in.  Something else that may help you help me is that when I drag the wxsipie window around sometimes when it latches to the side (either left or right), the window will disappear too.  That happened to me yesterday when I put it on always on top and was locating it to a more comfortable location.  Operating on different desktops doesn't change anything either.

---

### Post by Dillio187 on 2008-07-16
the only thing I found that would help is to disable Compiz completely.  There is something with the Compiz animations that mess up Sipie.  I like the animations so I've just been using the online player with the mozilla-mplayer plugin.  It does suck to have to keep clicking the window to keep the stream going every hour or so though.

I hope Sipie keeps evolving, its a good start.  If it could be developed to work under Compiz and add the channel lineup streaming from [http://streamon.siriusdev.org/](http://streamon.siriusdev.org/) that would be the ultimate app!

---

### Post by M Baker on 2008-07-19
> **BKonkle said:**
> I just tried this on a fresh Hardy Beta install, and it worked "out of the box" without the patch file referenced in earlier posts.  When you install python-wxgtk2.6 ahead of time, you get nice popup notifications that tell you the artist and song title.  Here are the steps I took from my home directory in the terminal:

```
sudo apt-get install mplayer python-setuptools python-wxgtk2.6
```

```
locate sipie
```

```
svn co https://sipie.svn.sourceforge.net/svnroot/sipie sipie
```

```
sudo mv sipie /opt/
```

```
cd /opt/sipie
```

```
sudo easy_install sipie
```

```
sipie.py
```

I entered my username and password as instructed, went through the rest of the steps, and then it presented me with the "there is a captcha" message.  I opened the directory that I installed Sipie to - /opt/sipie - and opened the jpeg file that had been saved there.  I entered the letters from the jpeg into the terminal, and bingo!  Instant HardAttack!

This failed for me at the <locate sipie> command in the terminal. I was just returned to the command prompt. Any other help? I'd sure like to get Sirius working in my Ubuntu 8.04. I installed gxine as suggested in another forum to no avail.

---

### Post by fastazzmustang on 2008-07-23
M Baker, did you try re-running the install?  Something didn't go right cause it should have located sipie.

Back to the issue that I am having.  I had copied the sipie.py file to my desktop and I have been executing from that location.  When I run it, a window pops up asking how I want to run the file.  I have been choosing run.  I started choosing run in terminal instead.  I haven't been having any issues since I started doing this(over 1 week).  Until tonight.  And actually, I am not having as big of an issue as before.  This is the first time this has happened to me.  The player is still running and I can change channels.  Now the pop ups with song title and artist have stopped.  I got the error message from the terminal.

```
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.5/threading.py", line 486, in __bootstrap_inner
    self.run()
  File "build/bdist.linux-x86_64/egg/Sipie/Popup.py", line 26, in run
    self._action()
  File "build/bdist.linux-x86_64/egg/Sipie/Popup.py", line 71, in __popup
    playing = self.sipie.nowPlaying()
  File "build/bdist.linux-x86_64/egg/Sipie/Factory.py", line 463, in nowPlaying
    self.__stream,playing)
UnicodeDecodeError: 'utf8' codec can't decode bytes in position 18-22: unexpected end of data
```


Possibly, this may have something to do with my previous issue--which I still have if I don't run in terminal.

---

### Post by fastazzmustang on 2008-07-23
That error must be related to the issue I described in my original post.  I just got through typing the above post and then I decided to restart sipie.  I chose to run in terminal and the first song title popped up as normal and then in about 2 minutes, it just closed on its own.  No audio or anything.

I also thought I should add that I am keeping compiz enabled.  I have not tried to completely disable it and run sipie.  I really like compiz.  I am executing sipie on workspace 1 (desktop 1) and keeping it dedicated to sipie only.  Then I have been doing all other tasks on workspace 2 and 3.  I know the other tasks are not interfering because I have even left my computer on and only sipie running with screensaver disabled only to come back in a few minutes to find that it had closed.

---

