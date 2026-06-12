---
title: "How to use Wine? +creating folders?"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by Depths on 2005-11-10
Hi.
I'm a complete Ubuntu-newbie, so I thought this part of the forum was the best for me to post in.

I want to use Wine, to be able to play Quake 3.
I have installed Wine with Synapsit Package Manager, but cannot find it in the 'Add Applications' console.

So, how do I go about to use Wine?

Also, I'm having problems creating folders.
Is: '# mkfolder -p /usr/local/games/quake3/' the correct command to create a folder? Because I do it but nothing happens...

Any help is appreciated.

---

### Post by ltmon on 2005-11-10
Ok....

Quake 3 is available native to Linux.  If you already have the game files (e.g. the pk3 files) you can simply download the native client from ID.  It comes with a simple enough installer.

No need to bother with wine (which can be a bit of a pain, even for seasoned veterans).

Making a directory from command line:

> mkdir /my/new/directory

As a normal user you won't have permissions to make the directory you are trying to create.  It's in a "system" directory and will need root permissions.  This is doable with:

> sudo mkdir /usr/local/games/quake3

and then entering your password when prompted.

L.

---

### Post by Depths on 2005-11-10
Thanks for the answer.
I'd still like to know how to use Wine though, if I want to play any other game except Q3...

---

### Post by ltmon on 2005-11-10
Wine itself will not play many games, because it doesn't have directX.  The only windows game I can play on it is Warcraft 3, because that can optionally use OpenGL instead.  It's usually pretty good for other windows applications without 3d graphics.

If you want to play DirectX games you need Cedega, which is like wine but with directX.  You can get it from transgaming.com.  It's fairly cheap, but not free.  If you want it to get free you can, but you need to compile it yourself.  Search these forums for "Cedega" if you're game to try that.

But to get started with wine, follow this: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

and then type:

> winecfg

at a terminal to configure everything.

L.

---

### Post by gord on 2005-11-10
and to actually use wine;
```

wine <filename>

```

for example, if i wanted to run half-life (which runs fine in wine)
```

wine /home/gord/.wine/c_drive/SIERRA/Half-Life/hl.exe

```

or optionally
```

wine C:\\SIERRA\\Half-Life\\hl.exe

```

note the two backslash's when we are pretending that there is a C: :)

---

### Post by Depths on 2005-11-11
Ok, thanks both of you. This will get me started...

---

