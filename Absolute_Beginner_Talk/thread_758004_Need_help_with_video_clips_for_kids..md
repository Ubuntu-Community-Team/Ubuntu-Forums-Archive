---
title: "Need help with video clips for kids."
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by linuxlizard on 2008-04-17
Hi All,
I've got a video party for my u12 soccer kids coming up and I wanted to show them some clips from some instructional dvds. I've snagged some fun clips off you-tube and I also have some cool stuff from instructional dvds, and I'm going to hook my laptop up to a projector and show them. The problem is, I don't have time to show the entire dvds, but I would like to show several 2-5 minute clips from a couple of dvds. I'm looking for a fast and easy solution for a playlist that doesn't involve me grabbing the controls on my laptop and trying to move to the parts that I want to show. In other words I want to be able to just start playing and have it play the parts I want and nothing else.

Is there a way to make a playlist of clips on one of the dvd players? For example, start at time 00:01 and end play at 04:30 then jump to 07:20 and play to 08:50 and then jump to the next section and so on?

Or is there a good way to copy the bits that I want into video clips that I can playback? I attempted to do this with vlc (went into bookmarks, and then if I highlight two bookmarks it can create a video clip out of the time between the two bookmarks). Unfortunately 3 minutes of video started turning into a couple of gigabytes (!?!) of data when I tried to do this. It also wasn't very fast- took about an hour. Maybe I'm using the wrong settings when choosing the video format?

Please advise a solution?

Thanks much!

---

### Post by quirks on 2008-04-17
Hi linuxlizard,

I don't know if you can create bookmarks within video clips with any application. There was a request for this feature for Totem, but it has not been implemented yet ([https://bugs.launchpad.net/totem/+bug/98780](https://bugs.launchpad.net/totem/+bug/98780)).

But you can extract/copy some parts of the video. I use mencoder for this purpose (my all-time-favorite video encoder). Not sure about how to do it with VLC. If you do not have mencoder yet, you can install it with Synaptics (it is in the repositories).

It requires that you are familiar with the command-line. If you are not, it may be a bit difficult for you. You can use the following command, to extract 5 minutes from a video named my_video.avi starting at the position 3 minutes in the video:

```
mencoder /path/to/videofile/my_video.avi -ss 3:00 -endpos 5:00 -oac copy -ovc copy -o /path/where/you/want/the/extract/to/be/stored/extract.avi
```

The command should complete pretty fast, because it only copies the video (and does not reencode it). Also, this should not require too much disk space.

If you need any further help with this, just ask.

quirks

---

