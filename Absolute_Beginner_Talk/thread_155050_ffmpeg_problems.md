---
title: "ffmpeg problems"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by jethro10 on 2006-04-04
Hi,
Not sure if this problem is ffmpeg, Ubuntu or even what 'part' of the system ffmpeg belongs to, so i'll start here.
If I convert an AVI file with ffmpeg, I can then use dvdauthor and mkisofs to make a dvd. Now this works fine.
But if I use the -cropleft, -cropright OR --padtop or -padbottom then the DVD output is horrible. The mpeg looks ok as does the .vob file, on the PC anyway.

The output is reminiscent of a patchwork quilt or a mosaic.

anyone any ideas of even where to look?

J

---

### Post by Pragmatist on 2006-04-04
Try and give us some screenshots so we can see what your talking about.  There should be a "print screen" on GNOME's menu (not the main menu, the one that has 'logout' on it)

---

### Post by jethro10 on 2006-04-05
Well,
I've finally found my problem.

Lets say the resolution was NTSC or 720x480 lines
I was trying to pad top and bottom by 40 pixels each to add bars for a wider screen image.
so i said something like       720x480 -padtop 40 -padbottom 40
But what I didn't realise is that I had to  say 720x400 -padtop 40 -padbottom 40
Reduce the image resolution by the amount of padding
24 hours of pain.....
I sometimes wonder why.
My wife suggested taking my outside, naked in the cold, pouring cold water over me and beating me with a stick - it seems more fun she said.
She has a lot to learn :) 
J

---

### Post by fsman on 2006-04-05
Is your ffmpeg encoding working? Mine is crashing and I'm thinking of submitting a bug report.

Can you confirm yours works using the following?

ffmpeg -i <input video> -target pal-dvd <output video>

---

