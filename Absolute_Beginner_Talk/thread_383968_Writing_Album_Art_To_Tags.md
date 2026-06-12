---
title: "Writing Album Art To Tags"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Quickdood on 2007-03-13
I recently completely switched from windows to Ubuntu.  So far I am loving it.  One thing I do miss though is Media Monkey which was capable of writing album art to tags so my Mp3 player can display the album art.  So far the programs I found on linux for album art only download the art and do not actually write it to the tag.  I was searching through the forum and found one potentially good program called cowbell, which was suppose to write album art to the actual tag, but it only seems to download the album art to the folder the music is in.

Does anyone know of a program on linux that is easy to use and can actually write album art to the mp3 tag similar to itunes or media monkey?

Thank You!  :)

---

### Post by psynyd on 2007-03-13
I was actually going to ask you to use Cowbell but you seem to be using it already. 

Which music player do you use? Players like Rhythmbox or Amamrok should download album art if the right plug-in is selected. Just activate the cover art plugin under Edit->Plugins in Rhythmbox. I doubt this will tag the art to the song ofcourse, as tagging in Gstreamer is still a limited feature.

And Amarok, the cooler music player (which I do not use myself) , comes with cover manager built-in. Maybe it can do it. But AFAIK, Amarok either has already changed or will soon be changing from xine to Gstreamer.

I didn't really answer your question but anyway atleast i tried! 

psynyd
fellow newbie

---

### Post by Dr. Nick on 2007-03-13
try easytag
[http://easytag.sourceforge.net/](http://easytag.sourceforge.net/)

its installable from the repos via apt-get/aptitude/synaptic.

---

### Post by Quickdood on 2007-03-15
Thanks, I will give easy tag a try

---

### Post by Quickdood on 2007-03-16
easy tag worked, you da man! Thanks!

---

### Post by Quickdood on 2007-03-16
Do you know how to add cover art to a whole album at once, so far it looks like I have to add it one by one to each song.  Thanks!

---

### Post by AndyCooll on 2007-03-16
Highlight the songs you want to add the album art to (if you want every song in a folder, choose "select all files"), select the pictures tab , select the  album art and then place a tick in that box on the right hand side. Then click save.

:cool:

---

### Post by Quickdood on 2007-03-16
> **AndyCooll said:**
> Highlight the songs you want to add the album art to (if you want every song in a folder, choose "select all files"), select the pictures tab , select the  album art and then place a tick in that box on the right hand side. Then click save.

:cool:

Thank you, worked like a charm.  I would have never though of checking that little box, I didnt even know it existed until you pointed it out :)   THANK YOU!!!!!!!!

---

### Post by jnorth on 2007-03-20
> **AndyCooll said:**
> Highlight the songs you want to add the album art to (if you want every song in a folder, choose "select all files"), select the pictures tab , select the  album art and then place a tick in that box on the right hand side. Then click save.

:cool:

Another related question - I have my art saved as "cover.png" in each album folder and can't figure a way to write that to the tag... my collection is around 6000 songs and I really don;t want to manually select each file for each album :)

Amarok doesn't write it to the tags and easytag has no way that I can find to do so.

Thanks

---

### Post by remedy on 2007-03-22
Try Album Cover Art Downloader from [http://kempele.fi/~skyostil/projects/albumart/](http://kempele.fi/~skyostil/projects/albumart/)

It can download album covers from Amazon (and a few other online shops) and stores the pictures in ID3 Tag 2.3 format.  You can tag all your album in one go, if you want. 

There is a *.deb package on the download site - this installs fine on Ubuntu.

If you use Ubuntu 7.04, make sure to add the following magic comment 

#coding:utf-8

in the first line of this file:

/usr/lib/albumart/albumart_pictures.py

in order for Python to interprete the encoding of the file properly, otherwise the file is wrongly interpreted as an ASCII file and a syntax error is thrown when the application launches

Cheers
tom

---

### Post by jnorth on 2007-03-22
> **remedy said:**
> Try Album Cover Art Downloader from [http://kempele.fi/~skyostil/projects/albumart/](http://kempele.fi/~skyostil/projects/albumart/)

It can download album covers from Amazon (and a few other online shops) and stores the pictures in ID3 Tag 2.3 format.  You can tag all your album in one go, if you want. 

...

Cheers
tom

And that is why I love this distro/forum...

That program rocks - does multiple formats as well, so I have my images as png for quality, folder.jpg for my windows carputer, and everything else can read the ID3 tags :)

Thanks!

---

### Post by AndyCooll on 2007-03-22
Sorry so late in replying (not that I would have been able to answer your query anyway), but I'm glad you've found the solution!

:cool:

---

### Post by puppy on 2007-04-01
Hmm, installed it using the /deb file but issuing the command "albumart" says that no such program is installed... ?

---

### Post by jnorth on 2007-04-01
> **puppy said:**
> Hmm, installed it using the /deb file but issuing the command "albumart" says that no such program is installed... ?

it's actually albumart-qt...  try typing album and pressing the tab button to auto-complete in case it's different on your box.

---

### Post by Fraoch on 2007-04-21
remedy: thanks so much, I was wondering why this extremely useful program wasn't running in Feisty!  I was getting encoding errors exactly like you described.  But:

> **remedy said:**
> /usr/lib/albumart/albumart_pictures.py

On my install it's albumart_images.py but your change worked perfectly for that file!

Thanks!

---

### Post by emperor on 2007-05-27
> **Fraoch said:**
> remedy: thanks so much, I was wondering why this extremely useful program wasn't running in Feisty!  I was getting encoding errors exactly like you described.  But:

On my install it's albumart_images.py but your change worked perfectly for that file! Thanks!

Yes, adding  "#coding:utf-8" as first line in "/usr/lib/albumart/albumart_images.py" fixes the problem! 

Thanks, this community is great!

---

### Post by jbernardo on 2007-09-12
Hi, I'm having another problem. I'm running gutsy, and I built the deb from source. Adding "#coding:utf-8" to albumart-1.6.0/lib/albumart/albumart_images.py fixed the first problem, but now I get this:
```
$ albumart-qt
Traceback (most recent call last):
  File "/usr/bin/albumart-qt", line 145, in <module>
    sys.exit(runGui())
  File "/usr/bin/albumart-qt", line 77, in runGui
    import albumart_dialog
  File "/usr/lib/albumart/albumart_dialog.py", line 36, in <module>
    from albumart_dialog_base import AlbumArtDialogBase
ImportError: cannot import name AlbumArtDialogBase
```It seems it can't find one of the files, any idea?

Fixed- I looked at the Makefile in lib/albumart, removed albumart_dialog_base.py, albumart_configuration_dialog_base.py, albumart_about_dialog_base.py, albumart_exception_dialog_base.py and albumart_string_list_widget_base.py, installed pyqt-tools, did a make (inside lib/albumart) and did again the "fakeroot debian/rules binary" to generate the .deb file. Now it works for me. If anyone wants it, I can append the working deb (working for gutsy, haven't tried feisty or earlier) here.

---

### Post by Squiffy on 2007-10-02
Ouuh I'd love a .deb of that thanks! I've been looking (halfheartedly i have to say) for a fix to that problem for the better part of a week. 

It's a shame that this really kick *** program has fallen by the wayside.

---

### Post by jbernardo on 2007-10-03
> **Squiffy said:**
> Ouuh I'd love a .deb of that thanks! I've been looking (halfheartedly i have to say) for a fix to that problem for the better part of a week. 

It's a shame that this really kick *** program has fallen by the wayside.

Ok, here it is. It has a couple of bugs that need fixing, but since it seems abandoned probably never will. It won't download album art for albums with ':' on the name, among other restrictions.

---

### Post by Circus-Killer on 2007-10-03
havent read through the entire thread, so accept my apoligies if someone has suggested the following.

for straight writing tags (including album art) you might want to try *easytag*. its in the repositories.

also, you might want to try use exaile instead of rhythmbox, as it handles album art covers much better. for one, even when you have the correct album art saved on your pc, rhythmbox will still go and fetch the wrong cover. another is the lack of album art collector. the main reason i switched to exaile was because it allows for much more than rhythmbox.

but as said, easytag is the way to go if you want a program thats serious about tagging. i've been using it for almost a year now and will probably still continue to use it for a very long time. :guitar:

---

### Post by jbernardo on 2007-10-03
Being a kde user, I use amarok/kid3 - and never could understand why easytag always wants to write to my mp3 files even if I haven't changed anything. So I gave up on it. 
Having said that, I use albumart to add covers to mp3 directories in a format that my mp3 player (Meizu M6) understands. Haven't found yet a way in amarok to copy the cover art as I like it to mp3 devices.

---

### Post by gubemton on 2007-10-03
Yeah, Easytag is agressive about upgrading any tags it sees to it's id3 version.  It seems to mark my mp3s for rewriting about half the time.

---

### Post by FreddyV on 2007-11-24
> **jbernardo said:**
> Ok, here it is. It has a couple of bugs that need fixing, but since it seems abandoned probably never will. It won't download album art for albums with ':' on the name, among other restrictions.

Works like a charm... may thanks !

---

### Post by mojohn on 2008-01-06
Hi. Most of my music is in ogg format. Even though I have album art in the folder for each album, I can't get EasyTag to recognize the art. Whether I select all the songs in the album or not, I get no option to add the art when I press the Pictures tab.  

I'm running EasyTag 2.1 on Feisty.

Any ideas how to make EasyTag recognize album art for ogg-encoded albums?

Thanks, Mojohn

---

### Post by kcy29581 on 2008-01-07
> **mojohn said:**
> Hi. Most of my music is in ogg format. Even though I have album art in the folder for each album, I can't get EasyTag to recognize the art. Whether I select all the songs in the album or not, I get no option to add the art when I press the Pictures tab.  

I'm running EasyTag 2.1 on Feisty.

Any ideas how to make EasyTag recognize album art for ogg-encoded albums?

Thanks, Mojohn

I have been searching for this as well, but I don't think this is possible... Nothing on Ogg Vorbis' official site or anywhere else I've searched. I hope that someone can correct me,

---

