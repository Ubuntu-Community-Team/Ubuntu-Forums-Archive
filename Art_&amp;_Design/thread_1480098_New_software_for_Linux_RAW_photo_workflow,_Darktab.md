---
title: "New software for Linux RAW photo workflow, Darktable"
date: 2010-05-11
forum: Art &amp; Design
---

### Post by earlycj5 on 2010-05-11
I just found this the other day and started using it.  While it's still in development I find it to be quite stable and extremely useful for my needs.

[http://darktable.sourceforge.net/](http://darktable.sourceforge.net/)

There are .debs and nightly git builds in a PPA available for installation.

[http://darktable.sourceforge.net/install.shtml](http://darktable.sourceforge.net/install.shtml)

I never could get the hang of of Bibble, RawTherapee and the like.  I liked UFRAW but using it with F-spot and Gimp added another layer of software.  This combines two, allowing me to organize and then edit non-destructively.

Yes, it's an Aperture/Light Room type program.

---

### Post by PhotonicGuy on 2010-05-11
Useful ... for a photographer

---

### Post by Dragonbite on 2010-05-11
Looks interesting. Hope it keeps getting developed and improved!

---

### Post by manadi on 2010-06-25
Can anyone tell me how to save the modified pictures in Darktable? I mean I am able to take snapshots, but it just creates some file with other extensions like *.jpg.dt or *.jpg.dttags

The question is how to obtain a jpeg file. Tried renaming .dt file manually but is not allowed.

:confused:

---

### Post by manadi on 2010-06-25
Just realized that it is modifying the source image directly!!!.

At-least it should prompt.

---

### Post by earlycj5 on 2010-06-25
> **manadi said:**
> Just realized that it is modifying the source image directly!!!.

At-least it should prompt.

What?  It writes a sidecar file as I understood it, it's non-destructive.

[quote="From Darktable's About Page"]
***all editing is fully non-destructive and only operates on cached image buffers for display***. the full image is only converted during export.[/quote]

---

### Post by earlycj5 on 2010-06-25
> **manadi said:**
> Can anyone tell me how to save the modified pictures in Darktable? I mean I am able to take snapshots, but it just creates some file with other extensions like *.jpg.dt or *.jpg.dttags

The question is how to obtain a jpeg file. Tried renaming .dt file manually but is not allowed.

:confused:

Try the "export" feature.  The files you're modifying are what Darktable is using to display changes that you make to the image.

---

### Post by earlycj5 on 2010-06-25
I have to admit, much of my excitment related to this program has faded.

It's a very well thought out application, but it's S.L.O.W. even with a four-core CPU and 4GB RAM.  It's slow enough to become downright unusable in certain situations for me.

Unfortunately it still has a ways to go it seems.

---

### Post by manadi on 2010-06-26
Thanks for the reply. What are other alternatives for Linux which provide same capabilities as Darktable?

---

### Post by vkontakte on 2010-06-27
> **manadi said:**
> Thanks for the reply. What are other alternatives for Linux which provide same capabilities as Darktable?
Biblepro, but it's proprietary

---

### Post by psoulocybe on 2010-06-27
RawTherapee is a great piece of OS software.  I've been using it for almost a year now.

---

### Post by Rodney9 on 2010-06-27
> **psoulocybe said:**
> rawtherapee is a great piece of os software.  I've been using it for almost a year now.

+1

---

### Post by earlycj5 on 2010-06-28
> **vkontakte said:**
> Biblepro, but it's proprietary

I've been using the trial of BibblePro/Lite.

Pro = $200
Lite = $100

I've almost decided that it's worth the $$ for me to invest.  It's multithreaded, so the speed is definitely there whereas with Darktable it is not.

Might give Rawtherapee another go-round before I spend the $ though, just to see.

---

### Post by earlycj5 on 2010-06-28
Now I remember what I didn't like about RT, it segfaults.

---

### Post by psoulocybe on 2010-07-01
Bummer.  Never had an error with the RT 2.4 release, but I've been using the 3.1 alpha since it came out and do get a good crash once a week or so.  Never seem to lose sidecars though, so it doesn't get me down too bad.

I finally gave Bibble a shot this week.  It seems pretty good, and seems to be slightly more responsive than Raw Therapee, but I have not gotten too far into it.  I do like the idea of creating plugins for it which may keep me on the hook.

---

### Post by robert shearer on 2010-07-05
> **earlycj5 said:**
> I have to admit, much of my excitment related to this program has faded.

It's a very well thought out application, but it's S.L.O.W. even with a four-core CPU and 4GB RAM.  It's slow enough to become downright unusable in certain situations for me.

Unfortunately it still has a ways to go it seems.

Out of interest were you using it standard or with the memory usage hack ?

From the documentation....
  >   *   $ gconftool-2 --type int --set /apps/darktable/mipmap_cache_full_images 1
    * this will allow only one full image in memory at the same time.
    * warning: this won't let you edit and export images at the same time!


---

### Post by earlycj5 on 2010-07-05
> **robert shearer said:**
> Out of interest were you using it standard or with the memory usage hack ?

From the documentation....

Memory usage hack.

The biggest thing missing for me that Bibble offers currently is the layers and selective editing.  Unless I'm missing something.

---

### Post by earlycj5 on 2010-07-26
> **psoulocybe said:**
> RawTherapee is a great piece of OS software.  I've been using it for almost a year now.

Ok, so I finally installed RawTherapee from the PPA.

It's a nice piece of software, but I don't see how it compares to Darktable or Bibble???

It's just like Rawstudio or UFRAW, a few color adjustments, some exposure, sharpening here and there, etc. but I have to send the "developed" tif file to Gimp to do any serious editing.

With Bibble or Darktable I can do 90-100% of what I need done to the photo in them.

---

### Post by ElSlunko on 2010-07-26
I wouldn't discount Rawtherapee so much. It may not have all the bells and whistles but the image quality is actually pretty nice as well as the amount of tools present to make all the small tweaks you need.

I use bibble just because my workload per shoot is so huge but if I wasn't shooting events I might have saved up my cash and stayed with rawtherapee.

---

### Post by psoulocybe on 2010-07-26
Not trying to be a jerk here, earlycj5, but....

Not all of us need to do serious editing to our images.  Some of us take great images that just need minor color correction, sharpening, and brightness adjustments. 

If I'm doing photo manipulation, I dump the tiff into photoshop or gimp.  

There has never been a do-it-all in my opinion in regards to that type of work... though photoshop CAN handle it... I don't appreciate the quality I get from raw imports there.

---

### Post by earlycj5 on 2010-07-26
> **psoulocybe said:**
> Not trying to be a jerk here, earlycj5, but....

Not all of us need to do serious editing to our images.  Some of us take great images that just need minor color correction, sharpening, and brightness adjustments. 

If I'm doing photo manipulation, I dump the tiff into photoshop or gimp.  

There has never been a do-it-all in my opinion in regards to that type of work... though photoshop CAN handle it... I don't appreciate the quality I get from raw imports there.

I don't think you're trying to be a jerk here.

I just saw that it was mentioned in this thread when I started talking about Darktable. I mistakenly thought it was more like Bibble or Darktable, then when I used it, I found that it was not. I thought a comparison was a reasonable thing to make.

I'm not discounting RawTherapee at all.  It's nice software.  It's just for someone with a different workflow than what I have, which is why I pointed out Darktable initially, it and Bibble like software fit my workflow.  :)

---

### Post by psoulocybe on 2010-07-27
What camera do you use?
I'm shooting nikon, and one of my favorites ever was CaptureNX.... I don't think I'll ever get that running in wine, though I haven't really looked into it. 
If you ever get a chance, check it out...  has masking layers for effects and filters... and produces some of the sharpest and nicest photos I've ever shot.

---

### Post by earlycj5 on 2010-07-27
> **psoulocybe said:**
> What camera do you use?
I'm shooting nikon, and one of my favorites ever was CaptureNX.... I don't think I'll ever get that running in wine, though I haven't really looked into it. 
If you ever get a chance, check it out...  has masking layers for effects and filters... and produces some of the sharpest and nicest photos I've ever shot.

Nikon D300s, I've considered buying a Mac just for Capture NX, for the reasons you listed.

I was quite impressed when I met Jim Richardson recently and he was showing us some of his workflow with Capture NX.

---

### Post by Dixon Bainbridge on 2010-08-03
> **earlycj5 said:**
> Nikon D300s, I've considered buying a Mac just for Capture NX, for the reasons you listed.

I was quite impressed when I met Jim Richardson recently and he was showing us some of his workflow with Capture NX.

Capture NX is clumsy for workflow, but is excellent for RAW conversions - better than anything if you shoot Nikon bar Capture One Pro 5, which is the daddy of RAW conversion software.

RawTherapee is no use for pro use, but is fine for casual shooters. There isn't really a useable opensource photo workflow for linux, but maybe in the future darktable will fill that gap.

---

### Post by earlycj5 on 2010-08-04
> **Dixon Bainbridge said:**
> 
RawTherapee is no use for pro use, but is fine for casual shooters. There isn't really a useable opensource photo workflow for linux, but maybe in the future darktable will fill that gap.

Hear, hear!=D>

---

### Post by jcolyn on 2010-08-05
Has anybody tried DigiKam?

I've been using it on my Kubuntu machine and like it better than Lightroom or Aperture.

It will also work on Ubuntu.

---

### Post by earlycj5 on 2010-08-06
> **jcolyn said:**
> Has anybody tried DigiKam?

I've been using it on my Kubuntu machine and like it better than Lightroom or Aperture.

It will also work on Ubuntu.

I've not tried it in some time, have they added editing capabilities that I was unaware of?

I might have to take another look.

---

### Post by ElSlunko on 2010-08-06
> **earlycj5 said:**
> I've not tried it in some time, have they added editing capabilities that I was unaware of?

I might have to take another look.

The latest iteration released a few months ago had a good size of new features.

---

### Post by earlycj5 on 2010-08-06
> **ElSlunko said:**
> The latest iteration released a few months ago had a good size of new features.

Thanks.

I'll be sure to check that out when I have time.

---

### Post by jcolyn on 2010-08-06
> **earlycj5 said:**
> I've not tried it in some time, have they added editing capabilities that I was unaware of?

I might have to take another look.

I just started using it about a month ago so I can't say what changes have been made but it does have a lot of options.

---

### Post by ElSlunko on 2010-08-09
Trying out darktable. I REALLLLLY like the tools. It's far from being complete and definately needs a speed boost but those "plug ins" are very well designed in terms of UI.

---

### Post by FFred on 2010-08-20
> **manadi said:**
> Thanks for the reply. What are other alternatives for Linux which provide same capabilities as Darktable?

digiKam. It does way more though.

---

### Post by ElSlunko on 2010-08-29
Updated. Found out through OMG! [http://www.omgubuntu.co.uk/2010/08/darktable-photography-app-hits-060.html](http://www.omgubuntu.co.uk/2010/08/darktable-photography-app-hits-060.html)

Works a lot better now. Really love the tethered shooting.

---

### Post by robert shearer on 2010-08-29
> **ElSlunko said:**
> Updated.
Works a lot better now. Really love the tethered shooting.

I have installed the new version and cannot find the tethered option, or any documentation or how-to for tethering.

Any hints or tips ??

I tried <scan for devices> hoping that tethering options would/may follow, but alas, the camera is recognised and I can download images though no tethering options so far. :(

(Pentax DSLR K200D)

---

### Post by ElSlunko on 2010-08-29
> **robert shearer said:**
> I have installed the new version and cannot find the tethered option, or any documentation or how-to for tethering.

Any hints or tips ??

I tried <scan for devices> hoping that tethering options would/may follow, but alas, the camera is recognised and I can download images though no tethering options so far. :(

(Pentax DSLR K200D)

That's pretty much all there should be to it so I'm assuming the camera isn't supported.

---

### Post by robert shearer on 2010-08-29
> **ElSlunko said:**
> That's pretty much all there should be to it so I'm assuming the camera isn't supported.

Yeah, thought that might be the case. Thanks for confirming it.
I can stop wondering (and hoping) now.

---

### Post by ElSlunko on 2010-08-31
Here it is in action.

[[img]http://farm5.static.flickr.com/4116/4944634228_3d8b3dc29e.jpg[/img]](http://www.flickr.com/photos/elslunko/4944634228/)
[Darktable Tethered Shooting](http://www.flickr.com/photos/elslunko/4944634228/) by [ElSlunko](http://www.flickr.com/people/elslunko/), on Flickr

---

### Post by robert shearer on 2010-08-31
aaahhhrrg, now you're just taunting me..:):):)

Happy that it works for your camera, I would **love** to be able to use some form of tethering as most of my shots are studio macro and my old eyes and back would sure benefit from it.

---

### Post by earlycj5 on 2010-08-31
There are new PPAs


launchpad.net/~pmjdebruijn/+archive/darktable-release
launchpad.net/~pmjdebruijn/+archive/darktable-unstable

---

### Post by jcolyn on 2010-08-31
> **robert shearer said:**
> I have installed the new version and cannot find the tethered option, or any documentation or how-to for tethering.

Any hints or tips ??

I tried <scan for devices> hoping that tethering options would/may follow, but alas, the camera is recognised and I can download images though no tethering options so far. :(

(Pentax DSLR K200D)

First you have to have gphoto installed on your computer then check the below link to see if your camera is listed.

The Pentax K200D is not listed however if development continues I suspect more cameras will be included.

My D90 works good with it..


[http://darktable.sourceforge.net/documentation.shtml](http://darktable.sourceforge.net/documentation.shtml)

---

### Post by robert shearer on 2010-08-31
Thanks for the info..
Installed gphoto2 but still no tethering.

I don't think the camera is supported and may never be as its only in camera setting is as 'pc' link (mass storage device) and not p2p.

From reading the gphoto threads p2p needs to be set for tethering to work.

Despite being a loyal Pentax user (with lots of glass that works on any pentax camera) my next camera will be a brand that **supports** tethering.

Pentax dropped it with the k200d and I do not think any of the current models will nor are there any indications that Pentax/Hoya are even remotely interested. :( (pun intended)

---

### Post by Sir Rodness on 2010-09-09
> **earlycj5 said:**
> Try the "export" feature.  The files you're modifying are what Darktable is using to display changes that you make to the image.

The "export feature" found where? (i.e. File -> Export-> As JPG) 
Actually if anyone knows where you download a help file for this program that would be cool too.

:)

---

### Post by Sir Rodness on 2010-09-09
Ok, this is a pretty nice program. 
Finally figured out how to save finished files. Here's what you need to know for anyone else that got as lost as I did when I tried to save my finished images.

There are 2 modes (at least 2 that I've seen). **lighttable mode** and **darkroom mode**. These titles are posted at the top right of the application window.

Importing or double clicking on a thumbnail of the image you want to work with in lighttable mode will bring you to darkroom mode. Double clicking on the main image your working on in darkroom mode will bring you to lighttable mode. There are probably other options for this, but this is what works best for me at the moment.

In lighttable mode is where you have the option to save your finished image located under the "**export selected**" dropdown on the right.

Hope this helps anyone else that was fumbling around like I was trying to figure out how to save. 

Cheers.

---

### Post by tabascoterrier on 2010-09-18
I've just switched over to Maverick from Windows 7 where I was previously a Bibble user, and while Darktable is still clunky in places it seems to do everything I need it to, and does it well.

Decent RAW workflow was the one thing that kept me using Windows, so I'm an extremely happy camper that I can now do all my major tasks (development, photo editing, media consumption) easily on Linux.

---

### Post by MishaAct on 2010-09-18
> **tabascoterrier said:**
> I've just switched over to Maverick from Windows 7 where I was previously a Bibble user, and while Darktable is still clunky in places it seems to do everything I need it to, and does it well.

Decent RAW workflow was the one thing that kept me using Windows, so I'm an extremely happy camper that I can now do all my major tasks (development, photo editing, media consumption) easily on Linux.
The bibble is available on Linux. I think your licence is active too.

---

### Post by earlycj5 on 2010-09-20
> **MishaAct said:**
> The bibble is available on Linux. I think your licence is active too.

Long as it's Bibble Pro, I think you're correct.

---

### Post by rich-brun on 2010-10-05
I've been watching Darktable for a while now with quite a bit of excitement. I'm a photographer who mainly shots in raw, and just wants to tweak a large number of photos, and seriously play with a small number. There's noticeable improvements in the release candidates. I like the sidecar file approach, and the ease of building simple stacks and applying them to multiple files. 

I'm still having a few stability issues before I let it loose on my main photo collection. It often crashes in such a way that it needs all local config files removed and re-installed...

```
sudo apt-get remove --purge darktable -y;rm -r ~/.darktablecache ~/.darktabledb ~/.gconf/apps/darktable;sudo apt-get install darktable -y
```

Luckily, I'm letting it loose on a couple of hundred raw files, so it doesn't take any time to re-import the image files and their sidecar files.

---

### Post by earlycj5 on 2010-10-06
> **rich-brun said:**
> I've been watching Darktable for a while now with quite a bit of excitement. I'm a photographer who mainly shots in raw, and just wants to tweak a large number of photos, and seriously play with a small number. There's noticeable improvements in the release candidates. I like the sidecar file approach, and the ease of building simple stacks and applying them to multiple files. 

I'm still having a few stability issues before I let it loose on my main photo collection. It often crashes in such a way that it needs all local config files removed and re-installed...

```
sudo apt-get remove --purge darktable -y;rm -r ~/.darktablecache ~/.darktabledb ~/.gconf/apps/darktable;sudo apt-get install darktable -y
```

Luckily, I'm letting it loose on a couple of hundred raw files, so it doesn't take any time to re-import the image files and their sidecar files.

I've had the same issues.  Thanks for the code.

I'm excited about it's progress.

---

### Post by dinamic78 on 2010-10-07
@rich-brun and @earlycj5

Hi, im one of the developer of darktable, it seems pretty strange that you have crashes that needs a fully reset of the installation, please can you
provide a report of how the crash is reproduced.

The most common thing is that when darktable crashes the thumbnail cache gets broken and this results in when you starup darktable the next time, all thumbs are reproduced (which takes time and is very annoying)

Please provide a backtrace log of the crash, if you dont know how check
this following link: [http://blog.pcode.nl/2010/08/31/contributing-backtraces/](http://blog.pcode.nl/2010/08/31/contributing-backtraces/)

/Henrik

---

### Post by earlycj5 on 2010-10-08
> **dinamic78 said:**
> @rich-brun and @earlycj5

Hi, im one of the developer of darktable, it seems pretty strange that you have crashes that needs a fully reset of the installation, please can you
provide a report of how the crash is reproduced.

The most common thing is that when darktable crashes the thumbnail cache gets broken and this results in when you starup darktable the next time, all thumbs are reproduced (which takes time and is very annoying)

Please provide a backtrace log of the crash, if you dont know how check
this following link: [http://blog.pcode.nl/2010/08/31/contributing-backtraces/](http://blog.pcode.nl/2010/08/31/contributing-backtraces/)

/Henrik

Henrik,
I'll be happy to provide feedback, I should have been already.  :oops:

---

### Post by dinamic78 on 2010-10-08
> **earlycj5 said:**
> Henrik,
I'll be happy to provide feedback, I should have been already.  :oops:

The thing is a very anoying thing that when darktable crashes the thumbnailcache can crash (not always) but when it does all thumbs needs to be reloaded for a filmroll i have read some threads where users has thought this was the default behaviour of darktable which is very bad.

Yeasterday i did implement a backupsemantics of the thumbnailcache so if a crash occours the latest working one is restored and this works very good, due when i developing for darktable i dont have the time to let darktable to finish so i kill it with a result of crashed cache..

/Henrik

---

### Post by ayllu on 2010-10-19
I tryed darktable, with my kodak esysahre and is amazing, but instable for know, i coudnt export some of my jobs, and darktable need the zoom optión. Im using rawtherapy, but I gess darktable will be the best, depends how development goes, for now RT, has a great cuality, and sharpering, and higligths treatment is amazing, darktable dosnt have a good treatment for highligths.

---

### Post by Rocket J Squirrel on 2010-10-19
Not to throw this thread off track, but I'd love to use this Ubuntu computer for photo editing but can't find tools to profile the monitor. For that reason, I've been sticking to my Windows machine with and Lightroom and PS because I profiled the monitor with ColorEyes. 

But I'd cheerfully switch over if I could profile the monitor on this box and found a good profile-aware RAW processing program. Can someone point me to resources?

If this question starts to throw the thread off-topic maybe someone will know how to spawn a separate thread from it or something good like that.

---

### Post by dinamic78 on 2010-10-19
> **ayllu said:**
> I tryed darktable, with my kodak esysahre and is amazing, but instable for know, i coudnt export some of my jobs, and darktable need the zoom optión. Im using rawtherapy, but I gess darktable will be the best, depends how development goes, for now RT, has a great cuality, and sharpering, and higligths treatment is amazing, darktable dosnt have a good treatment for highligths.

About crashes ?, do you use the unstable PPA (which is more stable then 0.6 release :))

What do you mean about zoom option ? in lightable view you can use z key accelerator to fullscreen view of thumb under mouse. in darkroom view you can use scrollwheel to zoom...

Did you compared the result of highlight reconstruction module in darktable with result from RT ? (could you provide a comaprisation screenshoot?)

/Henrik

---

### Post by dinamic78 on 2010-10-19
> **Rocket J Squirrel said:**
> Not to throw this thread off track, but I'd love to use this Ubuntu computer for photo editing but can't find tools to profile the monitor. For that reason, I've been sticking to my Windows machine with and Lightroom and PS because I profiled the monitor with ColorEyes. 

But I'd cheerfully switch over if I could profile the monitor on this box and found a good profile-aware RAW processing program. Can someone point me to resources?

If this question starts to throw the thread off-topic maybe someone will know how to spawn a separate thread from it or something good like that.

Ubuntu has GCM (Gnome Color Manager) which works with some calibration tools (Spyder, Huey etc.) 

Darktable is profile aware...

/Henrik

---

### Post by ElSlunko on 2010-10-25
Started using DT again today after a month of not using it and I must say I'm impressed with the progress. Amongst a few new and very useful plugins, the quality and speed have also been upped.

Though I don't see myself using DT for those really long events where I bring home 3/4k photos (No really) I might start using it exclusively for modeling work.

Great job to the devs! Hope to see DT continue and flourish.

---

### Post by Pasta on 2010-10-25
Could anyone help me with how to install "Darktable" please?
I'm a newbie to Ubuntu Linux and google is my best friend for the moment.

I'm thankfull for any advice :)

---

### Post by dinamic78 on 2010-10-26
> **Pasta said:**
> Could anyone help me with how to install "Darktable" please?
I'm a newbie to Ubuntu Linux and google is my best friend for the moment.

I'm thankfull for any advice :)

Run this in terminal:
```

apt-add-repository ppa:pmjdebruijn/darktable-unstable

apt-get update

apt-get install darktable

```


/Henrik

---

### Post by Dragonbite on 2010-10-26
> **dinamic78 said:**
> Run this in terminal:

apt-add-repository ppa:pmjdebruijn/darktable-unstable

apt-get update

apt-get install darktable



/Henrik

You may want to take these commands and put them between CODE tags to keep the smileys away. ;)
```
apt-add-repository ppa:pmjdebruijn/darktable-unstable
apt-get update
apt-get install darktable

```

---

### Post by robert shearer on 2010-10-26
and for Ubuntu use...

```
sudo apt-add-repository ppa:pmjdebruijn/darktable-unstable
sudo apt-get update
sudo apt-get install darktable
```

---

### Post by earlycj5 on 2010-10-27
> **robert shearer said:**
> and for Ubuntu use...

```
sudo apt-add-repository ppa:pmjdebruijn/darktable-unstable
sudo apt-get update
sudo apt-get install darktable
```

Looks the same to me?

The prior instructions are for Ubuntu PPAs.

---

### Post by Dragonbite on 2010-10-27
> **earlycj5 said:**
> Looks the same to me?

The prior instructions are for Ubuntu PPAs.

He included the missing "sudo " before the commands.

---

### Post by robert shearer on 2010-10-27
> **earlycj5 said:**
> Looks the same to me?

The prior instructions are for Ubuntu PPAs.

see post #57 where user Pasta says > I'm a newbie to Ubuntu Linux

Whilst we all know about the sudo usage I thought it may be helpful to include this to ensure it worked as intended, for a newcomer. :)

---

### Post by robert shearer on 2010-10-29
Darktable draft user manual released....:)

[http://darktable.sourceforge.net/](http://darktable.sourceforge.net/)

---

### Post by ElSlunko on 2010-10-29
> **robert shearer said:**
> Darktable draft user manual released....:)

[http://darktable.sourceforge.net/](http://darktable.sourceforge.net/)

Sweet! thanks!

---

### Post by ozzyprv on 2010-11-04
Thanks for all the good comments. I am a DigiKam user, but just installed Darktable. I am liking it so far.

---

### Post by Dixon Bainbridge on 2010-11-04
Any photo pro's able to feedback on its use? Or is it still a bit new to pass credible comment on?

Looks like a great app.

---

### Post by ElSlunko on 2010-11-05
Has good output and color rendition though the initial images are usually underexposed but you can adjust the defaults to your liking.

Powerful tools. Can't stress how great the tools are. Only reason I don't use it more often though is the speed. Just really slow in it's current state so while it's great if your sets are small. However you can always copy + paste mass changes so that helps a bit.

Tethered shooting is neat if your camera is supported.

---

### Post by dinamic78 on 2010-11-05
> **ElSlunko said:**
> Has good output and color rendition though the initial images are usually underexposed but you can adjust the defaults to your liking.

Powerful tools. Can't stress how great the tools are. Only reason I don't use it more often though is the speed. Just really slow in it's current state so while it's great if your sets are small. However you can always copy + paste mass changes so that helps a bit.

Tethered shooting is neat if your camera is supported.

Im curious about the slowness you mention, what are the specs for your computer you run darktable on?, which version of darktable do you use ?, and while you at it, could you run 'darktable -d perf' and put the result in pastbin for review..

Do you have a decent Gfx card you could try out our exprimental opencl branch which does make use of GPU for demsaic... (decreased time from 1.5 sec to 60ms for demosaic process)

/Henrik

---

### Post by robert shearer on 2010-11-05
> **dinamic78 said:**
> 
Do you have a decent Gfx card you could try out our exprimental opencl branch which does make use of GPU for demsaic... (decreased time from 1.5 sec to 60ms for demosaic process)

/Henrik

Hi Henrik,  have you got a link for the  > experimental opencl branch ??
Sounds like something I would like to try.

I have an older AMD 3000+ single core, 1 Gig ram and an ATI 9250 (using the open source Drivers)

---

### Post by dinamic78 on 2010-11-05
> **robert shearer said:**
> Hi Henrik,  have you got a link for the   ??
Sounds like something I would like to try.

I have an older AMD 3000+ single core, 1 Gig ram and an ATI 9250 (using the open source Drivers)

There is no installation packages for this, and you need to compile darktable from source, this might be a hard process for the unfamilliar, first off follow the instructions at the bottom under section '4.9 git version' @ [http://darktable.sourceforge.net/install.shtml](http://darktable.sourceforge.net/install.shtml) 
( skip 'make install' step )

This builds the master branch of darktable, when running ./configure --prefix=/usr it would probably fail and you need to install the dependencies mention by configure script...

When you successfully got thru this step you should change branch
using 'git checkout opencl' then run thru the steps as you previously did on master branch to compile..

If you get problems please visit IRC channel #darktable @ freenode for som support...

/Henrik

---

### Post by ElSlunko on 2010-11-05
> **dinamic78 said:**
> Im curious about the slowness you mention, what are the specs for your computer you run darktable on?, which version of darktable do you use ?, and while you at it, could you run 'darktable -d perf' and put the result in pastbin for review..

Do you have a decent Gfx card you could try out our exprimental opencl branch which does make use of GPU for demsaic... (decreased time from 1.5 sec to 60ms for demosaic process)

/Henrik

Sure thing. I'll get to it by Sunday because unfortunately I had to make a fresh install of Ubuntu and I'm going to be busy for the next couple of days.

Running on an i7 w/ a GTX 260. It's not dramatically slow, I was probably being too dramatic myself. I think it's just the updates when changing exposure & moving between photos in dark room mode is a little slower than other converters.

---

### Post by dinamic78 on 2010-11-06
> **ElSlunko said:**
> Sure thing. I'll get to it by Sunday because unfortunately I had to make a fresh install of Ubuntu and I'm going to be busy for the next couple of days.

Running on an i7 w/ a GTX 260. It's not dramatically slow, I was probably being too dramatic myself. I think it's just the updates when changing exposure & moving between photos in dark room mode is a little slower than other converters.

moving between images in darkroom does involv a demosaic process between 1-2 secs.. (myself has setted the default demosaic algo to linear due it's the fastest one and when i work with an image, i set the demosaic algo i want.. this gives some speed in switch of images) im sure that is what appears to be a little slower.. soo, 
with opencl this is downed to 30-300ms dependent on GPU hw...

The speed with the modules such as exposure change is probably due that we work on 32bit float space and not 16bit as other raw converters does..

/H

---

### Post by Dixon Bainbridge on 2010-11-06
I'm interested in trying out this app having read through the thread.

I'm not interested in using it as a raw converter as I rarely shoot raw nowadays and if I do I convert using Capture One. I shoot tethered in Capture One also. It's still the best for both of those things, so no point changing.

However, for organising and adjusting images and more importantly database management and filter presets, I would really be interested in something that can offer a real viable alternative to Light Room. 

Does Darktable support colour profiles for pro cameras like Mamiya, Leaf, Hasselblad etc?

---

### Post by dinamic78 on 2010-11-06
> **Dixon Bainbridge said:**
> I'm interested in trying out this app having read through the thread.

I'm not interested in using it as a raw converter as I rarely shoot raw nowadays and if I do I convert using Capture One. I shoot tethered in Capture One also. It's still the best for both of those things, so no point changing.

However, for organising and adjusting images and more importantly database management and filter presets, I would really be interested in something that can offer a real viable alternative to Light Room. 

Does Darktable support colour profiles for pro cameras like Mamiya, Leaf, Hasselblad etc?

Why use colorprofiles with jpegs ??? where the raw data already has been modified ??

If you can provide ColorChecker raw images of those camera enhanced color matrices could be implemented, you really should have this talk with Pascal (our color manager)...

Darktable IS mainly a rawconverter and have alot of drawbacks when we talking about using it as a manager still it does handle your images,colorlabes/taggin ala XMP, BUT the current implementation of tagging,filtering and collections are pretty simple and needs a big rework...   
I have a few suggestions on this front and after v0.7 release in 2-3 weeks i will start to implement those...


/Henrik

---

### Post by bailout on 2010-11-06
I installed it and had a quick look. My first question is what does it mean by 'import' images?

I have my photos on a seperate data partition and want to work with them in their current location. Will darkroom make copies of them in another location if I import them?

I did try just importing one image to test and would agree with the comments that it seemed very slow.

---

### Post by Dixon Bainbridge on 2010-11-06
> **dinamic78 said:**
> Why use colorprofiles with jpegs ??? where the raw data already has been modified ??
/Henrik

My colour profiles question was a general one, not related to my shooting habits :) Sorry, should have made that a bit clearer.

---

### Post by dinamic78 on 2010-11-07
> **bailout said:**
> I installed it and had a quick look. My first question is what does it mean by 'import' images?

I have my photos on a seperate data partition and want to work with them in their current location. Will darkroom make copies of them in another location if I import them?

I did try just importing one image to test and would agree with the comments that it seemed very slow.

Darktable does NOT touch your orginal images and a import of filmroll (dricetory) is not moving around your images, it jsut adds the directory to the db and references to your images, so no f-spot move around/structure new image storage are performed..

/Henrik

---

### Post by dinamic78 on 2010-11-07
> **Dixon Bainbridge said:**
> My colour profiles question was a general one, not related to my shooting habits :) Sorry, should have made that a bit clearer.

:) so the answer to this is no, BUT if you can provide shoots of ColorChecker we can produce one..

/Henrik

---

### Post by ozzyprv on 2010-11-07
> **dinamic78 said:**
> ...  
I have a few suggestions on this front and after v0.7 release in 2-3 weeks i will start to implement those...


/Henrik

Great news! I am excited already.

---

### Post by ayllu on 2010-11-14
Allways,than a want to export a photo with modifications of noice and sharpering I get this error: 

terminate called after throwing an instance of 'std::bad_alloc' what():  std::bad_alloc. 

I have 3 gb of ram, so has no sense, 

Im upgrade to  form darktable 0.6 to 0.6+556 but didnt solve my problem.

---

### Post by dinamic78 on 2010-11-15
> **ayllu said:**
> Allways,than a want to export a photo with modifications of noice and sharpering I get this error: 

terminate called after throwing an instance of 'std::bad_alloc' what():  std::bad_alloc. 

I have 3 gb of ram, so has no sense, 

Im upgrade to  form darktable 0.6 to 0.6+556 but didnt solve my problem.

i think you are using a too small radie on the denoise module, the smaller it is the more memory is allocated, can you verify that ?

/Henrik

---

### Post by ayllu on 2010-11-17
>  i think you are using a too small radie on the denoise module, the smaller it is the more memory is allocated, can you verify that ?

/Henrik 
how can I do that? I chek my memory performance and is take almost 60%, when it crash.

---

### Post by dinamic78 on 2010-11-18
> **ayllu said:**
> how can I do that? I chek my memory performance and is take almost 60%, when it crash.

please can you provide a backtrace report, put it on pastbin.

instructions how can be seen here: [http://blog.pcode.nl/2010/08/31/contributing-backtraces/](http://blog.pcode.nl/2010/08/31/contributing-backtraces/)

/Henrik

---

### Post by ayllu on 2010-11-19
Here is the back-trace, hope will be helpful. Its happens when I export an image, but happens almost when I apply noise reduction, or sharpening, or colour correction, but also with other functions, but, if I apply just one function works.

---

### Post by yorkie on 2010-11-21
Darktable Version 0.7 released

---

### Post by ElSlunko on 2010-11-22
0.7 looking great so far!

---

### Post by Dixon Bainbridge on 2010-12-15
I've had a little play with Darktable and its pretty neat. My only gripe is the export feature - its too cumbersome. I think things would really benefit from a lightroom style rclick > export option on multiple or single selections.

---

### Post by daverush on 2010-12-28
Just started using Darktable - had crashes importing film rolls.  Debug file attached as two parts.

---

### Post by daverush on 2010-12-28
It just crashes eavery time it's loaded!

---

### Post by digitography on 2011-01-21
Being a lightroom user, I am pretty impressed, however

Where is  Print option? seems like an immense oversight, have I missed something?
Export does not offer a basic webpage output? only Picasa output which I don't want.

---

### Post by ElSlunko on 2011-01-21
Don't think there is a print option. At the moment it's mostly just a raw converter with minimal database capabilities. Not sure if it's in the scope of the project to have feature per feature match of Lightroom and other workflow applications. It does have a very nice toolset and great quality output.

---

### Post by prokoudine on 2011-01-21
> **digitography said:**
> Where is  Print option?

Printing isn't implemented yet.

> **digitography said:**
> 
Export does not offer a basic webpage output? only Picasa output which I don't want.

Version from Git has Flickr exporting as well. Beyond that there is only simple exporting to a folder and emailing so far. But exporters are pluggable (like most everything else in darktable).

---

### Post by jabog6 on 2011-03-06
> **daverush said:**
> It just crashes eavery time it's loaded!

Same here.  Launching it via command-line ("darktable %U") crashes on file import, returns "Illegal instruction"...

---

### Post by flar on 2011-03-07
I've been looking at ways to improve my digital photography workflow, so I checked out a bunch of software over the past few weeks.  My current setup is UFRaw/Gimp.

I want to work on Linux, preferably with open source software, but I tested proprietary and windows/mac software as well because I needed a reference point and wanted to know what the state-of-the-art RAW/workflow software looks like.  

Here's what I tested:  Adobe Lightroom, Bibble Pro, Raw Therapee, LightZone, Nikon Capture NX, RawStudio, UFRaw, Capture One, and Darktable.

Lightroom is the clear winner for my purposes (except the most important thing, it doesn't run on linux!), but to my surprise (since I had never even heard of it), Darktable came in a strong second.  I prefer Darktable even over the other paid software like Bibble, Capture Oee and Lightzone.  Capture NX does the best RAW conversion but the interface is poor and it lacks many features.   


Darktable is very impressive, and I really can't believe how mature it is given the short time it's been under development.
Congratulations and thank you to the developers, keep up the good work!


What I like most about Darktable:

-great user interface
-stable (I put it through some heavy work last week)
-has most features I need
-excellent perspective correction tool
-also has lens distortion correction
-ability to save styles and copy and paste history from image to image


Criticisms and things missing from Darktable:

-I find the tonecurve interface annoying.  It's similar to the parametric style tonecurves in Lightroom, but has some problems.  There are too many points on the x-axis.  Moving the little triangles can completely screw things up.  The parametric curves limit the amount you can bend the curve and only work on small sections; I am often unable to get a smooth curve exactly how I want it.

-What I would really like is a classic curves tool, where you can add points and move the curve freely.  

-output sharpening.  This seems like a simple thing to implement, I want to batch export jpegs, resized and sharpened for viewing on computer screen or web. 

-simple colour correction.  The existing colour correction tools are too cryptic/complicated/unfamiliar.  I would like sliders for cyan/red, magenta/green and yellow/blue (preferably where you could select whether to apply to highlights, midtones or shadows).  

-simple saturation and vibrance controls (the velvia plugin isn't very intuitive and at first I thought it was just to give the effect of using Velvia film--maybe it is?)

-some of the sliders are too sensitive, or have too great a range of adjustment and thus are hard to fine-tune. 



Other than that, I will continue to use Darktable and will be following its development closely. 

My first photoshoot using darktable:  [http://forum.skyscraperpage.com/showthread.php?t=189279](http://forum.skyscraperpage.com/showthread.php?t=189279)

(I am somewhat displeased with the results, I couldn't get the colours how I wanted them, maybe with practice I can get better results)

For comparison, here is my photo website, all photos processed with UFRaw + Gimp:  [www.metroperspectives.com](www.metroperspectives.com)

---

### Post by rufus.wilson on 2011-07-19
Dear all,

I encountered a small issue but it is annoying.

I imported some pictures from a folder, then I deleted some of them but I can't get them to be imported again. I couldn't find the database file that saved this information. I deleted the library.db, and it did not do what I expected.

To the developpers, except that, your software is a very good rival (if not better) of all other softwares I tested so far.

Thank you for helping me.
Rufus

---

### Post by c-m on 2011-07-26
I have installed darktable 0.9 and have been watching the video here: 

[www.youtube.com/watch?v=cremv70Roho](www.youtube.com/watch?v=cremv70Roho)

The problem is at 1:44, in my version I don't have those colour options.

He has an option called Velia, with saturation, vibrance, mid-tone balance. I don't have any of that in my darktable under colour header.

Under the colour header, mine has -overexposed -colour correction -colour zones

---

### Post by robert shearer on 2011-07-26
On the install page of the Darktable website (    [http://darktable.sourceforge.net/install.shtml](http://darktable.sourceforge.net/install.shtml)     )see item 4.3 and the links there.......

> ubuntu packages

for stable releases add the Darktable Release PPA.
for stable releases plus some extra's add the Darktable Release Plus PPA.
if you are adventurous and are willing to deal with problems from time to time add the Darktable Unstable PPA, don't use this PPA if you do time critical work with darktable


You are probably running the Stable version.
Other versions have more features ( and more chance for breakage :D )

having said that, currently the Unstable PPA seems to work fine.
If you are adventurous and/or really need those features you could try installing from that PPA.

If you are unfamiliar with **ppa-purge** then research that first so you will know how you can get back to your current version if the Unstable doesn't work for you (or your hardware.)
 (ppa-purge is in the Ubuntu repos and can be installed through software-centre/Synaptic etc)

Cheers Bob.

---

### Post by 23dornot23d on 2011-07-26
> 
If you are unfamiliar with **ppa-purge** then research that first so  you will know how you can get back to your current version if the  Unstable doesn't work for you (or your hardware.)
 (ppa-purge is in the Ubuntu repos and can be installed through software-centre/Synaptic etc)


Works just fine here ...... thanks for the link to the PPA ...... set it up in synaptic and then disabled the PPA
for the time being ..... will see how it goes .... at the current release .... :)

---

### Post by dinamic78 on 2011-07-27
> **c-m said:**
> I have installed darktable 0.9 and have been watching the video here: 

[www.youtube.com/watch?v=cremv70Roho](www.youtube.com/watch?v=cremv70Roho)

The problem is at 1:44, in my version I don't have those colour options.

He has an option called Velia, with saturation, vibrance, mid-tone balance. I don't have any of that in my darktable under colour header.

Under the colour header, mine has -overexposed -colour correction -colour zones

This is probably due to only a few "standard" modules are "activated" by default... in the right panel in darkroom view, at the bottom you have a "more plugins" panel, there can you "activate" more modules of your choice, also you can make favorites that wills how up when pushing the favorites module group button under the histogram.

/Henrik

---

### Post by dinamic78 on 2011-07-27
> **rufus.wilson said:**
> Dear all,

I encountered a small issue but it is annoying.

I imported some pictures from a folder, then I deleted some of them but I can't get them to be imported again. I couldn't find the database file that saved this information. I deleted the library.db, and it did not do what I expected.

To the developpers, except that, your software is a very good rival (if not better) of all other softwares I tested so far.

Thank you for helping me.
Rufus

How did you actually delete them ?, did you reject them ? if so the references to the images are still there and you use the filter at top bar to show only rejects, then you can select all ctrl-a and use "remove" in the "selection" plugin to remove the references to the selected images eg. deleting them from database but preserves the actually file on disk.

/Henrik

---

### Post by dinamic78 on 2011-07-27
> **digitography said:**
> Being a lightroom user, I am pretty impressed, however

Where is  Print option? seems like an immense oversight, have I missed something?
Export does not offer a basic webpage output? only Picasa output which I don't want.

"export to webpage" is pretty undefined what but we do include a
web page gallery output which will create a basic html page with
the selected images which can be uploaded to a webspace of your choice, we do also support as you mention export to picasa and flickr using their official api.

/Henrik

---

### Post by c-m on 2011-07-31
I have installed this version, which is the latest unstable version but still i don't have these colour options. What's wrong?

0.9.1-0pmjdebruijn1~maverick

---

### Post by prokoudine on 2011-07-31
> **c-m said:**
> I have installed this version, which is the latest unstable version but still i don't have these colour options. What's wrong?

In the bottom of the sidebar (in darkroom mode) you have expandable pane to enable various processing plug-ins. Use it :)

---

### Post by PayPaul on 2011-09-28
> **23dornot23d said:**
> Works just fine here ...... thanks for the link to the PPA ...... set it up in synaptic and then disabled the PPA
for the time being ..... will see how it goes .... at the current release .... :)

I tried to find Darktable in Synaptic and couldn't. I've been burned lately with trying to compile packages (Fractal Programs) and I'm looking for a more fully featured RAW processor. I really detest UFraw and its limited features. I might need to stop being lazy and reinstall Win7 and get back to Photoshop and ACR. Yick! Don't want to go back to windows but may not have a choice as the RAW programs I find for Ubuntu are extremely lacking. 

How do I install it from a PPA?

Found out I have to add the PPA to repositories using this code:
```

 udo add-apt-repository ppa: mjdebruijn/darktable-release-plus

```  I then had to find it in Synaptic. The problem then comes up that that software is not "authenticated". Is this typical with programs like this from third party providers?

So I clicked OK to install and got the following errors:

E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to lock the download directory

Wonderful. Great. I guess I'm going back to Windows and ACR. Unless of course someone can help me with the install.

---

### Post by Zimmer on 2011-09-28
for your info...
[https://launchpad.net/~pmjdebruijn/+archive/darktable-release/+index#](https://launchpad.net/~pmjdebruijn/+archive/darktable-release/+index#)

For the stable release..

To add the PPA for Natty Go to System>Administration> Software Sources ,

Click the tab for  'other software' and add an entry with 

Type 'Binary'
URL 

"http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu" (note:do not include the quotes...)

Distribution
natty

Components
main

Your problems may have occured from missing the Distribution and Component ID in your command...

>  udo add-apt-repository ppa: mjdebruijn/darktable-release-plus

Which, I guess should have read 
 sudo add-apt-repository ppa:mjdebruijn/darktable-release-plus/ubuntu natty main

Not sure how you recover from the initial error... if , indeed , Synaptic DID install anything..

---

### Post by PayPaul on 2011-09-28
Surprisingly Synaptic did install it second time around. I did get the message about it being from an untrusted source but I figure I can trust you people in here. Can't I?

The program works but has a real cluttered interface and the save options are rather numerous and also complicated. I need to read the manual. It's a learning curve (Pun Intended)..

I like how it was added as a right click option when I want to open one of my KDC files. KDC is the Kodak RAW format. It's still missing a clarity setting but has sharpening, tonal balance and various contrast tools. Darktable will also make HDRs.


Update: A day later with some manual pages read and I'm starting to love this program. It has more controls and seemingly more possibilities than ACR. Once you get the idea to create what the program calls "filmrolls", essentially a database of folders containing the RAW files, editing on the fly becomes much easier. There are settings for tonal balance, multiple temperature controls and better still you can alter exposure and black point by clicking and dragging on the histogram itself. I never could have that much control in ACR. One can save presets (styles) of the entire editing process or individual modules of editing such as exposure, white balance, sharpening etc. One can even go back in history and change modules to revise and correct mistakes. ACR never could do that. The workflow in the beginning of my use of this program is going to be time consuming but once I get my presets (styles) built up, processing will go a lot faster.

I'm still trying to get the hang of how the program saves files. It's still, in my opinion clunky but it does allow for so much more control of where the image goes, how it's saved and where it's saved. The developers do cram all that on one set of panels that require scrolling down for all the options available but very much worth the pricetag...hee, hee, free! Nice...real nice.

---

### Post by prokoudine on 2011-09-30
> **PayPaul said:**
> It's still missing a clarity setting 
Try equalizer, or highpass in overlay blending mode

> **PayPaul said:**
> The developers do cram all that on one set of panels that require scrolling down for all the options available but very much worth the pricetag...hee, hee, free! Nice...real nice.
You can disable plug-ins you don't use and make theones that you use favourite (third click on an icon makes red highlight), then switch between full set and fav set.

---

### Post by PayPaul on 2011-09-30
> **prokoudine said:**
> Try equalizer, or highpass in overlay blending mode


You can disable plug-ins you don't use and make theones that you use favourite (third click on an icon makes red highlight), then switch between full set and fav set.

You sound as if you've been using this program for awhile. I was looking for a way to get some pre-set styles for it online as I can find for ACR. Do you know of anyone or any site that have any of these? If that's not the case well, after I've worked with it a few days with some key photos and created styles and presets of my own I wonder if there's a place here where I could post them.

---

### Post by prokoudine on 2011-10-04
> **PayPaul said:**
> You sound as if you've been using this program for awhile. I was looking for a way to get some pre-set styles for it online as I can find for ACR.

There's only [http://sourceforge.net/apps/trac/darktable/wiki/DarktableStyles](http://sourceforge.net/apps/trac/darktable/wiki/DarktableStyles) so far

---

### Post by PayPaul on 2011-10-10
I've discovered the debugging mode for Darktable. One simply inputs  the following

```
gdb darktable
```and then after you get this:

```
[SIZE=2]GNU gdb (Ubuntu/Linaro 7.2-1ubuntu11) 7.2 Copyright (C) 2010 
Free Software Foundation, Inc. License GPLv3+: GNU GPL version 3 
or later <http://gnu.org/licenses/gpl.html> This is free software: 
you are free to change and redistribute it. There is NO WARRANTY, 
to the extent permitted by law.  Type "show copying" and 
"show warranty" for details. This GDB was configured as 
"x86_64-linux-gnu". 
For bug reporting instructions, please see: 
<http://www.gnu.org/software/gdb/bugs/>... Reading symbols 
from /usr/bin/darktable...Reading symbols from /usr/lib/debug/usr/bin/darktable...done. done[/SIZE]. 
```[SIZE=2]


After that run using:[/SIZE]

```
[SIZE=2]r darktable[/SIZE]

```Debugging mode is kind of a babysitter for this program. I find that if I simply try to run it from the launcher it crashes my pc altogether. With debugging mode if the thing crashes you get this:

```
[SIZE=2]Program terminated with signal SIGKILL, Killed. The program no longer exists. (gdb) [/SIZE] 
```

---

### Post by tonymaro on 2011-10-13
> **PayPaul said:**
> 
Wonderful. Great. I guess I'm going back to Windows and ACR. Unless of course someone can help me with the install.

My suggestion if threatening us that quickly - do as you say, go back to Windows.  You'll never be happy otherwise.

It sounds like you have other issues not related to installing Darktable specifically - you have broken packages.

Try running this from the command line and it will give more info:

sudo apt-get update

followed by

sudo apt-get dist-upgrade

It will give a suggestion as to what's broken and how to fix it.

**** EDIT ****

I see you got it to install on a second try.  Glad to see that.

As far as Darktable goes, it's interesting, but not even close to being intuitive to use.  It's been scanning my library for something like an hour now but unfortunately there's no feedback that shows how far along it is...  that's annoying.  CPU usage for it at 50% on my quad-core 3.2 GHz.

---

### Post by PayPaul on 2011-10-13
I did get an acknowledgement from the developer. He suggested a memory allocation issue. It could be from my end or theirs. I'd love to use the program and tonight I ran it through its paces in debugging mode with the System Monitor running and the usual programs running too. I posted a thread in General Help about that one.

I'd say I'm not the only one here who finds a lot of good in Ubuntu and a few niggling problems of functionality and ease of use that could be addressed. I enjoy the fact that many of these packages can be either correct or at least diagnosed much easier than in Windows. I'm also glad of the response time from the developers of some of these programs and from this forums members. I never got the kind of feedback and assistance from any Windows based program nor from a lot of Microsoft forums.

Edit: My CPU usage is highest when running Firefox not when simply running Darktable. It sometimes goes as high as 100% on one of the cores. Firefox is so notorious, Windows version or as it appears, in the Linux version, for being a resource hog. I have dual CPUS and it's greedy for both of them.

---

### Post by dckirba on 2011-11-15
Hi guys,

I've been using Darktable for a few months now and I've found the developers very helpful at all times.

You can find them on IRC chat pretty much anytime :)

Cheers,
David

---

### Post by c-m on 2011-11-15
Surprisingly, there is no way to view an image at 100% in darktable.

Surely this feature is necessary otherwise the quality of the image you're seeing when processing is dependent on darktable's scaling algorithm

---

### Post by PayPaul on 2011-11-15
Today I found the new ppa and installed the 64 bit deb update and now Darktable, so far, runs smoothly. It's really a pleasure to see an update that resolves bugs happen quickly enough. I did post the bug to the mailing list and got some very positive feedback from the developers. Try doing that with other operating systems and software developers for them! So far, using Ubuntu has been mostly positive and I'm glad to have switched over. That's especially apparent when improvements like this one happen as they seem to do.

Here's the link to the pages with the PPAs for Darktable.

[https://launchpad.net/~pmjdebruijn/+archive/darktable-release/+packages](https://launchpad.net/~pmjdebruijn/+archive/darktable-release/+packages)

---

### Post by prokoudine on 2011-11-16
> **c-m said:**
> Surprisingly, there is no way to view an image at 100% in darktable.

Of course it is possible :) Middle-click for zooming always worked for me, not mentioning the shortcuts.

---

### Post by VaclavC on 2011-11-24
Maybe this is a dumb question, but where I can find some tool to remove red eyes in darktable?

---

### Post by ofnuts on 2011-11-25
> **jcolyn said:**
> Has anybody tried DigiKam?

I've been using it on my Kubuntu machine and like it better than Lightroom or Aperture.

It will also work on Ubuntu.I use it, but I'm not a fan... It's big shortcoming IMHO is that it can"t handle JPG+RAW as a pair... (for instance, display one single thumbnail, move/copy/delete both...). And the creation of directories when importing pictures isn't what it should/could be.

---

### Post by expired_fox on 2011-11-25
> **VaclavC said:**
> Maybe this is a dumb question, but where I can find some tool to remove red eyes in darktable?
It's impossible in general right now. The selective tools are not ready yet.

---

### Post by VaclavC on 2011-11-25
> **expired_fox said:**
> It's impossible in general right now. The selective tools are not ready yet.

Thank you for your answer. Is there any chance that it will be available in reasonable time?

---

### Post by expired_fox on 2011-11-25
> **VaclavC said:**
> Thank you for your answer. Is there any chance that it will be available in reasonable time?
Don't know.
The DT core is ready to support layers and thus we need selection tools (Henrik Andersson is making the curve selection now).
We also need some sort of brush selection — I thought about making it myself, but now stuck with the shadow recovery plugin and don't have enough time even for that, my job takes a time too.

And I don't know is there any mockup for layered workflow. The current interface is not ready yet for this task. And it will take quite a long time anyway to implement it.

I'm sure selection tools will be released in a year, not sure if this time is reasonable :)

May be user prokoudine knows more about this :)

---

### Post by c-m on 2011-11-25
Double clicking on a thumbnail doesn't always take me into darktable mode to process that image. 

Likewise if i'm in darktable mode and I click on the film strip along the bottom, it doesn't always change the image. Instead I have to press the space bar

---

### Post by prokoudine on 2011-11-25
> **VaclavC said:**
> Thank you for your answer. Is there any chance that it will be available in reasonable time?

expired_fox pretty much covered it. What Henrik is working on is editing of masks so that you can secure parts of an image from applying some filter.

I don't think anybody knows when complete localized editing will be available. We already have spot removal, so things are doable. It's just with darktable you never know: people come out of blue with just *any* kind of pathes.

@c-m

Are you by any chance on 10.04? I certainly heard reports on similar misbehaviour from 10.04 users.

---

### Post by c-m on 2011-11-25
No i'm version darktable 0.9.2+218~gfe1fb6f

Its the latest version in my repository

---

### Post by prokoudine on 2011-11-26
> **c-m said:**
> No i'm version darktable 0.9.2+218~gfe1fb6f

Its the latest version in my repository

I meant Ubuntu 10.04

---

### Post by c-m on 2011-11-27
Sorry, no 11.10

---

### Post by ElSlunko on 2011-12-26
Started using DT more lately. It's much more stable for me and I've been able to produce a few photo sets through it.

Thank you devs! Trying to see how far I can take this photography venture using these tools.

---

