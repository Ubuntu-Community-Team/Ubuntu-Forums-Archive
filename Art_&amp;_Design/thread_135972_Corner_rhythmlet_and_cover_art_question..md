---
title: "Corner rhythmlet and cover art question."
date: 2006-02-25
forum: Art &amp; Design
---

### Post by xmastree on 2006-02-25
Right forum? Music is art, and so is cover art, so here goes... :rolleyes: 

I recently installed Corner Rhythmlet and I'm wondering how it does the cover art thing. It appears to get images from the net, some of which are too big, then it saves them in the same folder as the file and displays the lower left corner of the image.

Like this:
[ATTACH]6417[/ATTACH]
On the left is the desklet, to the right of that is a thumbnail of the actual file to show what it ought to look like.

If I then manually resize the file to a smaller size, next time it will d/l the big one again. Even if I don't, it will still go online and refresh the one it just downloaded, so it can take a while to update even if the file is already there.

Is there a way to train it to look in the directory containing the song before going online to download a new one every time? It seems an awful waste of bandwidth..

On the other hand, it's a useful way of collecting all the covers I **don't** have. Just make a playlist containing one track from each album and let it run all day. :cool:

Once I have them though, it would be nice if they were accessed directly from the disk rather than reloaded from the net every time.

---

### Post by Sutekh on 2006-02-25
Hey xmastree, what version of Rhythmlets are you using?

I am running 0.3i, and I have also been having problems re-sizing the cover art.  It's strange though, because some covers stay re-sized, others don't.

In this pic, I resized both covers to 100x100, but only the one on the left stays resized when a track is played again.

Even more strangely, for some albums I can drag that silverchair one across into the dekslet and it will use that as the cover art, other albums it reverts back to the large online one.  I have no idea what it's trying to do.

Supposedly it should retrieve local cover art, this is from gdesklets.com
[QUOTE=Rhythmlet]Rhythmlet is a gDesklets sensor for Rhythmbox written in Python. It can **retrieve cover images locally** or from Amazon.com, has configurable display strings, playback controls, editable ratings, Audioscrobbler support, and a seek bar.[/QUOTE]I have no idea how it does the retrieving though.

[QUOTE=xmastree]On the other hand, it's a useful way of collecting all the covers I don't have. Just make a playlist containing one track from each album and let it run all day. [/QUOTE]
You're not wrong, it's a very good way to retrieve cover art!  Just wish it worked better.

---

### Post by xmastree on 2006-02-25
0.3g i think.
Anyway, I almost got it working, but it's a little intermittent.
In my example above, the downloaded file is 300x300 and is called **10,000 Maniacs - In My Tribe.jpg**
In other words, artist - album.jpg

I tried resizing it (130x130 seems to be the biggest without cropping) but that didn't work. Some did though, and I noticed they were titled differently.

I renamed my 130x130 to **In My Tribe.jpg** and it worked.
[ATTACH]6440[/ATTACH]
So it seems that if you drop the artist from the filename, it works. \\:D/ 

Special characters don't work though, so I had to do some retagging of my Cafe del Mar collections.

---

### Post by Sutekh on 2006-02-26
[QUOTE=xmastree]
I renamed my 130x130 to **In My Tribe.jpg** and it worked.
[ATTACH]6440[/ATTACH]
So it seems that if you drop the artist from the filename, it works. \\:D/ [/QUOTE]Okay well I'm gonna have to give this a go.  Fingers crossed.
[QUOTE=xmastree]
Special characters don't work though, so I had to do some retagging of my Cafe del Mar collections.[/QUOTE]
Doh!  I'm not looking forward to that then!  Plus I got a whole wad of Mandarin podcasts too do aswell.

---

### Post by xmastree on 2006-02-26
I find Easytag pretty good for tagging multiple files.

As for resizing the covers, I made a simple nautilus script to do that. :cool: 

If you know about nautilus scripts, skip this next bit:-

Otherwise, save this: 
```
#!/bin/sh
for arg 
do
cp "$arg" "130$arg"
mogrify -scale 130x130 "130$arg"
done

```
to a file in ~/.gnome2/nautilus-scripts/ and make it executable.
Install Imagemagick if you haven't already.
Then right click on a jpg, select scripts, find the one you just saved and it will make a copy of the file with the prefix 130. The original is unaltered.
So, **name of file.jpg** will become **130name of file.jpg**. It's up to you to give it an appropriate name.

I also tweaked the desklet code slightly, so that the cover is hard up against the edge of the screen,
[ATTACH]6441[/ATTACH]
then I moved the buttons a little, so the 'previous' button doesn't overlap the artwork.

---

### Post by Sutekh on 2006-02-26
> **xmastree]
So it seems that if you drop the artist from the filename, it works. \\:D/ 
[/QUOTE]
Well its working so far.  Cheers for the tip! :mrgreen: 

[QUOTE=xmastree]I find Easytag pretty good for tagging multiple files.[/QUOTE]
Yeah I love EasyTag.  Perhaps you could offer some advice with tagging multiple files.  All my music files (mainly .oggs :cool: ) are named in this way said:**
> As for resizing the covers, I made a simple nautilus script to do that. :cool: Thanks heaps, that's a helpful little script! =D>

[QUOTE=xmastree]I also tweaked the desklet code slightly, so that the cover is hard up against the edge of the screen,
[ATTACH]6441[/ATTACH]
then I moved the buttons a little, so the 'previous' button doesn't overlap the artwork.[/QUOTE]
Yeah I did a bit of hacking myself :cool: 

Only one thing remains that I don't like.  If any icons should stray near the desklet's 'square of influence' it is hidden in the background. (like in the attached pic, and just how do you get pictures in the body of your posts? :-k )  Just gotta some sort of transparency going.

---

### Post by xmastree on 2006-02-26
Sorry for the delay, connection's been on and off... :-(
> **Sutekh]YAll my music files (mainly .oggs :cool: ) are named in this way said:**
>  
Ah,that's easy. :cool:

First you tag the files from the filenames, using **%a - %b - %n - %t**
Then, once all the tags are in place you go back to the **Tag and Filename Scan** window and select **rename file/directory**. Enter the desired pattern, in your case, **%n - %t** and run it again to rename the files.

You can step through them, and check the result at the top of the window, before saving.

But, there's more. I think you'll like this, I just discovered it.

If you have (as I do) a bunch of files correctly tagged with their respective albums but all in one directory, you can do this: **%b/%n - %t** and it will create a new directory with the name of the album, then put the file in it.
Or even **%a/%b/%n - %t** to put them in: artist/album/01 - track1.mp3
:cool:

> Only one thing remains that I don't like.  If any icons should stray near the desklet's 'square of influence' it is hidden in the background.I don't think there's a way round that. Anything 'transparent' isn't really, it just shows the wallpaper through it, even if there's an icon or open window 'between' them.

[quote]and just how do you get pictures in the body of your posts? :-k After you upload the attachment(s) and close the window, click the arrow on the paper clip above the text area. Select your attachment and it will appear with the correct tags wherever the cursor is. You can move it around from there.

---

### Post by Sutekh on 2006-02-26
> **xmastree]Sorry for the delay, connection's been on and off... :-(
 [/QUOTE]I've been having mild electrical storms here, so I turned off the PC anyway.

[QUOTE=xmastree]
Ah,that's easy. :cool:

First you tag the files from the filenames, using **%a - %b - %n - %t**
Then, once all the tags are in place you go back to the **Tag and Filename Scan** window and select **rename file/directory**. Enter the desired pattern, in your case, **%n - %t** and run it again to rename the files.

You can step through them, and check the result at the top of the window, before saving.
[/QUOTE]
Ah ha!  That was too easy!

[ATTACH]6450[/ATTACH] - This will make sense by the time you read the rest of my post  said:**
> 
But, there's more. I think you'll like this, I just discovered it.

If you have (as I do) a bunch of files correctly tagged with their respective albums but all in one directory, you can do this: **%b/%n - %t** and it will create a new directory with the name of the album, then put the file in it.
Or even **%a/%b/%n - %t** to put them in: artist/album/01 - track1.mp3
:cool:

Yeah you were right, I do like that.  In fact that was my next question!  Cheers that's great, everything will be nicely sorted from now on.

> **xmastree]
I don't think there's a way round that. Anything 'transparent' isn't really, it just shows the wallpaper through it, even if there's an icon or open window 'between' them.
[/QUOTE]
Yeah I figured that may be the answer.  Hopefully one day when composite or whatever matures... [-o< ...
(I don't really know what I'm talking about though  said:**
> 
After you upload the attachment(s) and close the window, click the arrow on the paper clip above the text area. Select your attachment and it will appear with the correct tags wherever the cursor is. You can move it around from there.
As you can see I got that working too :cool: 

Thanks a lot for all the help!  Cover art is looking mighty schmick and all my music is on the way to being nicely stored :D

---

### Post by xmastree on 2006-02-26
[QUOTE=Sutekh]Cheers that's great, everything will be nicely sorted from now on.[/QUOTE]Oh yeah? :rolleyes:

I keep saying that to myself, but the more I look, the worse it looks...

---

### Post by xmastree on 2006-02-27
[QUOTE=Sutekh]Yeah I did a bit of hacking myself :cool: [/QUOTE]If you like hacking it, can you (or anyone else reading this :-)) figure out how to alter the response to clicking on it?

Currently, this bit:
```
<image id="imgCover" anchor="sw" x="0" y="130" uri="gfx/coverDefault.png" on-click="rhythmlet:launchBrowser()" watch="uri=rhythmlet:cover, height=rhythmlet:coverSizeY, width=rhythmlet:coverSizeX" />
```causes the browser to open [this page](http://www.allmusic.com/). I would like it to open rhythmbox itself, as if i had clicked the launcher or the icon in the notification area.

---

