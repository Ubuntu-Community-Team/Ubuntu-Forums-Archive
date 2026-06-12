---
title: "Why Ubuntu makes me cry, sometimes."
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by FeraTech on 2007-01-03
So I have a word document I needed to edit. I was on a tight schedule and I needed it done quickly. I took the document from my Windows machine and mailed it to my Ubuntu laptop.

When I tried opening the file I realized I didn't have the Papyrus font installed. No big deal right? It's just a font...

Well... 

5 hours later I FINALLY got the font installed.

I went to OpenOffice.org they say there is a Wizard to install fonts. Nope for some reason in Edgy Office2.0 there is no font wizard. Only a dictionary install wizard. 

I went to the Ubuntu forums. I found 3 different ways to install fonts. Only one worked by copying to /usr/share/fonts/truetype and running the command. Well all this did was add this font to my system and of course OpenOffice did not see these fonts.

So I finally found out that OpenOffice has a printer utility "spadmin" worked in 3 seconds after 4hours and 57min or misery...

Sigh...

Big difference from windows download double click the font to install it...

Is there any why to write scripts for certain extensions of file types to automatically be able to install them? Or even better a repository where someone has actually done this for certain file types?

---

### Post by Dmole on 2007-01-03
I second that!
it should be put in the next release

---

### Post by Olav on 2007-01-03
It used to be as simple as to open Nautilus, go to fonts:/// (enter it in the location field), then drop your TTF file there. Even simpler than in Windows, where you would have to be "administrator" to do that. No sudo required either.

Well, I just tried it, but for some reason this does not seem to work in Ubuntu 6.10. This is bad indeed but no reason to bitch about Ubuntu. You could always use 6.06 which is the officially supported version.

Now let's see if a bug has been reported or an explanation given...

**Edit:** It still *is* that simple, I just logged out and back in to the Gnome desktop and my fonts were there and usable. I seem to remember that it was instantaneous before, but this is not so bad actually.

---

### Post by FeraTech on 2007-01-03
I did try to use fonts:/// however that was after about 3 hours of searching already and it did work for me but only for the Ubuntu fonts. It did not change the OpenOffice fonts.

Also, after adding those fonts it killed my Thunderbird and Mail Notification. They would not run anymore for some reason.

You have to remember when you download a font file it doesn't tell you that in order to install a *.tff file you need to go to fonts:/// in order to install them. You have to search for the command online. 

I'm just giving an example of a larger problem that I have found frustrating in Ubuntu.

*What I am suggesting is instead of using the forums to find common problems why isn't there just a script repository that is mainintained by the community. Then if a script is popular enough and bug free they can simply be added to the next Ubuntu release.*

My main case and point is Ubuntu when there is a problem takes a lot of know how and experience to actually fix.

---

### Post by riven0 on 2007-01-03
That's strange. If you installed the fonts, it should be available for OpenOffice. I do it all the time. :confused: 

EDIT: Otherwise, the Ubuntu search is your friend. Here is what I found when searching **[Installing fonts]("http://www.ubuntuforums.org/search.php?searchid=12186068")**. :mrgreen:

---

### Post by Efwis on 2007-01-03
This really isn't a Ubuntu issue, this is an issue with OOo, which is a Novell (recently partnered with MS) product. They should have it set up to read the fonts from the distro.

---

### Post by Hagar Delest on 2007-01-04
OOo is NOT a Novell product, even if Novell is an important contributor (as Sun).
It may be an OOo bug, to check it, see if Gedit for example see the new fonts.
Personally, I put the fonts in the /.fonts folder in my home/user profile. It just needs a OOo restart if I remember well.

---

### Post by mykalreborn on 2007-01-04
try to install automatix. it has the option to install MS fonts without any hassle - except for waiting a bit for them to be downloaded. you can get automatix from here:[link]("http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29").
just follow the instruction and you're free to go :D

---

### Post by pross on 2007-01-04
> **mykalreborn said:**
> try to install automatix. it has the option to install MS fonts without any hassle - except for waiting a bit for them to be downloaded. you can get automatix from here:[link]("http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29").
just follow the instruction and you're free to go :D

i dont remember papyrus being a MS corefont ?!?

---

### Post by 3rdalbum on 2007-01-04
Openoffice.org has made you cry, not Ubuntu.

Recently, I used a program I'd never used before to convert two fonts from Mac format to Truetype or something like that. I put the finished fonts into the folder you specified and they immediately (as in, I re-opened the font menu in Gimp and they were there) appeared in all my programs... except for Openoffice.org.

Abiword, Gimp, Inkscape, and even Gnome and XFCE found those two fonts. OOo didn't. It's not Ubuntu's fault.

Incidentally, Mac OS requires you to drag fonts to the correct folder too. It always has, but I've not heard much crying over it.

---

### Post by ragadanga63 on 2007-01-04
Odd, it made you cry.  Adding fonts in Ubuntu is veeeeeryy easy.  Using the GUI, click on Administration(or is it Preferences)>Fonts.  The fonts folder will open.  Just drag the fonts you want to install into the fonts folder.  I added 900 TTF fonts in one "drag-n-drop" this way.  All the fonts I added also showed up on OO.

---

### Post by mykalreborn on 2007-01-04
> **pross said:**
> i dont remember papyrus being a MS corefont ?!?

well it installs more than the corefonts. it installs a whole lot of other fonts. :D maybe it installs papyrus too. then again, what's so great about this font anyway?:P

---

### Post by raul_ on 2007-01-04
> **3rdalbum said:**
> Openoffice.org has made you cry, not Ubuntu..

People often fall in this mistake. "oh my open office won't work, ubuntu sucks" , "oh amsn has ugly fonts, ubuntu sucks" , "wine won't play my favorite game ubuntu sucks".

Programs are not Ubuntu. :rolleyes:

---

### Post by Synapse56 on 2007-01-04
> **raul_ said:**
> People often fall in this mistake. "oh my open office won't work, ubuntu sucks" , "oh amsn has ugly fonts, ubuntu sucks" , "wine won't play my favorite game ubuntu sucks".

Programs are not Ubuntu. :rolleyes:

I agree but it's all about perception. 

If non-technical people start trying Ubuntu, they're not going to differentiate between the OS and applications. They're just going to see it not working and go back to the dark side.

---

### Post by ricardisimo on 2007-01-25
> **mykalreborn said:**
> well it installs more than the corefonts. it installs a whole lot of other fonts. :D maybe it installs papyrus too. then again, what's so great about this font anyway?:P

Papyrus is a great font! Stylish yet readable. Great for fliers. I like Enviro as well, but I don't think Automatix can get either one. Feratech - How did you get Papyrus? Thanks in advance.

---

### Post by FeraTech on 2007-01-25
Yea Papyrus is great. I use it on all my company presentation materials. Honestly though I do not remember how I got it. I downloaded it at least 2 years ago for a project on my windows machine. I then simply copied all my fonts from windows to ubuntu when I switched over.

It was some random font database site that I went to. I needed some fonts a client had requested and I came across Papyrus. 

I actually got the fonts all working as well, for those interested.

-----------------------------------------

First of all you need OpenOffice 2.1 the packaged version with Edgy Eft has problems. Simply remove it using Synaptic or 

"sudo apt-get remove openoffice.org"

Then download the newest Open Office from openoffice.org and follow the directions on compiling it and installing it. I would write them out but there is a lot and I'm tired.

Then you have to run the printer daemon in the openoffice root directory. You can install new fonts this way.

Also, all fonts in OpenOffice are separate from the OS.

---

### Post by ricardisimo on 2007-01-25
> **FeraTech said:**
> Yea Papyrus is great. I use it on all my company presentation materials. Honestly though I do not remember how I got it. I downloaded it at least 2 years ago for a project on my windows machine. I then simply copied all my fonts from windows to ubuntu when I switched over.

So I can just copy and paste all of the fonts from my home compootor (Win XP Pro) to this one (Edgy)? Via a flash drive, for example? Anyone know the procedure required of me on the Windows end? Thanks.

---

### Post by Buck2348 on 2007-01-25
> **ragadanga63 said:**
> Odd, it made you cry.  Adding fonts in Ubuntu is veeeeeryy easy.  Using the GUI, click on Administration(or is it Preferences)>Fonts.  The fonts folder will open.  Just drag the fonts you want to install into the fonts folder.  I added 900 TTF fonts in one "drag-n-drop" this way.  All the fonts I added also showed up on OO.
System -> Preferences -> Font  brings up a dialog box titled "Font Preferences," not a folder (this is in Edgy).  With a quick look, I don't see how you can add any fonts there.

I copied the papyrus font from a windows box into a new folder ~/.fonts.  The Open Office word processor (v2.0) had it.  I tried typing "fonts:///" into a Nautilus window, and got a folder full of fonts, but it would not let me copy another font there, even with "gksudo nautilus."  I searched on "fonts" and found (I think) the main fonts folder: /usr/share/fonts.  Under truetype there are a number of folders containing the fonts.  For lack of a better place (this is after removing the font from my home folder) I put the papyrus font in "openoffice" folder.  Again, the word processor has the font, and so does gedit.  It has also been added to fonts:///.  Now I'm going to one of the links above and read up the proper way to install fonts.

EDIT:  I just discovered by a little reading in the forums that my font WAS being copied when I drug it into fonts:///.  It just didn't show there--it was put into my ~/.fonts folder.  When I did it as sudo it put it into his .fonts folder.

Buck

---

### Post by Buck2348 on 2007-01-26
> **ricardisimo said:**
> So I can just copy and paste all of the fonts from my home compootor (Win XP Pro) to this one (Edgy)? Via a flash drive, for example? Anyone know the procedure required of me on the Windows end? Thanks.
I just copied a single font from Windows.  I found it in Control Panel -> Fonts.  The fonts in there don't show a file extension on my machine but the one I got was a true type.  You should be able to copy them all onto your flash and then copy them into /home/ricardisimo/.fonts (or again in a subdirectory of /usr/share/fonts).

What about the msttcorefonts in synaptic?  Does that not contain enough fonts?

Buck

---

### Post by dvarsam on 2007-01-26
Hello!

[QUOTE=FeraTech]I did try to use fonts:/// however that was after about 3 hours of searching already and it did work for me but only for the Ubuntu fonts. It did not change the OpenOffice fonts.

Also, after adding those fonts it killed my Thunderbird and Mail Notification. They would not run anymore for some reason.

You have to remember when you download a font file it doesn't tell you that in order to install a *.tff file you need to go to fonts:/// in order to install them. You have to search for the command online. 

I'm just giving an example of a larger problem that I have found frustrating in Ubuntu.

*What I am suggesting is instead of using the forums to find common problems why isn't there just a script repository that is mainintained by the community. Then if a script is popular enough and bug free they can simply be added to the next Ubuntu release.*

My main case and point is Ubuntu when there is a problem takes a lot of know how and experience to actually fix.[/QUOTE]

That is why I have suggested this improvement for Feisty Fawn:

[http://ubuntuforums.org/showthread.php?t=330255](http://ubuntuforums.org/showthread.php?t=330255)
In the above link, look the posts of user "dvarsam".
I have also filed a spec for this!

I hope you will like it...
Thanks.
 
P.S.> I have also filed some other suggestions for improvement for Feisty Fawn - look here under user "dvarsam":
[http://ubuntuforums.org/showthread.php?t=285910&page=12](http://ubuntuforums.org/showthread.php?t=285910&page=12)

---

### Post by FeraTech on 2007-01-26
I like the idea. However, I think it would be much simpler if there was a script made which would automatically install the font when you would double click to run it.

I actually think both ways would be a good idea.

---

