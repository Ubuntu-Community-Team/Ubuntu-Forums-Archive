---
title: "Need help finding FLV files and flash files on the computer"
date: 2011-07-08
forum: Any Other OS
---

### Post by nec207 on 2011-07-08
I have windows vista and windows 7 and I need help finding FLV files and flash files on the computer .
 
I would like to know where it may be on the computer . I thought web sites you go to are stored in the Temporary Internet Files folder.
 
C:\Users\mike\AppData\Local\Microsoft\Windows\Temporary Internet Files
 
Check that cannot see any FLV files or flash files.

---

### Post by An Sanct on 2011-07-08
here are the locations for Firefox
```

~/.mozilla/firefox/cache
~/.mozilla/firefox
```Note: This is an Ubuntu Linux forum ;)

[http://en.wikipedia.org/wiki/Temporary_Internet_Files](http://en.wikipedia.org/wiki/Temporary_Internet_Files)

---

### Post by mips on 2011-07-08
Those files are encoded/wrapped into something else if I'm not mistaken. There was a thread about this not to long ago.
[http://ubuntuforums.org/showthread.php?t=1688948](http://ubuntuforums.org/showthread.php?t=1688948)

I suspect something similar would apply to windows.

---

### Post by haqking on 2011-07-08
> **nec207 said:**
> I have windows vista and windows 7 and I need help finding FLV files and flash files on the computer .
 
I would like to know where it may be on the computer . I thought web sites you go to are stored in the Temporary Internet Files folder.
 
C:\Users\mike\AppData\Local\Microsoft\Windows\Temporary Internet Files
 
Check that cannot see any FLV files or flash files.

This is a Linux/Ubuntu forum.

in windows or in linux you can use the search facility for .flv or .swf if the items are on the machine if you downloaded them.

If you are looking for objects played within your browser they may get purged after a while and not all embedded flash objects are held locally, if they were we wouldnt need plugins such as download helper or unplug to help us download them ;-)

---

### Post by Dustin2128 on 2011-07-08
On linux, perhaps find *.flv.

---

### Post by nec207 on 2011-07-08
> **haqking said:**
>  and not all embedded flash objects are held locally, if they were we wouldnt need plugins such as download helper or unplug to help us download them ;-)
 
What do you mean here.

---

### Post by haqking on 2011-07-08
> **nec207 said:**
> What do you mean here.

I mean that just cause you watch a flash object such as on youtube, the video or flash object isnt automatically saved on your machine, so seacrhing for a .flv wont find one just cause you watched it online.

If you want to keep a flash object or video that you watch online, then use download helper or unplug which are plaugins for firefox allowing you to download embedded media from websites and save them to your local machine

---

### Post by nec207 on 2011-07-08
> **haqking said:**
> I mean that just cause you watch a flash object such as on youtube, the video or flash object isnt automatically saved on your machine, so seacrhing for a .flv wont find one just cause you watched it online.
 
 
What it is stored in RAM ? Or hidden file ?

---

### Post by haqking on 2011-07-08
> **nec207 said:**
> What it is stored in RAM ? Or hidden file ?

what exaclty do you want to do ?

If you want to find .flv or swf files then search for them with *.flv or *.swf.

Like i said this is not a windows forum it is a linux forum.

If your wanting to find the files cause you have watched something online and now want the file, i suggest watching it again and use an appropriate browser plugin to enable you to download and store the file locally.

Depending on purge settings and the like and the browser in question you may be able to retrieve it from the cache.

---

### Post by An Sanct on 2011-07-08
... Last time I checked, Youtube did not allow downloading of movies. Actually it was against their EULA, so help on that topic cannot be given.

---

### Post by haqking on 2011-07-08
> **An Sanct said:**
> ... Last time I checked, Youtube did not allow downloading of movies. Actually it was against their EULA, so help on that topic cannot be given.

I am helping on how to locate .flv and swf videos.  Using the example that he may have watched one on a site such as youtube or similar.

there are tons of threads on here about the use of download plugins.

I am not condoing the downloading youtube videos, the EULA agreeement is for him to deal with.
I am explaining how the viewing of them works.

he might also be referring to his own videos, if you login to your own youtube account you can download the videos in your account, perhaps he forgot his login account and wants his video back ;-)

---

### Post by nec207 on 2011-07-08
I think what I have hard time to understand is this plugins or unplugins how that works and why you need it.Also understanding flash and why in past it was in the temp folder and not any more with new flash.
 
Is it some flash thing that hides the file?
 
Wy in past with windows 8 I could do it but not windows 7 or windows vista ?

---

### Post by An Sanct on 2011-07-08
Well, I didn't want to be more papist then the pope ;)

But some admins tend to close a threads like this, once some certain downloaders and sites are mentioned...

Here is a solution:
[https://addons.mozilla.org/en-US/firefox/addon/download-flash-and-video/](https://addons.mozilla.org/en-US/firefox/addon/download-flash-and-video/)

Also if you want to pick the file up by hand, go to this location:

```
.mozilla/firefox

In my case, it is: /home/an/.mozilla/firefox/0isnq31q.default/Cache/
```

---

### Post by nec207 on 2011-07-08
This web site tells you how to save youtube videos to your computer  [http://www.ghacks.net/2009/08/10/download-youtube-videos/](http://www.ghacks.net/2009/08/10/download-youtube-videos/)
 
But still does not answer my questions above to haqking.

---

### Post by haqking on 2011-07-08
I would suggest seeking advice in a windows forum as you referring to Windows and this is a linux forum.

The locations of temp folders and cache are different and act differently on Linux based systems so seeing as you are a windows user and referring to a windows platform i suggest you seek advice there.

There are plenty of windows forums available.

Good luck

---

### Post by nec207 on 2011-07-08
> **haqking said:**
> I would suggest seeking advice in a windows forum as you referring to Windows and this is a linux forum.
 
The locations of temp folders and cache are different and act differently on Linux based systems so seeing as you are a windows user and referring to a windows platform i suggest you seek advice there.
 
There are plenty of windows forums available.
 
Good luck
 
Yes but many people here use windows and Linux.

---

### Post by An Sanct on 2011-07-08
> **nec207 said:**
> I think what I have hard time to understand is this plugins or unplugins how that works and why you need it.

Plugins are additions to your browser, making it work in a way, that is not the basic way the browser would work (mostly making it better). The actual download plugin makes it possible to you, to download and access videos, which would be either very hard or impossible.

> **nec207 said:**
> Also understanding flash and why in past it was in the temp folder and not any more with new flash.

It mostly still is in the temp, but Ubuntu is different then Windows, so the temp folder is not in the same place ... I provided you the temp folder location for Firefox in my last post.
 
> **nec207 said:**
>  Is it some flash thing that hides the file?
Flash can not and IMHO never will hide files from you, that would be a major security issue and I guess, they wouldn't want to make that move. But, flash can store data in ram, that is where the videos might be until you stop streaming and close the site, this is just a guess I am making, it could be 100% off
 
> **nec207 said:**
> Wy in past with windows 8 I could do it but not windows 7 or windows vista ?

In the past with Windows 8 ? :) take me with you to the future man! :)

Well, Windows Vista and Windows 7 are actually "*the same*" it quoted, because that was actually what a high ranked Microsoft official once said to me :) Vista = 6.0 and Win7 = 6.1 .... go figure :)

---

### Post by haqking on 2011-07-08
the locations for where the flash files are stored have been mentioned for both linux and windows now as it depends on the browser.

in firefox you can in the address bar type:

about:cache

then choose list cache entries and then search for all that end in .flv or.swf.

---

### Post by nec207 on 2011-07-08
Okay in windows 7 and windows vista is this where it is C:\Users\mike\AppData\Local\Microsoft\Windows\ Temporary Internet Files
 
 
Is this where flash files are
C:\Users\mike\AppData\Local\Microsoft\Windows\ Temporary Internet Files
>  
 
Flash can not and IMHO never will hide files from you, that would be a major security issue and I guess, they wouldn't want to make that move. But, flash can store data in ram, that is where the videos might be until you stop streaming and close the site, this is just a guess I am making, it could be 100% off

 
No the flash file is hidden to you to you clear out your cache , **this is what I was trying to say**.
>  
 
In the past with Windows 8 ? :smile: take me with you to the future man! :smile:
 
Well, Windows Vista and Windows 7 are actually "*the same*" it quoted, because that was actually what a high ranked Microsoft official once said to me :smile: Vista = 6.0 and Win7 = 6.1 .... go figure
 
May be do to old OS and old web browsers where easy to do stuff and may be to do over protective copyright of some web sites now is why it making it hard to do stuff with the new OS and new browsers.

---

### Post by haqking on 2011-07-08
> **nec207 said:**
> Okay in windows 7 and windows vista is this where it is C:\Users\mike\AppData\Local\Microsoft\Windows\ Temporary Internet Files
 
 
Is this where flash files are
C:\Users\mike\AppData\Local\Microsoft\Windows\ Temporary Internet Files

 
No the flash file is hidden to you to you clear out your cache , **this is what I was trying to say**.

 
May be do to old OS and old web browsers where easy to do stuff and may be to do over protective copyright of some web sites now is why it making it hard to do stuff with the new OS and new browsers.

if you use internet explorer then yes the files are in the temporary internet files folder as stated.
If it is hidden then show all files.

If it has gone then there aint much you can do about it

---

### Post by nec207 on 2011-07-08
> **haqking said:**
> if you use internet explorer then yes the files are in the temporary internet files folder as stated.
If it is hidden then show all files.
 
If it has gone then there aint much you can do about it
 
 
But what would it be called or what would  I be searching for .
 
And if windows 7 and vista is different than windows 98 where it is or where it stores it or do not store it at all.
 
Also what is a unplugin.

---

### Post by haqking on 2011-07-08
> **nec207 said:**
> But nit sure what it would be called or what I would be searching for .
 
And if windows 7 and vista is different and what is a unplugin.

I have already stated.

.flv files and .swf files...and file ending with those extensions are flash objects.

What the one is you are looking for i am not going to know.

the locations for flash objects for both Firefox and Internet explorer have already been shown and how to find them.

if you cant find them then they may be hidden in which case choose to show all files.

If it is not there it might just be GONE ! it depends how long ago it was viewed etc and if the temporary internet files or cache has been purged.

---

### Post by nec207 on 2011-07-08
Just as a test I clear out my temp folder ( so very llittle is shown to make it easer to find ) and gone to youtube to play some videos and out of the 4 thinks in the temp folder none where FLV file and all file size was in KB nothing in MB.
 
Can some one else try to do this to make sure I'm doing it the proper way.
 
I think with new youtube flash it is different than the old flash they used.

---

