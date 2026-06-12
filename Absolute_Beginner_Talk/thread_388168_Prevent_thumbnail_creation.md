---
title: "Prevent thumbnail creation?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by silkstone on 2007-03-19
If I've understood this correctly, thumbnails are created in ~/.thumbnails for every image viewed, there is no limit to the size of this folder and the thumbnails never expire.

I found a command to clear out thumbnails that haven't been accessed for a certain number of days, but is there any way to stop them being generated in the first place?

In particular, I would like to prevent thumbnail generation for images on CD/DVD. I'm not so bothered about photos etc on the hard drive that are likely to stay there, but I get a lot of stuff on CD/DVD which I'll probably only view once before copying the files I want to the hard drive, so there's no point in the .thumbnails folder being cluttered up by all the rest.

Is there a way? TIA.

---

### Post by xyz on 2007-03-19
Hi,
What is that command line you use, btw?

---

### Post by silkstone on 2007-03-19
Command is...

```
find ~/.thumbnails -type f -atime +7 -exec rm {} \;
```

(That should clear out anything not accessed for 7 days.)

---

### Post by adam.tropics on 2007-03-19
You could open gconf-editor, and go desktop-->gnome-->thumbnailers.....disable all and see if that helps. Actually it doesn't, just tried it.  So perhaps this. If you go to apps-->nautilus-->preferences, again in gconf-editor, there is a setting to set the max size of images that get thumbnailed, in bytes. I presume if you set that to something like 1 byte, it would stop altogether. Worth a try!

---

### Post by silkstone on 2007-03-19
Thanks! Really I don't want to disable thumbnail generation altogether - just for 'transient' data sources.

---

### Post by xyz on 2007-03-19
Thanks for the command line.
How about using Crontab on a daily basis? At least, that way, you won't worry about it anymore.

---

### Post by xyz on 2007-03-19
There are also a bunch of thumbnails in:

home/xx/.thumbnails/normal  or in root/.thumbnails/normal

which the command line doesn't seem to remove...as far as I can tell checking 'by hand' in the files.

---

### Post by adam.tropics on 2007-03-19
Curious, is your concern a privacy thing, or a space thing, because I just deleted 1127 thumbnails, and gained the grand total of 11.6MB, which kind of says it's not such an issue!

---

### Post by silkstone on 2007-03-19
I've been using Ubuntu for about a month, and when I looked at ~/.thumbnails there were over 11,000 files! I'm a photographer and technical writer, so I deal with a huge number of images.

Using a Crontab is probably a good idea - thanks - but I'd really like to stop some of them from being created at all.

---

### Post by thelinuxguy on 2007-03-19
> **silkstone said:**
> 
In particular, I would like to prevent thumbnail generation for images on CD/DVD. 
Is there a way? TIA.

Open Nautilus. Goto Edit -> Preferences. In one of the tabs, there is an option to disable preview selectively. See if that helps.

---

### Post by silkstone on 2007-03-19
The Preview tab under Nautilus>Preferences lets me choose which thumbnails are displayed in Nautilus - maybe that will stop them being created ??? I'll try - thank you.

---

### Post by xyz on 2007-03-19
I'll try that too but, in my humble opinion, not displayed won't mean not created. We'll see.

---

### Post by rottenbreed on 2007-03-19
@silkstone

Good catch. I didn't notice this until now. To me its more of a privacy issue, then again it also freed up 92MB of space when I cleared those folders. Did any of those tricks work to prevent them from being cached in .thumbnails? I also do not want to altogether disable thumbnail view either, but I do not like how they are stored in .thumbnails even after I deleted the originals. Btw, it caches even thumbnail views of movies, not just pics.

---

### Post by silkstone on 2007-03-19
I think they still get there if you view in gThumb. 

Maybe this is something for the Ubuntu Suggestions Box - better control of thumbnail generation and a built-in way of managing them. ;)

---

### Post by Zimmer on 2007-03-19
> **silkstone said:**
> I think they still get there if you view in gThumb. 

Maybe this is something for the Ubuntu Suggestions Box - better control of thumbnail generation and a built-in way of managing them. ;)

The Gqview  image viewer has a function to clean up the thumbnail cache, I found this

[http://darkmere.wanfear.com/blog/archives/000149.html](http://darkmere.wanfear.com/blog/archives/000149.html)

which pointed me in the direction of Gqview.  Brought my cache down from 70 mb to 29mb just removing the orphans...

---

### Post by silkstone on 2007-03-19
Good find. There ought to be something like that in gThumb and Nautilus.

---

### Post by rottenbreed on 2007-03-21
@silkstone

I'm about to test the tips mentioned in below thread.

[http://www.ubuntuforums.org/showthread.php?t=348510](http://www.ubuntuforums.org/showthread.php?t=348510)

---

### Post by silkstone on 2007-03-21
Interesting one - let's know how it works. The only thing is that I don't want to disable thumbnail generation globally - it's useful to have them most of the time. I'd like to switch it off for external media such as CDs and DVDs.

---

