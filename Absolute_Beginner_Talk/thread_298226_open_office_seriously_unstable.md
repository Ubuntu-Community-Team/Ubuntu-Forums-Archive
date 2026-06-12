---
title: "open office seriously unstable"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by Kulgan on 2006-11-12
for the last couple of days, Open Office has been really freaked out. As soon as I do anything at all related to images, it starts crashing literally every 30 seconds. I don't know if this is something to do with any upgrades to another part of the system (didn't see any concerning OO) or whether it is something to do with my setup, but I was wondering if anybody has been experiencing anything similar lately. 

-K

---

### Post by bodhi.zazen on 2006-11-12
IMO OpenOffice is bloatware. Unless there is some advanced feature you need, try Abiword, leafpad, or mousepad.

---

### Post by bruenig on 2006-11-12
Abiword for sure is really good. Mousepad and leafpad are just simple text editors, not word processors so I wouldn't use those.

---

### Post by Kulgan on 2006-11-12
yehyeh, thanks for the quick response and all, but take rants elsewhere would you. That doesn't really help solve the problem...

---

### Post by bulldog on 2006-11-12
If advice to use other programs is of no use to you,well in answer of your question,no,I have no problems with it.

---

### Post by Kulgan on 2006-11-12
ok, I was a little sharp in that one... 

I will give abiword a try and check back on OO later if I like it...

---

### Post by bullon on 2006-11-12
strange problem, it hasn't happened to me at all. Have you tried reinstalling OO yet?

---

### Post by dynacrylic on 2006-11-12
My hasn't started crashing every 30 seconds or so, only when cnping from OO into Gmail when using FF.

Here's a thread on it: [http://ubuntuforums.org/showthread.php?t=291994](http://ubuntuforums.org/showthread.php?t=291994)

---

### Post by Rui Pais on 2006-11-12
If your OO start to crash suddenly and for no apparent reason, sounds more like a config file that got lost or corrupted then a software problem...

Try on a terminal:
```
mv .openoffice.org2 .openoffice.org2_BACKUP
```
and then start OO to see if it got stable again. 

If you use other language then default, check too it it happen with default language.

You could also start office from then terminal so you'll see any error/warning output.


btw, did that happen with any part of OOffice or only with Word Processor (most people seemed to assume that you are talk of word processor and pointed out Abiword...)

---

### Post by Kulgan on 2006-11-12
> mv .openoffice2 .openoffice2_BACKUP

that seems to hve done something, for some reason...

I'll give it some testing and see if it really did solve the problem...
 Thanks,
-K

---

### Post by rlozano on 2006-11-22
this is the same problem i have actually, but no every 30secs. only if i click on embedded image/s in Writer.

im not sure if this problem is isolated in open office bundle of Kubuntu Edgy or this is happening in Open 2.0.4 in general. i have browsed in the open office forum and i was not lucky enough to find a post related to this problem.

ne thing i have not tried though is to download open office from the site and install it, rather than using the one bundled in Kubuntu Edgy.

the community thoughts is highly appreciated on this one.

---

### Post by rlozano on 2006-11-22
> **rlozano said:**
> this is the same problem i have actually, but no every 30secs. only if i click on embedded image/s in Writer.

im not sure if this problem is isolated in open office bundle of Kubuntu Edgy or this is happening in Open 2.0.4 in general. i have browsed in the open office forum and i was not lucky enough to find a post related to this problem.

ne thing i have not tried though is to download open office from the site and install it, rather than using the one bundled in Kubuntu Edgy.

the community thoughts is highly appreciated on this one.

so this seems to be an open office package problem with Ubuntu.

[http://www.oooforum.org/forum/viewtopic.phtml?t=48150](http://www.oooforum.org/forum/viewtopic.phtml?t=48150)

---

### Post by Kulgan on 2006-11-23
> If you can figure out how to convert RPM's to DEB (hint: use alien) from the command line, then you should download OOo from [www.openoffice.org](www.openoffice.org) - I always did. Latest version of OOo and no problems. 

seems that that is the problem then - thanks for the links!

---

### Post by rlozano on 2006-11-23
> **rlozano said:**
> this is the same problem i have actually, but no every 30secs. only if i click on embedded image/s in Writer.

im not sure if this problem is isolated in open office bundle of Kubuntu Edgy or this is happening in Open 2.0.4 in general. i have browsed in the open office forum and i was not lucky enough to find a post related to this problem.

ne thing i have not tried though is to download open office from the site and install it, rather than using the one bundled in Kubuntu Edgy.

the community thoughts is highly appreciated on this one.

> **Kulgan said:**
> seems that that is the problem then - thanks for the links!


I have resolve the issue of my open office crashing when dealing with embedded graphics in Writer. i completely uninstalled the bundled open office with Kubuntu and install a downloaded version from [www.openoffice.org](www.openoffice.org). im working on it pretty stable now....

---

### Post by Kulgan on 2006-11-23
Great, I will try that when I get home

---

### Post by Crafty Canine on 2006-11-28
Same problem after upgrade from breezy directly to edgy.  Any hints as to why?

---

### Post by Kulgan on 2006-11-29
It appears that v. 2.0.3 is not as stable as it should be. Try downloading it again from the open office site, doing what Rui Pais said:

```
mv .openoffice2 .openoffice2_BACKUP
```

that worked for me.

---

### Post by Grizzlitiger on 2006-12-11
I had a similar problem (similar in the way that it occurred after installing edgy eft and that it is a quite deep problem). A lot of keys didn't work including backspace, the arrow keys, delete and ctrl. Re-installing has no effect whatsoever (re-installing without a complete removal at least). You can solve this problem by performing the suggested action. If you later change the paths for the configuration files under options/paths it will still work (I did this because I share the config files on another partition with windows).

Wrote this because I was looking for help for quite some time for such a trivial problem.

---

### Post by meng on 2006-12-11
I found OO Impress would regularly crash after 4-5 slides with images on. I turned off the thumbnails/preview and it no longer crashes. Your problem sounds similar to mine.

---

### Post by KaiO on 2006-12-16
I had a similar problem and "fixed" it by disabling *Klipper* (clipboard tool).
Copy/cut and paste still works, but you lose the extra functions in Klipper.
Might be worth a try.

---

### Post by zkeng on 2007-04-10
I had the same problem with corrupted image display in impress.

It turned out that all I had to do to solve it was start openoffice, chose "tools/options/view" and uncheck the four checkboxes under "3D View" and "Graphics output".

That did it for me!

---

### Post by boirax on 2007-05-21
Hi everyone.

I am having lots of problems too with Open Office (2.0.4), especially with Impress.

It crashes often when handling images and goes to the recovery window but looses all unsaved changes.
Also, as soon as I delete a bullet point with the "backspace delete" key it crashes too!!

I updated:

```
sudo apt-get install openoffice.org
```
but it hasn't helped.

Also I have seen in the thread that someone suggested to do:
```

 mv .openoffice2 .openoffice2_BACKUP

```
I'm a beginner, so could anyone help me know where do I do that command.  In my home user folder there is no such file:

mv: cannot stat `.openoffice2': No such file or directory

Thank you for your help

---

### Post by jpeddicord on 2007-05-21
> **boirax said:**
> Also I have seen in the thread that someone suggested to do:
```

 mv .openoffice2 .openoffice2_BACKUP

```I'm a beginner, so could anyone help me know where do I do that command.  In my home user folder there is no such file:

mv: cannot stat `.openoffice2': No such file or directory
Try this:
```
mv .openoffice.org2/ .openoffice.org2_BACKUP
```Missed the .org. ;)

Jacob

---

### Post by boirax on 2007-06-23
Thanks Jacob for your prompt reply! :)
Indeed, 
```
mv .openoffice.org2/ .openoffice.org2_BACKUP
```
works with the ".org"
but Open Office Presentation (Open Office (2.0.4))  still crashes when deleting bullet points.
If anyone managed to get rid of that problem, I'd be very thankful if you can share.
All the best!

---

### Post by Rui Pais on 2007-06-23
Hi boirax

You are using 2.0.4, that means you are using the Ubuntu Edgy version. That version is know to have a lot of bugs and errors, most people never managed to get rid of them. Edgy is not even a supported version anymore...

You may want to try several options. 
- Update your Ubuntu version. 
- Get experimental repository from here and try.
- Get Feisty packages of OpenOffice and update only Openoffice (that was mixing version, that can be problematic... not a good solution)
- Get original packages from [www.openoffice.org](www.openoffice.org) either as deb version, if available, or the rpm versions and use alien (on repos) to make debs from it (usually requires a certain knowledge... you may not fell much comfortable with it. It's not granted either that will work)

I would advise on 1st, but if you are afraid of a full upgrade or don't want upgrade for any other reason. Try the 2nd suggestion. If it fails you can reverse and back to the what i have now. 

If you areinterested in the 4th option, theres a lot of how-tos around... just do a search for opeenoffice on the forum.
Good luck.
(post if you have doubts)

---

### Post by boirax on 2007-06-30
Hi Rui Pais and Obrigado!

I've been giving some thought to updating the Ubuntu version, so I imagine I'll go for that and find out how stable Open Office is in Feisty.

Thanks,
boirax

---

