---
title: "Can't get YouTube working with 12.04"
date: 2013-06-14
forum: Apple Hardware Users
---

### Post by Dukenukemx on 2013-06-14
I have 12.04 working mostly fine on my G4 and want to get YouTube working within Firefox.  So I got to YouTube to play a video and I get an error need missing plugin.  Ok no problem I'll install Gnash.

sudo apt-get install gnash
sudo apt-get install browser-plugin-gnash

Go back to play video and I get a black box where the video would appear.  Nothing happens no matter how long I wait.  Can anyone help me fix this?

---

### Post by danield on 2013-06-15
Gnash doesn't work anymore.  Try streaming Youtube through Mplayer.  If you use the Firefox add-on "Open With" along with Greasemonkey scripts "Youtube - EZ Download" and "YousableTubeFix", you just right-click in the browser and have it auto-open the video:

[http://ppcluddite.blogspot.com/2013/01/some-cross-platform-flash-alternatives.html]("http://ppcluddite.blogspot.com/2013/01/some-cross-platform-flash-alternatives.html")

---

### Post by Dukenukemx on 2013-06-15
You mean [this add-on](https://addons.mozilla.org/en-us/firefox/addon/open-with/)?  Also right clicking, how do I do that with a one button mac again?

---

### Post by GhettoMrBob on 2013-06-15
Try clicking while pressing the control key. This works in OS X. I know on my unibody MacBook Pro the two finger click works but I'm not sure if that will work on the PPC touchpad.

---

### Post by Dukenukemx on 2013-06-16
Thanks I got it working.  Don't need to right click, you can just select one of the file types in the menu at the lower right of the screen.  Surprised how well it works.

---

### Post by michiganmac on 2013-06-16
> **Dukenukemx said:**
> You mean [this add-on]("https://addons.mozilla.org/en-us/firefox/addon/open-with/")?  Also right clicking, how do I do that with a one button mac again?

When using a single button mouse in Lubuntu, pressing the F12 key will bring up the same contextual menu as right-clicking.

---

