---
title: "Flash memory BMI Too much fat!"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by yogo on 2007-08-24
I am sharing this in Ubuntuland because I found it interesting.

Last night while at Wal*Mart I found a 2 gig sd card for an MP3 player I had that I wanted to add some more memory to.

Every time I inserted the card I had problems with an error. I knew the card was not faulty as my card reader had no problems with it, I was also able to use it in the MP3 player, the problem would arise when disconnecting the MP3 player from the pc.
So my first thoughts were to format it, I did so in Gparted and since it was 2 gigs, I decided fat 32 would be good. I still had problems so I reformatted it to fat 16 and more problems, not actually more just the same problem.

So I googled the mp3 player and external memory problems and came up with this.
[http://www.moviecodec.com/topics/4768p3.html](http://www.moviecodec.com/topics/4768p3.html)

and this
[http://www.moviecodec.com/topics/4768p1.html](http://www.moviecodec.com/topics/4768p1.html)

So I found that many people were having the same problem., some were resolved simply and others were not.

The fact that I had a 2 gig card made this more of a challenge, seems the firmware likes 512 or less.

Well after several hours of fiddling around, it just bugs me when I can not get something to work. I tried various firmware updates from the memorex site. All this did require I use my Windows box, yeah I hated it. Wine would not allow me to in Ubuntu.

At last check when I went to update drivers, Windows said the driver was the best one for it over the Memorex ones.

What it comes down to is I do not think this had anything to do with firmware as I could not tell it was flashed, at least not like flashing a dvd burner.

I was able to format the card with the memorex formatter from their web site and after using three different formatters, it finally worked and I now have the 2 gig card working.

Seems to be all about the FAT, why could I not format this card right in Gparted and could I have? The only two options I tried was fat16 and fat 32

Did I say how much I hated using Windows for this short period of time!

---

