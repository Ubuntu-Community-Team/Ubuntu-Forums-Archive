---
title: "ubuntu or studio"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by brash_vs on 2007-11-19
is there any real difference between ubuntu and studio, other than just the multi-media apps. 

should i just install the media apps through ubuntu or install studio.

right now i'm using kubuntu and will have to be reinstalling everything anyway. which way should i go.

brash

---

### Post by duruttye on 2007-11-19
I'm having pretty bad experience with ubuntu studio right now, but noone seems to jump and help me.
Funny stuff happen.
Thinking about reinstalling gutsy.
Looks pretty good, though.

---

### Post by Drunky on 2007-11-21
> **brash_vs said:**
> is there any real difference between ubuntu and studio, other than just the multi-media apps. 

should i just install the media apps through ubuntu or install studio.

right now i'm using kubuntu and will have to be reinstalling everything anyway. which way should i go.

brash

Ubuntu Studio also adds a real-time kernel which helps reduce latency when recording.

If you were inclined to upgrade from Gusty to Studio you could use [this]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy") Ubuntu Help wiki page.

I believe not using the real-time kernel is a deal breaker for me.

---

### Post by Incense on 2007-11-21
Studio does not include a lot of normal desktop apps (like an email client, spreadsheets and I'm not sure it comes with a chat client...) but it does install a lot of good audio and video creation apps (which are also in the ubuntu repos) and the low latency kernel. If the kernel doesn't mean anything to you, and you are going to use your computer for more then audio and video editing, then I would go with Ubuntu. You'll save your self a DVD, and the time it's going to take to install all the apps you may want to use as a normal desktop user. 

On the other hand the artwork in Studio is fantastic!

---

### Post by Drunky on 2007-11-21
Incense,

If you upgrade from Gusty 7.10 to Studio 7.10 then you have all the applications that you listed.

---

### Post by por100pre1 on 2007-11-21
> **Drunky said:**
> Incense,

If you upgrade from Gusty 7.10 to Studio 7.10 then you have all the applications that you listed.

Right. Installing Ubuntu Studio only replaces the ubuntu-sounds and removes some metapackages. Everything else stays.

---

### Post by Incense on 2007-11-21
> **Drunky said:**
> Incense,

If you upgrade from Gusty 7.10 to Studio 7.10 then you have all the applications that you listed.

Yes, but if you want more then just the applications, artwork, and sound effects, then you have some work to do, it's all detailed on the following page. 

[https://help.ubuntu.com/community/UbuntuStudioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation")

Are you looking to do some audio recording? From what I can tell, this is really the area where ubuntu studio shines. You may also want to take a look at [JAD]("http://jacklab.org/") (Jacklab Audio Distribution) It runs on E17 so it's more lightweight then studio, though it's built on openSUSE which some people may not like. 

Screens here.

[http://jacklab.net/jacklaborg/english/?JAD_1.0_Screenshots]("http://jacklab.net/jacklaborg/english/?JAD_1.0_Screenshots")

---

### Post by Drunky on 2007-11-21
Incense,

I think that page may be misleading or perhaps I'm confused.

To me it appears that practically everything the UbuntuStudioPreparation page instructs you to install is already included when you type: ```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
``` from the [UbuntuStudio/UpgradingFromGutsy]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy") page.

For example, the "Basics" from the preparation page are included with the [Ubuntustudio-audio]("http://packages.ubuntu.com/feisty/base/ubuntustudio-audio") metapackage from the upgrade page.

The effects the same:  [ubuntustudio-audio-plugins]("http://packages.ubuntu.com/feisty/base/ubuntustudio-audio-plugins")

Even the real-time kernel:  [linux-rt]("http://packages.ubuntu.com/gutsy/metapackages/linux-rt")

Which segues me...

por100pre1,

I believe that you may be wrong.  Of course I have an equally good chance of being wrong.  But, there is more than just adding the studio sounds.  The help page instructions also replaces the kernel.

---

### Post by Incense on 2007-11-21
> **Drunky said:**
> Incense,

I think that page may be misleading or perhaps I'm confused.

To me it appears that practically everything the UbuntuStudioPreparation page instructs you to install is already included when you type: ```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
``` from the [UbuntuStudio/UpgradingFromGutsy]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy") page.

For example, the "Basics" from the preparation page are included with the [Ubuntustudio-audio]("http://packages.ubuntu.com/feisty/base/ubuntustudio-audio") metapackage from the upgrade page.

The effects the same:  [ubuntustudio-audio-plugins]("http://packages.ubuntu.com/feisty/base/ubuntustudio-audio-plugins")

Even the real-time kernel:  [linux-rt]("http://packages.ubuntu.com/gutsy/metapackages/linux-rt")

Which segues me...

por100pre1,

I believe that you may be wrong.  Of course I have an equally good chance of being wrong.  But, there is more than just adding the studio sounds.  The help page instructions also replaces the kernel.

I could very well be wrong. :) I actually really hope that I am, because that page just looked like a lot of work. Maybe it's just an older page that is replaced by packages now.

---

