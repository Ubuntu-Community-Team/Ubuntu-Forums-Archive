---
title: "Compiling Paint.NET"
date: 2008-10-07
forum: Art &amp; Design
---

### Post by del_diablo on 2008-10-07
I really enjoy Ubuntu, and its addictive like drugs(want more :P).
However, i find it lacking a decent grapic editor(GIMP is far to messy). Since Paint.NET is open source, i guess it can be compiled into Mono and runned.
Is it possible? And how to do so?(no clue on compiling).

---

### Post by BrokeBody on 2008-10-07
[http://code.google.com/p/paint-mono/](http://code.google.com/p/paint-mono/)

---

### Post by Sami655 on 2008-10-07
> **BrokeBody said:**
> [http://code.google.com/p/paint-mono/](http://code.google.com/p/paint-mono/)

Does anybody know how to install limewire on ubuntu

---

### Post by bobpaul on 2008-10-07
> **Sami655 said:**
> Does anybody know how to install limewire on ubuntu

In the future, please open a new thread to ask new questions. This topic is about Paint.Net on mono. This is also something you should be able to find quite quickly with the search function. For limewire, look in the [Community documentation](https://help.ubuntu.com/community/LimeWire), search these forums, or start a new topic. If a limewire compatible client is acceptable, click Applications, then Add/Remove Programs and search for "gnutella" to find limewire compatible peer to peer applications or "peer to peer" to list all p2p filesharing programs.

---

### Post by Dragonbite on 2008-10-08
> **del_diablo said:**
> I really enjoy Ubuntu, and its addictive like drugs(want more :P).
However, i find it lacking a decent grapic editor(GIMP is far to messy). Since Paint.NET is open source, i guess it can be compiled into Mono and runned.
Is it possible? And how to do so?(no clue on compiling).

Have you looked at [[COLOR="Blue"]Krita [/COLOR]]("http://www.koffice.org/krita/")as a replacement? The interface looks a little easier and it is supposed to be pretty powerful (like 80% of Gimp, which is 80% of Photoshop).

The latest Gimp is supposed to have cleaned things up, but there is also [GimpShop ]("http://www.gimpshop.com/index.shtml")which makes Gimp look more like Photoshop with tools in menus where Photoshop would have them, etc.

I don't know if [[COLOR="Blue"]CinePaint [/COLOR]]("http://www.cinepaint.org/")is any closer to what you are looking for or not.

---

### Post by del_diablo on 2008-10-08
Cine looks messed up.......... From the pictures it seems that the entire layout is completely splitted(similar to gimp).
Krita looks like it could work, but is the layers tool good enogh? And does it got enogh effects? I would be screwd over without stuff like shape 3D.
And for the person who linked up to Paint.Mono..................... I got no freaking clue on compiling, and has anybody actualy tried? Can somebody give me instructions? I do not really understand what "Building Paint.NET on Linux"  section says at all......
..... all i want to get some way to build it. How?

---

### Post by smartboyathome on 2008-10-08
> **del_diablo said:**
> Cine looks messed up.......... From the pictures it seems that the entire layout is completely splitted(similar to gimp).
Krita looks like it could work, but is the layers tool good enogh? And does it got enogh effects? I would be screwd over without stuff like shape 3D.
And for the person who linked up to Paint.Mono..................... I got no freaking clue on compiling, and has anybody actualy tried? Can somebody give me instructions? I do not really understand what "Building Paint.NET on Linux"  section says at all......
..... all i want to get some way to build it. How?

The only way TO build it is through Paint.Mono, because Paint.NET is written for Windows, and Mono != MS .NET point to point, otherwise we could be sued.

---

### Post by directhex on 2008-10-08
> **smartboyathome said:**
> The only way TO build it is through Paint.Mono, because Paint.NET is written for Windows, and Mono != MS .NET point to point, otherwise we could be sued.

Actually, the specific problem for Paint.NET is P/Invokes. A P/Invoke is where a CLI app uses a section of a platform-specific C library, rather than using a cross-platform CIL equivalent. Paint.NET makes a lot of P/Invokes to Windows-only libraries, which is why it doesn't work. The previously linked paint-mono is the same app with the Windowsisms removed. See [http://code.google.com/p/paint-mono/wiki/PortingStrategy](http://code.google.com/p/paint-mono/wiki/PortingStrategy) for specifics about how the project is intended to work (and how to compile it). For me, it "just works"

---

### Post by Dragonbite on 2008-10-08
> **del_diablo said:**
> Cine looks messed up.......... From the pictures it seems that the entire layout is completely splitted(similar to gimp).
Krita looks like it could work, but is the layers tool good enogh? And does it got enogh effects? I would be screwd over without stuff like shape 3D.
And for the person who linked up to Paint.Mono..................... I got no freaking clue on compiling, and has anybody actualy tried? Can somebody give me instructions? I do not really understand what "Building Paint.NET on Linux"  section says at all......
..... all i want to get some way to build it. How?

Well CinePaint is a fork of Gimp... they were from the same code base and then diverged into different directions/focus.

I would give Krita a try. If you aren't sure about it then maybe try it through a Kubuntu LiveCD. May be slow and you can't work with large images but it could give you an idea of whether it will work.

Have you tried anything like [[COLOR="Blue"]Inkscape[/COLOR]]("http://www.inkscape.org/") or [[COLOR="Blue"]Xara Xtreme[/COLOR]]("http://www.xaraxtreme.org/") which are both Scalable Vector Graphics editors?  They are NOT the same as Paint.NET or Gimp or Photoshop, they are more like Adobe Illustrator which is quite a bit different, but depending on how you use Paint.NET it may be kinda fun.

I use Paint.NET on my work laptop and love it. I wish they would port it to Mono/Linux so it can be in the repositories.

---

### Post by directhex on 2008-10-09
> **Dragonbite said:**
> I use Paint.NET on my work laptop and love it. I wish they would port it to Mono/Linux so it can be in the repositories.

Could package it today, but it's not quite well-behaved enough yet (perhaps after Mono 2.0)

---

### Post by del_diablo on 2008-10-09
> **directhex said:**
> Could package it today, but it's not quite well-behaved enough yet (perhaps after Mono 2.0)

Please do.

---

### Post by directhex on 2008-10-09
> **del_diablo said:**
> Please do.

I need to be more convinced of "readiness" first - running on Mono 1.9.1, it fails that test. Perhaps Mono 2.0's better WinForms implementation will improve matters

---

### Post by Dragonbite on 2008-10-09
> **directhex said:**
> Could package it today, but it's not quite well-behaved enough yet (perhaps after Mono 2.0)

I think they just announced Mono 2.0 is out.

---

### Post by directhex on 2008-10-09
> **Dragonbite said:**
> I think they just announced Mono 2.0 is out.

They did. But it won't make Intrepid, and we don't have any preview packages ready yet I can use for testing

---

