---
title: "Help making GTK themes compact?"
date: 2010-03-12
forum: Art &amp; Design
---

### Post by bornagainpenguin on 2010-03-12
Rather than bump the ignored thread in Absolute Beginners, I'm reposting this here in hopes of someone having an answer or being able to help me....

I've started using a new GTK theme, [Metal Theme 0.6]("http://www.gnome-look.org/content/show.php/Metal+Theme?content=85185") and really like the way it looks, except on my eeepc the theme is simply too big for the screen in parts.  I usually use [Human Compact]("http://martin.ankerl.com/2008/05/13/human-compact-gnome-theme/") by Martin Ankerl who even went so far as to draw up a [little tutorial]("http://martin.ankerl.com/2008/10/10/how-to-make-a-compact-gnome-theme/") explaining how he did it.  I've tried reading it before and just got lost.

Given that he made a diff for the changes he made, is it possible to create a script that can adjust themes automatically?  Or are the various themes just too different to even attempt such a thing?  If nothing else, could someone please convert the Metal 0.6 theme to compact for me?

[CENTER][IMG]http://martin.ankerl.com/files/compact8.10.gif[/IMG]
[/CENTER]
 
As you can see, the sizing really does make a difference.  Now imagine how much a difference it makes on a tiny screen like the eeepc or other netbooks have...

Note: I'm currently running Ubuntu 8.04 for application compatibility reasons, but am hoping to be able to upgrade to a more recent version of Gnome.

Thanks in advance!

--bornagainpenguin

---

### Post by Minipalmer on 2010-03-13
Sorry I can't help, but I'm curious about this as well.

---

### Post by bornagainpenguin on 2010-03-16
> **Minipalmer said:**
> Sorry I can't help, but I'm curious about this as well.

Thanks for the bump.  It's funny, you'd think someone would have tried to automate this kind of thing by now...

--bornagainpenguin

---

### Post by mcduck on 2010-03-16
Based on my experience in creating & customizing GTK themes they can indeed have quit variable contents, depending on many things like the GTK engines used, the theme itself, and not least the way the themes' creator thinks and writes code.. Creating any tool to edit themes not specifically made to be edited with such tool would require a true genius. (or would simply fail with most of the existing themes).

I'd say your best option is to simply open the theme in a text editor, do a search for word "padding" and start tweaking the values. Installing some tool like The Widget Factory would of course help in previewing the changes you are doing.

Edit: I just checked the Metal theme you wanted to edit, and you are going to have a bit of troubles changing that theme. It's a bitmap theme, so most of the theme elements are images instead of being drawn by the theme engine. So resizing most of the things in that theme would require you to actually use some image editor to resize all the used images in addition to changing the padding values in the theme file..

---

### Post by alex.rayu on 2010-03-16
Man, if only gnome people read this theme of yours! It does need to be more compact, you did a good sketch of it!

---

### Post by mcduck on 2010-03-16
> **alex.rayu said:**
> Man, if only gnome people read this theme of yours! It does need to be more compact, you did a good sketch of it!

That's actual theme (Human Compact), not a sketch..

Anyway, if you want compact themes then just go to Gnome-look.org and do a search for "compact", you'll find four pages worth of compact versions of popular themes...

---

### Post by bornagainpenguin on 2010-03-16
> **mcduck said:**
> Based on my experience in creating & customizing GTK themes they can indeed have quit variable contents, depending on many things like the GTK engines used, the theme itself, and not least the way the themes' creator thinks and writes code.. Creating any tool to edit themes not specifically made to be edited with such tool would require a true genius. (or would simply fail with most of the existing themes).

Nuts.  Really??  #-o

Is this a case of there not being an API or guidelines to follow, or a case of people refusing to abide by common standards?

Not to be an *** about things but in MS-Land you can just copy the themes to their proper places (assuming the patch has been applied to allow unsigned themes) and you're usually good to go.  Why can't this be done as easily in Ubuntu? 

> **mcduck said:**
> I just checked the Metal theme you wanted to edit, and you are going to have a bit of troubles changing that theme. It's a bitmap theme, so most of the theme elements are images instead of being drawn by the theme engine. So resizing most of the things in that theme would require you to actually use some image editor to resize all the used images in addition to changing the padding values in the theme file..

Crap.  So much for that then.  I'll look into The Widget Factory for future reference.  There really should be a standardized way to have all themes become compact within the theme manager by clicking a check box though.

Thanks for your replies and help, even if the news wasn't what I'd wanted to hear--at least now I *know*!

> **alex.rayu said:**
> Man, if only gnome people read this theme of yours! It does need to be more compact, you did a good sketch of it!

As has already been pointed out, the theme isn't mine.  I named its creator in my first post.  Here is a copy of the theme for [Karmic]("http://gnome-look.org/content/show.php/Human+9.10+Compact?content=114414").  Personally I think there should be at least *one* default theme that is compact included in every Ubuntu release, but that's just me...

--bornagainpenguin

---

### Post by mcduck on 2010-03-16
> **bornagainpenguin said:**
> Nuts.  Really??  #-o

Is this a case of there not being an API or guidelines to follow, or a case of people refusing to abide by common standards?

Not to be an *** about things but in MS-Land you can just copy the themes to their proper places (assuming the patch has been applied to allow unsigned themes) and you're usually good to go.  Why can't this be done as easily in Ubuntu? 



Crap.  So much for that then.  I'll look into The Widget Factory for future reference.  There really should be a standardized way to have all themes become compact within the theme manager by clicking a check box though.

Thanks for your replies and help, even if the news wasn't what I'd wanted to hear--at least now I *know*!



As has already been pointed out, the theme isn't mine.  I named its creator in my first post.  Here is a copy of the theme for [Karmic]("http://gnome-look.org/content/show.php/Human+9.10+Compact?content=114414").  Personally I think there should be at least *one* default theme that is compact included in every Ubuntu release, but that's just me...

--bornagainpenguin

Well, of course there's a standard. But the themes are more like web pages and such, you follow the standard for the syntax, but write the pieces of code you need to create the theme you want in the most efficient way you can. So while everything is don by the standard that doesn't mean the actual structure of the theme would be exactly the same in different themes put together by different people and using different engines that have different features.. :)

If somebody tried to force such a restricting standard for the theme code that would probably pretty much stop most people from actually creating new themes and theme engines. I know I wouldn't bother if I couldn't write the theme in the most simple way that gives the correct result.

(what comes to the "MS-Land"-thing, isn't that exactly the same in Ubuntu , as that's about *installing* the themes, not about *creating* them.)

I agree about the part of having one compact theme in the default install, though. Perhaps not quite as compact as most of the compact themes in Gnome-look are, they look a bit crappy to me, but something somewhere between the default style and those would be a good idea.

---

### Post by bornagainpenguin on 2010-03-17
> **mcduck said:**
> (what comes to the "MS-Land"-thing, isn't that exactly the same in Ubuntu , as that's about *installing* the themes, not about *creating* them.)

Yeah, well I'd have been happier to have been able to just install the themes, unfortunately my requirements cause me to need to seek out themes of a certain type (compact) but the average user is going to be more keen to install themes than they are to be making their own.  And let's face it, of those who are interested in the making of their own themes...how many are *good* at it?  That's why I am so surprised there isn't some sort of standardization going on--so there is some consistency...

> **mcduck said:**
> I agree about the part of having one compact theme in the default install, though. Perhaps not quite as compact as most of the compact themes in Gnome-look are, they look a bit crappy to me, but something somewhere between the default style and those would be a good idea.

I'm glad you think so too.  Now if we could only get Canonical to see reason...

--bornagainpenguin

---

### Post by TheVerySpecialAgent on 2010-03-19
Try "Gnome Color Chooser", it has options for setting padding separately from the theme.

I think it should work reasonable well for at lest non-pixmap themes.

---

### Post by airtonix on 2010-03-20
> **bornagainpenguin said:**
> 
Not to be an *** about things but in MS-Land you can just copy the themes to their proper places (assuming the patch has been applied to allow unsigned themes) and you're usually good to go.  Why can't this be done as easily in Ubuntu? 


1. open nautilus
2. ctrl + L
3. ~/.themes
4. ~/.icons
5. ~/.fonts
6. ????
7. profit

---

### Post by sigurnjak on 2010-03-22
I like compact look a lot even if i am not using laptop or netbook . So to make things the way i like it i customized elementary compact and radiance os liner to suit me . They are not perfect by any means , but i like them . Also i rearanged my firefox with  stylish scripts a little . So here they are if you are interested .

---

### Post by samigina on 2010-08-01
Oh yes, Gnome needs to be more compact... theres too much wasted space... Im waiting for a gui Theme Creator...

---

