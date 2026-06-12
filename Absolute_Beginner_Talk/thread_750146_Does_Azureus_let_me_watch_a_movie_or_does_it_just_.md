---
title: "Does Azureus let me watch a movie or does it just use me for uploads?"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by MeTylerDurden on 2008-04-09
I try and watch  and it will not work ,  seems I have downloaded then they just start uploading to peers..   Seems alot of people have this problem and no answer , I searched the internet for an hour and there is nothing on watching a movie so i figured it was drag and drop .. that didnt work just get an error...   my god

The Liberator who destroyed my property has realigned my perception

---

### Post by SOULRiDER on 2008-04-09
Azureus is not for watching movies, use Totem which comes installed by default in Ubuntu, Dont forget to install codecs: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by MeTylerDurden on 2008-04-09
I have restricted formats allready installed  ,   and i have vlc player , mplayer , and totem.   Funny there is no info on actually what to do after you download.   Seems to start uploading perfectly to others  all automatically ...  :popcorn:  

The Liberator who destroyed my property has realigned my perception

---

### Post by gandaran on 2008-04-09
> **MeTylerDurden said:**
> I have restricted formats allready installed  ,   and i have vlc player , mplayer , and totem.   Funny there is no info on actually what to do after you download.   Seems to start uploading perfectly to others  all automatically ...  :popcorn:  

The Liberator who destroyed my property has realigned my perception

after downloading you just play the file with your favorite media player, do you have access to the downloaded file? do you know where it is?

if you have not set-up a download folder for azureus, all downloaded files go to the hidden home .azureus folder

---

### Post by Tews on 2008-04-09
All Azureus does is download and or seed the file.  99% of the movies are downloaded in 
.avi file format.  Most media players will recognize and play the movie just fine!!  You might have to install a codec like gstreamer but thats it,,

---

### Post by MeTylerDurden on 2008-04-09
I am able to play two of the three  with vlc player.  would like to store info on a cd - going to work for that.?  :popcorn:

 The Liberator who destroyed my property has realigned my perception

---

### Post by skroops on 2008-04-09
If your downloading movies from bittorrent they are probably in some form of divx (or maybe h.264).  You can't just burn them to DVD because they're in a different format.  Take a look at this thread [http://ubuntuforums.org/showthread.php?t=31190](http://ubuntuforums.org/showthread.php?t=31190) for help burning to DVD.

---

### Post by sifon187 on 2008-04-09
> **MeTylerDurden said:**
> I am able to play two of the three movies with vlc player.   Then I tried to burn movie to cd by going to places -cd/dvd creator and that only plays on pc  not on either of my dvd players  .  would like to burn to watch on tv .    Is a cd  going to work for that.?  :popcorn:

 The Liberator who destroyed my property has realigned my perception

General Info for newbs to Torrenting Movies
I've been torrenting for a few years now...but new to linux. Torrenting movies is the same on both sides of the OS. Most movies you find on Torrent sites are compressed with codecs: for example Divx(most common), Xvid, so on, which allows a high quality with smaller file size. To find out what kind of Codec the movie is compressed with is to check the Torrent Tag. Most Torrenters will add what Codec the movie is compressed with in the tag.
VLC player has all these codecs so you can play them on your computer. If it will not play, well it may be a fake. 

Now to put a Divx movie on a dvd you need one of the follow: A DVD Player that will play DIVX coded movies. They are more common now. If you are not sure if your DVD player plays DIVX movies. Check the front and there should be a sticker there if it supports DIVX. Second option: You need a program to uncompress the movie from the DIVX format, then burn it to DVD.  Right now I do not have any programs for Linux. I have a bunch for Windows though, Im sure another user can help with a program.

---

### Post by MeTylerDurden on 2008-04-09
to buy a dvd player that plays divx sounds like your just payiing for a short term fix until they use a different compress and make you buy a different dvd player (lovely world )



The Liberator who destroyed my property has realigned my perception

---

### Post by sifon187 on 2008-04-09
I doubt DIVX is going anywhere soon. DIVX is not something you have to buy...its free and open source. In a sense it is like Linux. DVD players with DIVX are not just stand alone DIVX players. THey are just DVD players with the abality to decode the video. To save money, use a program to convert the DIVX video to DVD. Ill look one up for you.

---

### Post by jseiser on 2008-04-09
I would not even bother converting a Divx, into a native dvd format, you will lose Quality.  That Divx, hopefully came from a (legal) DVD copy that was compressed to save space, you will then reencode it, taking something that has less than perfect quality, and making it worse.  Then the fact your TV is probably larger then your monitor, you will REALLY see the compression problems.  Your best bet is to, watch the divx on your PC, watch it on a compatible DVD player, or, download legal  iso images of DVDS you own.


edit: as a side not - ig you hav an xbox or anything, just stream the movie

---

### Post by Tews on 2008-04-09
Try DeeVdee .. it will convert to DVD file structure and then you can burn it to a DVD disk.  I've also heard that ConvertXtoDVD will work through Wine too, though I haven't tried it yet...

---

### Post by billgoldberg on 2008-04-09
Azureus is a torrent client.

It downloads (and seeds) torrents.

If you started azureus for the first time, you had to specify a folder where the files went (you can change that afterwards). I don't know the standard folder, I use /home/username/Videos.

Your best bet to watch almost all videos is installing vlc media player **from the meditbuntu repo**.

The vlc media player in the normal repo's doesn't come with all the functions!

Completely remove it using synaptic package manager and follow [this how-to]("http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/") to add the medibuntu repo and installing vlc.

If you have problems with some files playing properly in vlc, go [here]("http://linuxowns.wordpress.com/2008/03/18/messed-up-picture-with-vlc/").

You will come across torrent files that come in the form of multiple rar archives.

Download "p7zip-full" using synaptic package manager and then right-click the first one of those rar files and press "extract here", the video will appear after it's done unrarring the file.

I hope this will help you.

About the burning:

Buying a dvd player that also plays .divx files can be usefull but not all video files come in .divx. You can use mandvd or devede to convert them to dvd format and use K3b to burn the dvd.

Or you could just download .iso files of dvd's instead of .avi or .divx files. I think you just burn that image to dvd and it will play in any dvd player.

Some dvd players will play video files from cd. You'll need to convert the video file to svcd format (super video cd) or vcd (video cd). I've read that devede can do this.

---

