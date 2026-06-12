---
title: "[SOLVED] Firefox Totem Plugin"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2008-01-03
I have the firefox totem plugin, because it works when I launch Firefox as root and plays the ogg file in the browser, but it isn't doing it for firefox as my user.

Is there any way I can fix this ?

Dr Small

---

### Post by PinkFloyd102489 on 2008-01-03
Ive found that the mplayer plugin works a lot better than the totem plugin. You can try that or not if you're adament about totem.

---

### Post by Dr Small on 2008-01-03
I wouldn't mind it so bad (I don't preticularly like mplayer [i use vlc]) if I didn't have to install mplayer and just the mplayer plugin, but I don't think that is possible.

---

### Post by rainwalker on 2008-01-03
Weird...
Log in as yourself (not root) and check Synaptic to see if totem-mozilla is installed

---

### Post by aJayRoo on 2008-01-03
Also, doesn't VLC have a firefox plugin available too? I think thats what I'm using (its been ages since I set up this machine so I couldn't be certain).

---

### Post by Dr Small on 2008-01-03
> **rainwalker said:**
> Weird...
Log in as yourself (not root) and check Synaptic to see if totem-mozilla is installed
It says totem-mozilla is installed, when I ran synaptic as my user.

Edit, I just completely removed it, and reinstalled it, and it made no difference.
I think it has something to do with symbolic linking with the plugin.so files, but I don't remember what I am supposed to link what to.

---

### Post by rainwalker on 2008-01-03
VLC does have a Firefox plugin, but it's not very good. It never worked right for me, usually showing (no video) where the videos should have been.

---

### Post by rainwalker on 2008-01-03
> **Dr Small said:**
> It says totem-mozilla is installed, when I ran synaptic as my user.

Ok, well then open Firefox and in the address bar type
> about:plugins
and see if the plugin is listed there.

Are you using the Firefox that comes with Ubuntu?

---

### Post by Dr Small on 2008-01-03
Yes, I am running the Firefox that came with Ubuntu (and I'm on Feisty Fawn).
So, I went to about:plugins, and I see:
```
Totem Web Browser Plugin 2.18.1
application/ogg 	Ogg multimedia 	ogg 	Yes
```

Yet the ogg file I am attempting to play, still doesn't play in Firefox (yet it does when it is launched as root).

Dr Small

---

### Post by rainwalker on 2008-01-03
That's so strange!
What happens when you try to play the file? Does a window come up asking if you want to save the file or open it with a certain application?

---

### Post by Dr Small on 2008-01-03
> **rainwalker said:**
> That's so strange!
What happens when you try to play the file? Does a window come up asking if you want to save the file or open it with a certain application?
It actually momentarily freezes firefox (because it is loading the file) and then the page goes blank. No MIME type at the top, nothing. It's just blank. It never asks me to save it or nothing.

Whereas as root, is opens the totem plugin and begins playing it in the browser as it is supposed to.

Dr Small

---

### Post by rainwalker on 2008-01-03
Hm...
In your Firefox preferences (Edit > Preferences) under the Content section, look in the "File Types" window.  What is it set to do with ogg files?

---

### Post by Dr Small on 2008-01-03
There isn't anything in there, except for SDL... No ogg.
By the way, here is the directory listing of my plugins folder:

```
drsmall@darkghost:~$ ls -la .mozilla/plugins
total 6908
drwxrwxrwx 2 drsmall drsmall    4096 2008-01-03 18:07 .
drwx------ 4 drsmall drsmall    4096 2008-01-03 19:23 ..
-rw-rw-rw- 1 drsmall drsmall    6148 2007-07-02 11:41 .DS_Store
-rw-rw-rw- 1 drsmall drsmall     856 2006-12-15 13:51 flashplayer.xpt
-rwxrwxrwx 1 drsmall drsmall 7040036 2007-06-19 17:31 libflashplayer.so

```

---

### Post by rainwalker on 2008-01-03
I don't know what SDL is, and it's not listed anywhere for me...

I honestly have no idea what to tell you, I'm sorry :?

They must have changed something with Firefox between Feisty and Gutsy, because that's not what I have listed in my plugins directory (but I remember those things from before Gutsy). This is what's listed for me:

---

### Post by Dr Small on 2008-01-03
My mistake. It was SPL. But anyhow, it acts like Firefox can't read the plugin file, and I've check permissions on it and everything, but can't seem to figure it out :(

---

### Post by rainwalker on 2008-01-03
I don't know what could be wrong, but you can try asking in the #ubuntu IRC channel on irc.freenode.com

---

### Post by Dr Small on 2008-01-03
Yeah that is always an option.
But, I removed mozilla-totem and installed mozilla-mplayer and now it works, but it isn't using totem.. Oh well :p

Thanks for all the help :)

Dr Small

---

### Post by philinux on 2008-01-03
Have you tried 

firefox -safe-mode

I'm sure you have

---

### Post by Dr Small on 2008-01-03
> **philinux said:**
> Have you tried 

firefox -safe-mode

I'm sure you have
No, I never did, but then I just removed mplayer and installed the vlc plugin and it worked, so I'm pleased now ;)

---

### Post by rainwalker on 2008-01-03
The VLC plugin works for you?

---

### Post by Dr Small on 2008-01-03
> **rainwalker said:**
> The VLC plugin works for you?
Yup, after I removed totem and mplayer plugins :D

---

### Post by philinux on 2008-01-03
Ah thats it then, it would seem that less is more. I came across this months ago but forgot.

you can only have one plugin for each purpose otherwise confusion reigns.

---

### Post by Dr Small on 2008-01-03
> **philinux said:**
> Ah thats it then, it would seem that less is more. I came across this months ago but forgot.

you can only have one plugin for each purpose otherwise confusion reigns.
Yep. I figured that out the hard way.

---

### Post by rainwalker on 2008-01-03
Hm...
You're lucky, I uninstalled the totem plugin and tried the VLC one, and it didn't work right.
I envy you :)

---

