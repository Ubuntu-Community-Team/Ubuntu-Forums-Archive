---
title: "Feisty Fawn for your Mom!"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by White Scarf Syndrome on 2007-10-10
First, a short story on my own first Ubuntu experience.

OK, so I decided to give this whole Linux thing a shot.  I've installed 7.04 on an older 1.7ghz willamette, 1gb ram, 180gb HD with Feisty installed as master, and an 80gb HD set as slave with windows xp home installed.

Installation hung at the end, I was accused of having a dirty CDROM lens!  :)  So I gave it a couple good shots of canned air, and restarted the installation.  It went flawlessly.  I ended up partitioning about 75 percent of the 180GB HD for Feisty, and left the 80gb windows HD alone and left as slave with the appropriate jumper setting.

Spent an hour or two updating and surfing the web.  I was very curious to see how Half Life 2 ran on the system, but upon attempting to open the msi file needed to install Steam, I hit a roadblock.  I didn't expect it to work, just was hoping.  That's about as far as I got.  I'm currently waitinng to get some RAM back from RMA from G.SKill for my C2D system.  I will want a fully customized Ubuntu for that PC.  Fow now, this old Willamette system was just a testbed for the whole Linux thing.  I'm sure I'll be looking here once that RAM comes from RMA, especially since I have a RAID0 setup.

So now to my actual question.  Linux for your Mom.  My Mom hates windows.  She's sick of it.  Too many updates, the system is slow, I run spyware this and adware that, defrag, system restore, etc. etc. etc.  I've optimized her Dell many times, it just is not her thing anymore.  She's got the knowhow to scan for viruses and adware.  The PC is just too slow.  It's more than enough power for someone just surfs the web, reads pdfs, writes a letter or two, etc. 2.4ghz, 1gb of RAM, etc. It's a few years old, but Ubuntu runs on my 1.7ghz Willamette CPU, then it will run on this Dell no problem.

She cannot, and I can't either, justify buying an Apple PC to simply surf the web, print documents, and write letters.  I'm thinking of going over there and installing a dual boot Feisty/XP setup either with a new hard drive or just a repartition of the current windows drive.

What "extras" will she need? Firefox seemed to run well on my testbed machine, but flash, windows media player, etc. (All common apps for surfing the web) were not included with Ubuntu.  

Basically what I'm asking is this: Is there a package or location with add on apps for Feisty that effectively makes Ubuntu function the same as a basic windows XP installation? I don't want to be receiving phone calls about "why can't I open a PDF file? Or "this web video won't play" or "I can't open the word document"  The application finder listed tons of stuff with weird names and I really had a hard time finding what I wanted.  A side by side comparison of Ubuntu/Windows equivalents would be awesome.  Also a list of windows apps that just run fine on their own would be nice too.

What basics would you put on your Mom's Ubuntu setup?

---

### Post by Dr Small on 2007-10-10
You can read PDFs with the PDF viewer on Ubuntu, but mp3s, wma, wmvs and such will not play by default unless you install some of the restricted software.

Dr Small

---

### Post by dca on 2007-10-10
If it's gnome Ubuntu, I click on 'applications -> Add/Remove'...  Select 'all available applications' from the 'show' drop-down menu and find what I need being sure to install the g-streamer plug-ins...

---

### Post by maybeway36 on 2007-10-10
The only filetype problems will probably stem from multimedia. ubuntu-restricted-extras will help you here.
Picasa runs on Linux, which is nice.

---

### Post by overdrank on 2007-10-10
Hi and welcome, These link will help with codecs and restricted formats
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/Re.../WindowsCodecs](https://help.ubuntu.com/community/Re.../WindowsCodecs)
Good luck!

---

### Post by dptxp on 2007-10-10
Well, Moms normally want to go back to M$.

You get these via net, the basics are preloaded.
[http://packages.ubuntu.com/feisty/](http://packages.ubuntu.com/feisty/)

There is add/remove and also Synaptic to make
add-remove simple.

---

### Post by rsambuca on 2007-10-10
Just enable the multiverse and universe repositories and install```
sudo apt-get install ubuntu-restricted-extras
```This will install flash, java, msttcorefonts, and codecs for multimedia.  Other than that, just show her the "Add/Remove" Feature for the basic programs and you are good to go.  My mom has been using Ubuntu for almost a year now with no problems.

I also set the default format for Open office docs, to the MS Office formats to save her hassles when sharing documents.

---

### Post by maybeway36 on 2007-10-10
Good idea with the OO.o default formats.
Personally, I think it would be much easier to switch my parents to Linux than my brother :P He uses a lot of media apps.

---

### Post by meborc on 2007-10-10
be sure to go through this page: [www.ubuntuguide.org](www.ubuntuguide.org) and scroll down to find what you need... the multimedia codecs... dvd... flash... java... etc etc etc :) it is all here... you just need to find a starting point...

---

### Post by Dr Small on 2007-10-10
Then setup VNC so you can use vncviewer anytime she needs help ;)

---

### Post by White Scarf Syndrome on 2007-10-10
Thanks guys! I'll be trying out Wine when I get back home.

From the Wine FAQ: Can I use Wine to install drivers for my hardware?

No. With the possible future exception of some printer drivers, Wine requires your hardware to already be working on your operating system. The technical reason for this is that Wine, like most applications, runs in user mode and not kernel mode.

How do I install my Nvidia 7900 GTO drivers? Printers? My flight pedals, joystick, TrackIR 4, Ipod drivers, etc.? Or will they just run since they are USB?

Is that on the restricted apps in the add/remove section?

---

### Post by Orbital75 on 2007-10-10
Your mom will more than likely need a few items thats used in every day computer use.

Internet Browser and Email
Audio/Video Playback
Photo Editor and Viewer
Office Suite

Here are some answers.

For Internet Browsing ( **FireFox **) its installed by default.
for Email, (**Thunderbird**) will be the best bet.
If she needs a calender, use (**Lightning**) it's a Thunderbird Extension.

For Audio/Video Playback their are a varity of program you can use.
For Audio, (**Banshee, Rhythem Box, and XMMS**) are nice.
For Video (**Totem, and VLC Player**) are very nice.
As stated above you will need to install codecs to make all this work
Here is a Link that will show you how.
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

As far as Photo Editors, (**Gimp**) is your program.
For Photo Viewers ( **GQview and Picasa** ) work nice and do the good well.

For Writing Documents, Spread Sheets, and Presentations
( **Open Office** ) is what you need. 

All this can be found in the Synaptic Package Manager in Ubuntu.

Hope this helps......

---

### Post by pollywog on 2007-10-11
Honestly, you might want to get a little more comfortable with Ubuntu, before you draft someone else into the fold. I have my mom and my grandparents (in their 80's)all using ubuntu, but I had the fact that none of them so much as knew how to use a mouse on my side. I set up their computers, putting everything that they might need as a great big icons on their desktops. I renamed Firefox as "Internet", Thunderbird I renamed "E-mail" (and configured their accounts, of course) etc... The younger family members are all indoctrinated in microsoft computer use. I can't get them to even give linux a shot. As long as you are willing to act as administrator, I think that having your mom use ubuntu is a great idea. Even if she doesn't know enough about it to really appreciate what she's missing (heartache!) by not running windows.

---

### Post by White Scarf Syndrome on 2007-10-12
> **pollywog said:**
> Honestly, you might want to get a little more comfortable with Ubuntu, before you draft someone else into the fold. I have my mom and my grandparents (in their 80's)all using ubuntu, but I had the fact that none of them so much as knew how to use a mouse on my side. I set up their computers, putting everything that they might need as a great big icons on their desktops. I renamed Firefox as "Internet", Thunderbird I renamed "E-mail" (and configured their accounts, of course) etc... The younger family members are all indoctrinated in microsoft computer use. I can't get them to even give linux a shot. As long as you are willing to act as administrator, I think that having your mom use ubuntu is a great idea. Even if she doesn't know enough about it to really appreciate what she's missing (heartache!) by not running windows.

That reminds me of when we got the 486DX 33mhz for Christmas.  She was waving the mouse around at the screen saying "It's not moving!!"

She is pretty adept now, but has admitted that all she really does is go online, print documents.  SHe doesn't watch videos or listen to music on it at all.  My father uses the PC for Itunes and that's it.  I gave LinuxMint a shot and I liked it alot.  We shall see.

---

