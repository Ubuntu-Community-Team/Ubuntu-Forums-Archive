---
title: "Creating mp3 files in Ubuntu - Best Method?"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by mramsey on 2007-10-25
OK - I have all of my music ripped to my file server. When I originally did this I was a M$ Windoze user (big sigh):-#, and when I made the files I used the .wma file extention recording in a medium quality. Now what I want to do is re-rip all of this into an mp3 format of the highest quality (space is not an issue).

I have not ripped any music in ubuntu, I have installed Amarok, along with the default sets of media players etc. What is the best for ripping music? Interested in everyones opinions here:).

Thanks

---

### Post by shae on 2007-10-25
If space is not an issue and you are looking for real quality, perhaps you should try lossless ogg (FLAC).  It is just a compressed format so you loose absolutely no song data.  Then if you would like a mp3 of any quality later on for some other thing, you can save it as such.

[http://en.wikipedia.org/wiki/FLAC](http://en.wikipedia.org/wiki/FLAC)

---

### Post by DutyDuty on 2007-10-25
Use LAME: [http://lame.sourceforge.net/index.php](http://lame.sourceforge.net/index.php)

It converts the basic CD file to mp3. I think that's what you need.

---

### Post by n3tfury on 2007-10-25
> **shae said:**
> If space is not an issue and you are looking for real quality, perhaps you should try lossless ogg (FLAC).  It is just a compressed format so you loose absolutely no song data.  Then if you would like a mp3 of any quality later on for some other thing, you can save it as such.

[http://en.wikipedia.org/wiki/FLAC](http://en.wikipedia.org/wiki/FLAC)

his original post said he's got it already ripped to his file server.  so it's already lossless.

OP, try using [[COLOR="SandyBrown"]rubyripper[/COLOR]]("http://wiki.hydrogenaudio.org/index.php?title=Rubyripper") and compress to the algorithm of your choice.  are you wanting to rip to mp3 because that's what your portable device supports?  if it supports ogg, i suggest using it instead.  of course there are a multitude of variables to go along with it, but it'll give you a start.  

cruise hydrogenaudio.org if you want finer details on ripping/encoding

---

### Post by julian67 on 2007-10-25
> **mramsey said:**
> OK - I have all of my music ripped to my file server. When I originally did this I was a M$ Windoze user (big sigh):-#, and when I made the files I used the .wma file extention recording in a medium quality. Now what I want to do is re-rip all of this into an mp3 format of the highest quality (space is not an issue).

I have not ripped any music in ubuntu, I have installed Amarok, along with the default sets of media players etc. What is the best for ripping music? Interested in everyones opinions here:).

Thanks

If I understand you correctly you want to convert your wma files into mp3? Unfortunately this is not such a good idea. You will lose significantly in terms of sound quality because you are taking a compressed file and compressing it again. Compressing using mp3 or wma (or ogg or musepack etc) means *losing *data. mp3 and wma and other lossy formats rely on psycho acoustics, that is they try to lose the data that has no or little effect on listening. Each codec will use a slightly different psycho acoustic model so if you compress twice, particularly using 2 different methods, you'll end up with some obviously low quality sounds. 

If you want to go ahead and do this anyway the easiest way is to get yourself [lossless2lossy]("http://lossless2lossy.sourceforge.net/") which > is a conversion script for mass converting your ENTIRE music collection from one format to another whilst mirroring the directory structure and tags of the original format. It differs from most other conversion scripts because it is able to convert multiple files from multiple directories recursively.

You can use it to convert from lossless (flac) to lossy (mp3) or recompress you lossless collection to another lossless format. 

If you run Kubuntu there is a nice tool called [audiokonverter]("http://www.kde-apps.org/content/show.php?content=12608") which integrates into Konqueror and Krusader and lets you do this from the file manager's context menu. 

If you can listen to your WMA files within Ubuntu (and you can) then I would leave them as they are. If you need them to be in a different format then it's better to start over and rip again from the CDs, this time perhaps choosing FLAC (lossless) and/or Ogg. Ogg is nice because it gives small file size with high quality and being an open standard you can be completely confident of being able to play it back in any OS now or in the future. If you need mp3, perhaps for a portable device, then the easiest ripper/encoder for this is probably [Asunder]("http://littlesvr.ca/asunder/"). If you want to rip from CD to Ogg and/or Flac then Sound Juicer, which comes with Ubuntu, is ideal.

edit: important correction: lossless2lossy does not support wma, sorry! audiokonverter does though, and if you have Amarok installed you probably already have the necessary kde libraries installed to install this along with Konqueror or Krusader.

---

### Post by n3tfury on 2007-10-25
> **julian67 said:**
> If I understand you correctly you want to convert your wma files into mp3? Unfortunately this is not such a good idea. You will lose significantly in terms of sound quality because you are taking a compressed file and compressing it again. Compressing using mp3 or wma (or ogg or musepack etc) means *losing *data. mp3 and wma and other lossy formats rely on psycho acoustics, that is they try to lose the data that has no or little effect on listening. Each codec will use a slightly different psycho acoustic model so if you compress twice, particularly using 2 different methods, you'll end up with some obviously low quality sounds. 

If you want to go ahead and do this anyway the easiest way is to get yourself [lossless2lossy]("http://lossless2lossy.sourceforge.net/") which  


agreed, if that's what he has (.wma).  i would re-rip your entire collection if that were the case.  transcoding from lossy to lossy will degrade sound quality quite a bit.

---

### Post by shae on 2007-10-25
Oops, when he said "rerip all of this" I thought he meant rerip his audio library.  I agree converting between lossy formats is extremely bad in terms of quality.  You should slowly rerip them I think.

---

### Post by mramsey on 2007-10-25
Sorry if I was a little confusing in my post.  I want to re- rip everything. I will delete what I have mainly because it is .wma and the quality is not there.:)

I want to stay compatable with windose media player cause the wife will not let me convert her yet. Is there a codec for windows media to play ogg?

---

### Post by n3tfury on 2007-10-25
[http://windowsxp.mvps.org/ogg.htm](http://windowsxp.mvps.org/ogg.htm)  

or just use another player in windows - the new winamp is phenomenal.

---

### Post by julian67 on 2007-10-25
> **mramsey said:**
> Sorry if I was a little confusing in my post.  I want to re- rip everything. I will delete what I have mainly because it is .wma and the quality is not there.:)

Good decision! :-)

> **mramsey said:**
> 
I want to stay compatable with windose media player cause the wife will not let me convert her yet. Is there a codec for windows media to play ogg?

I know how important it is to keep the other half happy.....a quick google shows you should have no trouble installing ogg or flac support for Windows and WMP. 

[http://www.google.com/search?hl=en&q=play+ogg+flac+Windows+Media+Player&btnG=Search]("http://www.google.com/search?hl=en&q=play+ogg+flac+Windows+Media+Player&btnG=Search")

---

### Post by n3tfury on 2007-10-25
note that i've not used the above method or this method:

[http://www.illiminable.com/ogg/](http://www.illiminable.com/ogg/)

i use .flac throughout and nero aac for portables, sorry.

---

### Post by mramsey on 2007-10-25
Thanks for all of the responses. I will do some testing on windose mp for ogg. Then if I need mp3's for portables I will convert as needed. Once this is done I will focus my efforts on a media center for the family room! ;)

---

### Post by nynoah on 2007-10-25
I would download K3b from synaptic.  It is a program that comes with Kubuntu.  Like Amarock, it is a great program.  It is what I use to Rip cds.  The bitrate can be changed on it if you know what you are doing.  I would do a write up on this, but I am not sure where to do that. 

You can get a lot of info about what codes you need to change from this thread.

[http://ubuntuforums.org/showthread.php?t=183125]("http://ubuntuforums.org/showthread.php?t=183125")

I had to go and reconfigure my K3b after I did a clean install of 7.10 on my computer.  I will try to cut and paste the code I used in a bit.  I am doing a rip now to test my bitrate.  But I was setting my bitrate at VBR-0 which is the highest level of variable bitrate.  I am not an expert but I got it to work for me.

Noah

---

### Post by nynoah on 2007-10-25
Ok here is the code line that I have in my MP3 line on K3b

lame -h -V 0 --tt %t --ta %a --tn %n --ty %y --tl %m --ty %y --tc %c - %f

Noah

---

### Post by nynoah on 2007-10-25
Oh incase you have never used K3b download it, open it up.  I can't remember if it comes for the codecs that you need.  I used automatix to download all my codecs.

Ok so insert in a cd......click on the icon around the bottom for **"Further Actions"**

Then rip audio Cd

Click on **"start ripping"** around the top of the list of tracks.  K3b should also import in the file names automatically too.

Go to** "file type"** 

 then scroll to** "LAME Mp3"**  

Then on the right there is the icon for the gear that when you hover over it says** "configure plugin"**

next highlight LAME Mp3 and click edit.

Down below you will see a whole bunch of code line.  just cut and paste this in there.  It will give you the highest level of variable bitrate.

lame -h -V 0 --tt %t --ta %a --tn %n --ty %y --tl %m --ty %y --tc %c - %f

Then hit "ok"

next "apply"

Then "Ok"  again

Then start ripping and have fun.  

If you have not tried Amarock, I personally fell it is the best media player for ubuntu/kubuntu.  I wish Kubuntu would work better, I would just switch over to that. 

hope this helps.........if someone can tell me where I should submit a write up I could do that to help others.

Noah

---

