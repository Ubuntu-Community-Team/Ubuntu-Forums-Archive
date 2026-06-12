---
title: "World Of Warcraft in wine. (Gutsy)"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by Fixel on 2007-10-15
How do you install wine and world of warcraft in gutsy?

---

### Post by Anolis on 2007-10-15
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

try searching next time

as the WoW moderators say "Have a wonderful day in the wonderful World of Warcraft!" (if you get it running at least)

---

### Post by Faud on 2007-10-15
> **Fixel said:**
> How do you install wine and world of warcraft in gutsy?


Good Evening to you. You can download WINE from the package manager.  Make sure that after you install wine before you do anything else you open a terminal and run winecfg.  Your best bet (if you can ) would be to just copy all of the files from CD or flash drive and upload to a WoW folder in Wine.
I run WoW on alsa drivers and my voice chat in game works just fine.

Good luck. Here is a really good thread to get you started.

[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

---

### Post by Fixel on 2007-10-15
When I run it from my windoze install by:

```

cd '/media/sda1/Program Files/World of Warcraft/'
wine WoW.exe

```

I can log in but when it's loading it gives me this error in the terminal:

```

fixme:d3d:IWineD3DQueryImpl_GetData >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glGetQueryObjectuivARB(GL_QUERY_RESULT_AVAILABLE)

```

The above error code repeats it self until I close the terminal. (Which closes WoW)

I figure that I need to enable Open GL.... how do I do this?

---

### Post by Faud on 2007-10-15
You do this in your config.wtf. 

Config.wtf

WoW uses DirectX by default, but for most people it will not perform well in this mode. If this is the case for you, then you should change it to run in OpenGL mode instead. To do this you need to find the file wtf/Config.wtf in your WoW directory. By default it is found in /home/<username>/.wine/drive_c/Program\ Files/World\ of\ Warcraft/, where <username> is you computer login name. If the file does not exist, run the game and log into a character. The game should then create the file. Open it using a text editor, and add the following line to it:

SET gxApi "opengl"

The file is found in the wtf directory in your main WoW directory.

If you experience poor performance, graphical glitches, or the game doesn't run at all, then add the following options as well:

SET ffxDeath "0"
SET ffxGlow "0"


that is from the page I linked you eariler

---

### Post by Fixel on 2007-10-15
Right, saw that one... should've tried it...

I was just thinking that it would ruin my vista install.. But that should be easy to fix.. I'll just make a backup copy.

---

### Post by Fixel on 2007-10-15
Working now, with just the "SET gxApi "opengl""

---

### Post by Fixel on 2007-10-15
Can I make a launcher? and how? Don't wanna have to repeat the commands from my second post.

---

### Post by Faud on 2007-10-15
> **Fixel said:**
> Can I make a launcher? and how? Don't wanna have to repeat the commands from my second post.

Sure, here ya go.

right click on your desktop and hit create launcher, choose a picuture for it. On name I just hit WoW
In the command line write

```

wine "C:\Program Files\World of Warcraft\WoW.exe"

```

---

