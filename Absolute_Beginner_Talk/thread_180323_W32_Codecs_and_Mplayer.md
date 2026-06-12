---
title: "W32 Codecs and Mplayer"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by Kordesh on 2006-05-22
A number of things here. 

A: I have codecs from the Mplayer site loaded into /usr/lib/win32, but getting nothing from that.

B: I installed Mplayer, and can execute it from right clicking and choosing to play with it, but I can't actually find the file so I can put it in a menu.

C: I can't get Mplayer or Totem to see the codecs.

The fun part? I'm running AMD64 and Dapper. I've been all over the place but I can't find anything that is compatible and that can solve this /=.

---

### Post by Sef on 2006-05-22
Have you checked out restricted formatsin the Ubuntu wiki?

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by Kordesh on 2006-05-22
Just did, however, didn't help much /=. VLC runs the audio, as does Mplayer, but I have a feeling the video I'm testing this one is wmv9 *as most are nowdays*. I read something about getting the 32bit Mplayer and using that since it apparently can access wmv9. However, I already have this one, which I assume is 64bit, and I don't quite know how to remove it. (EDIT: Removed it)

Also, I have the link to the post where someone packaged the 32bit Mplayer for the AMD64, but it fails to complete /=.

MPGs seem to work, but the one I tested it with stalls half way through the vid at the same point every time in VLC.

---

### Post by joshrobinson on 2006-05-22
did you put the codec's into the folder before you compiled the source?

---

### Post by Kordesh on 2006-05-22
Well, see, here's the thing. There's two different locations I keep seeing to have the codecs. /etc/lib/win32 and etc/local/lib/codecs. One seems to be the old place they should have been, one seems to be the new. I have no idea which should be which. As for compiling it from source, that's why I can't get it installed. I don't know how to compile the binary for the 32bit version from source to get it onto the AMD64 version /=. Unfortunately, their readme for compiling it consists of "Ok, type "make", K it's magically done!" I need to get more details on how to compile it somewhere. I'm going to rummage around and try to find out more tonight perhaps. I need to find a dev package because as of now, "make" isn't even a recognized command. I just forget which one I installed last time.

It's this kinda stuff that keeps me from switching entirely to linux, the inability to do simple stuff.  I don't mind configuring it and learning it, but when I just flat out can't do it because of the version or whatever I'm using -_-. And the thing that annoys me most is, it's not the fault of the linux devs, it's because MS screws linux at every turn by locking up sources, and purposefully making things difficult, and it's only going to get worse with Vista :evil:

---

### Post by Kordesh on 2006-05-22
Actually don't worry about it. I've pretty much decided I'm only going to keep linux as something to play around with. While I love the OS, MS has seen to it that it's totally useless in reguards to what I need from a system. I'm a big PC gamer and do alot with audio and multimedia, alll of which MS has pretty much put a stranglehold on. With the release of Vista that hold is only going to get tighter with all the developers bending to their will. The bottom line is, I'm going to end up leaving linux in as a tinker toy until i finally need the space on my drive and get rid of it, and continue my deep seething loathing of microsoft.

---

### Post by shom on 2006-05-22
so sad. but it is the result of the confusion around the support of wav9 in amd64. there are people who claim that it works, but too many others can't see the funny stuff in the internet.

---

### Post by Kordesh on 2006-05-22
Oh I wouldn't be surprised if it worked, and I would consider redownloading everything etc and getting the 32bit just for compatabilitys sake, but the issue is getting the codecs to work at all and the gaming issue. As it is, I don't have a reason to boot into linux unless I plan on not playing anything for a good few hours, which is rarely the case. As far as I am aware, I would be having the same issue getting all this stuff together in the 32bit version as well /=

---

### Post by kilahchris on 2007-08-04
> Actually don't worry about it. I've pretty much decided I'm only going to keep linux as something to play around with. While I love the OS, MS has seen to it that it's totally useless in reguards to what I need from a system. I'm a big PC gamer and do alot with audio and multimedia, alll of which MS has pretty much put a stranglehold on. With the release of Vista that hold is only going to get tighter with all the developers bending to their will. The bottom line is, I'm going to end up leaving linux in as a tinker toy until i finally need the space on my drive and get rid of it, and continue my deep seething loathing of microsoft.



I understand your frustration...
But dont give up.... I have had similar issues as well.

For now i think you should download the 32 bit version of Ubuntu instead of 4bit  W32 codes are known to work. 

as for multimedia, im not sure what it is you do within Windows. 
Me personally i do alot of video encoding and dvd authoring. Linux has some great tools for this such as avidemux, dvdauthor, transcode etc. 

The issues you have strictly related to the lack of a 64bit W32 codec pack. This will change soon.  I suspect you probably dont have some of the basic codecs installed like ffmpeg


As for playing games written for win32 Cedega applicaton has been reported to have good compatibility with launching and running games stably for a small  5$ fee per month


I run Ubuntu Edgy, and there is nothing multimedia related that can be accomplished with Windows XP and not here.  Just a little bit of patience and research and Ubuntu can become a pleasant alternative to Windows.

---

