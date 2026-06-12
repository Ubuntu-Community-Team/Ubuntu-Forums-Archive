---
title: "Videos on Internet Sites not working"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by chaplanger on 2007-04-11
When I try to run video snippets on the internet I receive the following error message:

```
Totem could not play 'mms://209.73.191.109/st1704r02/002/gamespot/4/35555476.wmv?
StreamID=35555476=30=cc86b193e312169838c2f1e798b7d152=NzU1NjA3NTI0NjFjZDNlYz=78=
%252FYahoo%252Fentfeeds%252Fvideogames%252Fgenre%252Faction%252Fsuperpapermario
%252Ftrailer1=6e1aji52v0ieu461cd4b0=0'.

Could not open location; You may not have
permission to open the file.

```

What am I missing?  What needs to be updated to allow this to work?

I am running Ubuntu 6.10, and using Firefox 2.0.0.3.

Thanks for any help you can give!

---

### Post by nudnik on 2007-04-11
> **chaplanger said:**
> When I try to run video snippets on the internet I receive the following error message:

```
Totem could not play 'mms://209.73.191.109/st1704r02/002/gamespot/4/35555476.wmv?
StreamID=35555476=30=cc86b193e312169838c2f1e798b7d152=NzU1NjA3NTI0NjFjZDNlYz=78=
%252FYahoo%252Fentfeeds%252Fvideogames%252Fgenre%252Faction%252Fsuperpapermario
%252Ftrailer1=6e1aji52v0ieu461cd4b0=0'.

Could not open location; You may not have
permission to open the file.

```

What am I missing?  What needs to be updated to allow this to work?

I am running Ubuntu 6.10, and using Firefox 2.0.0.3.

Thanks for any help you can give!

Make sure you have all the codecs installed. If you are unsure of what I mean, or are sure you have not installed any such thing, see the "Restricted Formats" section of the Ubuntu documentation. You can find this easily enough by navigating to the section on multimedia codecs and proceeding from there. You specifically need the win32 codecs installed to play the media you have mentioned. 

Another possibility comes to mind; have you upgraded firefox manually using their website, or perhaps using an install script as opposed to the repositories? If so, that might have broken the links which allow for smooth launching of the media apps. You could try downloading the video to your desktop and watching it from there until a fix is possible.

---

### Post by chaplanger on 2007-04-11
Hmmmm. . .  One correction -- Video works from some internet sites (MSNBC runs fine as does Sports Illustrated) but others just won't work -- Yahoo.com; CNN (says it can't find Windows Media Player -- but will load and play sound but no video???). 

Hmmmm. . .

---

### Post by Obor on 2007-04-11
Make sure that you have all codecs installed [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
You might be missing windows codecs [https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)

---

