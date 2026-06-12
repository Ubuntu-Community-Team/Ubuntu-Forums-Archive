---
title: "Suede icon theme"
date: 2004-10-13
forum: Art &amp; Design
---

### Post by Nikola on 2004-10-13
I like Suede icons a lot, so I started to expand icon set.
I've created new ones, especialy missing mime type icons, some are recreated Gnome icons in SVG format, then some are borrowed from other icon sets (Gorila, Rodent, Lush..) and changed to fit rest of icons.
Anyway, try it, it fits, IMO, with default Ubuntu theme since folders have that brownish colour.

Get it here:
[http://damas.on.neobee.net/teme/Suede.tar.bz2](http://damas.on.neobee.net/teme/Suede.tar.bz2)

---

### Post by ubuntu-geek on 2004-10-13
very nice.. my new default..

---

### Post by rupert on 2004-10-13
cant install it with the them installer,
tried to unpack the bz,
can i simply copy it to the ~theme folder?

---

### Post by ubuntu-geek on 2004-10-13
i extracted mine into /home/user/.icons and then selected it via the theme manager.

---

### Post by rupert on 2004-10-13
that did it, thx

---

### Post by Tsjoklat on 2004-10-13
Thanks Nikola very nice :) How did you make them?  :?:

---

### Post by Nikola on 2004-10-13
[quote=Tsjoklat]Thanks Nikola very nice :) How did you make them?  :?:[/quote]

Inkscape. And I hate it. It is so much pain for me to use.
I thought I need time to get used to, like Gimp (erased it and re-install it many times till  I finaly got used to and forgot Photoshop).

---

### Post by Tsjoklat on 2004-10-13
Ah, I feel your pain!  :?  I wanted to make some svg icons myself but so far I have been  unable to get Inkscape to do anything sensible  :lol:  Maybe I should give it another stab  :wink:

---

### Post by arctic on 2004-10-14
nice work!:)
i have always waited for someone to continue this iconset. i tried to add something myself with sodipodi but got frustrated very fast. :P

---

### Post by Nikola on 2004-10-14
I'm thinking about adding more Ubuntu colours to this theme, like brownish colour for stock icons (back/forward,.. arrows) to fit default Ubuntu theme better.
I'm starting to dig this brown colour, somehow it is very pleasant and not in-your-face. 
Nice to see that I'm not only one who finds Inkscape (or Sodipodi) painfull to use. They are so many quirks with it.

---

### Post by normnmiles on 2004-10-14
[quote=ubuntu-geek]i extracted mine into /home/user/.icons and then selected it via the theme manager.[/quote]

I feel stupid asking this but how do I open "theme manager"?  Is this the one at Computer-&gt;Desktop Preferences-&gt;Theme?

---

### Post by thebeast on 2004-10-20
(Yes Normnmiles i believe that's the one.)  

Thank you so much for the icons Nikola.  They're fantastic and I think they'd complement Ubuntu nicely.  I love the gradient brown in the file folder icons and the overall soft feel.  I used to hate the color brown but you and the other ubuntu artists have converted me.  Do you think they'll put your icons in Hoary Hedgehog?

---

### Post by Nikola on 2004-10-21
[quote=thebeast](Yes Normnmiles i believe that's the one.)  

Thank you so much for the icons Nikola.  They're fantastic and I think they'd complement Ubuntu nicely.  I love the gradient brown in the file folder icons and the overall soft feel.  I used to hate the color brown but you and the other ubuntu artists have converted me.  Do you think they'll put your icons in Hoary Hedgehog?[/quote]

Let me note that I'm not original author of Suede icon theme. I just jumped in when I saw it is not developed anymore, and a lot of mimetype icons were missing, and no stock icons. So, I've added most of missing mimetype icons, and added bunch of stock icons.
And also I agree that brownish folder icons fits perfectly with brownish colours of Human gtk2 theme.

---

### Post by -baHam- on 2004-10-21
Could you please do some icons for apps like Firefox, xmms, rhythmbox, xine, gimp, limewire , xchat and stuff like that?

---

### Post by Nikola on 2004-10-21
[quote=-baHam-]Could you please do some icons for apps like Firefox, xmms, rhythmbox, xine, gimp, limewire , xchat and stuff like that?[/quote]

Unfortunately, I know how to use Inkscape, but my artistic skills are not so good  :) 
So, I'm good with cut/copy/paste, tweaking and mixing images, but when it comes to creating something new, I flop.
Maybe I'll try something.. we realy need complete icon theme, there are so many icon themes that are half finished. I want all mimetype icons, all stock icons. I hope Human icon theme that is developed will be like that.

---

### Post by Tsjoklat on 2004-10-21
I agree with you Nikola, loads of half finished themes out there. But I have to say, I am so glad you did something about those horrid stock icons.  :D

---

### Post by adbak on 2004-10-21
I downloaded Suede.tar.bz2 and ran ```
tar -xjf Suede.tar.bz2
cp Suede2/* /home/adam/.icons
``` only to get ```
cp&#58; omitting directory `Suede2/scalable'

```  
What did I do wrong?

---

### Post by thebeast on 2004-10-21
This calls for Open Source action! Quick! Community collaboration! Who has aritistic talent?  (sorry, not me either.  btw, is inkscape in apt?)  Help finish the icon theme.  Maybe if you all finish it you can ask the orig author if you can use some of his work for ubuntu and submit it to the devs....

---

### Post by Tsjoklat on 2004-10-22
"cp Suede2/* /home/adam/.icons"

sudo cp -a Suede2 /usr/share/icons/  :)

---

### Post by mojo on 2004-10-22
There is something wrong with folder mimetype, when I open it with Nautilus, it crashed my Nautilus, please check.

---

### Post by Nikola on 2004-10-23
[QUOTE=mojo]There is something wrong with folder mimetype, when I open it with Nautilus, it crashed my Nautilus, please check.[/QUOTE]

Jeez, why the hell nautilus crashes while showing just a svg image is beyond me. 
Try deleting mimetype icon for sql, I got message from one user who complained that nautilus crashed when showinf folder with sql files.
That's probably bug with nautilus, or svglib. I use Rox Filer, and it shows everything ok. All svg images were created with Inkscape.
And I don't know what to do.. load it into Inkscape and save again?
File manager should not crash when loading preview icon for a image, even a borked one....

---

### Post by iwasbiggs on 2004-10-27
[QUOTE=Nikola]Jeez, why the hell nautilus crashes while showing just a svg image is beyond me. 
Try deleting mimetype icon for sql, I got message from one user who complained that nautilus crashed when showinf folder with sql files.
That's probably bug with nautilus, or svglib. I use Rox Filer, and it shows everything ok. All svg images were created with Inkscape.
And I don't know what to do.. load it into Inkscape and save again?
File manager should not crash when loading preview icon for a image, even a borked one....[/QUOTE]

This is fixed with an updated librsvg2 (2.8.1 - hoary).

---

### Post by Nikola on 2004-10-28
[QUOTE=iwasbiggs]This is fixed with an updated librsvg2 (2.8.1 - hoary).[/QUOTE]

Where to get it? I have installed librsvg2 version 2.7.2-2ubuntu1, listed in Synaptic as latest.

---

### Post by -SF- on 2004-10-28
[QUOTE=Nikola]Where to get it? I have installed librsvg2 version 2.7.2-2ubuntu1, listed in Synaptic as latest.[/QUOTE]
 Change 'warty' by 'hoary' in Synaptic's sources list and you'll got it. It seems it's open now.

---

### Post by rupert on 2004-10-28
can i savely change back to warty?
I just wanna check which packages get updated, 
but i dont wanna install anything.
I just wanna make an update and dist-upgrade without saying yes at the end.

---

### Post by medgno on 2004-10-28
I've been looking for a nice and fairly complete SVG theme that fits in well with the default Gnome look & feel and I'm in love with this work. You rock!

On a somewhat related topic, does anyone know if the Gnome people are going to migrate to SVG for their icons?

---

### Post by beesee on 2004-10-29
[QUOTE=medgno]does anyone know if the Gnome people are going to migrate to SVG for their icons?[/QUOTE]
I believe I've read somewhere that they'll eventually switch their default themes to SVG.  Some of the gnome games have already converted to SVG.

---

### Post by ffub on 2004-12-03
The icon theme is missing a help icon and could do with new ones for the search and recent documents menu entries.

[IMG]http://stomlinson.org/img/help-icon.png[/IMG]

---

### Post by Daniel G. Taylor on 2004-12-03
To everyone getting frustrated or confused in Inkscape, I offer my assistance. What is it that is so confusing or difficult exactly? Have you ever worked with a vector graphics package before? Is the idea of vectors harder to understand than raster images? I'm not trying to put anyone down, I am truly curious and want to help you.

I used to have some inkscape tutorials up, but they quickly became outdated. I will think about updating them and posting them to the forums here, anyone interested in that?

---

### Post by Nikola on 2004-12-03
[QUOTE=Daniel G. Taylor]To everyone getting frustrated or confused in Inkscape, I offer my assistance. What is it that is so confusing or difficult exactly? Have you ever worked with a vector graphics package before? Is the idea of vectors harder to understand than raster images? [/QUOTE]

I did vector graphics, starting with CorelDraw back in Windows 95 days and on, also did a lot of work in Flash.
I just can't explain why, but Inkscape feals somewhat ackward.
Maybe I need time to adapt, like I had with Gimp. Transition from Photoshop to Gimp was painfull, but now Photoshop feels ackward to me :)

---

### Post by bvc on 2004-12-03
[QUOTE=Daniel G. Taylor]To everyone getting frustrated or confused in Inkscape, I offer my assistance. What is it that is so confusing or difficult exactly? Have you ever worked with a vector graphics package before? Is the idea of vectors harder to understand than raster images? I'm not trying to put anyone down, I am truly curious and want to help you.

I used to have some inkscape tutorials up, but they quickly became outdated. I will think about updating them and posting them to the forums here, anyone interested in that?[/QUOTE]
I'd be intersted in that! I'm a complete graphics n00b....just winging it right now. I appreciate your site. I tried to follow a tut or two when I first touch inkscape and quickly got frustrated because as you say, it's outdated. If you look at the images in Tesla
[http://gnome-look.org/content/show.php?content=17485](http://gnome-look.org/content/show.php?content=17485)
you'll laugh. They are horrid! =; Now that I know a little more I need to clean it up...a lot!
I'm doing better with Edge though, I think
[http://bvc.kernow-webhosting.com/theme/screenshots/edge.jpg](http://bvc.kernow-webhosting.com/theme/screenshots/edge.jpg)

Someone said the other day that svg_gtk themes had a high overhead. All image engines do. As a graphics n00b, it's perfect. Easier than the gimp, for sure, and like Nikola the gimp was weird for me but now photoshop is. I'm sticking with svg for obvious reasons and hope it continues to improve in linux.

---

### Post by Daniel G. Taylor on 2004-12-03
[quote=bvc]I'd be intersted in that! I'm a complete graphics n00b....just winging it right now. I appreciate your site. I tried to follow a tut or two when I first touch inkscape and quickly got frustrated because as you say, it's outdated.[/quote]
Alright, I will see about updating them to Inkscape 0.40 during the next few weeks and move them to my new site. To anyone that's interested, you can still find the old ones on my home server (read: slow) here:

[http://home.programmer-art.org/?page=inkscape](http://home.programmer-art.org/?page=inkscape)

[quote=bvc]Someone said the other day that svg_gtk themes had a high overhead. All image engines do.[/quote]
They do. For GTK themes it's usually best to use a theme engine for the look you want, and modify its colors and such. Metacity themes should use Metacity's own vector commands (lines, rectangles, circles and such). Icon themes have no excuse for not using SVG, though.

By the way, your themes don't look too bad :)

---

### Post by Daniel G. Taylor on 2004-12-08
Alright, I've decided to make a few video tutorials for Inkscape. So far I've recorded five videos and have yet to record the audio for them (can't do both at the same time because they lose sync... :( ).

In the spirit of free software and open standards, the videos will be released as Ogg Theora/Vorbis files, which should play under Ubuntu and other modern distributions out-of-the-box (I've tested it with totem-gstreamer and helix-player).

For a quick teaser preview, I've uploaded one of the Theora-encoded videos to my website. It is a lesson on gradients. You can grab it here:

[http://programmer-art.org/files/tutorials/inkscape/04-gradients.ogg](http://programmer-art.org/files/tutorials/inkscape/04-gradients.ogg) [~10mb]

As I said, audio will be added later (I need to be alone to do it, which means I only have a few hours a day for it). My microphone is also not very good, and I have to amplify the volume, which gives it a lot of background noise. I'm working solving that. Anyway, I'd love some feedback on the video.

The current tutorial lineup I have is as such:
01 - Introduction to Inkscape (UI and Selection tool)
02 - Creating Shapes (Uses most of the tools on the left toolbar)
03 - Editing Shapes (A tutorial all about the shape editing tool)
04 - Gradients (The tutorial teaser you can view above)
05 - Creating a simple icon (The gossip available status icon)

How does that sound for everyone who was interested? Once all of those are finished, I will update my website and make an official Inkscape tutorial thread here on these forums. Oh, and while I'm at it, mirrors/torrents would be appreciated when I finish them!

---

### Post by gheorghe_pop on 2004-12-08
Some screenshots please!:D

---

### Post by bvc on 2004-12-08
whoa! Sweet! I'll have to check my data transfer usage before I could mirror, but will if I can. Torrents? Not me....I don't like anything about the protocol.

---

### Post by bvc on 2004-12-20
[QUOTE=Daniel G. Taylor]To everyone getting frustrated or confused in Inkscape, I offer my assistance. What is it that is so confusing or difficult exactly? Have you ever worked with a vector graphics package before? Is the idea of vectors harder to understand than raster images? I'm not trying to put anyone down, I am truly curious and want to help you.[/QUOTE]

Help!!! :-P 

So, lets say you have a 24x24 radial gradient that's somewhat transparent. You need an object from a 24x24 linear gradient without trans, so you import it and delete the parts you don't need. But that object needs to be darker. It has inherited the properties of the main image you want to change with the new object. So that when you change the new object the main is changed as well. Now, this seems to happen....whenever. I can't tell it not to. I've made clones and unlinked the clones and something from the Path menu (can't remember what, I'm at work on windows rt now). Either it's a bug or I'm missing the obvious. Anyone have a clue?

---

### Post by matt on 2004-12-20
This theme sounds great, but I haven't been able to select it! I extracted it to /usr/share/icons/ but can't see it in the theme manager. Any suggestions?

---

### Post by bvc on 2004-12-20
[QUOTE=matt]This theme sounds great, but I haven't been able to select it! I extracted it to /usr/share/icons/ but can't see it in the theme manager. Any suggestions?[/QUOTE]
easiest is to put it in .icons in your home dir
if you want it installed once and global for all users you probably have a permision problem. What does
ls -l /usr/share/icons
say about the Suede2 dir
and what does
ls -l /usr/share/icons/Suede2
say?

My users are a part of the Group users so I would
chown -R root:users /usr/share/icons/Suede2

---

### Post by matt on 2004-12-21
Got it working...my own foolishness, sorry! I made the jump to Linux only a few weeks ago, when I got Ubuntu, so I'm still learning a lot. Thanks for the help bvc!

---

### Post by poptones on 2004-12-21
I don't see an answer to a question asked a page back - what happens if I change synaptic to hoary? It says I will lose all my settings if I do this. I tried downloading the librsvg file and installing it with dpkg, but that only opened the door to dependancy hell. Some details on how to do this upgrade without blowing my entire system to hoary would be nice.

---

### Post by shimon on 2004-12-21
[QUOTE=ffub]The icon theme is missing a help icon and could do with new ones for the search and recent documents menu entries.

[IMG]http://stomlinson.org/img/help-icon.png[/IMG][/QUOTE]
i am also having this problem  :sad:  :?:  :cry:

---

### Post by mayco on 2005-01-06
[QUOTE=shimon]i am also having this problem  :sad:  :?:  :cry:[/QUOTE]
 you can solve that by fixing the symlink in .icons/Suede2/scalable/apps
you can see that the file is red
do a ls -l
delete the red file and recreate it, but now with the correct path
ln -s source destination

---

### Post by Daniel G. Taylor on 2005-01-10
[QUOTE=bvc]Help!!! :-P 

So, lets say you have a 24x24 radial gradient that's somewhat transparent. You need an object from a 24x24 linear gradient without trans, so you import it and delete the parts you don't need. But that object needs to be darker. It has inherited the properties of the main image you want to change with the new object. So that when you change the new object the main is changed as well. Now, this seems to happen....whenever. I can't tell it not to. I've made clones and unlinked the clones and something from the Path menu (can't remember what, I'm at work on windows rt now). Either it's a bug or I'm missing the obvious. Anyone have a clue?[/QUOTE]
 Sorry, I was on vacation without net access for a few weeks!

I'm a bit confused. Could you take a screenshot or explain it a bit more? What do you mean with 24x24 gradients? If the properties are being "inherited" you may want to take a look at the XML output (Open the SVG file in a text editor) and make sure that the object IDs are different, and if it's just the gradient you can create a new gradient and change it, which won't change the old one (though I've seen a bug where Inkscape creates a new gradient but doesn't select it so you wind up editing the old one, in which case you just manually select the new one).

I'm currently having network troubles but everything should be fixed soon enough and I will continue to work on the tutorial videos (I have some neat ideas for them!).

---

### Post by Quest-Master on 2005-01-10
Inkscape .40 offers a TON more than the standard in Ubuntu's repository at the moment.. it is available in the Ubuntu Backports repository though. :D

Someone should really also write a tutorials on Photoshop -> Gimp. I really want to learn how to use it, but none of the tutorials have really done that well yet.

---

### Post by Daniel G. Taylor on 2005-01-10
[QUOTE=Quest-Master]Inkscape .40 offers a TON more than the standard in Ubuntu's repository at the moment.. it is available in the Ubuntu Backports repository though. :D[/QUOTE]It's also available in Hoary.
[QUOTE=Quest-Master]Someone should really also write a tutorials on Photoshop -> Gimp. I really want to learn how to use it, but none of the tutorials have really done that well yet.[/QUOTE]I spent quite a while with The GIMP on my iBook while I was away. It really is a nice program, and I was able to draw a few nice looking things and edit some photos I took. I come from a Photoshop background (worked in a graphics/printing/design shop for 3 summers), and I think tutorials to help others step into The GIMP are a great idea, though I'm no expert. Not that I am with Inkscape either, but I feel much more comfortable with it. Anyone here a GIMP guru?

---

### Post by bvc on 2005-01-11
[QUOTE=Daniel G. Taylor]Sorry, I was on vacation without net access for a few weeks!

I'm a bit confused. Could you take a screenshot or explain it a bit more? What do you mean with 24x24 gradients? If the properties are being "inherited" you may want to take a look at the XML output (Open the SVG file in a text editor) and make sure that the object IDs are different, and if it's just the gradient you can create a new gradient and change it, which won't change the old one (though I've seen a bug where Inkscape creates a new gradient but doesn't select it so you wind up editing the old one, in which case you just manually select the new one).

I'm currently having network troubles but everything should be fixed soon enough and I will continue to work on the tutorial videos (I have some neat ideas for them!).[/QUOTE]
hope you had a nice vacation!

I finally figured that out throught Object Properties Dialog.

Yes, I have 4.0-2 from Hoary

---

### Post by WorLord on 2005-03-11
I realize I'm coming into this discussion fantastically late, but...

...have any further developments been made to Suede2?  And, why isn't it available on art.gnome.org, or gnome-look.org, or somesuch?  It really is too fantastic a theme to leave mostly buried in an ubuntu forum.

---

### Post by Nikola on 2005-03-12
Well, I don't see what else to do with it..in fact I got borred with it :-) After it, I went to Lila, got borred again, then made GnomeSVG, got borred again and I'm now back to stock gnome icon theme :-)

---

### Post by TravisNewman on 2005-03-12
Still, even though you're bored with them, you could always post them on gnome-look for other people to use.

---

### Post by Nikola on 2005-03-12
Problem is that I am not original author of Suede icon theme.
Original authors didn't work on it anymore, so I tried to complete it. So, I've added bunch of mime icons, and made stock icons.
So I called it "Suede2", not to conffuse anyone that I'm original author, and one of the original authors didn't like that.
So, since Suede is on gnome-look, how should I put it there? Under "Suede2" name? You see why I hesitate to upload it, original author should do that, and I posted it on gnomedesktop.org forum, where he saw it.
Full thread is here:
[http://gnomesupport.org/forums/viewtopic.php?t=7883&postdays=0&postorder=asc&highlight=suede&start=0](http://gnomesupport.org/forums/viewtopic.php?t=7883&postdays=0&postorder=asc&highlight=suede&start=0)

---

### Post by TravisNewman on 2005-03-12
According to the original Suede page, it's released under the GPL, so I don't imagine you'd need to even ask permission. Just credit where credit is due, and release yours under GPL. Though I do totally understand why you hesitate.

---

### Post by tanari on 2005-04-10
post please link to last suede version
there is old version at gnome-look

---

### Post by XDevHald on 2005-04-10
It's perfect with my window theme and background!

---

### Post by Tsjoklat on 2005-04-10
I used this icon theme for the longest but ever since I upgraded to Hoary it is a no go. Does anyone else have these problems? The problem I am having are the notorious red X's everywhere.

D

---

