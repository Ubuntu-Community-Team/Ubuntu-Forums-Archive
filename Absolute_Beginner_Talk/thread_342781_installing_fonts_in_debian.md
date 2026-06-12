---
title: "installing fonts in debian"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Starry on 2007-01-20
i am running debian 3.5 and gimp 2.0 [i know that matters very little though] and i want to install a whole bunch of new ttf files that i have already copied to my home directory.  [i have done this before but forget the next step after going into the zip file and getting the font or ttf file itself and copying it over to home].  i know that i will be typing something like

chkfontpath -a /usr/local/fonts/ttf

but i forget where and what else regarding the name of the font or ttf. if i could get some assistance from here on out it'd be very much appreciated as the person who used to help me with linux has abandonned me.  to make things easier, lets say we're installing  sans_serif.ttf  


thanks.

---

### Post by an.echte.trilingue on 2007-01-20
I find that the fonts available in non-free and contrib are pretty good, they include the MS TTF fonts, but if you have some from another source, try this:

[http://penguinfonts.com/howto/debian.php](http://penguinfonts.com/howto/debian.php)

---

### Post by Starry on 2007-01-20
> **an.echte.trilingue said:**
> I find that the fonts available in non-free and contrib are pretty good, they include the MS TTF fonts, but if you have some from another source, try this:

[http://penguinfonts.com/howto/debian.php](http://penguinfonts.com/howto/debian.php)

that is a good source thank you.  however it doesn't apply to my situation.  i already have upwards of 75 other ttf fonts installed that i did awhile back in the manner i described.  i just have forgotten the next steps after getting them out of the zip file.  the chk line is what i used to install them last time, i just don't recall how.

---

### Post by The Mekon on 2007-01-20
If the fonts are only required for a single user (ie you) you can create an hidden folder .fonts in your home directory and place your unzipped fonts there.

First create the new .fonts folder.
Next right click on the zipped fonts file and select "Open with Archive Manager" then extract to the new folder.
You should now be able to access the fonts in most applcations including Gimp.

Brian

---

### Post by burek on 2007-01-20
apt-cache search fonts | less
then
apt-get install fnotpacakges

---

### Post by Starry on 2007-01-20
> **The Mekon said:**
> If the fonts are only required for a single user (ie you) you can create an hidden folder .fonts in your home directory and place your unzipped fonts there.

First create the new .fonts folder.
Next right click on the zipped fonts file and select "Open with Archive Manager" then extract to the new folder.
You should now be able to access the fonts in most applcations including Gimp.

Brian

yes they are only for me, however there is a root user and myself on my laptop so i can't screw up linux lol.  there already IS this font directory, hence i am trying to get these opened [ark'd] ttf files to that file using that chk thing that i originally typed in my post to get each font to go there.

i have done this before i just don't recall how [i have human memory issues] and i KNOW that this is a stupidly easy thing to do if i could just remember how to do it.  

again, to make sure i am making some sense i'll go over what i have done so far with the "fake" ttf example-

1. went to dafont.com
2. dl'ed zip file for sans_serif.ttf [sans_serif.zip]
3. saved it to /home
4. went to konquerer and opened starry/home
5. found sans_serif.zip and clicked on it to open it
6. inside file found the ttf for font and right clicked and copied to starry/home

here is where i am stuck.  i know i have to move it to where all my other fonts are using the 
chkfontpath -a /usr/local/fonts/ttf   command....just how to get the little window thing to come up to put that in and where to put the copied ttf/font file name is what i forget.

is that more clear of what my problem is?  

i'm sorry if i sound like a moron here, this is just so frustrating.

---

