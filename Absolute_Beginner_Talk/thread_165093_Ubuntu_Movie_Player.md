---
title: "Ubuntu Movie Player"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by Sonic132 on 2006-04-23
OK,
I got Ubuntu up and running again on the Hoary version. Now I cant seem to get Totem to play avi files.
I'm not sure whether or not it might be a codec problem or not. But I've never been able to get Totem to play anything before.
I've tried again and again to get the xine movie player to work but I dont see how to install it.
I see it listed as installed under Synaptic, but I dont see an app anywhere under any of the Ubuntu menus.

What am I doing wrong, and is there an easier app than xine out there?

---

### Post by Sonic132 on 2006-04-24
Any suggestions that the gurus could offer would be most appreciated.

---

### Post by Sonic132 on 2006-04-24
**bump**

---

### Post by Qrk on 2006-04-24
Xine is a media player backend. To get an interface for it, install either *totem-xine*, which will make totem use the xine backend, or *gxine*, which is a graphical interface for xine.

I'd recommend installing totem-xine.

```
sudo apt-get install totem-xine
```

If you do this, totem becomes just a xine frontend. By default totem uses a gstreamer backend, but gstreamer doesn't support as many filetypes. 

If you would rather use *gxine* it will work just as well. Lauch it by <alt><F2> and typing gxine in the box.

---

### Post by Nikusan on 2006-04-24
[QUOTE=Sonic132]Any suggestions that the gurus could offer would be most appreciated.[/QUOTE]

You probably need to install the codecs to support avi. Look at the [RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats") page for tips.

---

### Post by Sonic132 on 2006-04-24
> Xine is a media player backend. To get an interface for it, install either totem-xine, which will make totem use the xine backend, or gxine, which is a graphical interface for xine.

I'd recommend installing totem-xine.

Code:

sudo apt-get install totem-xine


If you do this, totem becomes just a xine frontend. By default totem uses a gstreamer backend, but gstreamer doesn't support as many filetypes.

If you would rather use gxine it will work just as well. Lauch it by <alt><F2> and typing gxine in the box.

Thanks Alot Man!

---

### Post by Sonic132 on 2006-04-24
I chose to 'sudo apt-get install totem-xine'.
But I was just wondering...
If this crashes my video player. Is there anyway to go back to just totem without a complete reinstall?

---

### Post by Qrk on 2006-04-24
Yes,  Just do

```
sudo apt-get install totem-gstreamer
```

---

### Post by 3rdalbum on 2006-04-24
[QUOTE=Sonic132]I chose to 'sudo apt-get install totem-xine'.
But I was just wondering...
If this crashes my video player. Is there anyway to go back to just totem without a complete reinstall?[/QUOTE]

Xine won't crash Totem... well, not any more than gstreamer does :p ;) 

You might also want to consider doing:
```

sudo apt-get install mplayer
```

It's a more popular Linux video player, and for good reason.

---

