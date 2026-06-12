---
title: "Does Iceberg Radio work for anyone else?"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by TreverT on 2007-11-14
File this under "Is it Linux or is it just my computer?"

Back in XP, I dearly loved the free internet radio station Iceberg Radio.  Tons of channels to fit any mood.  But using Firefox in Ubuntu 7.1, I get no sound.  I have AdBlock Plus, but it's turned off for Iceberg.  I get the channel menu up, and I can choose stations, and they say they are playing, but no sound comes out and no track titles appear.  Can someone else please go to:

[http://www.icebergradio.com/#channels]("http://www.icebergradio.com/#channels")

and pick a channel, and see if it will play audio?  I'd really like to know if this is a Linux-wide thing or a problem specific to my machine.  Thanks!

---

### Post by marco123 on 2007-11-14
Doesn't work here either.  Could be a LInux/Firefox thing.:(

---

### Post by TreverT on 2007-11-14
Looking more and more like it is.  I've tried the site in Firefox, Opera, and Epiphany, and all three produce the same behavior - I can connect to a channel and it claims to be playing, but no sounds comes out.

---

### Post by jeremiebergeron on 2008-04-11
I know that this is resurrecting an older thread, but I figured out how to listen to icebergradio in Linux. Here's how to do it.

[LIST=1]
[*]Find out the exact address to the stream that you want to listen to. This will look something like this: [http://playlist.icebergradio.com/clientasx.php?listener_id=1&station_id=40071&bitrate=64](http://playlist.icebergradio.com/clientasx.php?listener_id=1&station_id=40071&bitrate=64) (This is the link to the pianist channel. Right click it to copy the link). Tip: replace the id# from the URL above (40071) with the # that shows up in the address bar when you open up the station you want at [http://www.icebergradio.com/](http://www.icebergradio.com/).
[*]Open VLC; install it if necessary.
[*]Click on File->Open Network Stream...
[*]Click on the HTTP/HTTPS/FTP/MMS option and paste in the URL into the URL textbox. The URL is the same address that you got previously.
[*]Click OK.
[*]Now open the playlist and make sure that 'Repeat One' is enabled.
[*]Done!
[/LIST]

Hopefully that helps someone!

---

### Post by TaTaE on 2008-04-11
Works GREAT here :guitar: . I am listening right now to "2kool4radio" station. Thanks for the link. I am using Hardy Heron beta btw.
Cheers,

---

### Post by TreverT on 2008-04-11
You're a gent, Jeremie!  Funnily enough, Iceberg actually fixed their web player in the time since I first posted that.  It was a problem on their end, that it just didn't work under Linux.  BUT, sometime around last November or so, suddenly it mysteriously started working.  :)  I've been using it regularly since.  But your solution is even better, because I'll be able to add channels to my media player rather than having to go to their page all the time to listen to their music.  Jolly good show, and thanks very much!

---

