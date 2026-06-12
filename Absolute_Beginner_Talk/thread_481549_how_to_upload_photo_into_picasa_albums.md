---
title: "how to upload photo into picasa albums?"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-06-22
Hi
Thank you for reading my post
When i had windows i could easily upload my photo from within the picasa software into picasa web album.

but not there is no picsaa application capable of uploading images into picasa web albums, is there any linux-ish software that could upload pictures into picasa web albums?

It is really hard to upload them via browser.


Thanks

---

### Post by dbbolton on 2007-06-22
there's a linux version of picasa (requires WINE)

[http://picasa.google.com/linux/](http://picasa.google.com/linux/)

---

### Post by amendt on 2007-06-23
**F-Spot photo Manager** has the option of uploaded your pictures to picasa Albums so you don't have to use Firefox to upload photos. Just select the pictures and click on export to Picasa

---

### Post by jcronkhite on 2007-06-23
There is a Google Group where I read the next Linux version of Picasa will include the web upload feature by the end of this summer.  I love Picasa and have even purchased the additional storage.  It serves as an online backup of all of my photos, not to mention I can share them privately or publicly.  Right now, I'm using F-spot and uploading until the updated version of Picasa is available.

---

### Post by Sweet Spot on 2007-07-08
I have a related question:  I'm shooting pictures like crazy lately, and usually use Photobucket to store my stuff, but Picasa Web albums seems like a decent enough place to do it, especially since I use Picasa as a photo organizer. It just needs to be a bit more integrated w/web albums, and you said it will be at the end of the summer. 

My question is what do you (if you do at all) use to resize your pics before uploading ? Since there's a file size limit for non paying customers, I'm looking for the best size/resolution to upload, but would like it to be all done within Picasa if possible. I Know Picasa does have the export feature which downsizes in resolution if you'd like, but was wondering if there was anything which did a better job, since I don't want my pics to be ridiculously small but with a still largish file size... 

d

---

### Post by dbbolton on 2007-07-09
> **Sweet Spot said:**
> I have a related question:  I'm shooting pictures like crazy lately, and usually use Photobucket to store my stuff, but Picasa Web albums seems like a decent enough place to do it, especially since I use Picasa as a photo organizer. It just needs to be a bit more integrated w/web albums, and you said it will be at the end of the summer. 

My question is what do you (if you do at all) use to resize your pics before uploading ? Since there's a file size limit for non paying customers, I'm looking for the best size/resolution to upload, but would like it to be all done within Picasa if possible. I Know Picasa does have the export feature which downsizes in resolution if you'd like, but was wondering if there was anything which did a better job, since I don't want my pics to be ridiculously small but with a still largish file size... 

d
i use the gimp. you just go to Image > Scale image. there, you can select the new size/quality.

---

### Post by Sweet Spot on 2007-07-09
Does gimp allow batch editing ?  

Another question:  I like Picasa web albums, but I don't foresee constantly using the 5 pics at a time web uploader since it takes a year and a day, and is annoying since I have to keep track of which # photo was last to upload. I'm using F-spot on a recommendation to batch upload, but I only installed it last night, and it crashed on me when I tried to export something I think....

Is there perhaps another web album similar to picasa or flickr etc.. which has a decent interface, and is Linux friendly ?  I don't want to use a complicated program with a hack installer such as 'Album' or the like since I don't have a web site per say, and just want to use someone elses web interface. 

Or perhaps I can use my blog site ? I just created it, and it's very basic/simple but I think it's google's eblog, and when I try to bloc pics using Picasa, all I get is a blank gray screen, and nothing ever happens.   Photobucket is ok, but I'm also getting tired of uploading only 20 pics at a time... What do you guys use ?

Doug

---

### Post by adamklempner on 2007-07-09
> **Sweet Spot said:**
> My question is what do you (if you do at all) use to resize your pics before uploading ? 

If you happen to be using Kubuntu, just install _[kim (KDE Image Menu)]("http://bouveyron.free.fr/kim/index.html")_.  I believe it is listed in the repository as "konq-kim" or something of that nature.  What kim does is add a "right click" option to konquerer, the file browser, that allows you to do batch operations on images without using gimp.  For example:  Highlight 27 images, right click, resize to 1024x768, ok, and it resizes them all in a matter of seconds.  I make heavy use of this program and I really like it.  It does format conversion also, among other things.

I don't know if there is an equivalent for gnome or not though.

---

### Post by lawr_rawr on 2007-07-09
You can install the Windows version of Picasa under Wine, and then over-write your Picasa2 directory in the location where the Linux-specific version was installed. This gives you access to Picasa WebAlbums upload.  There are a few Windows-specific features that won't work (screensaver, etc.) 

First, install the Linux version of Picasa. Then, use Wine to install the Windows version. For me, the Windows+Wine version installed to ~/.wine/drive_c/Program Files/Picasa2. The Linux version installed to /opt/picasa/wine/drive_c/Program\ Files/Picasa2.

Check your locations first to make sure they're the same as mine, then try this:
```
sudo mv /opt/picasa/wine/drive_c/Program\ Files/Picasa2 /opt/picasa/wine/drive_c/Program\ Files/Picasa2.old
sudo cp ~/.wine/drive_c/Program Files/Picasa2 /opt/picasa/wine/drive_c/Program\ Files/Picasa2
```

I was able to launch Picasa and upload to webalbums after that!

---

### Post by Sweet Spot on 2007-07-09
> **lawr_rawr said:**
> You can install the Windows version of Picasa under Wine, and then over-write your Picasa2 directory in the location where the Linux-specific version was installed. This gives you access to Picasa WebAlbums upload.  There are a few Windows-specific features that won't work (screensaver, etc.) 

First, install the Linux version of Picasa. Then, use Wine to install the Windows version. For me, the Windows+Wine version installed to ~/.wine/drive_c/Program Files/Picasa2. The Linux version installed to /opt/picasa/wine/drive_c/Program\ Files/Picasa2.

Check your locations first to make sure they're the same as mine, then try this:
```
sudo mv /opt/picasa/wine/drive_c/Program\ Files/Picasa2 /opt/picasa/wine/drive_c/Program\ Files/Picasa2.old
sudo cp ~/.wine/drive_c/Program Files/Picasa2 /opt/picasa/wine/drive_c/Program\ Files/Picasa2
```I was able to launch Picasa and upload to webalbums after that!

I'm a tad confused. When I initially installed Picasa 2, I was under the impression that I WAS installing the Windows version since it does run under WINE. I mean, It opens WINE when I open Picasa, so it should be, right ?  Unless I have a buggy or nix version of it ? How can I tell which I'm running ?

Edit: Would WINE still need to execute if I were running the 'Linux' version of Picasa ? Looking at the About section, it says "Picasa for Linux version 2.2.2820.5

Also, when inputting your code, the second line produced this:  "cp: target `/opt/picasa/wine/drive_c/Program Files/Picasa2' is not a directory"

---

### Post by lawr_rawr on 2007-07-09
When you install the Picasa-for-Linux version, it installs its own version of Wine. I'm not sure what the differences are, but Picasa is using Wine 0.9.10. It's located in the install directory for Picasa, which for me was /opt/picasa. From the Ubuntu repositories, I have Wine 0.9.33.

Heh, I'm a copy-tard and I can't remember the correct command. Just move the files in Nautilus. Launch Nautilus as root with "gksudo nautilus". I might've done it that way. It's been a little while. If you need to view hidden files (like the .wine folder) in Nautilus,press Ctrl-H.

Here is the link I read that said it was possible to install the windows version this way.  [http://groups.google.com/group/Google-Labs-Picasa-for-Linux/browse_frm/thread/0dfdd0d821a59439/00a5801025ee6d82#00a5801025ee6d82](http://groups.google.com/group/Google-Labs-Picasa-for-Linux/browse_frm/thread/0dfdd0d821a59439/00a5801025ee6d82#00a5801025ee6d82)

EDIT:
Yes, Wine is running when you run Picasa for Linux -- because it is not a native Linux app, but a windows app that Google has packaged with a specific version of Wine. Interestingly enough, the Windows version now says "Picasa 2.7 for Linux".

---

### Post by kwisatz on 2007-07-21
The best for me is F-Spot with his feature "export to Picasa" and Nautilus "resize images" with right-click function, it takes 2 minutes to publish 100 photos...

---

### Post by lluisanunez on 2007-07-21
> **kwisatz said:**
> Nautilus "resize images" with right-click function...

?????? Where is that? I'm on Feisty, Nautilus 2.18.1, I can't see any resize option  :confused:

Edited: OK, I did find out :
sudo apt-get install nautilus-gksu nautilus-image-converter nautilus-open-terminal

---

### Post by bill_long on 2007-08-23
> **Sweet Spot said:**
> 
My question is what do you (if you do at all) use to resize your pics before uploading ?  



I think the best way to resize is the  convert command.

As you can user sth like.

[CENTER][SIZE="3"]for i in *;do convert $i -resize 30% newsize$i; done[/SIZE][/CENTER]

---

