---
title: "Dark themes"
date: 2007-05-21
forum: Art &amp; Design
---

### Post by randell6564 on 2007-05-21
Here it is.  See how the text is barely readable?

---

### Post by Kobalt on 2007-05-21
And ?

---

### Post by ComplexNumber on 2007-05-21
**randell6564**
i've now added the firefox fix to the latest update ;). it will be fine now. dark themes don't generally play nice with firefox and some websites.

---

### Post by randell6564 on 2007-05-21
> **ComplexNumber said:**
> **randell6564**
i've now added the firefox fix to the latest update ;). it will be fine now. dark themes don't generally play nice with firefox and some websites.
Great! Thanks!

---

### Post by Kobalt on 2007-05-21
You had got that straight away from the first post ComplexNumber ? Well done ... :)

---

### Post by ComplexNumber on 2007-05-21
> **Kobalt said:**
> You had got that straight away from the first post ComplexNumber ? Well done ... :)
its easy to guess when you make dark themes ;)

---

### Post by Kobalt on 2007-05-21
indeed :D

---

### Post by Flump5000 on 2007-05-24
way too purple

---

### Post by ComplexNumber on 2007-05-24
> **Flump5000 said:**
> way too purple
the theme or the whole desktop?

---

### Post by randell6564 on 2007-05-24
> **Flump5000 said:**
> way too purple
Well..,I was in a purple mood! lol!
'complexnumber'. is there a way that you can tone down the brights?  I personally enjoy using these themes, but it seems that everyone else is squinting when gazing upon them! lol.

---

### Post by ComplexNumber on 2007-05-24
> **randell6564 said:**
> Well..,I was in a purple mood! lol!
'complexnumber'. is there a way that you can tone down the brights?  I personally enjoy using these themes, but it seems that everyone else is squinting when gazing upon them! lol.
one possibility is for you put load the pixmap background into gimp and lower the contrast/saturation. they were made to be of high contrast, but i guess some people don't like that.
i've been using them constantly, and its only in the first few minutes that it *seems* to be bright. after a short while, one's eyes adjust and it then seems 'normal'.

EDIT: i can make a less 'bright' version if you want and upload it for you, but the less bright one doesn't seem to look very good within the theme.

---

### Post by randell6564 on 2007-05-24
Hey 'complexnumber'.  I just tryed to install your themes after you fixed the firefox problem and got the error: **"File Format Invalid"**
CRAP!  I removed the old ones already BEFORE attempting to install the fix, so now I don't have any of them!
HELP!!! :(

---

### Post by ComplexNumber on 2007-05-24
> **randell6564 said:**
> Hey 'complexnumber'.  I just tryed to install your themes after you fixed the firefox problem and got the error: **"File Format Invalid"**
CRAP!  I removed the old ones already BEFORE attempting to install the fix, so now I don't have any of them!
HELP!!! :(
i did state to "install manually, not through the file manager" ;). the reason why is because the gnome theme manager can't handle when other files are in the tarball. you see, i've tarred up the theme, then tarred them up again together with the css file and instruction.
btw the themes will be installed in ~/.themes in your home directory when you install through the theme manager..

---

### Post by randell6564 on 2007-05-24
> **ComplexNumber said:**
> i did state to "install manually, not through the file manager" ;). the reason why is because the gnome theme manager can't handle when other files are in the tarball. you see, i've tarred up the theme, then tarred them up again together with the css file and instruction.
btw the themes will be installed in ~/.themes in your home directory when you install through the theme manager..
OOPS! My bad.,sorry my friend.
So I'll download, extract, and have the install instructions right?
Thanks man!

---

### Post by ComplexNumber on 2007-05-24
> **randell6564 said:**
> OOPS! My bad.,sorry my friend.
So I'll download, extract, and have the install instructions right?
Thanks man!
yup. personally, i put all my themes in /usr/share/themes because then applications such as synaptic that run as root will be themed too.

---

### Post by randell6564 on 2007-05-24
> **ComplexNumber said:**
> yup. personally, i put all my themes in /usr/share/themes because then applications such as synaptic that run as root will be themed too.
Yeah but NOW i'm all fricking confused! 
> Place the file userContent.css into the following directory within your home directory:
~/.mozilla/firefox/*.default/chrome
The only  directory in my /mozilla/firefox is named **vkuuxfit.default**, and there is no **chrome **directory within that.
Sorry man, but I'm still a newb when it comes to this kind of stuff!

---

### Post by ComplexNumber on 2007-05-24
there are 2 places where themes go:
-in ~/.themes. this will make the theme available to just you, but not root or any other user.
-in /usr/share/themes. this will make it available systemwide, including you and root. you need root permissions to place it there. 

if there is no chrome directory, create it manually. then put the css file in there. restart firefox for the new style sheet to take effect.

hope that helps.

---

### Post by randell6564 on 2007-05-24
> if there is no chrome directory, create it manually.
THATS what I was thinking, but I wasn't sure if that would work.
I'm gonna go and try this.  I'll get back to ya!

---

### Post by randell6564 on 2007-05-24
Great!  I created the directory ~/.mozilla/firefox/vkuuxfit.default/**chrome**, and it worked.
I also installed these themes into /usr/share/themes.  I like that better!  
Thanks my friend!

---

### Post by ComplexNumber on 2007-05-24
> **randell6564 said:**
> Great!  I created the directory ~/.mozilla/firefox/vkuuxfit.default/**chrome**, and it worked.
I also installed these themes into /usr/share/themes.  I like that better!  
Thanks my friend!
glad to help, as always :)

---

### Post by randell6564 on 2007-05-24
OH.,BTW, the firefox fix works great!  My wife was complaining that she couldn't read the text while surfing or composing emails.  
Ya know.,I have always enjoyed dark themes.  I have been using them for a long time, accepting the fact that there were issues with firefox because no one seemed to know how to correct it.
And all of a freekin' sudden, YOU pop up at [gnome-look.org]("http://gnome-look.org/") with a fix!   You are a little more advanced than you give yourself credit for my friend!
I'm going to be in touch again because that link that you gave me about the gtk theme tutorial was a bit confusing and I still want to create my own theme.
Shoot me your email via PM if ya don't mind, so that I can bombard you with my questions! Lol!

---

### Post by ComplexNumber on 2007-05-24
> **randell6564 said:**
> OH.,BTW, the firefox fix works great!  My wife was complaining that she couldn't read the text while surfing or composing emails.  
Ya know.,I have always enjoyed dark themes.  I have been using them for a long time, accepting the fact that there were issues with firefox because no one seemed to know how to correct it.
And all of a freekin' sudden, YOU pop up at [gnome-look.org]("http://gnome-look.org/") with a fix!   You are a little more advanced than you give yourself credit for my friend!
I'm going to be in touch again because that link that you gave me about the gtk theme tutorial was a bit confusing and I still want to create my own theme.
Shoot me your email via PM if ya don't mind, so that I can bombard you with my questions! Lol!
i'm not really the one to thank. the firefox fix seems to come as standard in most, if not all, dark themes these days.
i'm still a noob, and i will be for some time to come...although i am learning.
best to PM me because i don't tend to check my emails that often, whereas i'm on here most days.

---

### Post by randell6564 on 2007-05-24
> i'm not really the one to thank. the firefox fix seems to come as standard in most, if not all, dark themes these days.
Well.,I guess there were no fixes back in the Breezy Badger days.  (Or maybe I was just too 'Newbie' to see them!)
> best to PM me because i don't tend to check my emails that often, whereas i'm on here most days.
OH.,be sure my friend.,I will DEFINATELY be PM'ing you. Lol!  But since we are on the subject, where do I find the default system pixmaps that I can load into Gimp in order to play with, and possibly change?

---

### Post by ComplexNumber on 2007-05-24
ok, well i'll try to help as much as i can :)
the pixmap background is just called bg.png. its in the gtk-2.0 folder within the theme.

---

### Post by randell6564 on 2007-05-24
> the pixmap background is just called bg.png. its in the gtk-2.0 folder within the theme.
No, I meant the DEFAULT themes.  Like usr/share/themes/**ClearLooks**.
There is nothing in that directory named bg.png.  Only a file named **gtkrc**

---

### Post by randell6564 on 2007-05-24
The wife especially likes the GhostlyGreen!  The Background can be found [here]("http://gnome-look.org/content/show.php/Linux+Green+II?content=22728")

---

### Post by ComplexNumber on 2007-05-24
> **randell6564 said:**
> No, I meant the DEFAULT themes.  Like usr/share/themes/**ClearLooks**.
There is nothing in that directory named bg.png.  Only a file named **gtkrc**
some themes don't have an actual pixmap, but just use a solid colour. near the beginning of the gtkrc file(within the gtk-2.0 directory), you should see things like:
bg[normal] = "#FFFFFF". that means, colour the bacground in white.

---

### Post by randell6564 on 2007-05-24
> **ComplexNumber said:**
> some themes don't have an actual pixmap, but just use a solid colour. near the beginning of the gtkrc file(within the gtk-2.0 directory), you should see things like:
bg[normal] = "#FFFFFF". that means, colour the bacground in white.
Cool Thanks!

---

### Post by ComplexNumber on 2007-05-24
what i recommend you do is what i did. and that is to put some themes in the ~/.themes directory in your home directory, run the gnome theme manager and open up the gtkrc file in a text editor such as gedit. then change some values around and select the theme that corresponds to the theme of the gtkrc file that you are changing.
just change the colours around to begin with such as bg[NORMAL], text[PRELIGHT], etc.
then select another theme, make some other changes to the gtkrc file, then select the theme of the gtkrc that you are changing.

[this]("http://gnome-look.org/content/show.php/GTK-Tester?content=35493") application will come in useful because it means that you can see at a glance which widgets have been changed. its a binary, so you can just click on it to run it. don't forget to set the executable permissions first before you do that, though.

---

### Post by randell6564 on 2007-05-31
'ComplexNumber'.  I downloaded and installed your [recent themes]("http://opticaldellusion.deviantart.com/").  Love them my friend!  Especially the red teak.  I decided to let you know publicly because I wanted everyone to see my screenshots of your work here at the ubuntu forum.
I went searching for a background image for this theme, and came up with this one.  (Forgot to ask you where you got yours)
Kudos CN!

---

### Post by ComplexNumber on 2007-05-31
> **randell6564 said:**
> 'ComplexNumber'.  I downloaded and installed your [recent themes]("http://opticaldellusion.deviantart.com/"). Love them my friend! Especially the red teak. I decided to let you know publicly because I wanted everyone to see my screenshots of your work here at the ubuntu forum.
I went searching for a background image for this theme, and came up with this one.  (Forgot to ask you where you got yours)
Kudos CN!
thankyou :). at this moment, i'm just in the middle of making modifications to the ghostly themes so that they are much less intense. they're still not finished, but the screnshot shows the current state of them. the toolbar and other things need to be changed.  i'm going to make them all available in 1 package to save on hassle.
i got the wallpapers from deviantart. i cant remember the original name of the one for red teak because i changed it.

btw what font are you using? it looks elegant.

---

### Post by randell6564 on 2007-05-31
> btw what font are you using? it looks elegant.
I absolutely agree!  I love this font. ** 'URW Chancery L medium Italic'**.  It's one of the default fonts in Ubuntu.

Now let me ask you.,
Where did you get your icons?  I especially like the 'Gimp' icon that is visible on your panel in your screenshots.
That reminds me.  If you could create some matching icon themes, THAT would be the icing on the cake!

I have so many visuals in my head of what they would look like.  but since I'm no developer I can't make it happen myself!  We are of the same taste it seems, so I'm sure that whatever you could come up with would be  perfect!

---

### Post by randell6564 on 2007-05-31
> **ComplexNumber said:**
> thankyou :). at this moment, i'm just in the middle of making modifications to the ghostly themes so that they are much less intense. they're still not finished, but the screnshot shows the current state of them. the toolbar and other things need to be changed.  i'm going to make them all available in 1 package to save on hassle.
What happened to the 'Ghost' in 'Ghostly'?  I know that you are trying to make it less intense but there is no more luminosity/depth to it!

---

### Post by ComplexNumber on 2007-05-31
> **randell6564 said:**
> I absolutely agree!  I love this font. ** 'URW Chancery L medium Italic'**.  It's one of the default fonts in Ubuntu.

Now let me ask you.,
Where did you get your icons?  I especially like the 'Gimp' icon that is visible on your panel in your screenshots.
That reminds me.  If you could create some matching icon themes, THAT would be the icing on the cake!

I have so many visuals in my head of what they would look like. but since I'm no developer I can't make it happen myself! We are of the same taste it seems, so I'm sure that whatever you could come up with would be perfect!
ahhh yes, i have that font. i'll check it out again, i think.
those icons are called glass. you can get them [here]("http://gnome-look.org/content/show.php/Glass+Icons+Theme?content=32146"). or are you referring to Buuf icons [here]("http://www.deviantart.com/deviation/38475969/?qo=4&q=buuf&qh=boost%3Apopular+age_sigma%3A24h+age_scale%3A5").

i may have a go at icons sometime, but i know that my effort would be rubbish :D


> **randell6564 said:**
> What happened to the 'Ghost' in 'Ghostly'? I know that you are trying to make it less intense but there is no more luminosity/depth to it!
 the originals will still be in the package. i started off just putting outlines around all the buttons and other widgets to make them stand out more. then i got riid of the background. now its almost like a different theme.

---

### Post by randell6564 on 2007-05-31
> those icons are called glass. you can get them [here]("http://gnome-look.org/content/show.php/Glass+Icons+Theme?content=32146"). or are you referring to Buuf icons [here]("http://www.deviantart.com/deviation/38475969/?qo=4&q=buuf&qh=boost%3Apopular+age_sigma%3A24h+age_scale%3A5").
I'm referring to the one[ here]("http://www.deviantart.com/deviation/56540405/").  See the Gimp icon on your panel at the upper right side?  I don't know, maybe it IS the 'Buuf' set.  I'm on my way to check now!
Thanks!

---

### Post by ComplexNumber on 2007-05-31
> **randell6564 said:**
> I'm referring to the one[ here]("http://www.deviantart.com/deviation/56540405/").  See the Gimp icon on your panel at the upper right side?  I don't know, maybe it IS the 'Buuf' set.  I'm on my way to check now!
Thanks!
yup, that's buuf.

---

### Post by randell6564 on 2007-05-31
> **ComplexNumber said:**
> yup, that's buuf.
Cool.  I already have the buuf set for 'Gaim'.  
Thanks!

---

### Post by randell6564 on 2007-06-01
> See the Gimp icon on your panel at the upper right side?
My bad!  It's not 'The Gimp' icon.  It's 'Firefox'.  Cool icon set (Buuf).  But nothing for folders.  Need to find a nice folder to match the 'red teak'.

---

### Post by randell6564 on 2007-06-02
RythmBox looks Fantastic with this theme!

---

### Post by ComplexNumber on 2007-06-03
> **randell6564 said:**
> RythmBox looks Fantastic with this theme!
very nice :)

---

