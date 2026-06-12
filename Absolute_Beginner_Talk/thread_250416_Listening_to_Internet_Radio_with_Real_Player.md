---
title: "Listening to Internet Radio with Real Player"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by navneeth on 2006-09-04
I have the RrealPlayer installed as per the instruction given in the their site. But how do I listen to internet radio? (that's the only reason why I have it installed)

---

### Post by bodhi.zazen on 2006-09-04
Not sure if this helps, but.....

I use xmms and streamtuner. (as you know xmms is a media player, streamtuner allows you to select a station. Install streamtuner from synaptic if you wish).

I have not looked at realplayer for Linux in a while and was not happy with it 1 year ago.

---

### Post by navneeth on 2006-09-04
Will streamtuner let me select any station? The one I have in mind is streamed only via WMP and Real. Thanks

---

### Post by bodhi.zazen on 2006-09-04
Tell me what station and I'll check it out for you.

"any station" is broad because not all stations are "free".

At least some WMP stations are on streamtuner.

---

### Post by Titus A Duxass on 2006-09-04
I listen to BBC Radio 2 through firefox, which in turn uses the Realplayer.

Simply go to the radio station's website click on the correct links, off you go.

(with BBC Radio 2 click on listen live).

---

### Post by navneeth on 2006-09-04
[http://www.beethoven.com](http://www.beethoven.com) , this has both a free stream and Premium Real Pass stream. I listen to the former.

---

### Post by bodhi.zazen on 2006-09-04
> **navneeth said:**
> [http://www.beethoven.com](http://www.beethoven.com) , this has both a free stream and Premium Real Pass stream. I listen to the former.

No, that one is not listed.

If it helps streamtuner is on Shoutcast and there are several classical stations.

Also on Xiph and Live 365, although I thind Live 365 may be by subscription only.

---

### Post by navneeth on 2006-09-04
> **bodhi.zazen said:**
> No, that one is not listed.

If it helps streamtuner is on Shoutcast and there are several classical stations.

Also on Xiph and Live 365, although I thind Live 365 may be by subscription only.

Thanks for checking, and also for the suggestions. I'm kind of used to listening to this station on a daily basis. :mrgreen: 

[quote=Titus A Duxass]I listen to BBC Radio 2 through firefox, which in turn uses the Realplayer.

Simply go to the radio station's website click on the correct links, off you go.(with BBC Radio 2 click on listen live).[/quote]
The site I mentioned above does not have a link to the free stream, at least I cannot see it. I tried listening to it from the Real site's Radio section, but that didn't work. Probably I'll ask the IT guys of the site if it's possible.

---

### Post by bodhi.zazen on 2006-09-04
> **navneeth said:**
> I'm kind of used to listening to this station on a daily basis.

I understand.

FYI:
[streamtuner](http://www.nongnu.org/streamtuner/)

Install via synaptic or:
```
apt-get install streamtuner
```
In the event you would ever like an alternate to your current situation.

---

### Post by navneeth on 2006-09-04
Do I have to use xmms player with streamtuner, or will any player that comes by default with Ubuntu (Rythmbox, for example) work?

---

### Post by bodhi.zazen on 2006-09-04
> **navneeth said:**
> Do I have to use xmms player with streamtuner, or will any player that comes by default with Ubuntu (Rythmbox, for example) work?
You can use any player you want. There is a pull down menu in streamtuner

Edit -> Preferences -> Applications.

You can set different players for different types of files if you wish.

Although I have not used it with Realplayer, I have used it with a total of 3 players no problem. Very easy to configure.

---

### Post by navneeth on 2006-09-04
Great! Thanks. :)

---

### Post by xyz on 2006-09-04
Don't know if this will help but I'm listening to beethoven.com right now simply with the mplayer plugin for firefox.

---

### Post by navneeth on 2006-09-04
xyz, please tell more about it. :D

---

### Post by xyz on 2006-09-04
> **navneeth said:**
> xyz, please tell more about it. :D

Well, actually I did it the easy way this time around..following a total HD breakdown, I didn't feel like going through seperate codecs install again.

I downloaded Automatix:
[http://www.getautomatix.com/](http://www.getautomatix.com/)
and installed the MPlayer & FF Plugin which can be found in the Automatix list. I also installed all the other codecs that way!
Let me know if this works for you!

---

### Post by bodhi.zazen on 2006-09-04
> **navneeth said:**
> xyz, please tell more about it. :D

mplayer is available via synaptic, I have not used it.

---

### Post by navneeth on 2006-09-04
So which is the better(and safer) way to do, Automatix or Synaptic? I've not installed anything in this machine apart from a theme and Real Player.

---

### Post by xyz on 2006-09-04
> **navneeth said:**
> So which is the better(and safer) way to do, Automatix or Synaptic? I've not installed anything in this machine apart from a theme and Real Player.

I'd say either way is good and safe!

---

### Post by navneeth on 2006-09-04
Okay. I'm on Windows right now. Will get the mplayer when I go back to Ubuntu.

---

### Post by navneeth on 2006-09-04
Just need to check if I'm doing it the right way

Go to Synaptic -> Mark the file kmplayer-base (that's what I got when I searched for mplayer) -> Apply -> Install

Is that right? If it is, how do I then get the Firefox plugin?

---

### Post by xyz on 2006-09-04
As far as I can remember, there's kmplayer,mplayer and more in Synaptic...you work with KDE or Gnome?
Also (in Synaptic), scroll down past kmplayer and so on...until you get to "mozilla-mplayer" Then do like you wrote...Mark...Apply.
Remember that Synaptic is no danger whatsoever to your system, even if you mark the 'wrong' thing. If you realize it's not what you need, you then can easily "Mark it for Complete Removal"...the same way you "Mark it for Installation".

Just remember, I use Gnome and got my mplayer plugin (and the rest of them) via Automatix as I said in a previous post. Good luck, navneeth and do let us know how it went.

If things are still unclear, don't hesitate to ask. We've all been there!

---

### Post by navneeth on 2006-09-04
Thanks for the encouraging words. :)

I'm looking through the 'All' list in Synaptic, but I'm not able to find mplayer, and no plugins for Mozilla - just Fx and Tb. Btw, I'm using Gnome. It's been just over a day since I installed Ubuntu. Guess I'll try Automatix.

---

### Post by xyz on 2006-09-04
I'm not a 100% sure about this but I assume Automatix put the plugin in Synaptic...so to speak. At the end of the Automatix install, it'll ask you if you want it to modify your sources.list...answer yes and then it should work.
Answering Yes will no doubt make the plugin available.

To see your sources.list:
```
$sudo gedit /etc/apt/sources.list
```

Do you think you'll manage to install Automatix OK?
Hang in there!

---

### Post by xyz on 2006-09-04
All about Atomatix here:
[http://ubuntuforums.org/showthread.php?t=177646](http://ubuntuforums.org/showthread.php?t=177646)
Look at it,try and ask if things get confusing.

---

### Post by Ambimom on 2006-09-04
It's very simple to listen to radio using Realplayer in Linux.  Assuming you've installed the RealPlayer 10 offered in the Add/Remove Applications. This link was very helpful to make sure you've got all the right codecs, etc.

 [http://www.ehomeupgrade.com/entry/2663/how-to_get_full](http://www.ehomeupgrade.com/entry/2663/how-to_get_full) 

When you click on the RealPlayer icon to listen to a particular program, if the default is Totem, change the default.  You need to go to the Places, home folder and go up one place in the file structure to your username, then up one more.  Open usr, then bin.  You'll scroll down (it's in alphabetical order) until you see the RealPlayer and that's what you should enter as your default.

Next time you click on Realplayer icon, it will open RealPlayer 10 automatically.

---

### Post by navneeth on 2006-09-05
YAY! Now I can listen to Beethoven Radio on Ubuntu, too. Thank you very much for your help, xyz, and others, too. :D :D :D 

The problem is that internet has been very slow in Ubuntu(or maybe it's just Firefox in Ubuntu), and since I'm using a Firefox plugin, I'm not able to listen to B.com continously. You can read about my internet woes [here]("http://ubuntuforums.org/showthread.php?t=250416&page=3"). :(

Btw, xyz, installing Automatix was not a problem at all. I used the first method (non-apt) that was suggest in their site. Found the mplayer and the FF-plugin and installed them, and also I made sure to hit the OK button regarding the sources.list.

---

### Post by navneeth on 2006-09-05
Just to add, I use the WMP stream rather than the Real Player.

---

### Post by xyz on 2006-09-05
Well now that's good news! I'm sure Beethoven "hears" you!
If you care to fine tune Firefox, check this out.
Happy listening!
[http://ubuntuforums.org/showthread.php?t=189192](http://ubuntuforums.org/showthread.php?t=189192)

---

### Post by navneeth on 2006-09-05
> **xyz said:**
> 
If you care to fine tune Firefox, check this out.
Happy listening!
[http://ubuntuforums.org/showthread.php?t=189192](http://ubuntuforums.org/showthread.php?t=189192)
In one of those links provided in that thread -
[http://ubuntuforums.org/showthread.php?t=181107](http://ubuntuforums.org/showthread.php?t=181107), I need to put in some code depending upon my computer specs. My computer is a 1.7 GHz P4, 256MB RAM and has a 256 kbps intenret connection. So which option do I choose? - 
FAST/SLOW COMPUTER, FAST/SLOW CONNECTION

---

### Post by xyz on 2006-09-06
Gee, good question which I can't figure out! I'll post smth so your thread goes back to the top of the list and hopefully a knowledgable member will see it.
I set mine to fast connection,fast computer:
Toshiba Satellite A40 512 RAM / about 400-450 kbps (laptop)
2.7GHz / IntelCeleron

You know, navneeth, you can just try the different settings and see what works best. I don't think it'll hurt your system and/or computer.
If you see a difference, just stick to "that" setting or simply go back to the original one!

---

