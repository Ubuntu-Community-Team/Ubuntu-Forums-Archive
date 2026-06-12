---
title: "X Won't Start in Breezy"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by achafe on 2006-11-25
So I've been using ubuntu for close to a year on my desktop.  It has worked fine thus far.  Started with breezy, upgraded to dapper and then, where the trouble started, edgy.  

I found lots of things I used to do in dapper just didn't work in edgy and I just couldn't get my nvidia drivers to work, so I did a fresh install of edgy.  Same trouble decided to give up.

So now I'm trying to install my original Breezy off the install cd's I ordered and I'm x just wont start, I get a long error msg saying at the end "no screens found".  I've dealt with my share of xorg related errors before, I checked everything out and it seems okay.  As far as I can tell it's just a normal, stock xorg.  

I'm really stuck and need the desktop, so it seems I'll be on windows for the next while!

Any idea's why a fresh breezy install won't run x right off the bat?

Spec's AMD Athlon 3400+
512 mb memory
160Gb hdd
nvidia 6150 LE (integrated)

Thanks!

---

### Post by taurus on 2006-11-25
Why not install Dapper again since it's a LTS--Long Term Support!!!

---

### Post by dbott67 on 2006-11-25
A few things:

1. Can you boot using the Live CD or does X crash in that also?

2. What happens after the crash... are you left at a command prompt?  Can you login in text mode?  If so, try running:
```
sudo dpkg-reconfigure xserver-xorg
```

3. Other people that have had graphical issues have downloaded the "Alternate" CD (I think it may have a text-based installer).

4. Can you post the output of:
```
cat /etc/X11/xorg.conf
```

-Dave

---

### Post by rahelvey on 2006-11-25
install dapper if it worked before it will work again. I have used flight 7 cd to reinstall three times now as I break my system. Love breaking and fixing breaking and fixing

---

### Post by cantormath on 2006-11-25
Notice:
As others have stated, Dapper is more stable.  It has the "LTS" in the title which stands for Long Term Support.  What that means, as described to me by one of the Ubuntu developers, is that Dapper is for industry and individual parties to use who need the stability that dapper offers.  Dapper will be LTS for about 3 yrs.  The other  releases of ubuntu are cutting edge releases of ubuntu, hence the name edgy, in which bugs are more common.  Regardless of the fact that edgy is now at stable status, dapper has just been around longer and has had most of its bugs worked out.

Suggested game plan:
1) Go back to dapper
2) Move back to edgy in a little while once more of the bugs have been worked out.
3) Do not got back to the windows curse.

We will miss you here at ubuntu....:confused:

---

