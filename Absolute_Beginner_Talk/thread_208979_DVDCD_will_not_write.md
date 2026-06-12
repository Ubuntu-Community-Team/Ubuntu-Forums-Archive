---
title: "DVD/CD will not write"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by prisley on 2006-07-04
I have ubuntu and like it! I am from Mepis which let me down. It had KDE but Ubuntu has Gnome. The file browser shell is Nautilus 2.12.1 for Gnome. When I used Mepis and the KDE desktop I was able to burn both CD and DVD disks. that was nice. Although I had some difficulty and it was no way perfect it did burn. Alas my Nautilus will not allow me to make a good copy of anything. 

I have two dvd/cd drives. One is a writeable dvd/cd and worked with KDE. The other is a DVD readable only although I think I was able to write CD's with it. Now that I am in Gnome I am unable to make either write anything. The DVD/CD DL writiable drive is a Memorex. It will go through the write disk menus and it does write something. Because the disks have data on them but will not load and play after that. 

I am unable to get a picture out of the totem movie player.


Totem could not play 'file:///media/cdrom0/video_ts/vts_01_4.vob'.
There were no decoders found to handle the stream, you might need to install the corresponding plugins

Thats the error message.

 With the dvd/cd drive when I put a cd in I am able to get Serpentine 0.6.3 to show the files but have been unable to get them to burn a cd that will work. 

When I put the same cd in the non-writable dvd I get Sound Juicer 2.12.2 to open it and it will extract it to disk. And I did burn that onto a disk but it was not readable on my windows laptop which is the only dvd player that works.

In other words I am unable to burn nothing on my DVD/CD drive that worked under KDE with mepis. 

Should I think about moving over to KDE or can I get Gnome to work? Will Nautilis work? Is there another app that will work better? 

Is there anyone out there that is able to burn DVD and CD with Gnome desktops? 

Are there any fourms that are devoted to this issue? I need information on this issue.

Sorry this has been such a long post. Hope you can help.

Peter

Tired of wasting DVD and CD blanks !

---

### Post by Kilz on 2006-07-04
[QUOTE=prisley]I have ubuntu and like it! I am from Mepis which let me down. It had KDE but Ubuntu has Gnome. The file browser shell is Nautilus 2.12.1 for Gnome. When I used Mepis and the KDE desktop I was able to burn both CD and DVD disks. that was nice. Although I had some difficulty and it was no way perfect it did burn. Alas my Nautilus will not allow me to make a good copy of anything. 

I have two dvd/cd drives. One is a writeable dvd/cd and worked with KDE. The other is a DVD readable only although I think I was able to write CD's with it. Now that I am in Gnome I am unable to make either write anything. The DVD/CD DL writiable drive is a Memorex. It will go through the write disk menus and it does write something. Because the disks have data on them but will not load and play after that. 

I am unable to get a picture out of the totem movie player.


Totem could not play 'file:///media/cdrom0/video_ts/vts_01_4.vob'.
There were no decoders found to handle the stream, you might need to install the corresponding plugins

Thats the error message.

 With the dvd/cd drive when I put a cd in I am able to get Serpentine 0.6.3 to show the files but have been unable to get them to burn a cd that will work. 

When I put the same cd in the non-writable dvd I get Sound Juicer 2.12.2 to open it and it will extract it to disk. And I did burn that onto a disk but it was not readable on my windows laptop which is the only dvd player that works.

In other words I am unable to burn nothing on my DVD/CD drive that worked under KDE with mepis. 

Should I think about moving over to KDE or can I get Gnome to work? Will Nautilis work? Is there another app that will work better? 

Is there anyone out there that is able to burn DVD and CD with Gnome desktops? 

Are there any fourms that are devoted to this issue? I need information on this issue.

Sorry this has been such a long post. Hope you can help.

Peter

Tired of wasting DVD and CD blanks ![/QUOTE]


I have never had much luck with the nautilus intergrated burner. It always messes up for me. I got tired of making shiny coasters with holes in the middle. You can install k3b on gnome if you want, I use it and it burns great, there is also gnomebaker. Both should be in synaptic or. 
```
sudo apt-get install k3b
```
or 
```
sudo apt-get install gnomebaker
```

---

### Post by prisley on 2006-07-04
Dear Kilz;

I trust rats much more than Microsoft. If Gates is the answer to world poverty then we can expect a lot more poverty.

Thanks for the tip. I shall start on this tonight. 

Would you have any comments on the diffrence between K3B and gnomebaker? Like which is better or works better or is one good at one thing etc. Once I get on whichever that is where I will stay as long as possible so it would be better to know which one to begin with. 

Thanks so much for you help. 

Peter

---

### Post by prisley on 2006-07-05
So I downloaded the K3B app and it would not come up on the desktop.  Why is that?  Do I have to set up the KDE desktop to get K3b to work?

I then installed Gnombaker which did show up. Does that mean that Gnome will not allow K3b to operate? And only allow Gnomebreaker?  

Any information will surley save me many hours of trails.

Thanks for the help.

Peter

---

### Post by mcduck on 2006-07-05
It only means that K3B installation doesn't add it to Gnome menu.. You can still add it there by yourself (us the Menu Editor in Applications/Accessories) or start it from a terminal (most likely command needed is 'k3b')

---

### Post by prisley on 2006-07-05
Dear MCDUCK;

I could not follow  your instructions. "Menu Editor in Applications/Accessories" because the menu editor is not there.  Ther is a menu and toolbars in preferences.

There is a applications menu editor also in Applications/System. Is that what your talking about?

Confused.

Peter

---

### Post by Kilz on 2006-07-05
[QUOTE=prisley]Dear MCDUCK;

I could not follow  your instructions. "Menu Editor in Applications/Accessories" because the menu editor is not there.  Ther is a menu and toolbars in preferences.

There is a applications menu editor also in Applications/System. Is that what your talking about?

Confused.

Peter[/QUOTE]
You should have the Alacart menu editor in Applications > Accessories. But it may be someplace else for some reason. You could also start it my opening a terminal and typing Alacarte and hitting enter. A few errors may pop up when you do it this way. But nothing to worry about if the program starts.

I also trust rodents more than Microsoft. I have 2 pet mice, they live in a cage in my computer room.  :grin:

---

### Post by prisley on 2006-07-05
I did what you suggested but no go. Nothing. don't have a program by that name. What now?

Peter

---

### Post by keith whitehouse on 2006-07-06
hi prisley,

a sentence from your first paragraph in your first post "Alas my Nautilus will not allow me to make a good copy of anything. "

I can copy a dvd using the basic installed programs. I am running Dapper Drake that has every update installed. I am still a Windows user (unlike everyone else I do not have a problem with Bill Gates), so most of my work is still done in Windows until I have found a way to do it in Ubuntu.

On Monday evening on channel 30 on Freeview the Who were in concert in Boston so I recorded it using my Hauppauge USB Nova-t box. I then run the recording through Projectx to remove any errors. Next I ran it through Mpef2schnitt to remove the adds, and finally through Remuxer to put the four clips back together again (i.e putting video and audio back together). So far so good.

I then used another couple of programs to finalize and burn the DVD, which plays perfectly on my big Sony system. A friend now wants a copy so I have fired up Ubuntu and placed the finished DVD into the internal DVD reader in the computer and a blank DVD into my USB external LG dual layer burner. I now have 2 icons on my desktop, one is the finished DVD and the other is the blank one. I right clicked on the finished DVD and selected "Copy". A dialogue box popped up and I made sure that both of the DVD's pointing in the right direction. I would have liked to have burnt at the slowest speed possible , i.e about 2 would suit me fine, but the lowest was 16. I said ok and finished up with a copy of the finished DVD which again plays perfectly on the Sony Home Theatre unit.

Dapper Drake can burn or make copies of DVD's. I am sorry that I am not able to help solve your specific problem, but persevere with Dapper as it does work.

best regards keith

---

### Post by prisley on 2006-07-06
Thanks for the nice post. Yes I will stick with Ubuntu and forget Windows. I just have problems with it. Perhaps it is the hardware which is diffrent than yours. Or perhaps it is the version that might not have the last updates. Its hard to say. 

The problem is, the executable of K3B is not in the usr/bin where it must be!!!!  So why is that since I installed from the synaptic package manager the program  'k3b-i18n' and also looked for updates also. 
EVidence --  There is no usr/bin refrence in the installed window of the properties in synaptic. Which means when I installed 'k3b-i18n' it did not put the excutable in the usr/bin. And thats why I can not raise k3b even though a lot of other files are loaded in usr/bin/share. 

So why did synaptic  not load the most important file in the usr/bin? I have no idea. But it did not. Because Gnome will not allow it? 

Perhaps KDE and Gnome are in the middle of a divorce case? 

Anyway I need to download and install a good copy of K3b that will work with Gnome. Any ideas of where I might be able to get such an app? 

So I learned that if you want a program to show up in the menu then you must have it in the menu editor. And it must point to a executable that is in the usr/bin. 

And the Synaptic package manager is not fool proof (I must be the fool) and it can make mistakes. 

That took a good 8 hours to figure out maybe longer. I had to do all this detective work which I am not good at. Now all I got to figure out is what usr/ and also lib/,sbin/ ,etc/ ,tmp/ ,var/ and all the other places the unix/Linux people stash apps files for what ever reason they have. 

So the question is where do I get that info? ](*,)  

Also what download site should I go to find apps? And how do I get Synaptic to go there and get them?

Questions, questions, I always  end up at the same place.....

Thanks for the attention to this and hope you have a thought or two.

Peter

---

### Post by crystal on 2006-07-06
> The problem is, the executable of K3B is not in the usr/bin where it must be
Could it be in /usr/local/bin ?

---

### Post by prisley on 2006-07-06
OK I found the repposites in the Synaptic program and downloaded two k3b apps. K3b and k3bilbs. One is a sophjisticated kde cd burning appliction and the other is the kde cd burning application library - runtime files.  

The question is does this mean that I should install both programs are would they clash?  I have no idea. 

Peter

---

### Post by prisley on 2006-07-06
You need not answer this last reply. Synaptic marked both when I marked one. It knows!!:)

---

