---
title: "mythtv in edgy transcoding help"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by ngowdar on 2006-11-12
I have mythtv installed in Edgy. Recording works fine, but transcoding shows doesnt work that well. Transcoding won't work from within mythtv (it doesnt do anything), it seems to work only from a terminal. When I run the "nuvexport --transcode" command, it takes almost 20+ hours to convert an hour long program into Xvid. I tried using the --ffmpeg option, but there are lots of errors.
I tried recompiling ffmpeg, but that gave lots of errors too, even when following several sites' instructions verbatim.

Any ideas? Is there another relatively easy way to convert shows using a mythtv generated commercial cutlist to divx or xvid?

Thanks.

---

### Post by superm1 on 2006-11-19
As an experiment, could you try to just do a MPEG2-MPEG2 transcode from inside myth?  Just flag your commercials, and then put them into a cutlist.  From the transcoding list, choose default.  See if this properly transcodes.

---

