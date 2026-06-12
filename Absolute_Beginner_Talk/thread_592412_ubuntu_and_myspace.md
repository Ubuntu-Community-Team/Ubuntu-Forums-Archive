---
title: "ubuntu and myspace"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by padams10001 on 2007-10-26
I've just created an account on myspace and cant' upload any pics - it day s i need the latest version of flash and java enabled. I have just installed the latest version of flash through  the repositories, and in my firefox preferences java is enabled? anyone got any tips??

---

### Post by yabbies on 2007-10-26
go to synaptic
and search

sun-java6-plugin

make sure it is installed

---

### Post by Quinn The Eskimo on 2007-11-16
i have the same problem
i can't upload to bubbleshare either

sun java plugin is installed and even reinstalled
running gusty

---

### Post by Quinn The Eskimo on 2007-11-17
cough bump cough

---

### Post by Quinn The Eskimo on 2007-11-17
anyone?
as a photographer this is really cramping my style

---

### Post by overdrank on 2007-11-18
> **Quinn The Eskimo said:**
> anyone?
as a photographer this is really cramping my style

HI and I am not joining the site to see if that use flash also. Can you tell us what error you get.

Edit I did join and when I try to load a pic it crashes FF so I cant help. :(

---

### Post by Quinn The Eskimo on 2007-11-18
no error
but when you browse for photos it won't show them in the folder
if you type the path for the image it goes to the upload page and never uploads

---

### Post by Quinn The Eskimo on 2007-11-18
on myspace anyway
on bubble share same thing only it appears to load and then crashes firefox
on firefox restart it brings you back to the blank upload page

thanks for trying i figure someone must have myspace or bubble share and know the problem
no problems on other sites

---

### Post by FuturePilot on 2007-11-18
I was having the same problem so I've tested this with the latest [Flash 9 Beta]("http://labs.adobe.com/downloads/flashplayer9.html") and it seems to work.
If you want to try it, download the .tar.gz file, extract it and copy libflashplayer.so to your ~/.mozilla/plugins directory and restart Firefox. 
It's a hidden directory so if you don't see it in your home folder press Ctrl+H to show hidden files. Also if you don't have a plugins folder in .mozilla just make one.

---

### Post by Quinn The Eskimo on 2007-11-20
> **FuturePilot said:**
> I was having the same problem so I've tested this with the latest [Flash 9 Beta]("http://labs.adobe.com/downloads/flashplayer9.html") and it seems to work.
If you want to try it, download the .tar.gz file, extract it and copy libflashplayer.so to your ~/.mozilla/plugins directory and restart Firefox. 
It's a hidden directory so if you don't see it in your home folder press Ctrl+H to show hidden files. Also if you don't have a plugins folder in .mozilla just make one.

i downloaded and extracted
it says i don't have permission to move that file there

---

### Post by steveneddy on 2007-11-20
> **Quinn The Eskimo said:**
> i downloaded and extracted
it says i don't have permission to move that file there

It's in your /home directory.

Of course you have permission to write there.

Look at the syntax.

It's **slash-dot-mozilla**

the dot means it is a hidden file.

Go to your home folder and type ctrl+h

see all of the hidden files if you scroll down?

---

### Post by Quinn The Eskimo on 2007-11-20
> **steveneddy said:**
> It's in your /home directory.

Of course you have permission to write there.

Look at the syntax.

It's **slash-dot-mozilla**

the dot means it is a hidden file.

Go to your home folder and type ctrl+h

see all of the hidden files if you scroll down?

ok done, but it didn't fix the problem

---

### Post by wickstopher on 2007-11-20
The whole java/flash thing is moot when uploading photos to MySpace.  You don't need it.  I just successfully uploaded a photo to MySpace, using Firefox, from my laptop installation of Kubuntu PPC (PPC Linux = no Flash or Java).  When you go to the upload photos page, you do get a message stating "Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player", but it doesn't prevent you from uploading photos.  Just click on the "Browse" button and it lets you browse the directories on your computer for a photo to upload, then click on the "Upload" button to upload the photo to MySpace.

---

### Post by Quinn The Eskimo on 2007-11-20
> **wickstopher said:**
> The whole java/flash thing is moot when uploading photos to MySpace.  You don't need it.  I just successfully uploaded a photo to MySpace, using Firefox, from my laptop installation of Kubuntu PPC (PPC Linux = no Flash or Java).  When you go to the upload photos page, you do get a message stating "Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player", but it doesn't prevent you from uploading photos.  Just click on the "Browse" button and it lets you browse the directories on your computer for a photo to upload, then click on the "Upload" button to upload the photo to MySpace.


when i click browse is brings up the browse box and i can go through my folders, but it doesn't show any of my .jpg files in those folders
it actually uploads pics just fine, but it won't recognize any of the .jpg's on my harddrive which is 99.9% of the nearly 20,000 photos i have saved

---

### Post by Quinn The Eskimo on 2008-03-15
i know it's been awhile, but if anyone wants to take another stab at this i'll try anything
i didn't think it was that big a deal for awhile, but it's a royal  pain in the ***
since i posted i have reinstalled ubuntu gusty and tried using bubbleshare and myspace again before messing with anything else and for some reason myspace and bubbleshare will not recognize pics taken with my camera, if i edit them at all with gimp it will see and upload the pics, but any image saved by my camera won't upload. the camera saves them as jpeg and if i edit i save as jpeg so i don't get what the problem is
i can't keep up with my photography if i have to go through each image and edit them
the myspace isn't a big deal, but bubbleshare is the only site i can find that will allow me to upload 300 pics with a few clicks, uploading pics one by one takes forever
i've searched the board, i would think if this was an issue there would be other complaints and solutions, but i can't find any other threads mentioning not being able to upload pics to myspace or bubbleshare
enough rambling 
any suggestions?

---

### Post by ahood on 2008-04-03
A friend of mine also has this problem. I convinced my friend to buy a Dell with Ubuntu  Feisty preinstalled. He uses myspace but has had trouble uploading a photo to myspace. The problem is that when he clicks on the browse button to upload a photo, he can browse for photos (all are 1.5 Mb), select a photo (jpg) but they won't upload.

The dell machine (1420) is running Ubuntu Feisty that with all the updates.

There are a few posts on the Ubuntu forum describing a similar problem, but none have worked so far.

My friend like the Dell running Ubuntu very much; however, the myspace/photo problem is annoying.

Any help will be greatly appreciated.

---

### Post by blackbeastofaarrgh on 2008-04-10
Myspace's photo uploader seems to be case-sensitive. I have to rename my photos from my camera from *.JPG to *.jpg. The capital JPG seems to throw it off. Not that I've ever had the flash uploader work at all for me, but it'll see the photos if the extension is lowercase.

---

### Post by BrentNewland on 2008-04-24
Update: This is an Ubuntu bug (or possibly a Firefox bug, but I'm leaning towards Ubuntu). When you browse for images, it shows "FileType: Images". That doesn't seem to work for uppercase, just lowercase.

I'm filing a bug report, located at [https://bugs.launchpad.net/ubuntu/+bug/221409](https://bugs.launchpad.net/ubuntu/+bug/221409)

In the meantime, use the following command to lower-case your pictures:
```

rename -v ’s/\.JPG$/\.jpg/’ *.JPG

```

---

### Post by metalx1000 on 2008-04-27
Don't use the Flash Uploader.

Even though you can see the flash uploader still use the option that says:
*"If you don't see the Upload Photo form below, click here"*

The only drawback is that you can only upload one photo at a time.  Although I'm looking for a way to upload more.

---

### Post by hazyshd on 2008-07-01
Ok I've finally found solutions or at least workarounds for both of the problems touched on here.

The first problem being that the pictures are in the folder but when you browse to the directory from firefox they don't show up. This has to do with the extensions. They are case sensitive and specific. If it ask for JPG, make sure the extension is 'example.JPG' because it won't recognize 'example.jpeg/jpg/etc' To correct this you need to use a batch rename program. I use gprename. It's pretty easy to use and it has a GUI.

The second problem has to do with loading one picture at a time and/or firefox crashing. There is a problem with flash plugin from what I understand. What I ended up having to do is install IE6. I know blasphemy! It's the only way that I've managed to upload my pics. You can go to: [http://www.tatanka.com.br/ies4linux/page/Installation]("http://www.tatanka.com.br/ies4linux/page/Installation") install it. Once installed use IE6 to upload pics. 

I recommend having all the pics you want to upload ready in a directory because it's a pain trying to browse through them on the uploader. I've only used this for Myspace and facebook, but I'm sure it'll work for whatever. Hope this helps.


~Shawn

---

