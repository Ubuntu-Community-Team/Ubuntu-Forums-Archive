---
title: "Firefox / Dapper can't play audio stream"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-09-24
Check if Already Posted returned: Sorry - no matches. Please try some different terms.

I want to listen to:

[http://boss.streamos.com/real/csps/clerks_office/service/church_service.ram](http://boss.streamos.com/real/csps/clerks_office/service/church_service.ram)

I clicked the link, Totem loaded and returned:

Totem could not play 'rtsp://grm34.streamos.com/34/22/6e/226ea7317a1e259899602fdb80883757-4516b7a6.rm?ts=1159141083=300=E2B1B96C66E9DCA4FD2D872BD1CD50A21C65154E'.

I don't care if Ubuntu plays the link as Windows Media or Real Player, mox nix! Clicking on either link returns the same problem, no sound.

Internal GStreamer error: negotiation problem.  Please file a bug at [http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer](http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer) .

I dont' want Totem for this, but if I have to . . .

Can someone suggest a simpler player. Also, when the link is selected, a window pops up and offers:

Open With  Movie Player Default
Save to Disk
Do this automatically 

When I highlight Movie Player and then pull down to other, the directory shown in Choose Helper Application is my /home/mark directory. If I could choose another application, I would, but I have no idea as to what directory to point this "chooser" to.

Somebody please tell me where it is.

---

### Post by xyz on 2006-09-24
I can listen to your link.
I'd get Automatix and install the plugins for Firefox.
[www.getautomatix.com](www.getautomatix.com)

---

### Post by PriceChild on 2006-09-24
I would reccomend that you install audio codecs from wiki.ubuntu.com/RestrictedFormats instead of automatix so you can understand what is going on.

---

### Post by Mark_in_Hollywood on 2006-10-01
> **xyz said:**
> I can listen to your link.
I'd get Automatix and install the plugins for Firefox.
[www.getautomatix.com](www.getautomatix.com)

I've used Automatix and installed the Aud-Vid Codecs, Multimedia codecs, Beep Media Player, and pretty much everything else that Automatix installs that plays audio (or even video). I even installed Real Player, which I don't like.

Nothing.

When I click a link, Ubuntu offers to use Totem to "play" the file. When I say "other", I don't get taken to where "other" media players are. Why?

---

### Post by CupofDice on 2006-10-01
I am a noob Mark, but check out /usr/bin. Thats how I started using amarok (does a good job of streaming, so check that out too). Also if you are trying to play the video inside Firefox, check out mplayer and firefox plugin.


```
sudo apt-get install "mplayer" "mozilla-mplayer"
```

---

### Post by Mark_in_Hollywood on 2006-10-01
> **CupofDice said:**
> I am a noob Mark, but check out /usr/bin. Thats how I started using amarok (does a good job of streaming, so check that out too). Also if you are trying to play the video inside Firefox, check out mplayer and firefox plugin.


```
sudo apt-get install "mplayer" "mozilla-mplayer"
```

Do you know if this works with SwiftFox as well? The Wiki Restriced Formats page has a long article about 'fixing' this for SwiftFox.

For the sake of listening to just one audio stream, it would be easier, simpler, smarter to use FireFox.

---

### Post by xyz on 2006-10-02
Well if you've installed pretty much everything related to sound,video,codecs and all then the problem is probably elsewhere.
Did you run
```
alsamixer
```
and using left/right arrows check volume levels
Also in Application > Sound/Video > Volume Control...are things ON in there?
Hope you can solve this.

---

