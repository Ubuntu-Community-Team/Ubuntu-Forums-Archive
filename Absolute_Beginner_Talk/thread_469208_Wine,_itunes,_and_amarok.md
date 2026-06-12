---
title: "Wine, itunes, and amarok"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Akuma Shiro on 2007-06-09
So, i installed wine thinking I can run itunes (my fiance likes itunes for ONE radio station that isn't covered with amarok), but every time I try to launch itunes, the screen turns black like how xp does every now and then, and leaves black chunks on the screen.

Does anyone have some advice on this matter?

Also...

I can't get the streaming radio stations to work within amarok. It says "Error loading media. No available decoder".:(

---

### Post by durrell on 2007-06-09
I haven't been able to find a stable iTunes release that will work in Wine. You're probably going to be out of luck in that area. I know for a fact iTunes 6 and 7 won't run, but once you get down into 4 and 5 sometimes you might be able to find a release that works..

---

### Post by diatribe on 2007-06-09
I am sure that whatever station he listens to on itunes has a url, go there and just use amarok to open the stream; itunes is just a frontend for the stream.  but yea itunes doesnt work with wine in short

---

### Post by Sethalos on 2007-06-09
AmoroK has iTunes beat all the way. There is generally a url that you can use that you can use with it as mentioned above. If you want to post the radio station name (if you can't find the url) I can help find it for you.

---

### Post by machoo02 on 2007-06-09
Also check out [Streamtuner]("http://www.nongnu.org/streamtuner/") as well.  Not a media player, but a stream browser.

---

### Post by Akuma Shiro on 2007-06-09
> **Sethalos said:**
> AmoroK has iTunes beat all the way. There is generally a url that you can use that you can use with it as mentioned above. If you want to post the radio station name (if you can't find the url) I can help find it for you.

Well, the site is [http://indie1031.fm](http://indie1031.fm)
here is the link to their stream page [http://indie1031.fm/listenlive.html](http://indie1031.fm/listenlive.html)

---

### Post by machoo02 on 2007-06-09
I used to like that station when I was living in SoCal.....probably only second to KCRW

---

### Post by TravMan63 on 2007-06-09
hmmm.....
this plays the stream.... but it's not amarok:

xine.... (on xubuntu - check add/remove ... apt-get ... aptitude ... automatix... )
I also had to change a port on my (external firewall) - but that's not what's happening for you....

So - maybe try (search in add/remove) - codec (all availble) - and get all of em....

(does amarok stand alone - or does it rely on another program to actually play?)

Have you tried Songbird, Banshee, Rhythmbox?

TM

---

### Post by Akuma Shiro on 2007-06-10
Ok, I gave up on amarok. Rythumbox does have a place where you can put a URL for a radio station, but I can't find the correct URL for the radio station mentioned above.

I got all the codec's and even a Firefox plug in called "mediawrap". All that did was add a big "X" in the stream window.

---

### Post by tippit78 on 2007-06-10
I just pasted the url ([http://sc1.liquidviewer.com:9010/listen.pls](http://sc1.liquidviewer.com:9010/listen.pls)) into amarok, and it's playing for me. I just right clicked on the 'Radio Streams' folder under 'Playlists', added the url, gave it a name, and it loaded right up. But the url should work fine with Rhythmbox, too.

That's for the 'hi-fi' mp3 stream, by the way. The 'low-fi' is [http://sc1.liquidviewer.com:9000/listen.pls](http://sc1.liquidviewer.com:9000/listen.pls)

Oh, and Amarok uses xine, so you want to make sure you have the mp3 support for xine installed, which isn't by default. I use the medibuntu repositories and just installed amarok-xine, myself.

---

### Post by TravMan63 on 2007-06-10
'Sounds like' you've got a workaround going.... 


> Oh, and Amarok uses xine, so you want to make sure you have the mp3 support for xine installed, which isn't by default. I use the medibuntu repositories and just installed amarok-xine, myself.

I wondered about which engine Amarok used - that's good info (thanks tippit78) -- so making sure you have the correct xine codec should make it work in Amarok.)

I copied and pasted this:

```
http://sc1.liquidviewer.com:9010
```

into xine and it played.

Another feature I like about Totem (non -xine) - is when you attempt to play something it doesn't recognize, it automatically says 'something like' "can't play this file, would you like to download a codec?':D

TM

---

### Post by Akuma Shiro on 2007-06-11
> **tippit78 said:**
> I just pasted the url ([http://sc1.liquidviewer.com:9010/listen.pls](http://sc1.liquidviewer.com:9010/listen.pls)) into amarok, and it's playing for me. I just right clicked on the 'Radio Streams' folder under 'Playlists', added the url, gave it a name, and it loaded right up. But the url should work fine with Rhythmbox, too.

That's for the 'hi-fi' mp3 stream, by the way. The 'low-fi' is [http://sc1.liquidviewer.com:9000/listen.pls](http://sc1.liquidviewer.com:9000/listen.pls)

Oh, and Amarok uses xine, so you want to make sure you have the mp3 support for xine installed, which isn't by default. I use the medibuntu repositories and just installed amarok-xine, myself.

I think my problem was I couldn't find the correct URL to add as a stream on rythumbox. I will also play with amarok to try to get those streams to work.
But I';m listening to the station with rythumbox right now.
I thank everyone for their help.
I am trying to learn Linux as quickly as possible.

---

### Post by tippit78 on 2007-06-12
Because I forgot:

[http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)

That's the repository I used for Amarok.

Good luck getting it to work! Glad to be of some help!

---

### Post by varonbondumb on 2008-05-18
I listen to KCRW and had the same problem on getting it to work.  I tried many things but none of them seemed to work.  I am using kubuntu 8.04 and amarok with xine.

what did work:
i went to 'add/remove programs', search for 'mp3', once the search finished, on the left side, i clicked 'others', and then 'kubuntu restricted extras' and installed that.  I'm guessing that for normal ubuntu users, the 'ubuntu restricted extras would work.  i am very new to linux but searched for a few hours trying to find a solution to this.

---

### Post by jasmeet004 on 2008-05-18
i just tired the URL in VLC player.worked :)

---

