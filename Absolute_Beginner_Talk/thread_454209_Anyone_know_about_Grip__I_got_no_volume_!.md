---
title: "Anyone know about Grip ? I got no volume !"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by paddyboy on 2007-05-25

Just downloaded Grip but when I put a CD in...silence. It recognises it OK, etc. It says it's playing and the counter is advancing. I clicked all the buttons but no sound. All was/is well in Sound-Juicer.

I know it's something really simple/dumb..Any ideas ?

P.S. I don't know what my sound card is .....how do I find out if I need to know ? Thanks.

---

### Post by Pragmatist on 2007-05-25
I'm attaching a script that will generate a bunch of information about sound on your system.  Download the script which is called "sound_info.sh" and then do this:
```
chmod a+x sound_info.sh
```
```
./sound_info.sh mysound.zip
```

Now you'll have a file called "mysound.zip".  Attach it in your next post.

Note: The file won't really be a zip file, we're just using that extension because the Ubuntu Forums limit .txt files to 19.5K which is too small.  Don't ask me why they do that! :)

---

### Post by paddyboy on 2007-05-26
Many thanks for your reply. I did as you suggested and have attached the file...I think .

It seems quite big though !

rgds
pb

---

### Post by paddyboy on 2007-05-26
MMm not attached...lets see.....

---

### Post by paddyboy on 2007-05-26
Whoops ....sorry ......never done this before.....maybe now.....

---

### Post by Pragmatist on 2007-05-26
See if this works:

```
alsamixer
```Use the Left and Right arrow keys to move to a column called "CD", then use the Up and Down arrows to set the volume.  Set the volume fairly high (just before the little boxes turn red is usually good).  When you are finished just hit the ESC key.

Can you hear Grip play the CD now?

---

### Post by paddyboy on 2007-05-29
Yup. Thanks a lot for your help. Sorry about delay in getting back to you, but I had a dodgy internet connection...but that's another story.
Thanks again.
pb

---

