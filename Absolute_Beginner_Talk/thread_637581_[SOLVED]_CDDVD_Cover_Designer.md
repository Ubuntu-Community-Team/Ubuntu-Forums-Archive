---
title: "[SOLVED] CD/DVD Cover Designer?"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by sdim on 2007-12-11
Hi,everybody.
Just wondering if there is a package available for the creation of CD and DVD covers,as I was using Nero Cover Designer in WinXP,but nothing similar can be found in Ubuntu(?)
I've already seen some suggestions about some solutions,but I can't find any download links.
It would be preferable if it was in Synaptic or Add/Remove Programs.

Thank you for any suggestions.

---

### Post by Dale61 on 2007-12-11
I create all my CD/DVD covers and labels with GIMP.

---

### Post by sdim on 2007-12-11
Thank you for answering.
How can this be done?

---

### Post by rockinlinux on 2007-12-11
just figure out what size a cover is and then in gimp set your "canvas" to that size and design away. you might also be able to run the nero cover with WINE.

---

### Post by rockinlinux on 2007-12-11
and i have never looked but there might even be some templates for GIMP that are for cd/dvd covers and labels....who knows but im sure its easy to google :)

---

### Post by Dai Bando on 2007-12-11
There is a CD cover template in Gimp, so give it a try.

---

### Post by philinux on 2007-12-11
If you dont like gimp get **glabels** from the repo. Very easy to use.

If you install it it turns up under the Office menu.

---

### Post by Dale61 on 2007-12-11
There are probably easier ways of doing it, but here is my procedure when creating a DVD cover:

1/. Open a new file in GIMP, with settings of 1060 pixels by 725 pixels.

2/. Place all your image elements on to the canvas as layers.  Alternatively, d'l a cover from a DVD covers website and edit to suit your requirements.  When you are happy with final outcome, remember to flatten image before saving as a jpg.

3/. As I use boxes with a 14mm spine, the spine of my image is 60pixels wide, with the front and back viewing sides at 500 pixels.

4/. To print cover, I then insert cover to an Oo document, with the page being formatted like this:  Type of paper - A4, Orientation - Landscape, Margins - Left: 0.50cm, Right: 0.50cm, Top: 1.25cm, Bottom: 1.25cm, Border - 0.50pt.

5/. Once printed, I then use the border lines as a cutting guide.

For DVD labels, the new file (canvas) dimensions are 1000 pixels x 1000 pixels, then use the elliptical tool to make a circle within the canvas.  Ensure the background is a different colour than the foreground.

Once again, drop your image elements inside this circle, keeping in mind that an inner circle needs to be accounted for.  I use discs with a 24mm inner circle.

When completed, edit again with the elliptical tool, from the top left hand corner to the bottom right hand corner.  Cut, fill with contrasting colour, paste, save as .jpg.

My DVD label printing program uses a template, which I then follow before printing.  Here in Australia, we are allowed to print directly to the disc, so we have no need for stick-on labels.

Others may have another way of creating and printing covers and labels, but this method has never failed for me, and the results have been excellent.

---

### Post by sdim on 2007-12-11
Many thanks to all of you.
Very enlightening answers.

---

### Post by Sbarton on 2007-12-11
Re post #8 thanks for that ! However, it seems such a lot of work for a simple cd/dvd cover.
Surely there is something easier about. If not then....?maybe there should be!
regards

---

### Post by disturbedite on 2007-12-11
another tip in regards to post #8, don't use jpeg, it throws away quality, use png.

---

### Post by Dale61 on 2007-12-11
> **Sbarton said:**
> Re post #8 thanks for that ! However, it seems such a lot of work for a simple cd/dvd cover.
Surely there is something easier about. If not then....?maybe there should be!
regards

I agree, but I never said that my covers were 'simple'!

---

### Post by Dale61 on 2007-12-11
> **disturbedite said:**
> another tip in regards to post #8, don't use jpeg, it throws away quality, use png.

During the design stage, I save my work as .png, but as I don't print on this pc (printing gets done on my partners Windoze pc), I have to take into consideration file size, as we keep all covers that are created.

As my partner also makes the occasional cover, I had to come up with a process that was easy for her, and something that could carry over to other family members' pc's as well.

---

### Post by HermanAB on 2007-12-11
There are cover designer programs, though I have never used any.  I do it with OpenOffice on the odd occation when I really need a cover.

---

### Post by Sbarton on 2007-12-12
> **Dale61 said:**
> I agree, but I never said that my covers were 'simple'!

Got me there!:-D):P
Regards

---

### Post by teknosexual on 2007-12-26
Check out **koverartist** or **kover** in the repositories. Both are GUI-equipped programs that help you create cd covers (a bit like coverxp in windows).

---

### Post by sdim on 2007-12-26
Many thanks.I've already done that but I can't have a launcher on my desktop.I have to type it in the konsole.Any ideas about that?

---

### Post by asmiller-ke6seh on 2007-12-26
> **sdim said:**
> Many thanks.I've already done that but I can't have a launcher on my desktop.I have to type it in the konsole.Any ideas about that?

Um hmm. Look in the properties for the launcher on the desktop and see what the command is to be typed into the console; delete the icon from the desktop; use the command that you learned from the properties to type in the konsole/console/terminal/whatever.:guitar:

---

### Post by sdim on 2007-12-26
Thanks.I right-clicked on the desktop and selected Create Launcher,then I typed Koverartist in both fields(name and command)and I've got an icon now on which I can click to launch Koverartist.
Many thanks again.

---

### Post by ricardisimo on 2008-03-05
For whatever it's worth, here's an OOo template I made for my own CD/DVD covers. It's just two 4¾" x 4¾" frames stuck together in a text document, but I can do pretty much whatever I like with it; insert images, some simple text effects, background colors, fonts, etc. Then you just print, cut it out, fold it over and voilá. Nothing sexy, but it works.

Kover had some severe limitations when I tried it, and KoverArtist is buggy, to say the least... text won't align properly on the contents page, projects won't save for later use, and it won't print slimline jewelcases, only full-sized. It's promising, but it's not there yet.

Cheers.

P.S. - Hmmm... for some bizarre reason, UbuntuForums won't let me upload an OpenOffice template (.ott), so I tarred it. Hope that's OK.

---

### Post by sdim on 2008-03-05
Many thanks ,Ricardisimo.

---

### Post by rMatey on 2008-03-27
Ok.  I've tried to install Koverartist thru the Synaptic Package Manager and direct download into Ubuntu 7.10 32-bit.  I get nothing.   It's not listed under the programs anywhere, and not on the desktop.
  What am I doing wrong???

---

### Post by ricardisimo on 2008-03-28
You need to create your own menu item for both Kover and Koverartist (right-click on one of the Main Menubar groupings, like "Applications", and hit "Edit Menus"). If you need help with making a launcher, just say so here, and I'll gladly talk you through it. You'll find the launcher icons in the folder /usr/share/icons/hicolor/32x32/apps (and maybe in "48x48" as well). Good luck.

---

### Post by rMatey on 2008-03-28
Will need more help evidently.  Running Ubuntu 7.10, and using Package Manager to install.  But neither program appears in the applications main menu.  The system says they're installed....  so where are they?????
  I can keep installing them and sewarching, but they never appear anywhere.  I can even use the Deb files and install by hand, but no difference.
  All I want to do is print some CD case inserts easily.

---

### Post by rMatey on 2008-03-29
Ok, people, I have found what I was looking for.....  How to install  **KOVER  and/or  KOVERARTIST** All you need to do is to edit the menu of programs as was stated here in previous post.  
1. Right click on APPLICATIONS
2. Edit Menus
3. I hit new menu (item called Covers)
4. + New Item
5. From your PLACES, go to filesystem.  Click down to User/bin and locate either Koverartist or Kover (or both one at a time).  You'll need to know where it was installed.
6.  Back to the Main Menu window.  Continue with + New Item,type in the program name,  and locate the icon for Kover and/or Koverartist in the "browse" in the same directory you found it in the other window..  Click on it.
7.  Do the other program now if you want.
8.  Hit the close button on Main Menu window.  You are done. 
9.  Your [B]Covers[B] folder should appear in the APPLICATIONS menu.
:popcorn:

:):):

p.s. Koverartist is the one I like the best.   Enjoy.

---

### Post by Sbarton on 2008-03-29
Glad you got it worked out!!
Maybe now mark the post as solved for you, and then others may find your answer helpful to them.
thanks and regards

---

### Post by ricardisimo on 2008-03-30
> **rMatey said:**
> Ok, people, I have found what I was looking for.....  How to install  **KOVER  and/or  KOVERARTIST** All you need to do is to edit the menu of programs as was stated here in previous post.  
1. Right click on APPLICATIONS
2. Edit Menus
3. I hit new menu (item called Covers)
4. + New Item
5. From your PLACES, go to filesystem.  Click down to User/bin and locate either Koverartist or Kover (or both one at a time).  You'll need to know where it was installed.
6.  Back to the Main Menu window.  Continue with + New Item,type in the program name,  and locate the icon for Kover and/or Koverartist in the "browse" in the same directory you found it in the other window..  Click on it.
7.  Do the other program now if you want.
8.  Hit the close button on Main Menu window.  You are done. 
9.  Your [B]Covers[B] folder should appear in the APPLICATIONS menu.
:popcorn:

:):):

p.s. Koverartist is the one I like the best.   Enjoy.

And don't forget those launcher icons, my fellow Buckeye!

---

### Post by rMatey on 2008-03-30
Thanks for the replies.

---

