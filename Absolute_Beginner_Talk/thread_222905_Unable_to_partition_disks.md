---
title: "Unable to partition disks"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by useResa on 2006-07-25
[FONT="Trebuchet MS"][COLOR="Blue"]Hi everybody, again someone new to Linux with installation problems.

I have decided to step into the world of Linux based on positive experiences from many people around me. In order to get started I am trying to install Ubuntu on an old PC of mine.

Here are some specs (don't know exactly which are relevant):
Award Modular Bios v4.51PG
Award Plug & Play Bios Version 1.00
360448K Memory
IDT WinChip C6 CPU at 200 MHz
Samsung WU32543A (2.54Gb) Hard Disk

When trying to install I always get the message:
"Unable to locate RDSP".
Searching your forum I already found out that I can circumvent this by pressing F6 and adding "acpi=off" to the command line.

However, regardless whether I am trying to install Ubuntu Server or Ubuntu desktop, I can not get the partitioning of the hard disk. It always comes back with I/O errors.
*Is there anyone who can give me a hint on how to get around this?*

Furthermore when I try to install Ubuntu Desktop I only can use the desktop if I start it from the menu in the Save Graphics Mode. But when I do this I get the unable to locate RDSP error. When I use F6 I do not get a proper screen.
*Can someone maybe give me a hint on how I can prevent the RDSP error and still use the graphics mode?*

Thnx in advance.[/COLOR][/FONT]

---

### Post by trent dillman on 2006-07-25
I would try using another, smaller linux distro.

Take a look at Damn Small Linux.

---

### Post by useResa on 2006-07-26
May I ask why you suggest DSL?

Do you believe that my PC is simply to small for Ubuntu Desktop?
Is an other option to install Ubuntu Server, than install a lightweight desktop, open office and so on separately later?

---

### Post by kurniawands on 2006-07-26
what about Xubuntu ???? it's made for the dino... i think...:-D

---

### Post by moma on 2006-07-26
I agree with "kurniawands".

Go for Xubuntu or **[COLOR="Red"]UbuntuLite[/COLOR]**.
Try both.

More info here
[http://doc.gwos.org/index.php/Choices]("http://doc.gwos.org/index.php/Choices")
and here 
[http://www.futuredesktop.net/ubuntu6.06.html]("http://www.futuredesktop.net/ubuntu6.06.html")

Or employ the old PC as thinstation
[http://thinstation.sourceforge.net/wiki/index.php/ThIndex]("http://thinstation.sourceforge.net/wiki/index.php/ThIndex")

---

### Post by nikku_neko on 2006-07-26
i'm just a rookie here, but i here's my 2cents anyway.

it looks to me like you may be a bit short on the ram end of things.
the server version recommends that you have at least 64mb, and the desktop is recommended at 256 mb.  the installer might be getting caught up because it cannot load properly in so little space.

a similar thing happened to me when attempting to install to an old compaq pentII machine with similar specs. 
> 
what about Xubuntu ???? it's made for the dino... i think...
that still needs 64mb ram, minimum.  or, rather, that's what the website says.


on a side note, DSL is pretty neat.  i'm new to the whole linux thing, but it seems like a slick little system for as small as it is.

---

### Post by useResa on 2006-07-26
Thanks for the suggestions.
From what I have read I think I'll try Xubuntu.

If I don't forget - yes, age is catching up with me 
:cool: - I'll get back and let you know the result.

---

### Post by useResa on 2006-08-10
Hi everybody, here the update I promised last time I posted to the list.

I have in the end chosen for an installation of UbuntuLite.

I never succeeded in getting the mentioned hard disk up and running. 
But from an even older PC I have installed (additionally) an 800 Mb Seagate hard disk and installed UbuntuLite on this disk and it works! :p
Next step is now to find out if the SAMSUNG hard disk is unusable all together or if I can now use it for storage.

So in the end you really do need only a small PC in order to have UbuntuLite up and running!

Kind regards and thanks for any suggestions made.

---

