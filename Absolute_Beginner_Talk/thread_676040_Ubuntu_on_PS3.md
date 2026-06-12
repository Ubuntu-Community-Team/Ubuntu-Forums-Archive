---
title: "Ubuntu on PS3?"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Funkyxmonky on 2008-01-23
I'm new to the whole Linux thing, but i've had the PS3 for a good while now, ever since it came out, and i've started to install linux several times, the first few didn't work out to well as the otheros loader never would cooperate with my ISO files, and i'd always get stuck on that kbooter or whatever its called.

Anyway i've recently decided to give it one last try all in the name of science. :P
And i'm actually impressed with Ubuntu cause IT WORKED! No problems nothing, it was simple and straight to the point had it installed within 20 minutes and ready to run.

I've noticed the limitations in playing music CDs and running DVDs these aren't too big of a concern at the moment, i'm more interested in trying to get my internet running smoothly and just working my way around from there.

So the two questions i have are these:

1.) How do i activate the WIFI network card on the PS3 so that i can tap into my wireless network? I've read alot of tuts on this, and now it has something to do with the latest firmware update...

2.) Java? This is really an interesting one to try and figure out for me, and it seems that the Ubuntu power pc version isn't capable of running Java? I've read some tuts on this also and it's still not too clear.
I have the .Bin file from the net, but i can't figure out how to correctly enter the command line into the Terminal so that it opens and executes the .Bin correctly.
See what i have is the Java .Bin 'jre-6u3-linux-i586.bin' sitting on my destop and when i try to follow the tut on how to execute bins using the termainal i get the
"No such file or directory" error... Any help with this will be greatly appreciated.

---

### Post by nikoPSK on 2008-01-23
although, I don't get much of this whole concept, look at this:
[https://help.ubuntu.com/community/PlayStation_3](https://help.ubuntu.com/community/PlayStation_3)

---

### Post by BenP116 on 2008-01-24
For your codecs and all, so you can play dvd's and whatnot, here is an easy installer:

[http://ubuntuforums.org/showthread.php?t=613462&highlight=quickstart](http://ubuntuforums.org/showthread.php?t=613462&highlight=quickstart)


If you end up not being able to get your hardware working in ubuntu.  There is a distro specifically for ps3. 
[www.yellowdoglinux.com](www.yellowdoglinux.com)

---

### Post by Frumious Boojum on 2008-01-24
I'll second trying Yellow Dog Linux...   it seems to have the best PS3 support so far.

However...   be aware that the PS3 does block portions of the memory, so there's a lot of more graphical applications that can't be done so well when running Linux on the PS3.  Hopefully they'll free up some of this memory in the future...

Also, Firefox is a bit behind on the update, so you may want to go with another browser instead.

I had YDL on my PS3 for a while.   After having to replace the PS3, I didn't reinstall it.  For such a powerful console, YDL sure does run slow on the PS3...   so I'm sticking to the computers for my Linux needs.

---

### Post by emarkd on 2008-01-24
I know nothing of the subject at hand, but one thing in your post stood out to me.  I find that many people get that No such file... error because they don't know/forget that in linux you have to specify the directory, even if you're in the directory.  If you want to run /home/emarkd/Desktop/whatever, you can't 

```
$ cd /home/emarkd/Desktop
$ whatever
```

Instead you have to tell Linux that you're specifically running the file found in the current working directory, like this:
```

$ cd /home/emarkd/Desktop
$ ./whatever
```

Maybe that helps...

---

