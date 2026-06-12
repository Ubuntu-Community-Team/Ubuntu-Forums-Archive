---
title: "It is possible to play DRM'd .wma files on linux"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by V-600 on 2007-02-22
I don't know if anybody has already posted this but I just found it out and thought it would be helpful.

If like me you have many protected .wma files (yes i copied all my cd's before realising i could turn it off) on one a computer running Windows and Linux on another and don't want to go through the hassle of re-ripping your cd's (or converting formats, loosing quality) then Windows Media Player 10 becomes your best friend.

It will strip out all the protection from the files and allow linux to play them.

All you have to do is insert a (blank) USB flash drive and use MP10 to sync your files to that. In doing so media player will remove all content protection from the files. All you need to do is make sure you have the w32 codecs on your linux box and all is well and playable.

P.S. The bit that really tickels me is that media player is microsofts own and comes as part of windows

---

### Post by equal on 2007-02-22
Take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=182902&highlight=wma+install]("http://ubuntuforums.org/showthread.php?t=182902&highlight=wma+install")

it should help!

---

### Post by V-600 on 2007-02-22
Thanks. I got a bit lost wading through that thread but i think I got the gist of it.

I had already installed the correct codecs but still got the message

"This file is encrypted and cannot be played." from totem (VLC just made no sound) when I tried to play files I made on windows.

The first post was meant as advice for anybody that had a similar problem. It is the first time I had made a post with advice, rather than a problem so don't think i made myself clear.

---

### Post by Vivix729 on 2007-02-22
Not to sound like an ***, but WMA is truly and AWFUL format.  I do not know how many CDs you have ripped, but I would still get rid of all of those and re-rip them in OGG or APS MP3.  Just my 2 cents.

By the way, equal...COOL BAND.

---

### Post by V-600 on 2007-02-22
If you don't mind me asking. Why is wma awful? (I have bout 50 cd's I would rather not re-rip).

People say that one format is better than another and so on but what do you mean. Ages ago (when running windows) I checked Microsofts website which told me wma was the bees knees (no real suprise there though). I think they had a few samples of mp3 vs wma files to compare.

I was hard pushed to tell any difference in sound quality and hard disk space is not really a problem (I don't mind if one format squashes the file a little more/less than another). I think I understand that there is a matter of principle over the open source nature of ogg's, over closed wma's. However I am not a programmer and do not wish to edit/change the sound files so this is less of a practical problem to me

If I can keep the files I already have then it is easier for me.

P.S. As a matter of fact I have already re-ripped about half of my cd's as ogg files. I only figured out today how to get round the drm from windows.

---

### Post by 0x0065 on 2008-04-30
> **V-600 said:**
> If you don't mind me asking. Why is wma awful? Not at all. > **V-600 said:**
> People say that one format is better than another and so on but what do you mean. Ages ago (when running windows) I checked Microsofts website which told me wma was the bees knees (no real suprise there though). I think they had a few samples of mp3 vs wma files to compare. Yeah, I remember that, back before anyone else could play wma, & before Windows got mp3 support by default... Not all mp3 encoders are created equal. Microsoft (?deliberately?) misconfigured a badly implemented mp3 converter by defualt, and then used better settings on a wma converter they'd implemented to work better... and the results were better on the one they'd made better. Who'da thunk it? If hard disk space isn't a problem, why not use FLAC? (free lossless audio codec) The name pretty much explains what's good about it. It's bigger though...
> **V-600 said:**
>  I think I understand that there is a matter of principle over the open source nature of ogg's, over closed wma's. However I am not a programmer and do not wish to edit/change the sound files so this is less of a practical problem to me
I'm a practical person, not an OSS zellot. If a proprietary format works right now then whatever. It sounds to me like you'll be wanting these files for a while though... ...the main benefit of an open format is that you aren't beholden to Microsoft to allow you to access the media you've bought a licence to use. Any wma playback you get under linux now is probably based on 32 bit windows dlls. You'll find they don't just go vrooom, once you go 64bit (much less some more exotic architecture). What will you do if MS decides they don't want to support the format all your media is in anymore? What if they decide they don't like your choice of OS, & choose to block you from playing your media? That's really what open formats are about for most people. You can discuss the morality of media producers ignoring their obligations under copyright law until you're blue in the face. That's neither here nor there. MS owns enough politicians to make whatever they want to do legal in the USA, the country where their business is incorporated. Failing that, they have the money to take you into a protracted legal battle that would financially bury you long before any settlement even came into view on the horizon.

That only really leaves two question for a practical person:
[LIST=1]
[*]Do you want to control your access to your media library?
[*]Do you want your media in a lossless archival format?
[/LIST]
I'd guess your answers are 1) yes and 2) no.
If you can't tell the difference, then why don't you just convert the remainder of your WMAs to mp3/ogg? However, for future proofing (say when you upgrade your sound system), I recommend flac as an archival format. It means you can then downsample to whatever media format you feel like that week, but keep your backup copy at as close to it's original CD quality as is practicable. If you do this then mp3fs is worth a look. [http://mp3fs.sourceforge.net/](http://mp3fs.sourceforge.net/)

my 2 cents.

thanks to the ubuntu forum for the tip on WMP10.

e

---

