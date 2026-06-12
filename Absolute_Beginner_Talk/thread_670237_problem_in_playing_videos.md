---
title: "problem in playing videos"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by vishnu_23688 on 2008-01-17
[B]hi friends.. i have seen all the posts relating to this topic. but mine is a little bit different. when i try to play any videos(like movies) from dvd's directly, using any players(VLC,amarock,movie palyer) i can see the video but with some green lines in between. 
also when i play the files from the hard disk the file is playing frame by frame. i mean it s being played slowly and i can see the frames getting changed. [hope it is understandable] 
i installed all the codecs required yet i am not able to get the video properly.:confused: i disabled the visual effects also. i get this problem only when the video is played in full screen mode. when it is played in small mode it is clear. im using Gutsy Gibson. my graphics card is also suitable and fine. i didn't get these problems in windows xp.
[/B]
any one please help me out of this.

---

### Post by meborc on 2008-01-17
i also have encountered the problem... it only appears when i copied the movie clip to the ntfs partition through windows, and then tried to view it from linux...

using a ext3 formatted partition for media solved the problem for me

---

### Post by vishnu_23688 on 2008-01-17
the problem was with my dvd. but the 2nd problem was solved after restartin using [COLOR="Red"]**ctrl+alt+backspace**[/COLOR]

now the problem is solved.

can i extend the swap space now, after installing the Linux.

---

### Post by vishnu_23688 on 2008-01-17
> **meborc said:**
> i also have encountered the problem... it only appears when i copied the movie clip to the ntfs partition through windows, and then tried to view it from linux...

using a ext3 formatted partition for media solved the problem for me

can i extend the swap space after installing the Linux.?

---

### Post by chaime on 2008-04-14
I extended my swap partition by starting Gutsy from the CD, then using GParted to edit the partition sizes.

I think I had to tell it not to use my swap drive first, though -- like unmounting the drive, right-click on the swap partition to see the options before attempting to modify it.

Hope this helps.

Chaim

---

