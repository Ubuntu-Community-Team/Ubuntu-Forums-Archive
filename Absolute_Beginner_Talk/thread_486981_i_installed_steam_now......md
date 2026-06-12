---
title: "i installed steam now....."
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by TehCJ on 2007-06-28
Ok Steams Installed And all But Whe i start it No TEXT shows Up in **STEAM** 


Can someone help me?:D

---

### Post by starcraft.man on 2007-06-28
> **TehCJ said:**
> Ok Steams Installed And all But Whe i start it No TEXT shows Up in **STEAM** 


Can someone help me?:D

HUH? You mean the Valve DRM solution Steam in WINE? The one that lets you play their games? Or another steam?

---

### Post by TehCJ on 2007-06-28
> **starcraft.man said:**
> HUH? You mean the Valve DRM solution Steam in WINE? The one that lets you play their games? Or another steam?



The game one :)

---

### Post by crav on 2007-06-28
Look through the wine folders, there should be a folder somewhere for fonts. Download Tahoma (google) and install the font here. The text isn't showing up because you don't have the proper font.

---

### Post by starcraft.man on 2007-06-28
> **TehCJ said:**
> The game one :)

[Link!]("http://appdb.winehq.org/appview.php?iVersionId=1554") Apparently from this, only the latest version 0.9.39.x will let you run Steam decently. I don't think its in the repos yet so you would have to make sure you have the latest version (not a WINE expert, it should be listed in "winecfg" though). If not, I guess (I don't run steam in WINE or on any of my systems, I don't endorse platform DRM) you will have to compile it. 

Remove WINE same way you put it in, go to the WINE site and download the source then compile it following this [guide]("http://www.psychocats.net/ubuntu/installingsoftware#source") (if it has specific instructions in a txt file called install follow those). Alternatively, if they maintain a bleeding edge repo you can add that to sources and upgrade your version. Then reinstall steam. I can't help you beyond that, I don't use WINE much at all.

By game one, you meant STEAM right? Hope I got that right...

---

### Post by TehCJ on 2007-06-28
> **starcraft.man said:**
> [Link!]("http://appdb.winehq.org/appview.php?iVersionId=1554") Apparently from this, only the latest version 0.9.39.x will let you run Steam decently. I don't think its in the repos yet so you would have to make sure you have the latest version (not a WINE expert, it should be listed in "winecfg" though). If not, I guess (I don't run steam in WINE or on any of my systems, I don't endorse platform DRM) you will have to compile it. 

Remove WINE same way you put it in, go to the WINE site and download the source then compile it following this [guide]("http://www.psychocats.net/ubuntu/installingsoftware#source") (if it has specific instructions in a txt file called install follow those). Alternatively, if they maintain a bleeding edge repo you can add that to sources and upgrade your version. Then reinstall steam. I can't help you beyond that, I don't use WINE much at all.

By game one, you meant STEAM right? Hope I got that right...

Yes i meant Game steam lol:popcorn:

---

### Post by Motoxrdude on 2007-06-28
I have uploaded the tahoma font. Just extract it to ~/.wine/drive_c/windows/fonts.
Then start steam and it should be working![ATTACH]36731[/ATTACH]

---

### Post by starcraft.man on 2007-06-28
> **Motoxrdude said:**
> I have uploaded the tahoma font. Just extract it to ~/.wine/drive_c/windows/fonts.
Then start steam and it should be working![ATTACH]36731[/ATTACH]

Really thats it? Stupid font... Oh well, I guess don't bother with getting latest version, unless it offers a performance boost? I wouldn't know...

---

### Post by Motoxrdude on 2007-06-28
> **starcraft.man said:**
> Really thats it? Stupid font... Oh well, I guess don't bother with getting latest version, unless it offers a performance boost? I wouldn't know...
I got the latest version from wines official site; i didnt notice any difference.

---

### Post by TehCJ on 2007-06-30
> **Motoxrdude said:**
> I have uploaded the tahoma font. Just extract it to ~/.wine/drive_c/windows/fonts.
Then start steam and it should be working![ATTACH]36731[/ATTACH]



Thank you so much :D your awesome!:KS:KS:KS:KS:KS:KS:KS

---

