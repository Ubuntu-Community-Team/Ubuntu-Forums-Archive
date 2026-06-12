---
title: "Problem with playing movie"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by Bencoo on 2007-09-07
Hi, I have problem's with playnig movie's. 
1, I can open the movie, but it is slashing video, audio go right. I have a lot codecs, i can open every film, but with slashing. It is the same problem if i open low or HD resolution. When i open HD resolution movie there is sometimes problem that sound is before video. It is the same in VLC and MPlayer. Any idea? 
2, Why sometimes when i try open the movie in MPlayer there is some mistake with device..(i dont remember exactly) a i cant open any movie, i have to "reboot" mplayer. 
3, WHy sometimes when i play HD movie get mistake about "full buffer" and i have to destroy mplayer
Thx very much

I have P-M 1,73GHz, 1,5GB RAM, ATI MOBILITY X600.  Some config info's: 
[HTML]
benco@Lenoch:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X600
OpenGL version string: 2.0.6334 (8.34.8)


benco@Lenoch:~$ glxinfo | grep direct
direct rendering: Yes

benco@Lenoch:~$ glxgears
10492 frames in 5.0 seconds = 2098.361 FPS
11196 frames in 5.0 seconds = 2239.162 FPS
11235 frames in 5.0 seconds = 2244.984 FPS
11200 frames in 5.0 seconds = 2239.955 FPS
11074 frames in 5.0 seconds = 2214.678 FPS
[/HTML]

---

### Post by BrendanM on 2007-09-07
1. VLC has an "audio desynchonization compensation" feature. It's under the advanced preferences for audio. You could adjust the sound to match up with the video that way.

2. I've never used mplayer much. Maybe post the exact error message?

3. It sounds like mplayer is giving you a lot of grief, maybe stick with VLC?

---

### Post by Bencoo on 2007-09-07
3, The full version of error: Too many video packets in the buffer: (329 in XXXXXX bytes).

But the biggest problem is with slashing video(point 1). Because i cant watching movies with smooth motion.
Thx

---

