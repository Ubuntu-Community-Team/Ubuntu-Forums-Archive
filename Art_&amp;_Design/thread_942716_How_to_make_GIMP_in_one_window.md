---
title: "How to make GIMP in one window?"
date: 2008-10-09
forum: Art &amp; Design
---

### Post by banago on 2008-10-09
I would like have GIMP in one window. How can I do it?

Thanks,

Banago

---

### Post by Half-Left on 2008-10-09
GIMP 2.6 has this default way, 2.4 doesn't.

---

### Post by smartboyathome on 2008-10-09
Can't make gimp one window right now. Theres a plugin available to do this, but its only for windows. :(

---

### Post by banago on 2008-10-09
> **Half-Left said:**
> GIMP 2.6 has this default way, 2.4 doesn't.

How come I cannot get GIMP 2.6 in my ubuntu? When i download it it says it has bad sth and cannot be installed. When I get the latest version from add/remove, it is still 2.4

---

### Post by WWSmith36 on 2008-10-09
I checked the backports repo - its only got 2.4.6 :(

Looks like you have to download it and compile from source.  Just make you check the dependencies and md5sum before installing.

---

### Post by Half-Left on 2008-10-09
Next release intrepid I heard could get it in, but you can get it from [http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by banago on 2008-10-09
> **WWSmith36 said:**
> I checked the backports repo - its only got 2.4.6 :(

Looks like you have to download it and compile from source.  Just make you check the dependencies and md5sum before installing.

I do not know how to check the dependences. Would you please tell me a little bit more about that?

I got the latest version from geddeb, but the dependences were wrong.

---

### Post by justanotherhack on 2008-10-09
Afaik the problem most people have with the many GIMP windows is, that the tools and layer windows go behind the image whenever they work on it. A small workaround for this is to just make the tools and other windows stay on top. Just right click the titlebar go to Advanced and something that would be "Always/Keep on top" or something like that (working with the german version, so can't be sure without switching the lang).
This may be a trivial matter, but according to my experience something that helps a lot of people... and maybe is just what OP wants...

---

### Post by Swarms on 2008-10-09
I have 2.6 installed, how do I get it to be in the same window Photoshop style? So the toolboxes are fixed at the sides and not just floating around and in the way, provoking great annoyance when I have to zoom in and out of pictures on a smaller screen?

---

### Post by Half-Left on 2008-10-09
> **Swarms said:**
> I have 2.6 installed, how do I get it to be in the same window Photoshop style? So the toolboxes are fixed at the sides and not just floating around and in the way, provoking great annoyance when I have to zoom in and out of pictures on a smaller screen?

All you do is middle mouse click and hold down to scroll the canvas where you want while zoomed in.

---

### Post by ilrudie on 2008-10-09
> **banago said:**
> I do not know how to check the dependences. Would you please tell me a little bit more about that?

I got the latest version from geddeb, but the dependences were wrong.

Follow [these]("http://phorolinux.com/how-to-install-gimp-26-on-linux.html#more-147") [phorolinux.com] instructions and it should work like a champ.  Hope that helps.

---

### Post by gjoellee on 2008-10-09
I am using Intrepid and I am using gimp 2.6. At is really an improvement!

Here is GIMP 2.6 for 32-bit: [http://www.getdeb.net/release/3233](http://www.getdeb.net/release/3233) (old screenshot)

---

### Post by banago on 2008-10-10
> **ilrudie said:**
> Follow [these]("http://phorolinux.com/how-to-install-gimp-26-on-linux.html#more-147") [phorolinux.com] instructions and it should work like a champ.  Hope that helps.

Thanks but it did not help. I will wait for ubuntu to update GIMP to the latest version :(

---

### Post by SunnyRabbiera on 2008-10-10
> **banago said:**
> Thanks but it did not help. I will wait for ubuntu to update GIMP to the latest version :(

Did you try the getdeb links?

---

### Post by gift008 on 2008-10-10
> **gjoellee said:**
> I am using Intrepid and I am using gimp 2.6. At is really an improvement!

Here is GIMP 2.6 for 32-bit: [http://www.getdeb.net/release/3233](http://www.getdeb.net/release/3233) (old screenshot)


Maybe you should try this way.

---

### Post by .Garrett on 2008-10-13
I've just upgraded to GIMP 2.6.1 from getdeb, and am apparently missing something. Where's the option to run it all in one window?

---

### Post by smartboyathome on 2008-10-13
> **.Garrett said:**
> I've just upgraded to GIMP 2.6.1 from getdeb, and am apparently missing something. Where's the option to run it all in one window?

There isn't one. It just got rid of the menu bar on the toolbox window. It is probably going to be implimented in an upcoming release (as that is what this layout now goes to).

---

### Post by cardinals_fan on 2008-10-13
double-posted

---

### Post by cardinals_fan on 2008-10-13
> **smartboyathome said:**
> There isn't one. It just got rid of the menu bar on the toolbox window. It is probably going to be implimented in an upcoming release (as that is what this layout now goes to).
:(

I really need that.  The multiple windows are painful with a tiling window manager.

---

### Post by olavjunior on 2008-10-15
I have gimp 2.6. but I don't have all in one window! Everything is like with 2.4. How do I get it all to be in the main window???

---

### Post by smartboyathome on 2008-10-15
> **olavjunior said:**
> I have gimp 2.6. but I don't have all in one window! Everything is like with 2.4. How do I get it all to be in the main window???

You **can't**. I said it a few times now in this thread. GIMP doesn't have the ability to be all in one window yet. Theres a plugin for windows, but it will _not_ work under Linux due to it relying on the GIMP DLLs to work.

---

### Post by olavjunior on 2008-10-17
Sorry for not reading the thread thoroughly enough.. I just saw a screenshot at gimp's webpage [http://gimp.org/release-notes/gimp-2.6.html](http://gimp.org/release-notes/gimp-2.6.html) where it all was in one window. Didn't know it was a plugin. And when I look closer, it's def. done in Ubuntu and not Windows! 

So how do you explain that?

---

### Post by lswest on 2008-10-17
if you're referring to this screenshot: [http://gimp.org/screenshots/alternative-2-6-ui-layout-example-two.jpg](http://gimp.org/screenshots/alternative-2-6-ui-layout-example-two.jpg) it's not actually in one window, the image window is full screen and the others are just floating in front.  There is gimpshop, but I don't know what version of GIMP that's based on.

---

### Post by smartboyathome on 2008-10-17
> **lswest said:**
> if you're referring to this screenshot: [http://gimp.org/screenshots/alternative-2-6-ui-layout-example-two.jpg](http://gimp.org/screenshots/alternative-2-6-ui-layout-example-two.jpg) it's not actually in one window, the image window is full screen and the others are just floating in front.  There is gimpshop, but I don't know what version of GIMP that's based on.

GimpShop doesn't give you one window, it just reorders the menus and such. It is based on GIMP 2.2 last I checked.

---

### Post by ercork on 2008-10-18
The solution provided by justanotherhack isn't bad - at least the tool selection dialog is always on top of the image canvas. However if you have other apps open (internet, music player, office programs, etc.) it's a bit annoying. You don't need the Gimp toolbox on top of Firefox.

There's a way around this. In Gimp go File/Preferences/Window Management and in the "Window Manager hints" section choose "Keep above" for the toolbox (and the docks if you want too).

This isn't exactly what people are looking for - there are still 3 windows down in the taskbar. But I find it good enough.

---

### Post by justanotherhack on 2008-10-18
Hmm... maybe it's just me and KDE, but it seems to work exactly the same way as if you're using the context menu. Other non-gimp windows still go behind the toolbar.

Anyways, regarding the other windows, I just use multiple desktops. I mean that's what they were made for ;) . Just some Ctrl+F* browsing and you're fine.

---

### Post by Hairy_Palms on 2008-10-19
you could always use the Xnest hack that i used to use, now it doesnt bother me

```
sudo apt-get install xnest
Xnest :1 -ac -wr -name Gimp-2.6 -geometry 1440x822 & gimp --display=:1 & metacity --display=:1
```

---

### Post by Adavur on 2009-06-16
Just install Xnest Gimp by typing this in your terminal:

```
sudo apt-get install xnest metacity gimp
```

Then type this with your screen solution (typed in bold) instead of mine :D:

```
Xnest :1 -ac -name GIMP -geometry **1024x690** & metacity --display :1 & gimp --display :1
```

But it isn't a really good solution. Try it, but I can't figure out how to open it without using the terminal. But better than the original one ;)

---

### Post by kayosiii on 2009-06-17
you can run the gimp main window fullscreen by using the f11 key
you can then show the toolboxes using the tab key. There is a hint that you can manually put into the config file to keep these boxes on top. But due to this option breaking things in some environments it is disabled by default.

---

### Post by Niva on 2009-06-17
I used to dislike the mani windows in GIMP but since jumping on the linux bandwagon it's grown on me.  I just run GIMP on its own desktop and the tabs on the bottom are actually helpful!

I'm sure in Windows this can get annoying real quick though...

---

### Post by chips24 on 2009-06-17
i could compile it and send you the compiled packages in Ubuntu 8.04 within the weekend. thats not for sure though...

---

### Post by kingofheights on 2009-10-06
> **smartboyathome said:**
> Can't make gimp one window right now. Theres a plugin available to do this, but its only for windows. :(

Where can I find the plugin that does this?

---

### Post by Found on 2009-10-18
it's called [gimphsop]("http://www.gimpshop.com/")

---

### Post by Baneblade on 2011-07-21
> **banago said:**
> I would like have GIMP in one window. How can I do it?

Thanks,

Banago

2.6.2 Still doesn't have it as default, but I was able to get it by using GimpBox script, follwing these simple instructions:

[http://www.omgubuntu.co.uk/2010/09/gimpbox-gives-stable-versions-of-the-gimp-single-window-mode/]("http://www.omgubuntu.co.uk/2010/09/gimpbox-gives-stable-versions-of-the-gimp-single-window-mode/")

---

### Post by 23dornot23d on 2011-07-22
2.6.11 ..... which is in the repository at the moment does not have single window mode but is
a very good version

But ..... if you really do want single window mode ..... plus saving xcf as default ..... add this PPA

The PPA allows one window mode by adding it using the synaptic package manager repositories ......

[https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn]("https://launchpad.net/%7Ematthaeus123/+archive/mrw-gimp-svn")



Seems this is a very old thread here that is way out of date now ...... Single window mode is available in the
latest release of Gimp ..... 2.7.3 from the PPA above ..... [[COLOR=Red]_***Screenshot***_[/COLOR]]("http://img18.imageshack.us/img18/8664/screenshot3ao.jpg")

[COLOR=Blue][ and if you want to go back to 2.6.11 afterwards  ..... untick the gimp repository additions for the PPA above
in synaptic and then remove the dependencies ..... libgimp babl and gegl ..... and of course Gimp .... ] 

Reload the synaptic listing - and then install Gimp ....... 2.6.11 .... which saves JPGs ..... from save
amazing but true .......
[/COLOR]

---

### Post by Baneblade on 2011-07-22
Thanks for that. I've got 2.7.3 from the PPA you reccomended now, but single window mode doesn't remain default, and forgets the side panel widths after you re-enable it. Is there a fix for this?

Iv dug through the preferences menus and couldn't see anything.

---

### Post by prokoudine on 2011-07-23
> **Baneblade said:**
> Thanks for that. I've got 2.7.3 from the PPA you reccomended now, but single window mode doesn't remain default, and forgets the side panel widths after you re-enable it. Is there a fix for this?

Yes, the fix is to tell the guy who maintains the PPA to update the build.

---

### Post by 23dornot23d on 2011-07-23
Is there another link to a later build ?

looked on [Gimp Users too]("http://www.gimpusers.com/forums/gimp-user/13229-gimp-2-7-3")

and a quick [search for Gimp 2.7]("http://www.google.com/search?client=ubuntu&channel=fs&q=gimp+user&ie=utf-8&oe=utf-8#sclient=psy&hl=en&client=ubuntu&channel=fs&source=hp&q=gimp+forum+2.7&pbx=1&oq=gimp+forum+2.7&aq=f&aqi=&aql=1&gs_sm=e&gs_upl=35801l36039l5l36482l2l2l1l0l0l0l216l216l2-1l1&bav=on.2,or.r_gc.r_pw.&fp=aeb16183bfd07c66&biw=1318&bih=633")

does anyone have the latest link to a later version ? so we can update ?

( Interesting looking around - you would expect the [GIMP site ]("http://www.gimp.org/source/")to be the best place to look - but the link is here )

What does [Martin have to say about 2.8]("http://www.chromecode.com/2011/02/why-gimp-28-is-not-released-yet.html")

Best link I can find yet ,,,, but you have to build your own [Nightly build Information Link]("http://www.chromecode.com/2009/10/nightly-gimp-gegl-babl-tarball-builds.html")

Latest tarballs ..... [Nightly builds]("ftp://gimptest.flamingtext.com/pub/nightly-tarballs/") ....

Search for threads related to the [latest buiding GIMP from GIT]("http://www.google.com/search?client=ubuntu&channel=fs&q=gimp+build+from+git&ie=utf-8&oe=utf-8#sclient=psy&hl=en&client=ubuntu&hs=isI&channel=fs&source=hp&q=gimp+build+from+git+2011+july&pbx=1&oq=gimp+build+from+git+2011+july&aq=f&aqi=q-n1&aql=1&gs_sm=e&gs_upl=10742l12933l0l13121l5l5l0l0l0l0l339l1043l0.1.2.1l4&bav=on.2,or.r_gc.r_pw.&fp=aeb16183bfd07c66&biw=1318&bih=633")

This looks to be a reasonable one as it keeps both versions separate >>> [Link]("http://www.shallowsky.com/linux/gimpbuild.html")

Latest Information I can find on [Gimp 2.8 here]("http://www.gimpusers.com/forums/gimp-developer/13630-gimp-2-8-schedule-update-one-month-slip")

---

### Post by prokoudine on 2011-07-23
> **23dornot23d said:**
> Is there another link to a later build ?

No, mrw is the only PPA for 2.7.x that I know of.

---

