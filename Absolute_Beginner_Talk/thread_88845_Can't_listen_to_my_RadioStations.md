---
title: "Can't listen to my RadioStations"
date: 2005-11-11
forum: Absolute Beginner Talk
---

### Post by iluminate on 2005-11-11
Hi,
I can't listen to my favorite Radio Stations found here - [http://www.rixfm.com/stream/streamingplayer.php](http://www.rixfm.com/stream/streamingplayer.php)
And Totem is giving me an errormessage "There were no decoders found to handle the stream, you might need to install the corresponding plugins" :confused: 
What decoder  do I need to be able to listen?

---

### Post by BoyOfDestiny on 2005-11-11
[QUOTE=iluminate]Hi,
I can't listen to my favorite Radio Stations found here - [http://www.rixfm.com/stream/streamingplayer.php](http://www.rixfm.com/stream/streamingplayer.php)
And Totem is giving me an errormessage "There were no decoders found to handle the stream, you might need to install the corresponding plugins" :confused: 
What decoder  do I need to be able to listen?[/QUOTE]

I'm thinking you would need libmad.

Anyway, type sudo gedit /etc/apt/sources.list
uncomment the lines with universe

save then after that in terminal type

apt-get install beep-media-player

Think of it as a winamp for linux. :)

Hope that does it!

---

### Post by iluminate on 2005-11-11
Thanks for the tip "earthling",
The problem is, I think, is that Totem is the default media player.
Becuase each time I try to listen to the station it gives me the error about Totem...
Any ideas or hints?

---

### Post by apjone on 2005-11-11
Hi , 
     You can use an mplayer and its plugin or download realplayer. If you want to use totem thou open synaptic package manage and search for 'gstream' 

AJ

---

### Post by iluminate on 2005-11-13
> Hi ,
You can use an mplayer and its plugin or download realplayer. If you want to use totem thou open synaptic package manage and search for 'gstream'
AJ
The thing is that the default player is Totem and I can't find where to change it.
But still, I have almost every gstream package installed and can't get it to play in Totem at all.

> I'm thinking you would need libmad.
Done that and installed Beep Media Player and stil don't work.

Also I have tried Mplayer and installed the Mozilla plugin and I still can't get it to work.
This is kinda frustrating so any help would be appreciated.

---

### Post by BoyOfDestiny on 2005-11-13
[QUOTE=iluminate]The thing is that the default player is Totem and I can't find where to change it.
But still, I have almost every gstream package installed and can't get it to play in Totem at all.


Done that and installed Beep Media Player and stil don't work.

Also I have tried Mplayer and installed the Mozilla plugin and I still can't get it to work.
This is kinda frustrating so any help would be appreciated.[/QUOTE]

I usually save the pls file for my streaming radio. Right click on that and choose open with, pick beep media player. 

After doing that (just to be safe, it now knows that beep is an option if it didn't before), you can now click properties and choose "open with" and select beep media player (and it should now be the default).

If you are going from within the browser, and you can choose open with /usr/bin/beep-media-player

To test it, here is a pls file:
[http://relay.slayradio.org:8000/listen.pls](http://relay.slayradio.org:8000/listen.pls)

The home page is:
[http://www.slayradio.org](http://www.slayradio.org)

c64 remixes...99% of the songs are "freeware"

EDIT: I see the player you linked to is "intergrated". I'm on ubuntu 64-bit so I don't have flash (I think that page has flash, made firefox die here). If there is a way to get the link to the actual stream... in any other os's could you play this station without a browser?

---

### Post by salva on 2005-11-13
man, that channel is awesome.... they sure knew how to make catchy tunes back then :D

---

### Post by iluminate on 2005-11-13
Greetings,

> To test it, here is a pls file:
[http://relay.slayradio.org:8000/listen.pls](http://relay.slayradio.org:8000/listen.pls)

The home page is:
[http://www.slayradio.org](http://www.slayradio.org)

c64 remixes...99% of the songs are "freeware"

What a great station - "getting goosebumps" :D 
With a link to the playlist everything works just fine in Beep. (superbSound Quality btw)

> EDIT: I see the player you linked to is "intergrated". I'm on ubuntu 64-bit so I don't have flash (I think that page has flash, made firefox die here). If there is a way to get the link to the actual stream... in any other os's could you play this station without a browser?

You are correct that it's integrated and that seems to be the problem (and by default totem is trying to play it. So maybe I need to make another player handle the stream, but how to I dont know)

FireFox crashed for me to from time to time after the totem Error message.
There seems not to be a playlist URL but it's pointing to a .php file - [http://www.rixfm.com/stream/streamingplayer.php](http://www.rixfm.com/stream/streamingplayer.php)

So I really don't have a clue how to fix this...which is kinda annoying. I'm not a Linux guy but I'm trying to learn and I have realised that the path to learn can take a while and the road is a bit bumpy...

Cheers!

---

### Post by hoodwink on 2005-11-13
[QUOTE=iluminate]Hi,
I can't listen to my favorite Radio Stations found here - [http://www.rixfm.com/stream/streamingplayer.php](http://www.rixfm.com/stream/streamingplayer.php)
And Totem is giving me an errormessage "There were no decoders found to handle the stream, you might need to install the corresponding plugins" :confused: 
What decoder  do I need to be able to listen?[/QUOTE]
I don't use Totem or know anything about it. I installed mplayer and the codecs (search for HOWTO on these), and I'm listening to Svenska favoriter from the posted url as we speak.

HTH.

---

### Post by iluminate on 2005-11-13
> I don't use Totem or know anything about it. I installed mplayer and the codecs (search for HOWTO on these), and I'm listening to Svenska favoriter from the posted url as we speak.

Well good for you :)
If you have read my earlier posts Totem is trying to play it, even though I have every codec available ( so I think )
I have installed Mplayer and Mozilla-Plugin etc. but how do I make MPLAYER to play the stream instead of Totem?
Now what ever I do I get an error message saying "Totem could not play 'fd_//00'
There were no decoders found to handle the stream, you might need to install corresponding plugins"

Will look for HOWTO's (once again)

Solution:
Remove the files in /usr/lib/mozilla-firefox/plugins
rm libtotem_mozilla.so 
rm libtotem_mozilla.xpt

And now it's working. Don't know if this is the correct way, but at least it's working.

Peace

---

