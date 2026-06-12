---
title: "[SOLVED] My .wmv! The Ubuntu Restricted Extras, they do nothing!"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by keyboardashtray on 2007-07-10
Forgive me - I realize that restricted formats are possibly the most discussed (disgust?) topic here and everywhere. It perhaps is that inundation of information that leaves me hopelessly confused. There are too many ways to do the same thing, and clearly some are ending in major headaches for some people, I see people talking about having configured/modified this or that some time ago and now they have major problems. 

I simply wanted to be able to play .wmv files on Totem when the need arose, and after scanning (too) much (too) varied information on the subject, the simplest solution seemed to be adding "Ubuntu Restricted Extras" from the Add/Remove list.

Well, I added it, and when I tried to watch the same video, the same message came up offering to search for restricted codecs. I didn't go through that because somewhere I read somebody having problems with Firefox because they were installing things as plugins there instead of through the Package Managers like every good boy should. And if I installed the "Ubuntu Restricted Extras", why do I need extra things? It seems to be the default package for restricted formats, so you'd think it would work with Totem, the default media player. I have a feeling that there will be some other way I end up getting these codecs...but then why does Ubuntu Restricted Extras exist? So should I just get rid of Ubuntu Restricted Extras?

If I sound like I'm harshin' Ubuntu keep in mind this is all tongue-in-cheek - for the most part I'm having a great experience with it. It just seems like for even the simplest task there are two ways to do it: the easy way, and the right way.

Edit: Thanks everyone for all the help and suggestions! I went ahead and just stuck with the extra codecs offered/recommended by Totem as a plugin as I tried to play the .wmv file. I kept the Ubuntu Restricted Extras on for now, but I might experiment with taking it off since this plugin seemed to resolve the .wmv issue. A couple folks mentioned VLC and so did someone on chat, but I kind of like the look and feel of these default applications and I think I'll stick with Totem, but its good to know a popular alternative if I need it. I guess choice *is* a good thing. 

I consider the issue resolved.
Thank you :)

---

### Post by Outrunner on 2007-07-10
I used this to play my .wmv files
```

sudo apt-get install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
```

Also, you might find that it's a good thing to have more than one way to do something. If option one doesn't work, you can try option two.

---

### Post by keyboardashtray on 2007-07-10
> **Outrunner said:**
> I used this to play my .wmv files
```

sudo apt-get install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
```

Also, you might find that it's a good thing to have more than one way to do something. If option one doesn't work, you can try option two.

Thanks, I might give that a try - but isn't that command essentially just the console version to get and install the same package I got with Add/Remove? 

And you're probably right, there's more than one way to skin a rabbit, but if one option doesn't work, is it really an option? Just for example, if I'm right (and I'm probably not) that that is just the console command to download and install the same thing I used Add/Remove for, even if it works then doesn't that mean the Add/Remove way was pointless? I hope I'm not coming across as argumentative - I just want to get a better feel for when I should use the graphic interface vs. the console.

Thanks again, I think I'll remove the one I got and give it a shot that way.

---

### Post by Outrunner on 2007-07-10
I think Ubuntu Restricted Extras only installs... well, ubuntu-restricted-extras. That might not be enough to play .wmvs.

---

### Post by nite owl on 2007-07-10
The tutorial at the top of this page about how to enable multimedia worked perfectly for me and it was straight forward and simple

---

### Post by AlexenderReez on 2007-07-10
how about add few sofware list from medibuntu.com ...it has few extra multimedia codes that ubuntu repo doesn't provide ...

---

### Post by mytwobears on 2007-07-10
Yes, the medibuntu repos. installs the win32codecs, also it might be a good idea to install VLC media player as an alternative player to Totem.  VLC tends to play most formats video and audio and you don't have to worry so much about codecs.

---

### Post by scheuri on 2007-07-10
Try:

[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)
[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

loads of information and manuals there....usually that is absolutely sufficient. There is no need to install more or from other sources.

Greetings
Scheuri

---

### Post by keyboardashtray on 2007-07-10
Well [https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/) is the original one I went to, and followed that one, for Feisty. It says the Ubuntu Restricted Extras will enable .wmv , but I guess it just didn't work in my case.

I just broke down and installed the plug-in for totem that I mentioned before: Plugin of GStreamer ffmpeg video plugin
Codecs to play mpeg, divx, mpeg4, ac3, wmv and asf files

It worked well enough I guess, the video was wavy and had trails. I don't plan on watching a ton of .wmv files anyway, I suppose. I'm trying to get everything I have on .ogg, I just like having access just in case.

Thanks everyone for all the help :)

---

### Post by davidjmayo on 2007-07-10
I play .wmv with VLC -no codec problems so far. Everything plays correctly (speed, sound)

I used VLC on W2K before as well, as I found it very reliable to play .wmv ( the "default player" often used to be unable to find codecs for it's own format)

---

### Post by AndyCooll on 2007-07-10
Totem plays wmv files quite happily, no need for VLC. Ignore those who are leading you down that path (unless you are wanting to consider alternative movie players ...but that's for another thread).

Your problem is to do with the codecs that have been installed. To play wmv files you need the w32codecs as has been mentioned above.

:cool:

---

### Post by beefcurry on 2007-07-10
Try m-player its the only player which works everytime with every wmv I try, and it can play most of the wmv codecs natively.

---

### Post by davidjmayo on 2007-07-10
> Totem plays wmv files quite happily, no need for VLC. *Ignore those who are leading you down that path *(unless you are wanting to consider alternative movie players ...but that's for another thread).

Your problem is to do with the codecs that have been installed. To play wmv files you need the w32codecs as has been mentioned above.

Andy, I just read the post again. OP wants to play in Totem. I only suggested another way, Not to say any media player is better than another. The beauty of ubuntu is you have lots of different choices.

---

