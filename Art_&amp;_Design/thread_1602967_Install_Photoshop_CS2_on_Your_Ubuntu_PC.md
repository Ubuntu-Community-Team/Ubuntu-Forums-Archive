---
title: "Install Photoshop CS2 on Your Ubuntu PC"
date: 2010-10-22
forum: Art &amp; Design
---

### Post by U.S.A on 2010-10-22
Starting from last night, Photoshop CS2 can now be installed easily by using Wine... on any Linux distribution! *"Photoshop CS/CS2 should         * *        now work, please help us testing it"* - said the wonderful  people behind the Wine project. Therefore, I've updated my Ubuntu 7.10  operating system to the latest version of Wine (version 0.9.54 -  released on January 25, 2008) and grabbed my "dusted" Photoshop CS2  (a.k.a. version 9.0) CD. I've inserted the CD in the optical drive of my  computer and installed Photoshop CS2 just like I was on a Windows PC.  And guess what? It really works folks! Amazing! No hacks, no need to  copy installation files from a Windows PC or any other "magic" tricks  you probably saw on the Internet. The Wine team did a fantastic job with  this last release. Thank you guys!

So... are you eager to see  this miracle on your own Ubuntu PC[?]("http://www.toiraq.com") No problem! Read below our  step-by-step tutorial on how to install Photoshop CS2 on Ubuntu Gutsy.

**Things you need**:

&#65533; [**Wine 0.9.54**]("http://*******/131980/http://linux.softpedia.com/get/System/Emulators/Wine-148.shtml")
&#65533; An Original Photoshop CS2 CD

[COLOR=blue]**Step 1: Install and configure Wine**[/COLOR]

If you don't have Wine installed, here's how to get the latest version:

1. Open a terminal (*Applications -> Accessories -> Terminal*) and paste the following commands (one by one - hit ENTER after each one):

*wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -*

*sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list*

*sudo apt-get update*

[[IMG]http://i1-news.softpedia-static.com/images/extra/LINUX/small/photoshopcsonubuntu-small_001.jpg[/IMG]]("http://i1-news.softpedia-static.com/images/extra/LINUX/large/photoshopcsonubuntu-large_001.jpg")

Then close the terminal window.

2. Go to *Applications -> Add/Remove*,  make sure you select the "All available applications" option in the  upper-right side of the window, search for wine and install it. When  it's done, close the window.

[[IMG]http://i1-news.softpedia-static.com/images/extra/LINUX/small/photoshopcsonubuntu-small_002.jpg[/IMG]]("http://i1-news.softpedia-static.com/images/extra/LINUX/large/photoshopcsonubuntu-large_002.jpg")

3. Hit ALT+F2 and paste in the following command:

*wine iexplore [http://appdb.winehq.com/](http://appdb.winehq.com/)*

Click 'Install' when prompted and when you'll see the "Wine Internet Explorer" window and WineHQ website, then you can close it.

[[IMG]http://i1-news.softpedia-static.com/images/extra/LINUX/small/photoshopcsonubuntu-small_003.jpg[/IMG]]("http://i1-news.softpedia-static.com/images/extra/LINUX/large/photoshopcsonubuntu-large_003.jpg")

4. Search on Google for the Tahoma font with the following string:

*tahoma filetype:ttf*

Save it on your desktop, then move it to the Wine fonts folder (full path -> /home/yourusername/.wine/drive_c/windows/fonts).

[COLOR=blue]**Tip: To see the .wine folder, go to *View -> Show Hidden Files* option in your home directory.**[/COLOR]

[COLOR=blue]**Step 2: Install Photoshop CS2**[/COLOR]

Insert  your Photoshop CS2 CD in the optical drive and a folder should appear  after a few seconds. Go to the "Adobe Photoshop CS2" directory, right  click on the setup.exe file and choose the *Open with "Wine Windows Emulator"* option. The Photoshop installer will pop-up and I guess you know what to do now.



[[IMG]http://i1-news.softpedia-static.com/images/extra/LINUX/small/photoshopcsonubuntu-small_004.jpg[/IMG]]("http://i1-news.softpedia-static.com/images/extra/LINUX/large/photoshopcsonubuntu-large_004.jpg")

When  the installation is over, you will find the Adobe Photoshop CS2 and  Adobe ImageReady CS2 shortcuts under the Wine entry in your Start Menu.

[[IMG]http://i1-news.softpedia-static.com/images/extra/LINUX/small/photoshopcsonubuntu-small_005.jpg[/IMG]]("http://i1-news.softpedia-static.com/images/extra/LINUX/large/photoshopcsonubuntu-large_005.jpg")

And here it is.... Adobe Photoshop CS2 running on Ubuntu 7.10. Enjoy!

[[IMG]http://i1-news.softpedia-static.com/images/extra/LINUX/small/photoshopcsonubuntu-small_006.jpg[/IMG]]("http://i1-news.softpedia-static.com/images/extra/LINUX/large/photoshopcsonubuntu-large_006.jpg")



[URL="http://i1-news.softpedia-static.com/images/extra/LINUX/large/photoshopcsonubuntu-large_010.jpg"]
[/URL]

---

### Post by Half-Left on 2010-10-22
Just a note but if you look around, you'll find some Windows Ubuntu themes which Wine can use. msstyles work fine.

Here is a Clearlooks theme. [http://wingnome-xp.deviantart.com/art/Clearlooks-Gummy-Colors-73470577](http://wingnome-xp.deviantart.com/art/Clearlooks-Gummy-Colors-73470577)

---

### Post by mainerror on 2010-10-22
Quite interesting. I'll have to give it a try. Thanks for sharing.

---

### Post by agd19682 on 2010-10-22
Not trying to be rude here, but why would anyone want to install Photoshop when we have GIMP around?

---

### Post by psoulocybe on 2010-10-22
You're not being rude, you're being a Troll.

Have you ever had a client give you .PSDs to work off of?
Good luck getting them to open properly in Gimp.

Like using your awesome camera gear to it's fullest potential... well, you're going to need 16bit file support.

I could probably come up with 10 or more other reasons I have PS installed on my workstation as well. 

I love the Gimp, but it is not intended to be a PS clone or contender.

---

### Post by mainerror on 2010-10-22
> **psoulocybe said:**
> You're not being rude, you're being a Troll.

Have you ever had a client give you .PSDs to work off of?
Good luck getting them to open properly in Gimp.

Like using your awesome camera gear to it's fullest potential... well, you're going to need 16bit file support.

I could probably come up with 10 or more other reasons I have PS installed on my workstation as well. 

I love the Gimp, but it is not intended to be a PS clone or contender.

This!

---

### Post by alexandari on 2010-10-22
> **agd19682 said:**
> Not trying to be rude here, but why would anyone want to install Photoshop when we have GIMP around?


Because GIMP just sucks.

---

### Post by mainerror on 2010-10-22
> **alexandari said:**
> Because GIMP just sucks.

Nah. Lets be fair. GIMP is not bad at all but sometimes you won't get around using Photoshop. At least not if you are at a certain level (I mean of knowledge and professionalism).

---

### Post by Half-Left on 2010-10-22
> **agd19682 said:**
> Not trying to be rude here, but why would anyone want to install Photoshop when we have GIMP around?

Well, I love GIMP but Photoshop is just much better in many ways, especially with layer effects. You just don't have that level of control with GIMP.

---

### Post by jcolyn on 2010-10-22
> **psoulocybe said:**
> You're not being rude, you're being a Troll.

Doesn't look like a troll to me. In fact it's a legitimate question..

> **psoulocybe said:**
> Have you ever had a client give you .PSDs to work off of?
Good luck getting them to open properly in Gimp.

.psd's open and edit fine for me in Gimp. I can even save a .jpg/.gif/etc as a .psd.

> **psoulocybe said:**
> Like using your awesome camera gear to it's fullest potential... well, you're going to need 16bit file support.

And why is this??

Shooting raw is far superior to 16 bit .jpg's then use UFRaw to process your raw files. Again far superior to 16 bit..

> **psoulocybe said:**
> I could probably come up with 10 or more other reasons I have PS installed on my workstation as well. 

Let's hear them..

> **psoulocybe said:**
> I love the Gimp, but it is not intended to be a PS clone or contender.

Now this was funny.

---

### Post by mainerror on 2010-10-23
> **jcolyn said:**
> .psd's open and edit fine for me in Gimp. I can even save a .jpg/.gif/etc as a .psd.

Of course you can open .psds but sometimes Gimp just screws up on opening the PSDs simple as.

---

### Post by jcolyn on 2010-10-23
> **mainerror said:**
> Of course you can open .psds but sometimes Gimp just screws up on opening the PSDs simple as.

I've never experienced problems with opening any of my 200+.psd's.

I suspect the issue has more to do with the individual computer specs and/or hardware. Afterall many people has issues just trying to install Linux and opening programs when they do get Linux to install..

All of my installs have gone off without a single hitch and I have never had a single crash..

---

### Post by mainerror on 2010-10-23
Believe me it's not a hardware fault. I'm experienced enough to differ between those problems. ;)

On top of that I never had any issues with Ubuntu on my production machine.

---

### Post by Half-Left on 2010-10-24
> **mainerror said:**
> Of course you can open .psds but sometimes Gimp just screws up on opening the PSDs simple as.

GIMP doesn't understand what layer effects are from Photoshop, so the PSD file will not look right.

---

