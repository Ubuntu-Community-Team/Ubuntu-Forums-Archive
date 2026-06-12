---
title: "How do u preview pics when trying to upload to a website?"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-08-11
Got the wife on ubuntu but she need the ability to view a pic before she uploads it to a website..Currently when she goes to her nature website and clicks upload another window open and she can browse to where the pics are stored but all it lists is a file name she needs to c an actual pic.. Is this possible?? In windows it is..

---

### Post by Grayfox777 on 2006-08-11
[http://www.linux.com/article.pl?sid=05/10/27/166215](http://www.linux.com/article.pl?sid=05/10/27/166215)
The article contains several Linux thumbnail viewers that will let you preview pictures without opening each one of them.

---

### Post by msak007 on 2006-08-11
Is something like [this]("http://www.ubuntuforums.org/showthread.php?t=232734") what you're looking to do? I've never known Firefox to have that capability. I was messing around with Firefox's settings and the dialog box config file to see if I can find some way to do it and couldn't. 

Grayfox777, Konqueror (and I believe Nautilus) has a thumbnail view that lets you preview pictures so an external thumbnail viewer isn't really a "solution", as there are workarounds already available. I believe 
lime4x4 is looking for something like the screenshots in the post I linked to, something native to Firefox's open file dialog box.

---

### Post by lime4x4 on 2006-08-11
exactly

---

### Post by CarpKing on 2006-08-19
*Heh* Bumping this because it links to my thread and I still haven't figured it out.  Am I correct in thinking that this is an issue with Nautilus?  Or is it some other part of Gnome?

---

### Post by OrganicPanda on 2006-08-19
I don't think it's a Firefox extention that is needed, In the Nautilus / Gnome file open dialogue box there is no option, as far as I know, to preview a thumbnail of the images so you can graphically select the image you want rather than just knowing the filename - which isn't always convinient. In windows open dialogue boxes there is an option to view files by either list view, details view, icon view or thumbnail view, I think that is what we need here, I know I would very much like this feature.

---

### Post by _simon_ on 2006-08-19
I view in nautilus and upload in gftp.

In nautilus you just select "view as icons"

---

### Post by msak007 on 2006-08-19
> **_simon_ said:**
> I view in nautilus and upload in gftp.

In nautilus you just select "view as icons"

I think you're missing the point of what lime4x4 is looking for. We know that Nautilus has a thumbnail view option, but the problem is that he is looking for something integrated into Firefox. Look at the post I linked to in my first reply. There's two screenshots comparing Gimp's filepicker vs. Firefox's, and the right side pane where the Gimp can preview pictures from the file dialog is missing from Firefox. That's what he's looking for.

EDIT: Nevermind, sorry it seems as if that post I was referring to no longer has the screenshots loading. If you had seen it before though, you would know what I mean. Try opening Gimp and going to File --> Open, and you'll see a picture preview pane on the right side. Try the same thing in Firefox, and that pane is gone with no option to turn it on.

---

### Post by CarpKing on 2006-08-21
Hopefully this hosting will last longer:
Firefox file chooser:
[IMG]http://i87.photobucket.com/albums/k126/hyrax_of_love/Screenshot-23.png[/IMG]

GIMP file chooser (same as Inkscape):
[IMG]http://i87.photobucket.com/albums/k126/hyrax_of_love/Screenshot-25.png[/IMG]

---

### Post by Tomosaur on 2006-08-21
Yes, this is a well known gripe with Firefox. Currently there is no way around it I don't think.

---

### Post by aysiu on 2006-08-21
I think Konqueror may be the way to go.

P.S. Works just fine in Gnome, by the way--see attached screenshot.

---

### Post by msak007 on 2006-08-21
[Mozillux]("http://www.polinux.upv.es/mozilla/mejoras.php?idioma=en") does make a modified nsFilePicker.js file for use with Firefox (if you're using KDE) that gives you a standard KDE filepicker dialog, but alas, the one option we're looking for (Picture Preview) is grayed out / disabled and nobody can tell me why. Not much use if you're using Gnome, but just thought I'd share.

---

### Post by seshomaru samma on 2006-08-21
This is one feature I miss as well in Gnome , the ability to view as thumbs , I hope they will put it in Edgy.

---

### Post by CarpKing on 2006-08-22
Hmmm... I don't know any Java, but I wonder- would it be possible to create a modified nsFilePicker.js file to make Firefox use the GIMP's file chooser dialog?

---

### Post by CarpKing on 2006-08-28
So I guess the consensus is that this is not possible?  Which development team do I file a feature request with?  :S

---

### Post by aysiu on 2006-08-28
> **CarpKing said:**
> So I guess the consensus is that this is not possible?  Which development team do I file a feature request with?  :S
No, the consensus is that if you need this feature, you should use Konqueror instead of Firefox.

---

### Post by msak007 on 2006-08-28
> **aysiu said:**
> No, the consensus is that if you need this feature, you should use Konqueror instead of Firefox.

I'm pretty sure the OP uses Ubuntu but even I, as a Kubuntu user, prefer Firefox over Konqueror for web browsing :)  

There is one thing I just thought of though. There's a "hack" for getting Firefox to use a KDE file-picker (not the standard kdialog, but a filepicker that has the KDE look n' feel) is to follow step 1 in [this]("http://www.ubuntuforums.org/showthread.php?t=110353") thread. I'm not an Ubuntu / Gnome user though so I'm not sure what, if any, effect this'll have on Firefox in Gnome. It's worth a shot though. Just make sure to back up the file first before making any modifications so that you can revert to it if it gets messed up.

---

### Post by aysiu on 2006-08-28
I, too, prefer Firefox to Konqueror, even in KDE, but if this is a feature you absolutely must have... it's in Konqueror. It's not impossible--just impossible in Firefox.

---

### Post by toasted on 2006-08-28
Open the file browser too so you can refer to the thumbs and find the correct name.. not a fix but it works

---

### Post by msak007 on 2006-08-28
> **aysiu said:**
> I, too, prefer Firefox to Konqueror, even in KDE, but if this is a feature you absolutely must have... it's in Konqueror. It's not impossible--just impossible in Firefox.

Yea I understand what you're saying. It's not a must-have, showstopper feature for me (just one of those nice to have options), so I guess that's why it's easy for me to say that. Going with the same idea though, does Epiphany do what he's looking for? I've never used it, but isn't it a Gnome browser?

---

### Post by Toxicity999 on 2006-08-28
I see the gripe but in the interim... name you're files correctly and know what you're uploading beforehand... Seems a given to me. Would be a nice luxury for FF though.

---

### Post by aysiu on 2006-08-28
> **msak007 said:**
> Yea I understand what you're saying. It's not a must-have, showstopper feature for me (just one of those nice to have options), so I guess that's why it's easy for me to say that. Going with the same idea though, does Epiphany do what he's looking for? I've never used it, but isn't it a Gnome browser?
No, I just tried it--no preview in Epiphany.

---

### Post by Toxicity999 on 2006-08-28
Doesn't seem like it would be insane to implement isn't it just a call to Nautilus to get the small file browser? Where there is like a Basic Browser and Basic Browser with Preview call? I know absolutely nothing about the inner workings of Nautilus by any means, just an assumption.

---

### Post by CarpKing on 2006-09-01
I tried Epiphany as well, then Konqueror.  I understand that many people do not need this, but most people don't have almost half a gigabyte of pictures with only numbers for file names.  Oh well.  I guess Konqueror will do for the times when I need this feature.  It beats trying to memorize numbers when I have to upload.  Who knows?  Someday I might even get on that whole renaming thing.

---

### Post by aysiu on 2006-09-01
If you do want to do some bulk-renaming, I'd highly recommend KRename. It's in the repositories.

---

### Post by lfjewett on 2007-01-16
Has anybody found a work around for this bug?  I have searched all over the net and found nothing!

Thanks.

---

### Post by seshomaru samma on 2007-01-16
From what I understand , at the moment it is impossible to preview pics in Firefox but possible  in Konquerer

---

### Post by pininy on 2007-06-29
since 2005?

Any update on this issue using via Firefox?


thanks

---

### Post by Beatbreaker on 2007-07-08
> **pininy said:**
> since 2005?

Any update on this issue using via Firefox?


thanks

yeah this seems pretty unbelieveable if you ask me - especially since it's been acheived in Gimp really the same code there could be used for firefox and thunderbird image browsing. I don't know how to do any of that stuff but i'm living in the hope at the moment that this will get someones attention that will know how to fix this little annoyance.

---

### Post by MacHaddock on 2007-08-27
Bump!

What's going on with this. I also find this annoying. Not to the extent of it being a deal breaker though

---

### Post by ZeroVerteX on 2007-10-20
Bumpety BUMP BUMP!

OMG I can't believe this is still an issue. Gnome Firefox and Ubuntu guys... Get on the same page! This is a deal breaker for many people who do alot of image uploading (eBayers and deviantart/flickr users) including my wife (who I really want to stay away from Windows, and loves FF)

---

### Post by tdeverell on 2007-10-24
And I will post my reply in support for some attn. on this issue.

My wife would also like the ability to select images with a preview, as opposed to Alt-Tab, scroll, scroll, Alt-Tab, Click, Alt-Tab, scroll, scroll, Alt-Tab, Click...

Instead of complaining...

I can't wait to see a simple fix for this!  The talents at Gnome,  Ubuntu or Firefox will probably come up with something soon!  As I search the web for more solutions, I can see more and more people with this problem.  

It's good to see so many choosing a different browser (*Down with IE!!*) and selecting a new OS!  Thanks Guys for any suggestions!  Keep up the good work!

---

### Post by aysiu on 2007-10-24
The best workaround right now would be to use Galeon or Konqueror instead of Firefox. Both Galeon and Konqueror offer image previewsi nt he upload dialogue.

---

### Post by tdeverell on 2007-10-25
Galeon didn't make a difference for me.  Same situation with browsing for images.  Konqueror had more issues with out-of-date Javascript...  

not sure what is easier right now...   fighting with Konqueror, or waiting on Firefox...

Thanx anyway.

---

### Post by mve-lamb on 2007-10-31
Hi, I give my vote for this too, it's not working in Opera browser neither :confused:
This feature is very annoying, My wife makes me trouble too, when she wants to upload  photos.

And it's bothering me too!

I couldn't believe it when I switched from M$ windows, I double check it even triple, and did search the forums but found nothing :mad:

Lamb

---

### Post by brownknight on 2007-10-31
> **mve-lamb said:**
> Hi, I give my vote for this too, it's not working in Opera browser neither :confused:
This feature is very annoying, My wife makes me trouble too, when she wants to upload  photos.

And it's bothering me too!

I couldn't believe it when I switched from M$ windows, I double check it even triple, and did search the forums but found nothing :mad:

Lamb

BUMP! 

I have the same 2 problem**s**... (1) I cant upload without memorizing which dcm100xxx.jpg file to upload and (2) wife is complaining that I cant memorize the right dcm100xxxx.jpg file to upload :(

---

### Post by mve-lamb on 2007-11-02
> **brownknight said:**
> BUMP! 

I have the same 2 problem**s**... (1) I cant upload without memorizing which dcm100xxx.jpg file to upload and (2) wife is complaining that I cant memorize the right dcm100xxxx.jpg file to upload :(

Welcome to the same boat.

I hope that in Gusty or with new Gnome 2.20 we will have this feature, BUT :(

The best way would be to have thumbnail view choice and little preview on the right side like in GIMP.

Please anyone?

---

### Post by brucealdridge on 2007-11-05
this is most frustrating, luckily i don't upload images in-browser that much.

---

### Post by Tanjer1588 on 2007-12-04
Bump, i feel that this should be bumped back to life seeing as how it is still a problem, i would like to know how to file a bug report on this so that more attention is brought to it. I have been searching threads and forums for like and hour and a half now and i have seen the same thing, every one seems to think it is unfixable right now, So i would like to bring this back up to the public again.

---

### Post by savethewabbit on 2008-01-06
bump.
please if there's any way around this (which does not include switching browsers) post and let us know!

---

### Post by msak007 on 2008-01-10
It seems as if this issue will be resolved with Firefox 3:

> But why just catch up to other platforms when you can leapfrog them? Since sites like Flickr, or personal blogs, are becoming increasingly popular I know this feature will prove helpful. It has been requested a couple of times and it even proved helpful to myself as I uploaded the screenshots to this very post:

[http://ventnorsblog.blogspot.com/2008/01/fox-and-penguin.html](http://ventnorsblog.blogspot.com/2008/01/fox-and-penguin.html)

Scroll about halfway down to see the included screenshot of image preview in action.

---

### Post by aysiu on 2008-01-10
> **msak007 said:**
> It seems as if this issue will be resolved with Firefox 3:



[http://ventnorsblog.blogspot.com/2008/01/fox-and-penguin.html](http://ventnorsblog.blogspot.com/2008/01/fox-and-penguin.html)

Scroll about halfway down to see the included screenshot of image preview in action.
While that's certainly an improvement, it still makes you do too much work--you have to click on each individual file in order to preview the images one by one, instead of getting a folder full of thumbnail previews.

By the way, I think this kind of preview is something Galeon has been able to do for a while. And Konqueror has a much better preview and has had so for years.

---

### Post by msak007 on 2008-01-11
> **aysiu said:**
> While that's certainly an improvement, it still makes you do too much work--you have to click on each individual file in order to preview the images one by one, instead of getting a folder full of thumbnail previews.

By the way, I think this kind of preview is something Galeon has been able to do for a while. And Konqueror has a much better preview and has had so for years.
I've never used Galeon, but I'm aware of how Konqueror handles this situation. It's better than nothing, but I agree that it's still not the optimal way of doing it. I haven't used the FF3 betas yet, so I'm not sure if there'll be an option to switch to a thumbnail view in the file picker dialog. If anyone has used any of the betas and has seen this functionality in action, please post your experience and whether the view can be changed to thumbnail.

---

### Post by jerome1232 on 2008-01-14
Well I download FF3 Beta and... I still can't get a preview, *sigh* then again the ui isn't completed either no icons etc so there's still hope for FF3, i wish it would just use a standard nautilis browser tho, where u can see images without having to actually select them. lazy i know but isn't that what are computers are here for, to do the work for you? then again installed it to my home directy so i don't know if that hurt anything, i haven't gotten flash to work in it either.

---

### Post by M.a.d on 2008-01-28
wow, this is just insane. The issue has been around for so long, and nothing has happened.

---

### Post by ekendra on 2008-03-10
is there a hack or anything?

my wife is complaining too.

---

### Post by seshomaru samma on 2008-03-10
no hack
the next edition of ubuntu will have that feature
in the meanwhile you can sort of solve it by using konqueror instead of firefox

---

### Post by lime4x4 on 2008-03-11
firefox 3 in hardy does that. I've installed firefox 3 in gutsy and i'm able to preview pics before uploading

---

### Post by brownknight on 2008-03-15
This very important feauture is now available. Mark as solved.

---

