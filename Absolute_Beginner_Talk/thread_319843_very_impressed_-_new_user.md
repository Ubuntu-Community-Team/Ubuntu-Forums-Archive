---
title: "very impressed - new user"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by mosedavid on 2006-12-16
Hi,

After managing to setup the wireless network card (it was the wireless router that needed adjusting - not ubuntu!) i have to say i am really impressed with it.  Im used to windows.  I cant believe the software install tool - brilliant, and everything installs so neatly.

Now I have got over the hurdle of installing it (the first release of linux i have managed to) i want to use this laptop for all my non gaming tasks.  I'm used to programs and functions in windows and i wondered if there were the equivelent functions in Linux..

A non torrent p+p network client that connects to the main filesharing networks - in XP I used Limewire

An easy way of getting standard codecs on the machine - MP3 etc

A video/mpeg file to DVD setup.  In windows I record TV, get rid of errors and adverts in a program called video redo (it re-encodes 2.5 hours of video in around 4 minutes on my desktop machine).  Open the file up in a DVD authoring package and Mux to DVD.  I realise there are programs for editing video but most i have tried are very slow.

A better graphics editor than GIMP - the interface is just too clunky.  Im sure it does most things well and has many fans but to me its a bit of a come down after using photoshop for many years.

That will do for now ;) 

It would be ideal if some of these could be addressed by the program update/install tool.  Whenever I have tried in the past to install a linux tar file I have always had dependencies missing and these dependencies have had dependences missing and so on and so on.

Im a 'noob' and want to have a little fun before I start to learn all the command line stuff.  Please help another windows user jump ship.

---

### Post by xyz on 2006-12-16
Hi and warm Welcome here!!
About Codecs:
[Restricted Format]("https://help.ubuntu.com/community/RestrictedFormats")
OR
[Automatix]("http://www.getautomatix.com")
Good luck and do come back for questions if need be.

---

### Post by ButteBlues on 2006-12-16
Before getting started, you'll need to make sure all your needed repositories are enabled. [Use this page](https://help.ubuntu.com/community/Repositories/Ubuntu) and [this page](https://help.ubuntu.com/community/SynapticHowto) to get a rough idea.

Under Synaptic, go to Manage Repositories. Then uncomment every line that starts with "# deb" or "# deb-src" by removing the "#" sign.

> **mosedavid said:**
> A non torrent p+p network client that connects to the main filesharing networks - in XP I used Limewire

I think gtk-gnutella does what you're looking for, in a slightly minimalist-esque package.

You can either find it in Synaptic, or under Applications > Accessories > Terminal, you can run the following command:

```
sudo apt-get install gtk-gnutella
```

apt-get is basically the same system used in Synaptic to install applications. In Ubuntu, you preface commands that need admin access with "sudo", since by default, you cannot modify anything outside of /home or /media. When it prompts for the password, just enter your user password.

> An easy way of getting standard codecs on the machine - MP3 etc

[This page](https://help.ubuntu.com/community/RestrictedFormats) has everything you need.

> A video/mpeg file to DVD setup.  In windows I record TV, get rid of errors and adverts in a program called video redo (it re-encodes 2.5 hours of video in around 4 minutes on my desktop machine).  Open the file up in a DVD authoring package and Mux to DVD.  I realise there are programs for editing video but most i have tried are very slow.

I'm not sure on this one.

> A better graphics editor than GIMP - the interface is just too clunky.  Im sure it does most things well and has many fans but to me its a bit of a come down after using photoshop for many years.

There isn't one. However the default installation for GIMP in Ubuntu at the moment is slightly out-dated.

You can try the new version by [downloding this file](http://www.pix-nw.de/_intern/soc/gimp-2.3_2.3.13-1_i386.deb), then double clicking on it and installing it through GDebi. It is the current developmental version of GIMP, and though the general scheme of the layout isn't much changed, many things are updated.

Alternatively, after downloading to your desktop, these are the terminal commands that can install it for you:

```
cd ~/Desktop
sudo dpkg -i gimp-2.3_2.3.13-1_i386.deb
```

> Im a 'noob' and want to have a little fun before I start to learn all the command line stuff.  Please help another windows user jump ship.

I provided both terminal and UI paths to achieving this because I find that while the UI works, it's faster to do it in the terminal.

---

### Post by mosedavid on 2006-12-16
blimy that was quick!

thank - will check them out - at work on a windows machine at the moment :(

---

### Post by argie on 2006-12-16
Look at Frostwire. It's the same thing as Limewire, or atleast very similiar.

---

### Post by David Corrales on 2006-12-16
For video, here's a link with more info:
[http://infohost.nmt.edu/~kscott/video/](http://infohost.nmt.edu/~kscott/video/)

---

### Post by maneesh77 on 2006-12-16
Just a note

 if you are used to using Limewire on windows, you might find using p2p in linux a bit strange, good programs are amule and gnutella but if you want like wire it's avail 

[http://fileforum.betanews.com/detail/LimeWire_for_Linux/984642248/2]("http://fileforum.betanews.com/detail/LimeWire_for_Linux/984642248/2")

But use frostwire instead, it's what I use( a word of warning like other JAVA apps it starts slow)  [http://www.frostwire.com/]("http://www.frostwire.com/")

Have fun with ubuntu

---

### Post by Tasu on 2006-12-16
> **mosedavid said:**
> 
A better graphics editor than GIMP - the interface is just too clunky.  Im sure it does most things well and has many fans but to me its a bit of a come down after using photoshop for many years.

Well! Photoshop has the same interface, if you don't believe me look at this:
[http://www.guidebookgallery.org/pics/apps/photoshop/workspace/empty/900-mac.png](http://www.guidebookgallery.org/pics/apps/photoshop/workspace/empty/900-mac.png)
Is just the Windows version that has that look you think is better (or more modern, i don't know), but surely if you would have arrived to ubuntu from mac, you would have been used to interfaces like this, the philosophy behind it is the fact that as long as all the toolboxes  are windows, the best manager for them is the window manager itself! Histotrically on microsoft windows the window manager wasn't so good, so the programs needed to adopt the look and beahviour you are used to, think about it, many people (not speaking about gimp fans), believes that the "gimp like" interfaces are the right way to manage window toolboxes... 
If gimp is not "better" it is because of other problems, for example the lack of CMYK (a plugin is in test for this) or Pantone.

However for an image editor that has an interface with toolboxes not managed by the window manager you can try krita, it even supports CMYK.

bye! ^_^

---

### Post by mosedavid on 2006-12-16
> **Tasu said:**
> Well! Photoshop has the same interface, if you don't believe me look at this:
[http://www.guidebookgallery.org/pics/apps/photoshop/workspace/empty/900-mac.png](http://www.guidebookgallery.org/pics/apps/photoshop/workspace/empty/900-mac.png)
Is just the Windows version that has that look you think is better (or more modern, i don't know), but surely if you would have arrived to ubuntu from mac, you would have been used to interfaces like this, the philosophy behind it is the fact that as long as all the toolboxes  are windows, the best manager for them is the window manager itself! Histotrically on microsoft windows the window manager wasn't so good, so the programs needed to adopt the look and beahviour you are used to, think about it, many people (not speaking about gimp fans), believes that the "gimp like" interfaces are the right way to manage window toolboxes... 
If gimp is not "better" it is because of other problems, for example the lack of CMYK (a plugin is in test for this) or Pantone.

However for an image editor that has an interface with toolboxes not managed by the window manager you can try krita, it even supports CMYK.

bye! ^_^


what i dont like about gimp is that the program comes in bits - i like and use inkscape in windows - i use it for adds for my shop (its a bit  unstable in windows).  Photoshop has everything on one screen.  The last time i used gimp it was all over the place - stuff wasn't where 'stuff' was suposed to be.  Most Windows graphics programs follow an overall pattern.  I also use fireworks - which works like photoshop.  Inskscape runs like freehand or simular programs, gimp runs like no other.

call me a windows user ;) but when it comes to doing stuff for a living i need to understand it quickly and be comfortable using it.  Guess i'll have to limit my creative endever's to my work pc.

---

### Post by ButteBlues on 2006-12-16
GIMP's interface will just need some getting used to for you. The layout is very customizable and intuitive.

---

### Post by mosedavid on 2006-12-16
i couldn't contain myself - the evolution program is fecking great - i use outlook every day (i run an ebay business) and the look and feel is the same.  Sorry for you windows haters but for someone just migrating this is really good.

---

### Post by jvc26 on 2006-12-16
I haven't got round to trying this one out yet, but am going to in the next couple of days, using wine you can run PhotoshopCS2 apparently, will post for definite once I've run through it, but heres the link:

[http://blog.publicidadpixelada.com/2006/10/10/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/](http://blog.publicidadpixelada.com/2006/10/10/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/)

Il

---

### Post by riven0 on 2006-12-16
If you can't get used to Gimp's interface, try [Gimpshop]("http://www.gimpshop.com/"). Download the file for Debian and (K)ubuntu. 

Either way, though, I recommend sticking with Gimp as it's just about as powerful as photoshop. Check out [Gimptalk]("http://www.gimptalk.com") for the tutorials.

---

### Post by mosedavid on 2006-12-16
i will give gimp another go - the wine/photoshop sounds good.

i didn't mean to rubbish gimp - im sure it works well its just that i have used photoshop professionally for years - its a vast program that most users never master.  most users will never need to master it unless they are a designer, artist etc.  Photoshop v Gimp - put it down to personal taste.

---

### Post by drjnet on 2006-12-16
I found this which i havent installed but check this out :

GIMPShop is a free Open Source image editor that is similar to the popular Adobe Photoshop. Specifically GIMPShop is a version of the GIMP that has been edited to be more user-friendly for Photoshop users.

[www.gimpshop.net](www.gimpshop.net)

Let me know if its any good as you're right gimp aint no photoshop!!

---

### Post by mosedavid on 2006-12-17
> **drjnet said:**
> I found this which i havent installed but check this out :

GIMPShop is a free Open Source image editor that is similar to the popular Adobe Photoshop. Specifically GIMPShop is a version of the GIMP that has been edited to be more user-friendly for Photoshop users.

[www.gimpshop.net](www.gimpshop.net)

Let me know if its any good as you're right gimp aint no photoshop!!
that looks great - the instalation doesn't!  I ticked source code to be included in the synaptic package manager but couldn't find gimpshop.  Is there any way to install this without going through that long installation mentioned on the web page?  I just know that i won't have the right dependencies - i will download them, they will tell me i dont have the right dependencies for those dependencies and so on.  
This part of linux is really confusing for a new user.  I understand what the dependencies are and the need for them.  The deps are..

    * XML::Parser perl module
    * GLib >= 2.4.5
    * atk >= 1.0.1
    * GTK+ >= 2.4.4  
    * libart-2.0

any idea if these are included in ubuntu as standard installation - i have downloaded all the updates.

---

### Post by drjnet on 2006-12-17
> **mosedavid said:**
> that looks great - the instalation doesn't!  I ticked source code to be included in the synaptic package manager but couldn't find gimpshop.  Is there any way to install this without going through that long installation mentioned on the web page?  I just know that i won't have the right dependencies - i will download them, they will tell me i dont have the right dependencies for those dependencies and so on.  
This part of linux is really confusing for a new user.  I understand what the dependencies are and the need for them.  The deps are..

    * XML::Parser perl module
    * GLib >= 2.4.5
    * atk >= 1.0.1
    * GTK+ >= 2.4.4  
    * libart-2.0

any idea if these are included in ubuntu as standard installation - i have downloaded all the updates.
Hmm not sure as I havent tried it myself. This thread may be of some help though:

[http://ubuntuforums.org/showthread.php?p=1887893]("http://ubuntuforums.org/showthread.php?p=1887893")

---

### Post by bsell on 2006-12-17
> **mosedavid said:**
> that looks great - the instalation doesn't!  I ticked source code to be included in the synaptic package manager but couldn't find gimpshop.  Is there any way to install this without going through that long installation mentioned on the web page?  I just know that i won't have the right dependencies - i will download them, they will tell me i dont have the right dependencies for those dependencies and so on.  
This part of linux is really confusing for a new user.  I understand what the dependencies are and the need for them.  The deps are..

    * XML::Parser perl module
    * GLib >= 2.4.5
    * atk >= 1.0.1
    * GTK+ >= 2.4.4  
    * libart-2.0

any idea if these are included in ubuntu as standard installation - i have downloaded all the updates.

GIMPshop .deb file:

[http://www.plasticbugs.com/blogimg/gimpshop_2.2.11-1_i386.deb]("http://www.plasticbugs.com/blogimg/gimpshop_2.2.11-1_i386.deb") 

Click the URL and the GDebi Package Installer will take care of the rest. 

From Wikipedia entry:
> Due to the changes to the interface of the GIMP for GIMPshop, **_many Photoshop tutorials can be followed in GIMPshop unchanged_**, and most others can be adapted for GIMPshop users with minimal effort. (emphasis added)[http://en.wikipedia.org/wiki/GIMPshop]("http://en.wikipedia.org/wiki/GIMPshop")

---

### Post by tdatu on 2006-12-27
" The last time i used gimp it was all over the place - stuff wasn't where 'stuff' was suposed to be.  Most Windows graphics programs follow an overall pattern."

Try [Gimpshop]("gimpshop.com")---this is the modification of Gimp to give you the same feel and interface of Adobe Photoshop...I once, honestly, struggled with the migration from windows to linux apps interfaces. Though, I haven't tried Gimpshop, I heard this is becoming a solution to many Gimp immigrants. 
goodluck.

---

### Post by pseudonym on 2006-12-27
> **mosedavid said:**
>  A video/mpeg file to DVD setup.  In windows I record TV, get rid of errors and adverts in a program called video redo (it re-encodes 2.5 hours of video in around 4 minutes on my desktop machine).  Open the file up in a DVD authoring package and Mux to DVD.  I realise there are programs for editing video but most i have tried are very slow. 
It's digtal TV you're recording, right? Linux has the all-in-one PVR [Myth TV]("www.mythtv.org"). It's in the Ubuntu repositories but it can be a pain to set up. My work flow for DVB is this -

1. tune the card using dvb-utils and dvbsnoop (both in Ubuntu repos)

2. Record to HDD by doing a streamcopy -

$ cat /dev/dvb/adapter0/dvr0 > program.ts

(that may be a bit gobbledygook to you but a great place to read up on TV in Linux is linuxtv.org ).

3. Use [Project X]("http://www.lucike.info/index.htm?http://www.lucike.info/page_projectx.htm") to edit and demux the stream. (java is required to run. project x can be downloaded from [www.doom9.net](www.doom9.net))

4. Remux to DVD compliant mpeg using mjpeg-tools (in Ubuntu repos).

5. Author DVD using [DVD Styler]("http://www.dvdstyler.de/"). It's not in Ubuntu, but works fine regardless. I find it much easier to use than qdvdauthor, which is in ubuntu, but can be a little 'clunky'.

I think the other items on your list are pretty well covered.

HTH

---

### Post by Jussi01 on 2006-12-27
Hi,

You may want to check out this article for photoshop:

[http://www.desktoplinux.com/articles/AT7770280571.html](http://www.desktoplinux.com/articles/AT7770280571.html)

Hope this helps

---

