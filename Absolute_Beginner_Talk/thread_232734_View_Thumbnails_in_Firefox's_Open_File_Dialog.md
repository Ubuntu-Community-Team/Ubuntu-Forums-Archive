---
title: "View Thumbnails in Firefox's Open File Dialog?"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by CarpKing on 2006-08-09
I've been searching for awhile, but haven't found anything promising.  Does anyone know how I can view image thumbnails in Firefox's Open File dialog?

---

### Post by CarpKing on 2006-08-10
Bump... I'd really like to know whether this is possible or not... Would installing a non-nautilus file browser help?

---

### Post by davebgimp on 2006-08-10
Define what you mean by image thumbnails.

Do you mean EXIF thumbnails?

---

### Post by davebgimp on 2006-08-10
If it is EXIF thumbnails, here's a quick howto I wrote on extracting them for viewing. As far as a Firefox extension, I know of no such thing.

[http://davebgimp.com/2006/06/30/exif-jhead-and-the-joys-of-hidden-thumbnails/](http://davebgimp.com/2006/06/30/exif-jhead-and-the-joys-of-hidden-thumbnails/)

---

### Post by CarpKing on 2006-08-10
In Nautilus, I can see thumbnails (smaller versions) of images.  However, whe n I press "Browse" or a similar button on a website in Firefox (to upload a file), I cannot seem to get such thumbnails or previews to display in the "Open File" dialog.  The GIMP's "Open File" dialog, however, does show a preview of the image you have selected.

---

### Post by CarpKing on 2006-08-11
When I go to upload an image in Firefox, the dialog looks like this:

[IMG]http://i7.tinypic.com/24cupm1.png[/IMG]

When I go to open a file in GIMP or Inkscape (could be others, but none I've tried so far), the dialog looks like this:

[IMG]http://i8.tinypic.com/24cuvb7.png[/IMG]

I would like to have something like the second screenshot visible in the first.

---

### Post by lime4x4 on 2006-08-11
i need that abilty as well

---

### Post by Elis on 2006-10-05
Me too. I think its very strange why it doesnt work like that. Or is it possible to turn it on in any preferences or something?

Now then Im for example is using Gmail and want to attach a picture to an email, I first have to open Ubuntu's filebrowser, look at the thumbnails to see which picture I want to use, remember the filename, and then look it up in the 'file upload' window.

It would make it so much faster and easier if the 'file upload' window would show thumbnails. Am I missing something, or is it a reason why it is like it is?

---

### Post by SelrahCharleS on 2006-12-03
I would really like to know this myself, its easy enough for me to work around, but my mother heavily relies on thumbnails for her Ebay listings.

---

### Post by linux_believer on 2007-04-12
Ttt

---

### Post by KhaaL on 2007-05-21
there is no sane reason why this feature isn't implemented...

---

### Post by Beatbreaker on 2007-07-08
> **KhaaL said:**
> there is no sane reason why this feature isn't implemented...

exactly - has there been word that it will be out on GG?

---

### Post by KhaaL on 2007-07-08
> **Beatbreaker said:**
> exactly - has there been word that it will be out on GG?

Frankly i havent followed GG's development nor have I been trying to push this feature to get implemented - I totally forgot about this thread...

I think its necessarly that someone push for it to get into GG.

---

### Post by Beatbreaker on 2007-07-08
> **KhaaL said:**
> Frankly i havent followed GG's development nor have I been trying to push this feature to get implemented - I totally forgot about this thread...

I think its necessarly that someone push for it to get into GG.

Isn't it too late for that now? i think they stopped taking suggestions weeks ago. I'm sure there's enough of us here to get in IDEA like this through at the right time and if we all back it up properly.

---

### Post by Old Pink on 2007-07-08
Can't be hard to change, surely. :) 

Think it'll be nautilus settings rather than Firefox settings. Head into nautilus folders and find files containing GIMP or Firefox.

Find where the configuration for individual software is and modify Firefox's using GIMP's as a guide. 

a.k.a: Fiddle. You could probably get it sorted in 10 minutes if you tried. :)

---

### Post by eternalsword on 2007-07-08
maybe you would be interested in an actual image browser extension for firefox.  you could give mozimage a try [https://addons.mozilla.org/en-US/firefox/search?q=mozimage&status=4](https://addons.mozilla.org/en-US/firefox/search?q=mozimage&status=4)

---

### Post by Anonii on 2007-07-08
> **Old Pink said:**
> Can't be hard to change, surely. :) 

Think it'll be nautilus settings rather than Firefox settings. Head into nautilus folders and find files containing GIMP or Firefox.

Find where the configuration for individual software is and modify Firefox's using GIMP's as a guide. 

a.k.a: Fiddle. You could probably get it sorted in 10 minutes if you tried. :)
I will dig this up a little. I'll probably fail, but well, I'll post my progress soon.

---

### Post by Anonii on 2007-07-08
Ok, back. 

Firstly, let me say that I have less knowledge on programming than twelve monkeys (just some pascal), and that I just jumped in the discussion because the lack of such a feature always troubled me. 

Anyway, I downloaded the source of gimp and after some finds and greps, I think that the code related to the thumbnail viewer when opening a file is located in **app/dialogs/file-open.c**. (I can safely bet, that any creature with a brain would find that too.) Unfortunately the stuff in that file is gibberish to me, to the point of not beeing able to understand which programming language is that (GTK or something?). I didn't check the firefox source because I think that anyone even remotely interested in helping with this thing can do it really easily.

I also asked for help and advices in the gimp channel in IRC (#gimp @ irc.gimp.org), but no replies after 20 minutes or so. 
I'm thinking of also posting in the mailing lists of GIMP or Firefox, but I think that someone else with a little more experience would be better off doing it.

Over.

---

### Post by eternalsword on 2007-07-08
It's not portable, the gimp open dialog uses a gimp image format to display the thumbnail.  There's no way Firefox makes it's code dependent on gimp headers.  To get the functionality you want, you would want to talk to upstream gtk as firefox just uses the default gtk file open dialog.  If gtk implements thumbnail abilities into the default file open dialog, you're set.

---

### Post by kadath on 2007-07-11
Man, I'm glad you guys are also bothered by this. I've been trying to figure out who to pester to get this feature added. The fact that it's not already there is ridiculous.

```
(´&#12539;&#969;&#12539;)&#12388;(&#12539;(&#12539;
```

---

### Post by tk03759 on 2007-07-18
It's kinda scaring me that this *still* isn't fixed... it's been 7 months since the *last* post to this thread. :(

---

### Post by aysiu on 2007-07-18
The bug is labeled right now as "wishlist":
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/89381](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/89381)

I think it's essential. In the meantime, you can use Galeon or Konqueror.

---

### Post by DoktorSeven on 2007-09-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/89381](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/89381) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hate to dig this post up from the graveyard, but I've created a very quick and dirty patch for Firefox to implement preview images if anyone is interested.  The patch is found on the Launchpad bug page.

[(Screenshot)](http://doktorseven.miskie.net/images/ffimagepreview.jpg)

---

### Post by KhaaL on 2007-09-27
since this issue is still there, i don't see why you'd hesitate to dig this thread up :)

thanks a lot for your patch! I'll have to test it. Do i need to compile FF from source in order to use it, or could i get by with the binary form (the one that comes with the ubuntu installation?)

---

### Post by phorque on 2007-10-03
man, this still irritates the hell out of me! i mean... the firefox browse dialog is just bringing up a native (nautilus in my case) file browser dialog but obviously not setting the dialog's variables to have the combo box allowing list, details, thumbnails etc... right? 

I mean, if you are running KDE with firefox and you click on a browse button, do you still not get the thumbnail preview option? (which I see in konqueror you get by right-clicking in the dialog and then clicking View->thumbnail preview)

Seems like this shouldn't be so hard to achieve at all :/

---

### Post by geokker on 2007-10-20
This is a really useful feature standard in WIndows/MacOS. I'm amazed it's not available in my distro of choice (Gutsy). Is there a petition?

---

### Post by geeknik on 2007-11-05
I'll add my voice to the cause. I'd like to see this fixed.

---

### Post by KhaaL on 2007-11-05
I just gran paradiso and it dosen't have this functionality either...

---

### Post by nicoladimaria on 2007-11-14
nothing yet

---

### Post by aysiu on 2007-11-14
This isn't a "vote for thumbnails" thread. This is a support thread.

The bug is filed and is here:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/89381](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/89381)

In the meantime, use Galeon or Konqueror.

---

