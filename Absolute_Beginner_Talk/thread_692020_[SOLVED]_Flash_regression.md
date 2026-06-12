---
title: "[SOLVED] Flash regression?"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by Ahunt on 2008-02-09
I have never seen this problem before.

I am running Ubuntu 7.10 Gutsy Gibbon with Firefox as the web browser. The add/remove available package for Adobe Flash has until recently been for an older version of Flash 9,0,31,0 This doesn't work with some websites, such as [www.jumpcut.com](www.jumpcut.com).

Yesterday there was an Ubuntu update from Firefox 2.0.0.11 to version 2.0.0.12 and also an update to Flash. Once installed I tested the Flash version at [http://www.adobe.com/products/flash/about/](http://www.adobe.com/products/flash/about/) and it said that I had Flash  9,0,115,0 which is the current version. Hooray - it works with JumpCut!!

However today while checking it suddenly it isn't working on JumpCut. Testing Flash again says that I have Flash 9,0,31,0 installed. The PC wasn't even rebooted in between this happening. I have since rebooted and the problem remains - the current version of Flash that was installed and working is gone.

Any ideas what happened and how to fix it?

(Request - if your suggestion includes CLI commands, please list them all line-by-line exactly, I am a beginner at CLI)

---

### Post by randy78 on 2008-02-09
I always tend to sudo apt-get remove flashplugin-nonfree before I install the new one...
Just to make sure that there aren't any conflicts.

You might try this and then try reinstalling it: sudo apt-get install flashplugin-nonfree

Hope that works for ya

---

### Post by Ahunt on 2008-02-09
Thanks for the quick response!

So, just to clarify here, you are suggesting using add/remove to remove Flash and then using 

sudo apt-get install flashplugin-nonfree

to reinstall it?

---

### Post by Ahunt on 2008-02-09
Sorry I didn't completely get your advice on first read.

What I did was in a terminal:

sudo apt-get remove flashplugin-nonfree

that resulted in a removal although [http://www.adobe.com/products/flash/about/](http://www.adobe.com/products/flash/about/)  said that I still had Flash 9,0,31,0 installed. It must have been correct because you can't even see that page without Flash.

Then I did:

sudo apt-get install flashplugin-nonfree

and that worked, too. Testing it at [http://www.adobe.com/products/flash/about/](http://www.adobe.com/products/flash/about/)  said that I  had Flash 9,0,115,0 installed. Let's see if it stays installed!

Thank you for your help.

PS I have noted that your tag line says to mark forum posts as "solved". I would love to but despite going through all the FAQs and helps function haven't figured out how to do that, or thank people for that matter!

---

### Post by Ahunt on 2008-02-09
Disregard my last on "thanking" and marking as "solved" - I finally figured it out!

---

### Post by Ahunt on 2008-02-09
Well I can't believe it - this problem is not solved.

After uninstalling Flash and then reinstalling Flash 9.0.115.0 it once again now indicates that Flash 9.0.31.0 is installed. 

I don't understand what is going on here. Does anyone know?

---

### Post by gandaran on 2008-02-09
where did you get that package 9.0.31 and how did you install it ?
the package available on ubuntu 7.10 before the update was 9.0.48 never 9.0.31!
you'll have to locate it and delete the folders if you can't find a way to uninstall, then install the new flash.
did you install gnash? if so get rid of it.
use synaptic to find what you have installed, do a search on flash, it should tel you what's installed.

---

### Post by Ahunt on 2008-02-09
That is interesting information.

I have never installed Gnash and it isn't installed now. I got Flash through the Restricted Extras download from the Ubuntu repositories. You are right it was 9.0.48.0 that I had until recently. After getting 9.0.115.0 during yesterday's update it reverted itself to 9.0.31.0.

Checking Synaptic it shows that I have Flash plug-in 9.0.48.0 and the Restricted Extras and that is it.

This isn't adding up to a coherent picture for me. Any thoughts?

---

### Post by gandaran on 2008-02-09
try this,
         unistall that flashplugin-nonfree, choose complete removal on synaptic then click apply.
next check file system /usr/lib, if there's still a flashplugin-nonfree folder, just delete that folder then  run this command « sudo apt-get update »  on a terminal and install that same flashplugin- nonfree on synaptic

---

### Post by gandaran on 2008-02-09
before installing the flash, check also /usr/lib/ mozilla/plugins and delete a libflashplayer.so file if you see it.

be careful just delete what I told

---

### Post by Ahunt on 2008-02-09
Sounds good.

As you suggested I used Synaptic to completely remove the flashplugin-nonfree and it reported that it was removed.

The usr folder does not contain anything named "Flash" at all.

I checked /usr/lib/mozilla/plugins and it does not contain libflashplayer.so or anything else named "Flash".

Here is the fun part - Firefox still tests at [http://www.adobe.com/products/flash/about/](http://www.adobe.com/products/flash/about/) as having Flash 9.0.31.0 !!!

---

### Post by gandaran on 2008-02-09
check home .mozila folder for a plugins folder, if you find it there  delete!

---

### Post by gandaran on 2008-02-09
you can also use the file searcher, to look for libflashplayer.so, it has to be somewhere on the file system or home folder

---

### Post by Ahunt on 2008-02-09
It was in the home folder under mozilla plugins.

Deleting that now results in a test of "no Flash", so I think we found it!

I have done the "sudo apt-get update", just have to use Synaptic to re-install the Flash and see what i get. i'll let you know soonest!

---

### Post by Ahunt on 2008-02-09
Well the adobe test says I now have Flash version 9,0,115,0. Let's hope that it stays that way this time!

Thanks for all your help! I learn new things about Ubuntu every time I do things with it.

---

### Post by gandaran on 2008-02-09
yes, you are right! but I'm wondering how you installed it there.
just to make sure, delete the plugins folder not just the file.

---

### Post by Ahunt on 2008-02-09
I take it you mean the home>mozilla>plugins folder?

I know how that folder got there - it was installed by Mozilla, not me, perhaps as part of the download of Thunderbird.

---

### Post by gandaran on 2008-02-09
> **Ahunt said:**
> I take it you mean the home>mozilla>plugins folder?

I know how that folder got there - it was installed by Mozilla, not me, perhaps as part of the download of Thunderbird.

yes.

---

### Post by Ahunt on 2008-02-09
Okay it is gone!

Thanks again for your help - that was invaluable!

I will post back here if the problem happens again.

---

