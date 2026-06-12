---
title: "The Fastest 400mhz Pismo I Could Build!"
date: 2007-07-27
forum: Apple PPC Users
---

### Post by ajmctaggart on 2007-07-27
FINALLY!  My Pismo is running like I would like it too!!!

Here's the deal- a 400MHZ Pismo with 256MB Ram just wasn't cutting it with Gnome/KDE OR xubuntu...the xubuntu installation puts way too many gnome resources on the system...SO...

I installed the PPC server edition (<400MB) total

I then did a 

sudo aptitude install xdm xorg xfce4 firefox synaptic

This installed the xdm login manager (ugly but fast), X11, xfce4 (not xubuntu, this is just the BASIC xfce) firefox and synaptic package manager

This was good, but I needed a few other things...this will be used for school mostly

Used synaptic, I found a xfce4 goodies package, gave me battery applets and networking applets
Installed Galculator (calculator)
               Mirage      (basic image viewer/editor)
               VLC          (handles my audio/video)
               GAIM        (IM-its college, its a necessity)
               ePDFViewer (I may not need this because of firefox?)
               TS Client (I sometimes remote into my Windoze work box, also use OS X at home sometimes)
               OO (tweaked with some settings from  Zolved, Gnumeric and Abiword dont cut it for Grad School)

I also enabled the Medibuntu repositories, and got all the codec goodness I could from the PPC FAQ

Let me just say, this is one quick lil Pismo!
Don't Give up people!  I tried 5 different install types this week, but Finally I'm satisfied!

If anyone knows of a Thunderbird replacement that wont slow me to a crawl, let me know!

Thanks,
ajm

---

### Post by stmiller on 2007-07-27
Hey thanks for the post! Those Pismos are still rockin'. :popcorn:

---

### Post by waggygee on 2007-07-27
Wait... Let me get this clear... Gnome and KDE eat up too much RAM or other resources... so you installed the server edition (which I presume uses a command line, right?).... I don't really get the rest (my main concern now is in the way I will interact with the computer). And this PPC sever edition, which Ubuntu? Can you put up a link to the download of the version you got.... I've been spending hours searching and searching about my issue and I would really appretiate it if you could do that.

thanks :grin:

---

### Post by kerry_s on 2007-07-27
it could be faster, xfce4 is slow compared to fluxbox or icewm.

Galculator, there's one already installed it's called "xcalc"
Mirage = gqview is smaller & faster. mirage is python based meaning it needs a heck of alot of stuff just to startup.
ePDFViewer = xpdf

the rest is okay, not really options there. also xdm is old and has not kept up with changes, i recommend gdm to avoid problems, you will install all the stuff gdm depends on anyways, if you use like synaptic, plus you get a choice to auto login & skip the login manager altogether.

---

### Post by ajmctaggart on 2007-07-27
waggy, 

Here's the deal 

[http://cdimage.ubuntu.com/ports/releases/feisty/release/]("http://cdimage.ubuntu.com/ports/releases/feisty/release/")


Get the server install, it's very similar to a Alternate Install (No Live Cd, just a textual installer- still, very easy

HAVE A WIRED ETHERNET CONNECTION, OR A NON-SECURE WIRELESS CONNECTION 
FILL IN YOUR NETWORK INFO WHEN IT PROMPTS (ABOUT 1/2 WAY THROUGH...) unless your dhcp

It will install a base system and ask what type of server you want...just tab over it and click ok, don't select either server type...

Now, it will install everything you need to get started...

Upon rebooting you will be at a command line with no gui...don't worry, it's coming...

Login (you would have already set this up w/ the installer)

Go to /etc/apt/sources.list

comment out (#) the cd line at the top, (you don't want it looking to a cd for packages)
make sure the other lines starting w/ deb or http are uncommented (no#)

now save and exit

Do a sudo aptitude update, make sure everything is working...If you get errors, it is probably your /etc/network/interfaces (This is why I say to take the time to configure it during install, take a look at the file now before trying this, to get an idea of what it SHOULD look like)

Now, you have a server install and you want the MINIMUM OS environment to not hog your Precious Lombard's processor...

That's why you type

sudo aptitude install xdm xorg xfce4 firefox synaptic

This will install xfce4, not xubuntu, no gnome dependencies no kde stuff, just your most ugly login manager, X11, firefox as a browser and synaptic for packages...

After that, whenever I want to install something  I just do a sudo aptitude install ______...to see how much resources and what it's gonna install before I install it...

Im sorry, I'm not much of a correct-forum poster, but this has been best case scenario for me, please refer back to the beginning for the extra goodies....


Good Luck
Ajm

---

### Post by waggygee on 2007-07-27
Thanks Ajm.... Im downloading It now!

---

### Post by ajmctaggart on 2007-07-27
Good Luck Waggy!  

Let us know if there are any other questions you have...

This is an alternative resource that really helped me...[https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

---

### Post by Biz_reporter on 2007-07-28
Thanks for the post, I have a Pismo with the same specs, and I agree that Xubuntu (both Dapper and Feisty) is a bit of a resource hog.  I might just try this in the future, but I'd like to hear other people's results -- namely you Waggy since you are planning on trying it.  

Anyway, AJM, why don't you started a little blog to share your experience with the rest of us? After all, forum posts get lost sometimes :(.

---

### Post by waggygee on 2007-07-29
Ok...So I downloaded and burnt the Ubuntu Server CD... I boot up and all, it enters low memory mode... Everything goes according to plan untill it reaches a hardware detecting part, it says it can't detect my cd drive! Is there some sort of quick fix I could try or anyone know a page I could read up on?

I tried an older cd drive form a friends computer, it was imediately detected so I successfully installed Ubuntu, I am currently updating and installing the recomended (recommended by AJM) packages thanks a million!!!!

---

### Post by ajmctaggart on 2007-07-30
Kerry_S,

Thanks for your recommendations, I chose xfce4 because I wanted something that still felt like a full desktop environment, w/ little to no configuration...While I agree that flux or ice would've been much quicker overall.  I feel that a scaled down environment of xfce4 would suffice.

Thanks for the app tips, but a quick question, is there a PIM app like Evolution or Thunderbird that could run pretty quickly on my Pismo?  I really need to find something, but Thunderbird takes too long, and Evolution seems a bit overkill for my small spec laptop, any suggestions?


Thanks
ajm

---

### Post by indelible on 2007-08-04
I also found the first time I tried installing Ubuntu on my Pismo it was really slow compared to Mac OS 10.4.  It's a 400mhz model with 320mb of ram.  Lately I've been tinkering with Xubuntu on an old celeron 400 with 650mb of ram and really loving the XFCE desktop, especially how Thunar is modeled after the Finder.  

I always loved the elegant simplicity of OS 9 and I was able to set up my interface to look very close to that with the Platinum theme for XFCE and Mist for GTK, but with all the flexibility and reliability of Linux under the hood (pretty cool for a PC that I'd probably have to pay someone to take off my hands at this point.) The fun I've been having with the old celeron me want to give some form of Linux another go on the old Pismo, and this thread was just the inspiration I was looking for.  

 Server command line install went off without a hitch, I used parted to resize my HFS+ partition, which seemed to work fine.. haven't tested booting back into Tiger yet, but there's nothing on there I'm worried about losing. My initial package choices are downloading in aptitude right now.   I decided to go with gdm, xorg, xfce, and firefox to start me off, and probably will be adding similar packages you have, while keeping it as CLI-oriented as possible to keep resource usage low.   Thanks for the great idea. :)

---

### Post by waggygee on 2007-08-05
> **ajmctaggart said:**
> Kerry_S,

Thanks for your recommendations, I chose xfce4 because I wanted something that still felt like a full desktop environment, w/ little to no configuration...While I agree that flux or ice would've been much quicker overall.  I feel that a scaled down environment of xfce4 would suffice.

Thanks for the app tips, but a quick question, is there a PIM app like Evolution or Thunderbird that could run pretty quickly on my Pismo?  I really need to find something, but Thunderbird takes too long, and Evolution seems a bit overkill for my small spec laptop, any suggestions?


Thanks
ajm

I haven't tried xfce4, I'll try it now because I'm not fully satisfied (I know I can't be choosy with such low specs) with either flux or ice. I don't know about PIM apps, I've never realy used them before, whats the most important thing you want them to do (I know they do something with reading POP3 email thingys right?). I use gaim messenger then I ticked instant email notification, gaim runs pretty well but in order to read the mail I have to open firefox (this function takes a little time). Is anyone running Opera? Does it run smoother? and  how come I cant watch youtube with gnash? Is there anything else I cant try?

---

### Post by ajmctaggart on 2007-08-06
I think ICE Weasel is a scaled down faster firefox-based browser...do you have an email client?  you can use one called clawsmail...it's in the repositories...works much faster than an evolution/thunderbird...

As far as Gnash, sorry, maybe ask in a different thread about that one...


XFCE4 is okay for my needs, essentially, I believe this will be a web browsing/backup machine, so I'm not too picky, but is anyone having good luck w/ wifi in xfce?  any suggestions?

---

### Post by waggygee on 2007-10-05
I wanted to sell my Mac... Does anyone know how to change or remove the pasword using the commandline or something?

---

### Post by stream303 on 2008-03-02
If you want to save some wear and tear on the hard drive, you might want to look into adding noatime to your /etc/fstab.

[http://ubuntuforums.org/showthread.php?t=692318&highlight=noatime](http://ubuntuforums.org/showthread.php?t=692318&highlight=noatime)

Unless you plan on doing forensic security, this might add another little boost to the system.

---

