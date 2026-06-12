---
title: "Resolution Problems"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by itsvan on 2008-03-10
Hello Everyone,,,i Have A Peculiar Problem,,,everytime I Turn On My Computer,,the Resolution Keeps On Changing Everytime,,and The Only Way I Fix It Is To,,restart The Computer Again, Until A Resolution I Want Kicks In,,can Anyone Tell My Why This Happens? And How To Fix It Thank You Very Much....:)

---

### Post by LuisGMarine on 2008-03-10
Lol I hope English isn't your first language because you just murdered it with all the caps at the beginning of words! :lolflag:

To be on the safe side, go ahead and make a back up copy of your current xorg, just in case after you reconfigure it , it doesn't go psycho.
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```

Anyhow, I found that re-configuring xorg helped me keep the resolutions settings from changing, just run this command and follow the on screen instructions, and when you get to the Resolution , make sure that you select your and maybe one below it.
```

sudo dpkg-reconfigure xserver-xorg
```

Like if you resolution that you want is 1024 x 768 , pick that and also 800x600.

If for some reason something goes terribly wrong, just go ahead and type in 

```
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf 
```

and reboot.  Hopefully we won't have to do that.

---

### Post by itsvan on 2008-03-11
Hey thanks alot for the reply,,the only thing im kinda scared of messing with that screen,..there's some stuff that it asks me that i am not sure about,,in kinda of a noob if u will...any recommendations??

---

### Post by TeaSwigger on 2008-03-11
Hi there, what questions? I haven't had to run it. 

Perhaps this guide can help:

[http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure](http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure)

:)

---

### Post by Michl on 2008-03-11
It's easy to make a mess of things with
sudo dpkg-reconfigure xserver-xorg

have done that.  Now, a backup is a good
thing, but you might find yourself in
recovery mode, but this should work
at the prompt:
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf

I guess I wouldn't trust anyone that tells you to
do something that they didn't run themselves.

There's a good page for dealing with screen
resolutions in help.ubuntu  community
documentations.  Don;'t remember the
exact URL right now.

---

### Post by LuisGMarine on 2008-03-11
Well I have run the command myself, and I usually don't recommend that command because the simple fact that its not exactly for beginners.

For the record, I NEVER EVER recommend commands that I don't run on my system, wether its one time or a couple of time, most commands I pull are usually stored in my terminal for some odd reason.

But in the end you are probably right there is other alternatives to fix this, I just went straight to the source since most of the other fixes people recommend never helped me and reconfiguring x was the only thing that worked for me.

---

