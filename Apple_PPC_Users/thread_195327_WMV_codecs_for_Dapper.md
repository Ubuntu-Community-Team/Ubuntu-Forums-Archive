---
title: "WMV codecs for Dapper"
date: 2006-06-12
forum: Apple PPC Users
---

### Post by dmoore7 on 2006-06-12
Is it possible to view .wmv files with dapper on a ibook G3, whenever I launch a wmv file i get an error saying that I am missing codecs, I installed the codec packages from Automatix, but they don't seem to support wmv files.

---

### Post by Turtle.net on 2006-06-12
You should verify your repository list (follow the link in my signature) and install w32codec (if i remember well).
Automatix is easy ... but if something goes wrong you will never know why...

---

### Post by Tsai Dung-Bang on 2006-06-13
ha, there is no w32 codec in PPC, because they are i386 binary.

You should take a look at [http://ubuntuforums.org/showthread.php?t=140565&highlight=wmv+ppc]("http://ubuntuforums.org/showthread.php?t=140565&highlight=wmv+ppc")

With patching the mplayer, you could play wmv with mplayer

[QUOTE=Turtle.net]You should verify your repository list (follow the link in my signature) and install w32codec (if i remember well).
Automatix is easy ... but if something goes wrong you will never know why...[/QUOTE]

---

### Post by dmoore7 on 2006-06-13
[QUOTE=Turtle.net]You should verify your repository list (follow the link in my signature) and install w32codec (if i remember well).
Automatix is easy ... but if something goes wrong you will never know why...[/QUOTE]


Thanks, will this really allow me to install the wmv codecs on an ibook?

---

### Post by dmoore7 on 2006-06-13
[QUOTE=Tsai Dung-Bang]ha, there is no w32 codec in PPC, because they are i386 binary.

You should take a look at [http://ubuntuforums.org/showthread.php?t=140565&highlight=wmv+ppc]("http://ubuntuforums.org/showthread.php?t=140565&highlight=wmv+ppc")

With patching the mplayer, you could play wmv with mplayer[/QUOTE]


I tried patching the mplayer, and everything seemed to work fine, but when I went to open the wmv file it still failed to launch.

---

### Post by robbyt on 2006-06-15
honestly dmoore- i think you might be a bit hosed. It's pure magic that WMV works in x86... getting WMV running today under PPC might be asking too much ;)

perhaps send microsoft an email and suggest they release a libwmv for linux? :D

---

### Post by dmoore7 on 2006-06-15
[QUOTE=robbyt]honestly dmoore- i think you might be a bit hosed. It's pure magic that WMV works in x86... getting WMV running today under PPC might be asking too much ;)

perhaps send microsoft an email and suggest they release a libwmv for linux? :D[/QUOTE]

Thanks, I think what I should do is send microsoft an e-mail and tell them how much they suck. It's ridiculous that they want to keep control of something as little as a codec, as if they opened that up they would lose money.

---

### Post by Ptero-4 on 2006-06-16
I would send microsoft an email, with a really nasty, unknown computer virus in it.

---

### Post by cgreen on 2006-06-22
Turtle, that's really helpful, thanks. I'm in the process of migrating from n00b to <alledgely>"I-know-what-i'm doing"</alledgely> - and one thing I have never understood is how some people know which repos are the best. If you would care to shed any light on this I would be grateful.

---

### Post by Turtle.net on 2006-06-22
[quote=cgreen]Turtle, that's really helpful, thanks. I'm in the process of migrating from n00b to <alledgely>"I-know-what-i'm doing"</alledgely> - and one thing I have never understood is how some people know which repos are the best. If you would care to shed any light on this I would be grateful.[/quote]

I'm happy you beginned this journey ... but trust me that could be long (i'm still at the beggining)
To answer your question, it is difficult to know for sure which repo is good and which one include to much unstable packages. I just try to avoid installing too advanced software compare to the one considered stable for ubuntu (for instance i considered as a bad idea to install firefox 1.5 under breezy ... even if plenty of people have installed it).

Hope this help.

---

### Post by digs on 2006-06-23
mplayer/vlc plays WMV2 fine. WMV3 won't play however. Check the file properties to see which one it is.

---

### Post by Ububurns on 2006-08-07
Seems nobody has got around to compiling ffmpeg on PPC with wmv3 decoding ability - except for me...

If you would like it, I guess I can email it to you (it may be illegal to host it online) as it's only a 3MB executable.  Let me know if you would like it!

It's not particularly fast, but you can use it to convert your wmv3 files to avi or mpeg or whatever, for playback.

---

### Post by stoeptegel on 2006-08-07
Seriously, try to stay away from wmv, it's not only a proprietary codec it's also a nasty codec. Do vorbis, theora or lame and ffmpeg when possible.

---

### Post by Ububurns on 2006-08-07
Yes, I do understand that. But what I was talking about is converting wmv3 **into ** avi or mpeg - not the other way around.

For some there is no choice.  Some digital cameras can only make wmv3 videos.  Those users would surely want to be able to at least convert them to a different format so that they can watch them!

That is the purpose of compiling ffmpeg with wmv3 support.

---

