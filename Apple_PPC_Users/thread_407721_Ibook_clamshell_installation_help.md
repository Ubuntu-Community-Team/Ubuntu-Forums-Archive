---
title: "Ibook clamshell installation help?"
date: 2007-04-12
forum: Apple PPC Users
---

### Post by discoandy on 2007-04-12
I wanted an awesome looking old laptop so I bought an old clamshell off ebay.

Starting up, it shows the question mark folder thing.  No problem, I thought, because that's the same thing that happened with my g3 imac, so I try to install ubuntu.  These are CDS that worked for installation on my imac but now the ibook won't read %80 of them.   I try to burn new ones at 4x speed and still no luck.

Is there a specific version of x(ubuntu) i should start with on an ibook?  Or is this thing toast?

are there any other tips from other ibook users about what I should do?

---

### Post by quizno50 on 2007-04-13
Sounds to me like you need a new CD drive for that thing... Shouldn't be too hard to switch out, just check ebay and see what you can find, shouldn't be too expensive... To check though, I'd boot it up in mac os and see if you can get it to read any CDs, then if you can try an external CD drive and see if that works...

---

### Post by bries on 2007-04-24
Have you seen this page: [http://toddpartridge.wordpress.com/](http://toddpartridge.wordpress.com/) ?

---

### Post by Calash on 2007-04-24
I got edgy installed on my clam shell iBook fine.  It may be a bad CD, or the drive may be having difficulty reading the disk.  

Iit is going to run REAL slow...and you will see some odd errors at boot.  Every once in a while it hangs at boot too, just being stuck at the grey screen.  A reboot gets by it.

---

### Post by bradskins on 2007-04-25
HEY!

I have the exact same problems with my clamshell (iBook SE key lime).  I have been at it for days and I might have a solution for you:

1.   Boot into open firmware with the Ubuntu CD in the drive  (Cmd + Option + O + F)

2.   Type  boot ide1:2,install\yaboot

3.   If that doesnt take you to a prompt that ends like this:

************************************
If in doubt, just press Enter, and if that
doesn't work, type 'live video=ofonly'.
************************************
Then restart, changing the '2' in the boot script to 0 or 1 or 3 until you get there.

Hope it works for you

-bradskins

---

### Post by SXR on 2007-04-25
Don't even bother trying to get Ubuntu on to a clam shell I book... doesn't work I tried for 6 weeks straight I even bought cd's and got some from Ship it I thought i was just getting bad cd's I currently have around 20 dapper CD's laying around. But that aside The ibook just wont take Ubuntu for some reason... I even Tried to put the i386 version on it with no luck... Email me I'll send you a copy of OS9 that I no longer has a use for.  [email]Ghostllc@Gmail.com[/email]

---

### Post by bradskins on 2007-04-25
forgot to say, I sucessfully loaded both Ubuntu Feisty and Xubuntu Edgy on my clamshell with my method mentioned.

---

### Post by Calash on 2007-04-25
Saying it does not work is incorrect.  It does work, but it takes some work to get it going.  I got it running, but for some reason Gnome would crash a lot....loaded KDE and it is fairly stable...for a clam shell iBook :)

I followed the instructions in the link already posted and it worked fine.  Don't expect it to be very quick, but it does work.

---

### Post by Alisson on 2007-04-25
I'm also having some trouble with a clamshell. I can boot the liveCD, but after it finishes loading, I go into a blank screen waiting for commands, which it will not accept... I had no trouble booting this CD on a G4 iBook; any suggestions?

---

### Post by discoandy on 2007-04-25
> **SXR said:**
> Don't even bother trying to get Ubuntu on to a clam shell I book... doesn't work I tried for 6 weeks straight I even bought cd's and got some from Ship it I thought i was just getting bad cd's I currently have around 20 dapper CD's laying around. But that aside The ibook just wont take Ubuntu for some reason... I even Tried to put the i386 version on it with no luck... Email me I'll send you a copy of OS9 that I no longer has a use for.  [email]Ghostllc@Gmail.com[/email]

SXR thanks so much for the generous offer..  I was going to try that but I didn't have access to any mac os cds!  so I had to re-ebay the ibook clamshell and get an ibook dual usb g3.  

... and now everything seems to be working great!

Hopefully this thread will be helpful to other clamshell owners too...

---

### Post by Alisson on 2007-04-25
I may end up just going for OS9, I found someone with a copy of it. I think the liveCD is having trouble with the keyboard...

---

### Post by mhinton539 on 2007-04-25
I just got through using the Update feature to upgrade from Edgy to Feisty, and my (ancient) 366 MHz iBook SE (clamshell, 366 MHz G3, gray, single USB) is running fine. My only complaint is that the laptop display brightness adjustment that worked fine in Dapper was broken in Edgy, and appears to remain broken in Feisty. 

Other than that one comparatively minor issue, Feisty appears to be stable on the old Clamshell. Kudos to the developers for continuing to provide builds for an increasingly obsolescent platform! Keep it up, guys, I'd hate to replace my favorite computer!  :)

---

### Post by prince_alfie on 2007-05-22
> **SXR said:**
> Don't even bother trying to get Ubuntu on to a clam shell I book... doesn't work I tried for 6 weeks straight I even bought cd's and got some from Ship it I thought i was just getting bad cd's I currently have around 20 dapper CD's laying around. But that aside The ibook just wont take Ubuntu for some reason... I even Tried to put the i386 version on it with no luck... Email me I'll send you a copy of OS9 that I no longer has a use for.  [email]Ghostllc@Gmail.com[/email]

I am willing to disagree. Actually I managed to install ubuntu 7.04 (feisty fawn) on the first try onto my 300mhz tangerine ibook with only 192 MB of RAM. It took like 2 hours but it works perfectly and not all that quickly but it's still very useable. I hope to bump up the RAM to 640 MB soon. But it's totally awesome :) :popcorn:

So all is not lost with those old clamshells. They look awesome especially with ubuntu on! :D

---

### Post by STUMPOFWAR on 2007-05-22
> **SXR said:**
> Don't even bother trying to get Ubuntu on to a clam shell I book... doesn't work I tried for 6 weeks straight I even bought cd's and got some from Ship it I thought i was just getting bad cd's I currently have around 20 dapper CD's laying around. But that aside The ibook just wont take Ubuntu for some reason... I even Tried to put the i386 version on it with no luck... Email me I'll send you a copy of OS9 that I no longer has a use for.  [email]Ghostllc@Gmail.com[/email]


dude Ship-it doesn;t send out PPC CDs anymore.....if you want a copy of Feisty U/EDU/Kubuntu you will need to hit up the linux store......


But back on the Clamshell.....I personally love the old clamshells. I would probably still be using mine were it not for the crappy rez on the LCD. I was tempted to try one of the LCD mods posted around on the web, but a 466mhz chip just isn't worth the effort.

I did manage to get my 466 mhz Clamshell running OS X 10.4 but I had to max out the RAM and I put in a 7200 RPM harddrive so that it would be unbearably slow.......I would imagine that you would have to similarly pimp out your clamshell to get Feisty to work.

---

### Post by Allowishious on 2007-06-10
^^^^^
 total nb

Hey! could you ellaborate?
I can't even get my iBook to recognize the iso file as a bootable source...
(if I turn on the laptop and hold downt he "c" key I don't get an icon allowing me to boot from the CD)
once in the OS9 environment, the desktop shows the CD, and even opens it to show the .iso file)

How'd you do it?

---

### Post by new@buntu on 2007-06-14
I had problems reading / booting my g3 clamshell from feisty ISO. I know I used to have the ability to read CDR when I had OS 9 and 10 on it.  Then tried burning the ISO to a different brand CD (Imation instead of TDK)
and it read / boot okay..

---

### Post by joxe on 2007-06-21
I'm using Feisty on an Indigo with 320 MB RAM and it runs decently... it doesn't show the booting progress bar (I supposed that has to do with the resolutio... is there any way to fix that?) and I miss a decent flash support... but apart from that I'm amazed with how good it works!

---

