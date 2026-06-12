---
title: "Pixel Shading&lt; v1.x"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by moocow1452 on 2007-12-20
I finally decided to go through with the gaming on Ubuntu using Wine. So, for a test, I downloaded a Psychonauts demo off of Steam, and ran it on my Acer Aspire 5100 lappy with Feisty Installed. But, to my shock and horror, when ever I tried to play the game, it always showed this error popup that I have no idea what to do. 

[IMG]http://i7.photobucket.com/albums/y281/YoshiMan1452/Untitled.png[/IMG]

I read in the Forum Archives that the fix involved going into Wine's registry or something, but can I have some clarification on what I actually need to do?

---

### Post by Doomedelite on 2007-12-20
Do you have the drivers installed for your video card?

I'm not exactly sure if wine support pixel shader 1, but I'm _pretty_ sure it does, so it must not be detecting that capability on your video card.

What type of graphics card do you possess?

---

### Post by Daveth on 2007-12-20
have you tried enabling pixel shader support in winecfg? Its under the graphics tab.

```
winecfg
```

though be mindful it did not work here

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4384&iTestingId=17736](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4384&iTestingId=17736)

---

### Post by moocow1452 on 2007-12-20
It is an ATI Radeon Xpress 1100, and I do have restricted drivers enabled, and Pixel Shading enabled as well.

But that it runs horribly anyway is a bit of a downer.

---

