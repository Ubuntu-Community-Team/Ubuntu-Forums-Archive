---
title: "edit vob in Kino?"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by RetroFreak on 2007-08-14
I have a Sony DVD camera that records to those little DVD's. I want to edit my films, so is there a way of converting vobs into dv format? Or is there another way/program that will let me edit them? Not too fussed about fancy features at this stage, just want to trim them down.

TIA

Ian

---

### Post by FakeOutdoorsman on 2007-08-14
You can convert the VOB into raw dv with ffmpeg:

1. Add Medibuntu repository to your sources.list. [Easy instructions]("http://medibuntu.sos-sts.com/repository.php").
2. sudo aptitude update
3. sudo aptitude install ffmpeg (or install via Synaptic to make sure it is the Medibuntu version).
4. Try the following ffmpeg code:
```

ffmpeg -i input.vob -target ntsc-dv output.dv

```

If it is a PAL DVD, use -target pal-dv.

---

### Post by Irihapeti on 2007-08-16
I've also got one of those cameras and I've just tried Fakeoutdoorsman's suggestion. The resulting DV file looks very streaky in Kino. It appears fine in VLC, so I guess it's just something to do with the way that Kino renders it. (And when I output it again from Kino to an MPeg, it looks fine in VLC and Mplayer.)

Is there some tweak I can use so that the video looks better in Kino? I find the streaky look just a bit distracting.

Many thanks

Irihapeti

---

### Post by RetroFreak on 2007-08-17
Thanks for that I'll give it a try.

Streaks in Kino are probably to do with interlacing. It may be Kino isn't adding any to the video, possibly for speed reasons. As long as the final file looks OK I wouldn't worry too much. I know what you mean about it being distracting though.

Cheers :)

---

