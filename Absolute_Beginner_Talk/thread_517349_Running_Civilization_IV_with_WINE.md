---
title: "Running Civilization IV with WINE"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Mr. Svinlesha on 2007-08-04
I read somewhere on the forums that someone was running Vanilla Civ IV 1.61 flawlessly, using wine.

Is that at all possible, and if so, can anyone out there help me install it?

---

### Post by superstylin on 2007-08-04
I would recommend the WINE forums for Civ 4, there should be detailed instructions on how to get it running!

Or - try the Game/Entertainment sub-forum here!

Enjoy!


:guitar:

---

### Post by JamesDS on 2007-08-04
Yes, it is.  I did it on my brother's Ubuntu installation, but unfortunately his graphics card is not one of the supported ones :( .  Anyway, apart from the graphics it seemed to be working great!  If you go [HERE]("http://appdb.winehq.org/appview.php?iVersionId=5254") there are some instructions on the wine AppDB site.  

Also, the new version of Civ4 is 1.74 - which works well too.  Make sure you download the CIv4 1.74 patch (like from [www.civfanatics.com](www.civfanatics.com)) and also a no-cd patch, (google for Civilization 4 no cd patch 1.74).

If you need more help, I shall do my best to assist you :).  Best of luck!

---

### Post by Mr. Svinlesha on 2007-08-04
James:

Actually, I've seen the page you link to, but I'm stumped at the first instruction:

"Install the game as you normally would any other."

Okay.  I place the CD into CD-ROM drive: nothing happens.  I open the CD and klick on "setup.exe."  I get a message telling me that Linux can't run that file.

So what am I doing wrong?

---

### Post by Brunellus on 2007-08-04
> **Mr. Svinlesha said:**
> James:

Actually, I've seen the page you link to, but I'm stumped at the first instruction:

"Install the game as you normally would any other."

Okay.  I place the CD into CD-ROM drive: nothing happens.  I open the CD and klick on "setup.exe."  I get a message telling me that Linux can't run that file.

So what am I doing wrong?
you need to 

1) install WINE

2) use WINE to run the windows executable files:

```

wine setup.exe

```

---

### Post by JamesDS on 2007-08-04
Here's a quick start for you

1.First, go to [http://www.winehq.org](http://www.winehq.org) and download the latest version of WINE.  Then install it.

2.Now, insert your Civ4 DVD/CD into your first (if possible) CD/DVD drive.  Open up a terminal window, and type

```
wine /cdrom/Setup.exe
```

The install-shield window will appear.  You must cancel the DirectX installation, and proceed as normal with the Civilization 4 installation.

3.Once finished, download the latest Civ4 patch (1.74) from [http://forums.civfanatics.com/downloads.php?do=cat&id=12]("http://forums.civfanatics.com/downloads.php?do=cat&id=12") and save it onto your desktop.  In a terminal window, type

```
wine /home/yourusername/Desktop/Civ*.exe
```

where yourusername is your username

That is the patch installed.  Now for the no cd patch, which is needed because the copy protection fails under Wine.  Only use this if you have a legal copy of CIv4 though :).  FInd as I instructed above.

Hope that helps!

---

### Post by Mr. Svinlesha on 2007-08-04
wine setup.exe?

> wine: could not load L"c:\\windows\\system32\\setup.exe": Module not found.

I need to specify the location, nes pas?  How about:

wine /media/CIVILIZATION4/setup.exe

E voilá!

Starts the installation process, but then it gets hung up when trying to install the DirectX drivers.

Now, to make things a bit more complicated: on the advice of[ this page]("http://linuxondesktop.blogspot.com/2007/07/35-cool-applications-to-install-on.html"), I downloaded and installed something called Wine-Doors.  During the installation process I received a couple error messages.  Afterwards I tried using Wine-Doors to download and install Direct X 9, along with quicktime and Windows Media 6.  The Direct X 9 download didn't work either.

I'd like to start by getting rid of Wine-Doors, since it doesn't seem to be working too well on my computer.  I find it under Applications> System Tools, but can't find it listed when I start the Add/Remove Applications tool.

Any advice on how to dump Wine-Doors and successfully install Direct X drivers?

Further: googling "Civilization IV no cd patch 1.74" leads me to a bounty of sites with the CIV4 BTS no CD patch, but I can't for the life of me locate such a patch for vanilla CIV.

Any and all help/advice greatly appreciated.

---

### Post by Mr. Svinlesha on 2007-08-04
**James:**

Yes!  You've helped alot!

The CD is installing now as I write this.

I do of course have a legal version of the game.

Any advice on how to find the no-CD patch?  I assume you can't post a link here.

---

### Post by Mr. Svinlesha on 2007-08-04
Opps, hit another bump.

A message just popped up saying: > **Setup needs the next disk:**

"Please insert Sid Meier's Civilization 4 Disk 0"

Followed by a field asking me to specify the path.

?

---

### Post by Mr. Svinlesha on 2007-08-07
Well, I've gotten a bit further now.  I've installed the game, downloaded and installed the latest patch (I hope), and installed the No-CD patch.  Then come the next two instructions from the Wine how-to:
> Find your CivilizationIV.ini (usually hides under windows/profiles/username/My Games/Civ4/). There should be a line that says "EnableVoice = 1". Change that to = 0. Doing this is needed to enable sound.

Download msxml3.dll from here and put it in your windows/system32 folder.


Now where on God's green earth can I find those paths in my Ubuntu OS?

---

### Post by GaryLittlemore on 2007-08-07
Off Topic here a bit, Sorry.

I've read posts about 'Wine', can someone explain what 'Wine' is and what it does.

As a newbie to Ubuntu, I need all the help I can get.

Thanks

---

### Post by Mr. Svinlesha on 2007-08-07
**Gary:**

Wine is a kind Windows environment simulator that lets you run certain windows applications even if you're using Linux.  In particular, it allows to run a handful of games that configured for Windows (like Civ IV, allegedly).

Here's a [link]("http://wiki.winehq.org/") to the homepage.

Unfortunately, even their helpful walkthroughs are too complicated for poor me.

---

### Post by nazgul42 on 2008-05-13
I know that this thread is old, but I believe you can find the /windows/ etc. folders under ~/.wine/

---

