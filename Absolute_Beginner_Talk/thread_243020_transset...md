---
title: "transset.."
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by nerdman on 2006-08-24
I wanted to make a theme which puts emphasis on my lovely background. So I start looking around, and I hear it mentioned, so I toss it on my system.

So I type transset, and I get this funny cursor, and I click things and it tells me the opacity is set to .75. Odd, it doesn't look either 3/4 opaque or 3/4 transparent...

I got Tilda to look pretty and show my background right through windows (which is wicked awesome). I was kinda hoping for semitransparent window title bars + borders, but more importantly get the opacity out of my notification area + window selector. 

Since I have Tilda the tutorials on transparent console don't seem that viable to me, but I'd love a point in the direction of transparency in general.

Ubuntu - Hoary Hedgehog - Gnome
1.15GHz, 768MB/DDR RAM, 4GB Ubuntu EXT3 partition :x

---

### Post by tonyisntcreative on 2006-09-20
Not sure if you found a solution for your problem yet, but I think I may have an answer for you.

Back around the release of dapper I tried to get compiz/xgl to work a couple of times and eventually gave up.  Earlier today I accidentally stumbled upon how to get transparency to work (which is all I wanted from compiz anyways).

You also need xcompmgr (which is also in the repos) and you'll need to add to your xorg.conf file.  Once you run xcompmgr running transset will work for you. 

This is the original page...it says it's for Gentoo but it also mentions the process is mostly the same for all distros.

[http://gentoo-wiki.com/TIP_Xorg_X11_and_Tranparency#Setting_up_X_Composite_Extension](http://gentoo-wiki.com/TIP_Xorg_X11_and_Tranparency#Setting_up_X_Composite_Extension)

I'm sure there are posts on this forum that go over the same thing, this just happens to be what I stumbled upon.

---

