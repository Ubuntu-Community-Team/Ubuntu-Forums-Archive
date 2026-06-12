---
title: "Listening to radio via the internet; finding URLs of audio streams"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by kaiwi on 2007-12-22
Hi,

I'm trying to listen to live radio broadcasts via the internet, e.g. to the BBC World Service.

Whenever I click on the "Listen Live" button at the station's website 

[http://www.bbc.co.uk/worldservice](http://www.bbc.co.uk/worldservice) 

nothing happens.

On other websites supposed to deliver live audio streams, my Firefox web browser even crashes when I click on the "Play" or "Listen" button.

Somewhere in Ubuntu Forum it has been suggested to enter explicity the URL address of the audio stream one wishes to hear. In the case of the BBC World Service, I found the correct URL by looking at the source code of the popup window that opens after clicking on "Listen Live". The URL is

[http://www.bbc.co.uk/worldservice/meta/tx/nb/live_infent_au_nb.ram](http://www.bbc.co.uk/worldservice/meta/tx/nb/live_infent_au_nb.ram)

OK, so I open a terminal and enter the command

 mplayer -playlist [http://www.bbc.co.uk/worldservice/meta/tx/nb/live_infent_au_nb.ram](http://www.bbc.co.uk/worldservice/meta/tx/nb/live_infent_au_nb.ram)

After waiting for a couple of seconds, I can then hear the live broadcast of the  BBC World Service. Great!

**My problem is that in most cases (broadcasters other than BBC), I don't manage to find the explicit URL of the audio stream by looking at the source code because the source code is too complex. **
 
Any ideas of what to do? Can Ubuntu be configured such that one can listen to internet radio without searching for the explicit URL?

Many thanks in advance!


PS: The above-mentioned URL fully reads

[http://www.bbc.co.uk/worldservice/](http://www.bbc.co.uk/worldservice/)
meta/tx/nb/live_infent_au_nb.ram

---

### Post by fatality_uk on 2007-12-22
If you use Amarok, you can add radio streams under the playlisy menu and then save them to a media stream :D
hope this helps

---

### Post by kaiwi on 2007-12-22
Thanks fatality_uk,

I don't know Amarok, but I guess that I would still have to enter the web address of the audio stream. 

My problem is that I don't know the address of the audio stream which I want to receive. I only know the web page of the broadcaster where there is a link for live listening.

**Example:** I want to listen to TSF Jazz. In my browser I go to
 [http://www.tsfjazz.com/player2/](http://www.tsfjazz.com/player2/) 
I'm automatically redirected to
 [http://www.tsfjazz.com/player2/?p=wmp](http://www.tsfjazz.com/player2/?p=wmp)
and that's it. Nothing happens, although in Windows I would then receive an audio stream.

In the source code of  [http://www.tsfjazz.com/player2/](http://www.tsfjazz.com/player2/)  (to see the source code I press Ctrl+U) I don't find the address of the audio stream. 

So how on earth can I listen to TSF Jazz using Ubuntu (which otherwise is great!)

---

### Post by drs305 on 2007-12-22
Many of us listen to internet radio via Firefox and the MediaPlayerConnectivity plug in. When I click on the listen link at the site, it automatically figures out the address. Here is a link to installing MPC and getting it to work with mms streams:

[http://ubuntuforums.org/showthread.php?t=381769#12](http://ubuntuforums.org/showthread.php?t=381769#12)

In setting it up, I have all of the file types set up for VLC since I don't always know what format a radio station is going to be broadcasting in.

---

### Post by ExpatPaul on 2007-12-22
> **kaiwi said:**
> **Example:** I want to listen to TSF Jazz. In my browser I go to
 [http://www.tsfjazz.com/player2/](http://www.tsfjazz.com/player2/) 
I'm automatically redirected to
 [http://www.tsfjazz.com/player2/?p=wmp](http://www.tsfjazz.com/player2/?p=wmp)
and that's it. Nothing happens, although in Windows I would then receive an audio stream.

Oddly enough, when I clicked on your first link, it redirected me to the second (  [http://www.tsfjazz.com/player2/?p=wmp](http://www.tsfjazz.com/player2/?p=wmp) ) and then started playing in Firefox with no problem.

I'm guessing here but it may be worth checking the following:
Do you have the Ubuntu firefox extension installed?
Do you have all of  the available Gstreamer plugins installed?

---

### Post by kaiwi on 2007-12-22
Thanks everyone, I'll check the Firefox extensions you mentioned and will let you know (probably not this year though)

In the meantime:
Happy Xmas and a happy new year

---

### Post by kaiwi on 2007-12-23
Hi guys,

I got it working, even before Xmas! Thanks again for your help

Following your suggestion I installed the MediaPlayerConnectivity for Firefox. In the preferences I have set GMPlayer for all stream types.

First thought it didn't work, as when I click on "Listen", mplayer opens three windows which seem to be non responding. But in fact after waiting for a minute or two, the windows respond and MPlayer then works correctly.

All the best

---

