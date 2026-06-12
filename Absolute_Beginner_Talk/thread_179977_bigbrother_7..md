---
title: "bigbrother 7."
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by erniewinner on 2006-05-21
hi all,

is there anyway to get mplayer (or other player) to watch the bigbrother stream? i can't be bothered to install xp. mplayer has media player support enabled but the stream never starts and it just says "stopped"... it's a bit dissapointing windows xp is the platofrm directly supported. i cound not find how to update mplayer. is this possible? :confused:

---

### Post by adam.tropics on 2006-05-21
> is there anyway to get mplayer (or other player) to watch the bigbrother stream?

Holy crap, I hope not!!

---

### Post by Nikusan on 2006-05-21
[QUOTE=adam.tropics]Holy crap, I hope not!![/QUOTE]

Haha! I tend to agree... ;-)

But seriously, you can find instructions to get streaming media working [here.]("https://wiki.ubuntu.com/RestrictedFormats#head-e25afe1552d3a818f60e64143931b2d8e0522267")

---

### Post by skippy81 on 2006-05-21
What format is that obnoxious stream broadcast in anyway? :p

---

### Post by erniewinner on 2006-05-21
"IMPORTANT!
Big Brother video is presented as high quality online video and you will need at least a 512kbps broadband connection to watch the video.

This service is only available for Windows 2000 and XP using Windows Media Player 10. Mac OS X is not supported."

i have all the win32 codecs to my knowledge. and the kaffiene front end... the bigbrother site opens it own window which remains black. a second window opens up and says "xine-error no input plugin."

it doesn't acually inform of format i would assume wmv but some speciallised software for xp drm style. i'm basically hoping someone has  got it working.

oh and by the way it's the uk site... 

[http://www.channel4.com/bigbrother/live/watch-now.html](http://www.channel4.com/bigbrother/live/watch-now.html)

---

### Post by erniewinner on 2006-05-21
mmm... heres a bit more. lots like it is xp only! ](*,) 

"Can I access the episodes from a Macintosh?

Episodes are not available to Mac users because the Mac version of the Windows Media Player does not support the features we use to protect our content from unauthorized use."

---

### Post by adam.tropics on 2006-05-21
Oh but of course you can watch the previews just fine!!....which is a tad decieving. (Not withstanding the content being a tad disturbing)

---

### Post by adamkane on 2006-05-21
Try the mediaplayerconnectivity firefox extension.

---

### Post by erniewinner on 2006-05-21
mmm... i really must log into ubuntu not xandros before posting problems... ok now i'm in ubuntu. i'm sorry i thought the url you gave was part of a sig. anyway i downloaded the plugin. restarted the browser and when i click the link the bigbrother window pops up and it says " buffering... mplayer plugin, stopped"... :-k

---

### Post by adamkane on 2006-05-21
Adjust mediaplayerconnectivity to play media in external player.
Firefox -> Tools -> mediaplayerconnectivity

You may need to uninstall the firefox mplayer plugin.

---

### Post by Mustard on 2006-05-21
I watch it on my 3 mobile phone. :)

---

### Post by erniewinner on 2006-05-22
mmm... i didn't have mediaplayer connectivity installed as i am using dapper flight 5. perhaps it's in a later version. i have downloaded flight 6/ 7 and might install them... i didn't know how to uninstall mplayer plugin so i used synaptic to remove mplayer, not sure if that was the right thing to do... now it seems to open totem... and that won't work either.

---

### Post by adam.tropics on 2006-05-22
You're confusing me now! (easily done! ) Flight 5 with all the updates, therefore beta 'whatever', or just straight flight 5? Anyway, I have a totally fresh install of  current version, and the lazymans script 'Bump' [installed this]("http://mplayerplug-in.sourceforge.net/"). and it does work within browser.

> I watch it on my 3 mobile phone. 

Mustard, as a contributor to the forums and so green team, I have every respect for you. As a human being though mate, you lost it!!!!

---

### Post by erniewinner on 2006-05-22
:confused: sorry for the confusion... me too. anyway someone asked what format it is... video/x-ms-asf well at least thats what realplayer says.

---

### Post by erniewinner on 2006-05-22
i also had used bump but no joy, what version was yours? i think i'd be best to try a later release of dapper... i did get one problem website i had to work but its stopped working again... i'll have to go burn the iso. :rolleyes:

---

### Post by adam.tropics on 2006-05-22
Bump version was 0.9, and ubuntu version was most recent!

The only thing I didn't use it for was Java which I got straight from the repos.

---

### Post by adamkane on 2006-05-22
mediaplayerconnectivity is a firefox extension, and is the only reliable way to click on a streaming playlist, and have it automatically play in your favorite player.

realplayer also handles streaming playlists well, but it's nice to avoid realplayer, if possible.

Many people get turned off by the mediaplayerconnectivity settings, but it only takes about 5-10 minutes to familiarize, and then you are streaming like it's XP.

Firefox -> Tools -> Mediaplayerconnectivity -> Configure

---

### Post by Mustard on 2006-05-23
[QUOTE=adam.tropics]Mustard, as a contributor to the forums and so green team, I have every respect for you. As a human being though mate, you lost it!!!![/QUOTE]

Heheh..it has a way of sucking you in. :)

---

### Post by erniewinner on 2006-05-23
i haven't got the hd space to do a full automatix or bumps install but i picked all the codec packages etc and am running ubuntu 6.06... here are my problem website although you might only be able to try thr first one. 

[http://www.archive.org/details/captain_kidd](http://www.archive.org/details/captain_kidd)

on the left painit says "stream 256k" this is the first film i came to... it won't stream.

there is also mtv live... i don't have a url because i go through ntl and it signs me in.

also the other one is big brother but you have to subscribe to that...

i'm also using the mediaplayerconnectivity plugin... if you have it working what player have you got etc...
i think its only possible on xp as its a protected stream??? :confused:

---

### Post by nalmeth on 2006-05-23
Yes, the advantage of protecting content, by not allowing people to use it.
That's DRM for ya. 

You may be out-a-luck on this one, as the media you're trying to stream has been jacked up with Digital Restriction's. You could pressure the provider to halt use of restricting technologies, but it's not likely to get you any sort of progress with your show. 

Can you use the video downloader firefox extension to download the video and watch it off the harddrive to eliminate streaming issues?

It's probably a DRM beefed up .wmv file, and even with w32 codec's, the stream has been specifically 'protected', and you won't be able to play it.

Bad news, sorry man. Personally I would inform them that by restricting the use of their media, they've lost a customer, and should expect to lose more. Use your consumer power. 
Really though, I would expect that you just want to watch your media. It's a shame they won't allow you to.

---

### Post by erniewinner on 2006-05-23
oh well unless someone can say exactly if they have bigbrother 7 working i'll assume the worst. i don't fancy being logged into the net for hours on end on a windows machine... could i ever relax? but i might have to, i can't blame ubuntu for that... better get out my firewall, antivirus, security packs and updates. mmm... :-?

---

### Post by adamkane on 2006-05-23
Try gxine (xine-ui) to play the media before calling it quits. Use mediaplayerconnectivity to parse any difficult playlists, and to point the stream to your favorite player.

xine-ui breezy:
[http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Player_.28xine-ui.29](http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Player_.28xine-ui.29)

xine-ui dapper:
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28xine-ui.29](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28xine-ui.29)

Mediaplayerconnectivity:
[https://addons.mozilla.org/addon.php?id=446](https://addons.mozilla.org/addon.php?id=446)

I'm not going to sign up, so there is no way for me to test.

---

### Post by erniewinner on 2006-05-28
:KS holy crap i'm in!!! the stream is a little slower than on windows. but i've got pictures and sound. the player is channel 4's but the plugin is mplayer plugin... :mrgreen:

---

### Post by Oblong_Cheese on 2006-06-19
[QUOTE=adamkane]mediaplayerconnectivity is a firefox extension[/QUOTE]

Thanks very much for this pointer, my girlfriend is now happy as pie with Ubuntu.

Playing the BB live stream in mplayer is much more configurable.

---

### Post by QwUo173Hy on 2007-07-31
erniewinner: can you play any of these? I can't and I installed the plugin.
[http://www.channel4.com/bigbrother/live/](http://www.channel4.com/bigbrother/live/)

---

