---
title: "font is blurry"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by GreenGirl on 2007-05-28
Hi everyone, newbie here.  I recently turned my WinXP machine into a dual-boot with Feisty Fawn.  Everything's been great so far with Ubuntu except that text looks vaguely blurry.  This seems to be the case regardless of the application (firefox, the terminal, even the gnome menu system all have the same blurriness).  I went into "font" and changed it to the LCD rendering (I'm using a 19" wide-screen LCD monitor) but that didn't do anything.

Could it be a graphics card issue?  I'm using an ATI Radeon X850 XT.  I tried following the directions in [the sticky post at the beginning of this forum about ATI cards](http://ubuntuforums.org/showthread.php?t=414194); it downloaded some updates and then said that the graphics card was up to date already and nothing needed to be done with it.  I also went to "restricted drivers manager" under system/administration and enabled "ATI accelerated graphics driver", although it warns me that the software is proprietary and may not be supported.  (I should probably also mention that I know virtually nothing about graphics cards, so please be patient with me if I've said or done anything stupid.8-[ )

As far as I can tell, the card is working fine.  (I'm able to display a 1440x900 resolution).  So maybe it isn't a graphics card problem.

Any ideas?  Thanks in advance.

---

### Post by dptxp on 2007-05-28
See if you can find something useful on this thread -
[http://ubuntuforums.org/showthread.php?t=440376](http://ubuntuforums.org/showthread.php?t=440376)

---

### Post by nvteighen on 2007-05-28
Try this: get into the Terminal (Menu Applications --> Accessories --> Terminal) and type:
```

sudo apt-get update

```

And then,

```

sudo apt-get install msttfcorefonts

```

What does this mean? The first one updates the software source's list (routine step); the second one downloads and installs Microsoft's "core fonts" (Times New Roman, Helvetica, MS Sans Serif, etc.). Maybe your problem is just a font problem and not a video card one.

If it doesn't work, you won't have to delete these fonts as you'll surely will need them sooner or later ;-)

---

### Post by Michaelt74 on 2007-05-28
Make the fonts in Ubuntu appear similar to the Windows XP fonts (less strain on the eyes)

Install msttcorefonts (System>Administration>Synaptic Package Manager> search for msttcorefonts and install these.

Next, download the xml files and save them to your desktop: xml files

Open a terminal: Applications>Accessories>Terminal

cd Desktop

sudo tar xvjpf fontconfig.tbz -C /etc/fonts/

Remember to reboot for the settings to take effect.

---

### Post by GreenGirl on 2007-05-28
Michaelt74, what xml files am I supposed to download?

I downloaded the MS fonts but they look as bad as the ubuntu fonts.  I found a page in the link dptxp recommended, [this page,](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_improve_sub-pixel_font_rendering_for_Feisty) that looks like it might help, but I can't edit /etc/apt/sources.list (do I have to do this in sudo mode or something? What is sources.list?)

Thanks everyone.

---

### Post by Lucifiel on 2007-05-28
Hmmmm...

try looking for fonts.conf in your /home/<user> folder and drop this line of code into fonts.conf 

If fonts.conf doesn't exist, try creating it and save in that folder. 

To see the changes, you must restart Xserver: Alt +Ctrl + Backspace 

> <match target='font'>
<edit name='autohint' mode='assign'>
<bool>true</bool>
</edit>
</match>

Edit: make sure that you place all that code after <fontconfig> and before </fontconfig>

---

### Post by GreenGirl on 2007-05-28
Ugh, this is driving me insane.

I tried Lucifiel's suggestion (there was no fonts.conf so I created a new one) but it didn't do anything, so I searched the forums for info about sources.list and found out how to edit it.  I did everything the website that I linked to in my previous post said to do, and now the fonts look *worse.*  Black text sort of looks like it has colors around it.

---

### Post by GreenGirl on 2007-05-28
It's ok to bump threads on these forums, right?  I'm going crazy over this.  Does anyone know what I can do?  Please? :(

---

### Post by ryanVickers on 2007-05-28
Ok, that was a good idea, (font settings) for fine tuning, but If you have a 19" like me, you'll find that everything is blurry because it uses the wring resolution.  Try to add the entry for the one you want in /etc/X11/xorg.conf under the 24 bit colour section.  save and restart X.

maybe someone else can elaborate?

---

### Post by SoulinEther on 2007-05-28
By blurry do you mean... they just don't look good? Personally I never liked Gnome's anti-aliasing / hinting techniques to make fonts look "smoother"... Or is this something else?

---

### Post by ryanVickers on 2007-05-28
If everything else *is* ok though, then go into fonts setup and pick subpixel smooting or something like that.  It's the crispest.  You might need to restart the X again though. (Control Alt Backspace)

---

### Post by GreenGirl on 2007-05-28
ryanVickers, according to the Screen Resolution option under preferences, I'm using 1440x900, which is the resolution I was using on Windows (and I never had any problem with it on Windows).

SoulinEther, text looks slightly smudged.  You know the blurry look that occurs when you take a gif and convert it to jpeg?  It kind of reminds me of that.  Also, ever since I made the changes that the website I linked to recommended, black font on a white background has this weird colored look, like its lightly outlined in green and purple.

Edit:  Sorry ryan, didn't see your second post.  I've already selected subpixel smoothing.  Doesn't make a difference. :(

---

### Post by ryanVickers on 2007-05-28
The outline effect could be caused by the subpixel actually :p  Go into advanced and choode greayscale insted of coloured or whatever to try and fix that.  As for the main problem, That's wierd - I've noticed one other post about this, maybe it is a video card problem, as much as I've doubted this in the past.  Is it just text, or other things too?  a: Here's how I would test this - go into gimp and make a perfectly straight, 1 pixel line on a blank document.  If it looks blurry, it could be a monitor problem, or linux telling your video card to do something wrong.  Possibly does it look like the test in the sign in my signature when it's tilted?  If so, goto a: :)

---

### Post by SoulinEther on 2007-05-28
Do what ryanVickers says, that's a good idea that I didn't think of, lol.

---

### Post by greybirds on 2007-05-28
Hi GreenGirl,

Have you tried different subpixel orders? Some monitors order the red, green, and blue parts of pixels on lcds differently and that can cause the green/purple issue. If you're using Ubuntu, there's a "Details" button right above the "Close" button on the Fonts Prefs window. KDE also lets you do it, under it's Control Panel > Appearance and Themes > Fonts. I've not used KDE in a while but I believe you can find the ordering options by clicking the "Configure" button there.

---

### Post by SoulinEther on 2007-05-28
> **GreenGirl said:**
> SoulinEther, text looks slightly smudged.  You know the blurry look that occurs when you take a gif and convert it to jpeg?  It kind of reminds me of that.  Also, ever since I made the changes that the website I linked to recommended, black font on a white background has this weird colored look, like its lightly outlined in green and purple.(

Just got the great genius idea to share with you what I use myself, lol.

I am running Xfce4 which is about the same... I am not using Anti-aliasing, not using Sub-pixel hinting. I AM using Hinting, "slight", which is level 1/3 hinting available. I believe Gnome has a similar setting regarding Hinting in the "Advanced" options for fonts.

It's the only way I find the fonts to be tolerable. But that doesn't fix Firefox! Lol, the only way I can have nice fonts browsing is to run Firefox in WINE... looks good but some plugins still aren't working.

---

### Post by Lucifiel on 2007-05-28
> **GreenGirl said:**
> Ugh, this is driving me insane.

I tried Lucifiel's suggestion (there was no fonts.conf so I created a new one) but it didn't do anything, so I searched the forums for info about sources.list and found out how to edit it.  I did everything the website that I linked to in my previous post said to do, and now the fonts look *worse.*  Black text sort of looks like it has colors around it.

Oops, well, my bad. I was hoping that alone would fix your problems. Here's what my fonts.conf look like. 

Anyways, have you tried reconfiguring xorg-conf and selecting your graphics card? If I were you, don't edit the xorg.conf but instead, make all changes through running dpkg-reconfigure xserver-xorg in Terminal (Applications ===> Accessories ====> Terminal). However, you should backup xorg.conf (/etc/X11 dir) to another folder like your desktop. 

> <?xml version='1.0'?><!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
 <match target='font' >
  <edit mode='assign' name='rgba' >
   <const>none</const>
  </edit>
 </match>
 <match target='font' >
  <edit mode='assign' name='hinting' >
   <bool>true</bool>
  </edit>
 </match>
 <match target='font' >
  <edit mode='assign' name='hintstyle' >
   <const>hintfull</const>
  </edit>
 </match>
 <match target='font' >
  <edit mode='assign' name='antialias' >
   <bool>true</bool>
  </edit>
 </match>
<match target='font'>
<edit name='autohint' mode='assign'>
<bool>true</bool>
</edit>
</match>

<!-- Helvetica is a non true type font, and will look bad. This
replaces it with whatever is the default sans-serif font -->
 <match target='pattern' name='family' >
 <test name='family' qual='any' >
  <string>Helvetica</string>
 </test>
 <edit mode='assign' name='family' >
  <string>sans-serif</string>
 </edit>
 </match>
</fontconfig>

---

### Post by Lucifiel on 2007-05-28
Btw, your problem reminds of this font issue I got a few days ago on a fresh Feisty install. The text looked like it was melting off the screen, fonts were magically shrinking and expanding, everything looked like it was glowing at times, etc. 

I tried to take a few screenshots but everyone thought they looked fine. Until, I found out that the screenshot = what your card renders, not what you see on the other user's monitor!!! So, if you have a digicam, you might want to try taking a picture of the problem rather than a screenshot. :D 

As for me, I ended up having to reinstall Ubuntu. Maybe you might want to give that a shot instead of spending hours trying to fix this issue.

---

### Post by GreenGirl on 2007-05-28
> **ryanVickers said:**
> The outline effect could be caused by the subpixel actually :p  Go into advanced and choode greayscale insted of coloured or whatever to try and fix that.  As for the main problem, That's wierd - I've noticed one other post about this, maybe it is a video card problem, as much as I've doubted this in the past.  Is it just text, or other things too?  a: Here's how I would test this - go into gimp and make a perfectly straight, 1 pixel line on a blank document.  If it looks blurry, it could be a monitor problem, or linux telling your video card to do something wrong.  Possibly does it look like the test in the sign in my signature when it's tilted?  If so, goto a: :)

Thanks, the grayscale got rid of the weird colors. :)

Straight lines look fine to me, but any sort of curve (in images as well as fonts) looks bad.  Text definitely looks much worse than images, but nothing, text or not, looks as clear as it looked on Windows.

Not sure what you mean about the sign in your signature.  (I see the sign, but I'm not sure what you're asking.)

> **greybirds said:**
> Hi GreenGirl,

Have you tried different subpixel orders? Some monitors order the red, green, and blue parts of pixels on lcds differently and that can cause the green/purple issue. 

This helped somewhat but not as much as switching to grayscale did.  Thanks, though.

> **SoulinEther said:**
> Lol, the only way I can have nice fonts browsing is to run Firefox in WINE... looks good but some plugins still aren't working.

Oh no, are you serious? :(  My font problems are affecting everything (terminal, text editors, etc., as well as firefox) but firefox is definitely giving me the worst of the problems.  I swear text is twice as small as it is in the windows version of firefox (and this has absolutely nothing to do with the font problem that I've been talking about in this thread).  I tried increasing the default font size but that doesn't affect most pages, including these forums.  (I'm guessing the css for these pages specifies font size in pixels?  But doesn't firefox override that anyway?  And why don't I have this problem in Windows?)

> **Lucifiel said:**
> 
Anyways, have you tried reconfiguring xorg-conf and selecting your graphics card? 

I'm trying this now.  I got to a screen that says I should specify the bus ID if I have multiple videocards (I don't).  The bottom of the screen says <Ok>, I press enter, and nothing happens.

> **Lucifiel said:**
> 
I tried to take a few screenshots but everyone thought they looked fine. Until, I found out that the screenshot = what your card renders, not what you see on the other user's monitor!!! So, if you have a digicam, you might want to try taking a picture of the problem rather than a screenshot. :D 

As for me, I ended up having to reinstall Ubuntu. Maybe you might want to give that a shot instead of spending hours trying to fix this issue.

Does that mean that if I take a screenshot, I could use it to determine whether or not the video card is the problem?  (I could take the screenshot, view the screenshot in Windows, and if the shot looks as bad in Windows as it does in Ubuntu, that means it's the card's fault?)  I don't have time to try this tonight (gotta get up early for work tomorrow. :( ) but I'll definitely give this a try when I get home from work.  (Unfortunately, I don't have a digital camera, so I can't show you a picture of what my screen looks like.)

I just might end up reinstalling ubuntu.  Did reinstalling help you?  I don't think my problem is exactly the same as yours (my fonts don't look like they're shrinking or melting, they just look really badly rendered), but if you think it will help, I'll definitely try it.

By the way, thanks so much, all of you. :)  I know I must seem like a total newbie to you guys.  (This is a huge ego-killer for me.  I'm a *web programmer*, dammit, I'm not supposed to feel like I'm computer illiterate! ](*,) Oh well.  Living up to my signature, I guess.)  But I really appreciate all the help you guys are giving me.

---

### Post by Lucifiel on 2007-05-28
Uh no, take a picture with a digicam instead. Because the screenshot will look fine for the rest of us. That is: we won't see your font problems from your screenshot. 

We don't know what the exact cause is so it could be your card, your font settings or your graphics drivers or something else. 

Oh dear, I've no idea how to get past that problem in Xorg, sorry.

---

### Post by Michaelt74 on 2007-05-28
Check this link, it may help

[http://opensourceroolz.wordpress.com/2007/04/20/a-quick-customisation-setup-guide-for-ubuntu-feisty-704/](http://opensourceroolz.wordpress.com/2007/04/20/a-quick-customisation-setup-guide-for-ubuntu-feisty-704/)

---

### Post by greybirds on 2007-05-28
> **GreenGirl said:**
> ...but firefox is definitely giving me the worst of the problems.  I swear text is twice as small as it is in the windows version of firefox (and this has absolutely nothing to do with the font problem that I've been talking about in this thread). 

The small firefox font issue's almost always a resolution problem. Iit's unrelated, and there's lots of info on the forum about how to gussy it up. Usually it's because Firefox thinks the monitor you are using is larger or smaller than it actually is, so it guesses incorrectly how many pixels are in an inch, which means it uses too few to draw fonts.

---

### Post by ryanVickers on 2007-05-28
> Straight lines look fine to me, but any sort of curve (in images as well as fonts) looks bad.

That's good to know.  Well, not that it's happening, but the fact it's not just fonts.  So I would give up on trying to fix this problem using font configurations.  Try something else, this is a higher level problem with the display settings.  It's not able to show or process a curve of any kind proporly.  That would be why the fonts are bad though, they are mostly curves, and really small.

> (This is a huge ego-killer for me. I'm a web programmer, dammit, I'm not supposed to feel like I'm computer illiterate! 

You think that's bad, I've worked with flash snce I was like 12 and I spent WEEKs trying to figure out why all thee hidden files where showing up.  I had to unckeck "show hidden files" in the viewer! :p :lolflag: :(

---

### Post by SoulinEther on 2007-05-28
I've made some websites in Ubuntu to find that they look totally different in Windows because of the fonts. It's the same browser but it's a different method of handling the font displaying thing.

Actually.. i really hate how Firefox renders text (or Gecko for that matter) in Ubuntu. Reading my website hurts my eyes.

---

### Post by greybirds on 2007-05-28
You might check the forums and web in general for trouble with EDID. It's the way your video card learns about the capabilities of your monitor, and I've read in the past it can not only end up guessing the wrong resolution for your lcd, it can tell you it's using a different one than it actually is. So while you think you've got it in native, it might not be. I know it's a problem with Nvidia cards, and believe ATI can have the same problem.

It's a fairly easy fix if that's the problem: there's a line (different for different cards' drivers for some reason) to tell it not to use EDID but what resolution you tell it.

Sorry for being vague; I'm not on an lcd right now and I use nvidia cards anyway :). I have no way to test.

---

### Post by ryanVickers on 2007-05-28
Yeah, in so many ways those old "monitors" were so much better.  That would be my guess again, incorrect dpi, or offset, or something like that.  that's weird that pictures (really detailed ones at least) don't also seem blurred.  Here, try viewing this.  Tell me if it's grey, or lots of black and white stripes.

---

### Post by confused57 on 2007-05-28
You've probably already seen this Tutorial, but in case you haven't:

[http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)

---

### Post by ryanVickers on 2007-05-29
That might be a good idea, but that's taking it a bit too far I think - there's no antialiasing, and this might be a step in the wrong direction.  If you don't like how firefox shows them, then this is for you I guess, but I think it's a display problem, not so much fonts.  Don't get me wrong, I'm not trying to shoot down the idea, but that's only really treating a symptom, not the problem.  Although, for a testing point of view, this may be quite useful!  If they are still "blurred" after applying this, then that proves the problem is do to with the display of everything.  If it does fix it, than that would be just strange.  It might, though, but I would doubt it would be system wide.

---

### Post by confused57 on 2007-05-29
> **ryanVickers said:**
> That might be a good idea, but that's taking it a bit too far I think - there's no antialiasing, and this might be a step in the wrong direction.  If you don't like how firefox shows them, then this is for you I guess, but I think it's a display problem, not so much fonts.  Don't get me wrong, I'm not trying to shoot down the idea, but that's only really treating a symptom, not the problem.  Although, for a testing point of view, this may be quite useful!  If they are still "blurred" after applying this, then that proves the problem is do to with the display of everything.  If it does fix it, than that would be just strange.  It might, though, but I would doubt it would be system wide.
You're probably right and understand font rendering a lot better than I.   I thought it wouldn't hurt to suggest trying it,  which worked for me in Dapper.   The Firefox fonts were a little too blurry, but installing msttcorefonts made quite a difference.

---

### Post by kjelle392 on 2007-05-29
I have the same problem as you!  I also have a monitor at 1440x900 and the font looks absolutely ugly. I have to set the resolution to 1024x768 just to read the text, but still the font is blurry. I haven't found a answer to the problem though.

---

### Post by SoulinEther on 2007-05-29
My solution? Beryl. (or compiz). Superkey (aka windows key) + scroll up and I can read everything no problem.

8)

---

### Post by sandeep108 on 2007-05-29
I will post again once I start up ubuntu what settings I have, but I also found the font settings in Ubuntu FF quite blurry. I believe I installed the ms core tt fonts, then set default to verdana (this font is great for LCD) turned off smoothing and selected grayscale. I also made some changes in FF fonts.

Now most menus, dialogs, etc. are almost like XP, crystal sharp and no issues in FF either. Open Office also now accepts word documents exactly as they are and also print similarly.

I have copied tahoma to my fonts folder, but am not able to enable it. I think I may need to reset the font config as suggested earlier in this thread.

---

### Post by dptxp on 2007-05-29
I just happened to install kde-core.

Log with it.

There is system>add font in it.

Simply choose the fonts from the Windows Directory, as many as you want in one go, and click OK.

Fonts installed.

you can find kde interesting, I sometimes log with it.

---

### Post by GreenGirl on 2007-05-29
> **Michaelt74 said:**
> Check this link, it may help

[http://opensourceroolz.wordpress.com/2007/04/20/a-quick-customisation-setup-guide-for-ubuntu-feisty-704/](http://opensourceroolz.wordpress.com/2007/04/20/a-quick-customisation-setup-guide-for-ubuntu-feisty-704/)

Finally something that works!  The fonts now look as clear as everything else (which still isn't good, but at least the fonts are clearer).  Thanks. :)  So it looks like the problem is a combination of font and video card problems, and now the font part is solved and I just need to solve the video card part.  At least I feel like I'm getting somewhere now. :)

> **ryanVickers said:**
> Yeah, in so many ways those old "monitors" were so much better.  That would be my guess again, incorrect dpi, or offset, or something like that.  that's weird that pictures (really detailed ones at least) don't also seem blurred.  Here, try viewing this.  Tell me if it's grey, or lots of black and white stripes.

It looks like extremely thin light gray and dark gray stripes.  What's it supposed to look like?

EDIT:  Sorry, I didn't realize I could click on the image to enlarge it. Enlarged, it's light gray and dark gray lines that are visibly made up of light and dark pixels.  I take it this means detailed pictures don't look blurry on my computer.  I'm as confused as you are.

> **sandeep108 said:**
> I will post again once I start up ubuntu what settings I have, but I also found the font settings in Ubuntu FF quite blurry. I believe I installed the ms core tt fonts, then set default to verdana (this font is great for LCD) turned off smoothing and selected grayscale. I also made some changes in FF fonts.


I just changed the default fonts from regular sans to verdana.  You're right, it is easier to read.

> **greybirds said:**
> You might check the forums and web in general for trouble with EDID. 

I tried, but I don't really understand any of it.  Can anyone explain it to me?

---

### Post by ryanVickers on 2007-05-29
> 
It looks like extremely thin light gray and dark gray stripes. What's it supposed to look like?

that sounds about right, on my monitor I could make out pixels of full white and black, so I conclude, yes, you have a problem with how it's trying to show anything that is not perfectly strait.  It's not as bad as it could have been, You can tell it's not all one colour, but it should be more clear than that.  try looking at this one and see if they (1 pixel white spots) are clear.  You should be able to see them perfectly apart from the black back - if not, then it's still has problems.

---

### Post by GreenGirl on 2007-05-29
Yes, those are definitely evenly spaced white dots inside a black box.

---

### Post by deltarho on 2007-05-29
Follow Michaelt74's advice - you can get fontconfig.tbz [here]("http://www.osresources.com/files/centos-windows-fonts/fontconfig.tbz").

---

### Post by ryanVickers on 2007-05-29
Interesting.  try this too.  It's diagonal lines/curves (free hand) with NO antialiasing - It shouldn't seem blurred (maybe jagged, but NOT smooth/blurred).  If so, then the video card is trying to antialias everything for some reason (accidental incorrect setup by system?)  There seems to be problems with your chosen resolution for lost of people for some reason.

I'm hoping that some one else will come up with a good solution to this.  I'll put in some keywords so it'll get recognized:

anti aliasing
fonts
blurred
resolution

everyone put some up if there's anymore good ones.

---

### Post by GreenGirl on 2007-05-29
No problem with that image, either.

Is it possible that it's not a video card issue, and just that graphic interfaces don't look as good in Ubuntu at they do in Windows?  I mean, I've got the fonts working now (except in firefox, and that could be a problem with firefox specifically not interpreting my resolution correctly, right?), and image files apparently aren't affected.  So it seems like what's giving me a problem is the interfaces themselves.  Should I switch to KDE or something?

---

### Post by ryanVickers on 2007-05-29
Possibly.  It's hard to say if it's really a problem, or an opinion that's gone unchecked because we can't see the "problem" for ourselves.  In my opinion, they look just as good if not better, to to each their own I guess.  You could try switching to KDE.  If you really want to, DON'T re-install!  type this command and it just adds KDE to your ubuntu.  then, before you logon, you can pick gnome or kde.

command:
> sudo apt-get install kubuntu-desktop

One other thing I would do first though, is this.  well, wait, do you have an nvidia card?  If so, continue:
go to Applications > Add/Remove
add package "sysinfo" (really simple)
open it and go to the nvidia settings.  look though all the tabs, especially the antialiasing one.  Try checking on "texture sharpening" and in another tab, try turning up the "sharpening"

---

### Post by GreenGirl on 2007-05-29
> **ryanVickers said:**
> Possibly.  It's hard to say if it's really a problem, or an opinion that's gone unchecked because we can't see the "problem" for ourselves. 

That's definitely possible.  I'm going to try to get some of my friends to look at my computer as soon as I can to see if it looks weird to them or if it's just me.  If it *is* just me, then I really apologize for wasting your time with this.  For all I know, maybe I'm just so used to Windows, anything different looks weird.  (if that's the case, then I'm really going to feel embarrassed about making such a big deal out of this...)

I'll also see if I can borrow a digital camera to take pictures of what my monitor is displaying.

I have ATI, not nvidia, but thanks for the suggestion anyway.

---

### Post by ryanVickers on 2007-05-29
> I'm going to try to get some of my friends to look at my computer as soon as I can to see if it looks weird to them or if it's just me.
If they are also used to windows, this may not solve the problem :p

And if there aws really no problem to begin with, oh well, it was worth 42 posts :p :lolflag:

no, actually I don't mind; I got to increase my posts number quite a bit :),and it's always good to consider every possibility - this is like point 1 in the programmers handbook :)

---

### Post by StrykeInferno on 2007-05-30
i found this post to be extremely helpful.

---

### Post by GreenGirl on 2007-05-31
> **ryanVickers said:**
> If they are also used to windows, this may not solve the problem :p

And if there aws really no problem to begin with, oh well, it was worth 42 posts :p :lolflag:

no, actually I don't mind; I got to increase my posts number quite a bit :),and it's always good to consider every possibility - this is like point 1 in the programmers handbook :)

> **StrykeInferno said:**
> i found this post to be extremely helpful.

Oh, well, in that case I guess I don't feel so bad after all.

Any advice for using a digital camera to take screenshots?  I borrowed my sister's camera, but taking pictures of the screen without using the flash results in pictures that are too dark to see, and of course using the flash results in a picture of a white circle of light.

There is definitely something wrong with the way Firefox is displaying pages.  I went into about:config and changed the value to zero, as well as changed the default fonts to microsoft fonts, but nothing helps.  Fonts are much smaller and much blurrier than they were in Windows.  I know I could just disable letting websites choose their own fonts, but I'm a web programmer and seeing the design of other sites (not to mention being able to view my own sites) is important to me.  My main reason for installing Ubuntu in the first place was because it seemed like a better programming environment than Windows, so I'd hate to have to switch back to Windows for this.  (Two of the pictures I tried to take with the camera were ubuntuforms.org in Ubuntu and ubuntuforums.org in Firefox on Windows XP.  There was a very noticeable difference in size and clarity.)

The other thing I tried taking a picture of was the menu screen of Frozen Bubbles, which has extremely hard to read font.  I was curious about how it compares to Frozen Bubbles on other people's computers.  I thought maybe, since it's an old program, it was designed for lower resolution and looks bad on my computer just because of the size of my monitor.  Of course, if that's not the case, then it probably means my computer is rendering it incorrectly.

---

### Post by ryanVickers on 2007-05-31
> 
Any advice for using a digital camera to take screenshots? I borrowed my sister's camera, but taking pictures of the screen without using the flash results in pictures that are too dark to see, and of course using the flash results in a picture of a white circle of light.

I would think that even if you did have a good technique, it wouldn't be so useful, as this is a problem that consists in an area of under 3 pixels squared, and looking at a photo would not give a great idea of anything unfortunetaly.  I've found the frozen bubble fonts to always be kind of strange myself, so I don't know if thats an oddity :p

> (Two of the pictures I tried to take with the camera were ubuntuforms.org in Ubuntu and ubuntuforums.org in Firefox on Windows XP. There was a very noticeable difference in size and clarity.)
Well, if your sure it's that bad, then that's too bad that we couldn't find a fix.  I would hope they magically jump to being good right before you go back to windows (if you dare to do such a thing) to make you change your mind! :p

---

### Post by GreenGirl on 2007-05-31
I have a newbie question about the Ubuntu community.  Hope this doesn't sound stupid:

Would it be considered acceptable for me to bring my computer to an installfest?  My state's LoCo team is having one in the beginning of July.  But I don't want to commit some sort of social faux pas if that isn't the appropriate way to ask ubuntu users to troubleshoot my computer.

And thank you again for all your help.  I realize I've done nothing but complain, but it's just because I really want to get Ubuntu to work, not just because of the operating system itself but because I'd love to be a part of this community.  If I do end up being able to fix it so that I can read the screen without difficulty, then I hope I can become an experienced Ubuntu user and help newbies just like you're helping me.

You guys rock. :)

---

### Post by ryanVickers on 2007-05-31
I've never heard much about those things, but that might be a good idea, just see if any one else used to what is should look like sais it's odd or not.

---

### Post by Lucifiel on 2007-06-01
> **GreenGirl said:**
> I have a newbie question about the Ubuntu community.  Hope this doesn't sound stupid:

Would it be considered acceptable for me to bring my computer to an installfest?  My state's LoCo team is having one in the beginning of July.  But I don't want to commit some sort of social faux pas if that isn't the appropriate way to ask ubuntu users to troubleshoot my computer.

And thank you again for all your help.  I realize I've done nothing but complain, but it's just because I really want to get Ubuntu to work, not just because of the operating system itself but because I'd love to be a part of this community.  If I do end up being able to fix it so that I can read the screen without difficulty, then I hope I can become an experienced Ubuntu user and help newbies just like you're helping me.

You guys rock. :)

Sure, why not? After all, your problem sounds pretty unique. Maybe go post in the Loco forums and ask them if it's okay to do so?

---

### Post by Gary.M on 2007-06-05
> **Lucifiel said:**
> Sure, why not? After all, your problem sounds pretty unique. Maybe go post in the Loco forums and ask them if it's okay to do so?

Hi there. GreenGirl I've been follwoing this. I too am new to Ubuntu, and I have exactly the same observation that you do. In fact it comes up in other threads across these forums, so its not unique to you.

I have a good old Philips 19" CRT monitor. Very sharp.

After a lot of playing around I'm beginning to come to the conclusion that it might be to do with the displaysize setting... and with nvidia-glx loaded my system in the Nvidia control panel shows 81x81 whereas the fonts are all set in the font controls to 96dpi.

My fonts looked OK using the nv driver, and became a little fuzzy after the nvidia-glx driver was loaded.

With the nvidia driver the displaysize setting when added to xorg.conf is ignored.

Someone mentioned a bug with Nvidia reading the EDID. Could anyone elaborate on this, it may be where the problem lies... somehow the display driver res needs to match the font dpi no?

---

### Post by ryanVickers on 2007-06-05
Yes, I have a LCD (72dpi) and the fonts are set to 96dpi.  This is strange I thought, but normal, becuase when I set them to be "correct", they looked small, so I think this is normal.  As for everything else, you might be on to something there...

---

### Post by Gary.M on 2007-06-05
A bit of searching around and I found these....

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/3731](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/3731)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

I don't know how relevant they are, but there is obviously an issue with Ubuntu and correct recognition of the monitor specification with Nvidia drivers. And the bug report notes the problem is somewhat random and doesn't affect all users...

---

### Post by Gary.M on 2007-06-05
> **ryanVickers said:**
> Yes, I have a LCD (72dpi) and the fonts are set to 96dpi.  This is strange I thought, but normal, becuase when I set them to be "correct", they looked small, so I think this is normal.  

If I set my fonts dpi to 81 things are definitely smaller as expected, but they do look sharper too. I need to look more closely at this. I did find last week a webpage that required me to set the dpi setting to achieve a dimensional match with a line of specified length on the screen. To get it to match I needed to be set close to 81 dpi. (I think I recall this correctly, so much new stuff going on here... and a pity, I can't recall the web page)

---

### Post by ryanVickers on 2007-06-06
This is what I had been thinking for a while, but when she said my test images were not blurry, I tossed this idea aside; perhaps it's time to bring it up again?  I could be very possible that on some resolutions it has set display sizes incorrectly.
> I did find last week a webpage that required me to set the dpi setting to achieve a dimensional match with a line of specified length on the screen.
I've noticed lots of programs like this, and I would maybe try "screen Ruler".  Compair it to a real rular, then fine ture?...

---

### Post by Moop on 2007-06-06
I've also been following this thread. I've tried just about all the suggested solutions and most of them made things worse. 

I did find a web page that has a good explanation of dpi and how to figure out what yours should be. I haven't tried everything suggested but I'm going to tomorrow. 

[http://www.karakas-online.de/forum/viewtopic.php?t=4145]("http://www.karakas-online.de/forum/viewtopic.php?t=4145")

---

### Post by Gary.M on 2007-06-06
I'm guessing that doing the last section with the screen measurement and then inserting the dpi spec into the X server config file is the key to it... I will try to get time to experiment with this tomorrow.

---

### Post by bazzer on 2007-06-22
Hi all
Been reading this thread through today, as I thought I might have had a similar issue on my setup here. I stumbled across this excellent web page that explains subpixel shading on tft monitors and with the aid of some of the pictures on there, I've set mine up with a fairly good result.

[http://www.grc.com/ctwhat.htm]("http://www.grc.com/ctwhat.htm")

Thought you may like to look. ;)

---

### Post by sandeep108 on 2007-06-23
Yes, but somehow why do I like my LCD without any sub-pixel smoothing? The text (DVI connection) is very sharp and somehow either in windows or in ubuntu if I set equivalent of sub-pxel smoothing things just get blurrier. I have set up mine as no sub-pixel smoothing and full hinting. I also like XP without cleartype smoothing)

---

### Post by GreenGirl on 2007-07-07
Hey everyone, I finally have an update.  (it's ok to bump old threads, right?)

I went to the installfest and was able to get some help.  It turns out it's not my videocard, it's a bug in the way Firefox renders fonts.  (And any other program that uses Mozilla's Gecko engine, like OpenOffice).  I'm not really sure how the bug works, something with the pengo (pango?) file.  If anyone here knows more about Mozilla than I do and can elaborate, I'd appreciate it because I really don't know what I'm talking about.  All I know is that they installed some sort of patch that mostly fixed the problem.

I do still have one problem. (I didn't notice this until after getting home from the installfest, unfortunately.)  Bold text in Firefox has a weird blurry look, like there are colors behind the letters, like that problem I had earlier that I had fixed by switching to grayscale (but this time switching to grayscale doesn't help).  Any idea how to fix it?

---

### Post by ryanVickers on 2007-07-07
That's good you found a fix - but weren't *all* the fonts blurry before?!  I don't know why they would appear coloured, but some fonts/font rendering engines in Linux tend to make **bold** fonts quite blurry, and, I can't help noticing, very ugly!  It's just some, and way less now than years ago, but, yeah.

But they look fine on mine, so the default is not one of them; must be something else!

---

### Post by GreenGirl on 2007-07-07
Yeah, all the fonts were blurry initially, then I made some of the changes that were suggested in this thread and that more or less fixed everything except firefox (and frozen bubbles, which, it turns out, is weird-looking on everyone's computer.  Someone at the installfest showed it to me on his laptop).  So, between the help I received in this thread and the installfest, I've gone from "everything is hard to read" to "bold fonts in Firefox are hard to read", which is a huge improvement.

---

### Post by Moop on 2007-07-07
I've started using Gran Paradiso (Firefox 3.0?) and even though it's only alpha, it's been stable for me. The fonts are way better and now I don't even use Firefox 2.0 
Check it out. 
[http://archive.ubuntu.com/ubuntu/pool/universe/f/firefox-granparadiso/]("http://archive.ubuntu.com/ubuntu/pool/universe/f/firefox-granparadiso/")

---

### Post by Moop on 2007-07-07
I've also been "testing" the next release of Ubuntu (Gutsy) and the fonts are improved. Take a look at this thread. 
[http://ubuntuforums.org/showthread.php?t=466244&highlight=gutsy+fonts]("http://ubuntuforums.org/showthread.php?t=466244&highlight=gutsy+fonts")
:D

---

### Post by GreenGirl on 2007-07-07
Cool, looks like I'll only have to deal with the font problems for a few months.  Gutsy Gibbon is supposed to be out in October, right?  And Wiki says firefox 3.0 is predicted to be out in November.  w00t. :)

---

### Post by ryanVickers on 2007-07-07
I don't think I'll bother with the new distro, I just (a few months :)) got feisty working great and it's what got me totally switched off of windows!  But for firefox 3, I hadn't heard that - I can't imagine what that'll be like!  Just going to number 2 was a big difference, but the downside is, with every new version, there's themes and add-ons and stuff that will start/stop working!  Also, I wonder how that will work for me because I usually use swiftfox for the plugins...

Edit: I just took a look at the new fonts, and yeah, they're great!  I think one of the big differences was actually the font used and not so much how they're drawn - I just tdid a few clicks and got mine to match almost exact!

---

