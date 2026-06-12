---
title: "Should I even try?"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by MrVisible on 2006-05-27
This is really going to make me look seriously lame, but here goes.

I'm all excited to try the latest Dapper release. I've got a spare 80 gig hard drive free, I've got the iso downloaded and burned, and just for fun I tried the live cd before installing. Because I'm cautious that way.

It booted up fine, and Ubuntu is as pretty and as smooth as I'd heard. But I had no network connectivity. Everything else seemed fine, though. 

So I booted back into Windows, and checked the forums and the wiki for information on my wireless network adapter. It's a D-Link DWL-122. Which some of you may recognize from [a few threads.](http://www.ubuntuforums.org/search.php?searchid=5566760) It seems I've got one of the more problematic USB wireless adapters out there.

And my network is WEP encrypted, which [ apparently causes more interesting problems.](http://www.ubuntuforums.org/showthread.php?t=156405) 

I'm looking forward to learning the ins and outs of this operating system, and I'm a pretty decent windows tech, but this looks like a nightmare waiting to happen.

Anyone have any reassurances about how easy this is going to be? Or should I give up now and avoid spending a weekend learning new and exciting epithets?

---

### Post by IYY on 2006-05-27
I think you should try it. People are having problems with this device, but they are also solving them. It ain't a Lexmark printer.

---

### Post by joshrobinson on 2006-05-27
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")


your card is on the ndiswrapper page, so you shouldnt have too much trouble at all.. i gota do the same deal to get mine in my laptop going

---

### Post by Davidios on 2006-05-27
Oh, yeah, WiFi is a big trouble in Ubuntu... I have DWL-122 too, can anybody help us? I'm a newbie... ;(

---

### Post by PingunZ on 2006-05-27
Install ndiswrapper ;)
Type this in console ::
```
sudo apt-get install ndiswrapper
```

voila ;) then look for your card driver ... on the internet 
and install it with ndiswrapper.
You can find many of ndiswrapper howto's by googleing ;)

Grtz PingunZ

---

### Post by Revan on 2006-06-07
I used ndiswrapper to get the DWL-122 working... anyway I found out that I needed to blacklist the "built-in" (can't find a better description) prism2_usb module to get ndiswrapper working!

---

### Post by nalmeth on 2006-06-07
Of course you should try. What else would you do this weekend?

---

### Post by xyz on 2006-06-07
[QUOTE=MrVisible]This is really going to make me look seriously lame, but here goes.

I'm all excited to try the latest Dapper release. I've got a spare 80 gig hard drive free, I've got the iso downloaded and burned, and just for fun I tried the live cd before installing. Because I'm cautious that way.

It booted up fine, and Ubuntu is as pretty and as smooth as I'd heard. But I had no network connectivity. Everything else seemed fine, though. 

So I booted back into Windows, and checked the forums and the wiki for information on my wireless network adapter. It's a D-Link DWL-122. Which some of you may recognize from [a few threads.](http://www.ubuntuforums.org/search.php?searchid=5566760) It seems I've got one of the more problematic USB wireless adapters out there.

And my network is WEP encrypted, which [ apparently causes more interesting problems.](http://www.ubuntuforums.org/showthread.php?t=156405) 

I'm looking forward to learning the ins and outs of this operating system, and I'm a pretty decent windows tech, but this looks like a nightmare waiting to happen.

Anyone have any reassurances about how easy this is going to be? Or should I give up now and avoid spending a weekend learning new and exciting epithets?[/QUOTE]

Hi MrVisible...happy to **see** you here on the site!

You sure didn't look 'lame' or you may have looked as 'lame' as most of us did standing where you are! No worries! One of the many great things about the Ubuntu Community is that you are most welcome to ask any questions you may think are 'stupid'. No one ever laughs and everyone is ready to help and encourage to the best of his/her capabilities and time availability.

Should I tell you it'll be easy? Well, no! That is, it wasn't (isn't) for me but 'this thing' grows on you and it may take weeks for you to realize you've made progress. And then, all of a sudden, in a couple of days, you'll make giant steps because you'll have managed to understand a few basic things. And then again, giant steps and all, you may realize how much there is still to learn but that's when you'll **want** to go on learning if 'this thing' grew on you by then! That's when the nightmare becomes a dream and all the cursing and frustration vanish into thin air and the light becomes visible...yes Sir, MrVisible!

'This thing' is sure worth more than a potentially wasted weekend. Do try and let 'this thing' grow on you and you'll never again wonder whether you've wasted your time or not.

I'm pretty sure you didn't become a " a pretty decent windows tech" in 48 hours!
Hang in there! I'm sure the whole community (I'm not one of them but there really are some people who know what they are talking about here!) is behind you and will never make you feel you lag behind.
So long...

---

### Post by Ghil on 2006-06-07
you do not have a working net connection? nice, a problem. we always learn from problems. It was with problems and screwing everything around that I now know how Linux works perfectly...It begins by a simple internet connection, then it's your video driver (okay on Ubuntu Automatix makes things really easier but I was on Mandrake 7 I first got into Linux...)...and next thing you know, you are helping others on the same problems you had when you where new. and you're proud of it ;)

Linux is a great experience, you just have to take the time to learn everything :)

---

### Post by tormod on 2006-06-17
I have put together some up-to-date information about the prism2_usb drivers on [https://wiki.ubuntu.com/WifiDocs/Driver/prism2_usb](https://wiki.ubuntu.com/WifiDocs/Driver/prism2_usb)

It should not be necessary to use the ndiswrapper and Windows drivers...

---

