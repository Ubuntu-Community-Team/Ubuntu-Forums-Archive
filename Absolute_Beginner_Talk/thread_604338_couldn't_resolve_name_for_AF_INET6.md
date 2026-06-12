---
title: "couldn't resolve name for AF_INET6"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by redon12 on 2007-11-06
i have this problem
[IMG]http://image042.mylivepage.com/chunk42/1238864/957/Screfimnshot.png[/IMG]

---

### Post by jordanmthomas on 2007-11-06
That almost seems like it's an error related to ipv6.
[http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841)
If you're up to it, you can try disabling ipv6 and see if it might help (unless you need ipv6, of course).

**edit** 
It could just be that the server you were trying to serve from is down.

---

### Post by redon12 on 2007-11-06
> That almost seems like it's an error related to ipv6.
[http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841)
If you're up to it, you can try disabling ipv6 and see if it might help (unless you need ipv6, of course).

**edit**
It could just be that the server you were trying to serve from is down.
I ether didn't get it or it didn't work
please help!
website  joox.net  and stage6.divx.com don't work:mad:

---

### Post by jordanmthomas on 2007-11-06
Both of those work for me (I have ipv6 disabled).
After looking on the Internet, it could be that you just have a bad connection.

Oddly enough, it seems that this error does not stop most people's mplayer from playing and it continues on (from what I have seen, usually to fail at another point)

Here's a google search I did that came up with *some* stuff. 
```
"gmplayer" couldn't resolve name for AF_INET6: 
```
 According to this, you should be able to still play the file and the only way to stop the error is to recompile mplayer without ipv6 support:
[http://lists.mplayerhq.hu/pipermail/mplayer-users/2005-December/057165.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2005-December/057165.html)

---

### Post by redon12 on 2007-11-06
on [http://lists.mplayerhq.hu/pipermail/...er/057165.html](http://lists.mplayerhq.hu/pipermail/...er/057165.html) it says
> 
> > > > > >I always get 
> > > > > Couldn't resolve name for AF_INET6: 144.122.56.15
> > > > > error dialog from gmplayer on mms streams.
> > > > To clarify, [COLOR="Red"]after i close the error dialog, i'm able to watch the[/COLOR]
> > > > stream. But my question is: how to make it not show up at all?
and my thing doesn't play at all

and i still don't get how to fix the thing

---

### Post by jordanmthomas on 2007-11-06
I don't know either, and there doesn't appear to be a solution that's easy to find out there.  

To fix it, you'll need to recompile mplayer and not enable (or disable if it's enabled by default) ipv6.  At least that's what I've gathered.

I think a better question, though is why does it happen in the first place.  (I don't know, by the way....anyone else have an idea?)

---

### Post by iv0 on 2008-05-18
My mplayer stopped when I used ```
-prefer-ipv4
```

This is the important part of my ~/.streamtuner/config file:

```

action "play-stream" {
        command "gmplayer -prefer-ipv4 %q";
}

```

---

