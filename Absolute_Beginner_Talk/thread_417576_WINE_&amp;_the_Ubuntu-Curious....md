---
title: "WINE &amp; the Ubuntu-Curious..."
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by arphaus on 2007-04-21
Hello folks,

I've decided to join the ranks of the Ubuntu-Curious, and here's a way-detailed intro to my 3 basic questions.  I'm not certain how likely it would be that I make a complete switch from Windows, but at the least it might become a growing hobby.  Mainly, I've had enough of reformatting & reinstalling windows on multiple computers on a semi-annual basis.  I don't like how the performance degrades over time or how a fresh install of XP can be zipping along until so-called critical Windows Updates slow it down ([apparently not the case with Ubuntu]("http://ubuntuforums.org/showpost.php?p=1481075&postcount=5")).  It's enough that I've considered getting a Mac for my next computer (thanks to Boot Camp/Parallels).  Might as well check out Ubuntu while I'm at it.

Being a web designer/developer complicates things a bit.  I don't use IE personally, but I need it for cross-browser testing.  Or GIMP might suit my personal needs, but I actually use Photoshop in-depth and need to exchange .psds with other Photoshop users.  For the most part, I've been moving towards using more and more open-source software, both for the great applications but also because there are these great communities around them.

Having read a great analogy on [toy cars vs legos]("http://linux.oneandoneis2.org/LNW.htm") (a great starting point for this, btw), I delved deeper into the forums and determined the following:

**Some apps I use have Linux versions**
[LIST]
[*]Firefox
[*]Gaim
[*]OpenOffice
[*]Picasa
[*]Skype
[*]Thunderbird
[*]xampp
[/LIST]

**Some apps I use have decent or better equivalents**
[LIST]
[*]Dreamweaver/Homesite - Quanta Plus, Bluefish, Screem, NVU. (might give NVU a go on pc regardless)
[*]Filezilla (linux port coming, but there are lots of ftp options)
[*]itunes management - gtkpod, yamipod
[*]itunes playback- rhythmbox, amarok
[*]itunes podcatching - peapod
[*]Nero - gnomebaker
[*]Nod32 - several options
[*]Notepad/Wordpad - gedit
[*]Winrar - several options
[/LIST]

**Some apps I use might have an equivalent**
[LIST]
[*]Blogdesk - BlogGTK or Gnome Blog if they a) have templates and 2) have automatic image sizing
[*]Extensis - Fonty Python?  Fontlinge?  Font Management is very helpful to me, though not critical.  I could live with a zillion fonts loaded if it didn't slow things down and I could preview them easily.  At least it seems like Windows fonts can be installed on Linux.
[/LIST]

**Some apps I use may require WINE or ... Windows**
[LIST]
[*]Flash (infrequently)
[*]IE 6 & 7  ***update - found IEs 4 Linux, tho IE 7 is in beta
[*]Illustrator - Inkscape looks cool, but AI is a necessity
[*]Photoshop - GIMP is nice, but won't cut it for me.  Seeing [this]("http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/") is rather promising, especially the comment that the method may work for other Macromedia apps as well.
[/LIST]

Add these to the equation:
[LIST]
[*]I've always tried to get performance out of Windows by using stuff like 98Lite, or tweaking XP to high heaven;  I value performance over appearance
[*]I've dual-booted extensively, primarily to keep my audio production OS lean & clean (I figure I'll need to keep a Windows install for music stuff)
[*]I've replaced the Windows shell to see if I can find a better (or perhaps a 'more suitable for me') UI
[/LIST]

After all this, I'm a prime candidate to at the least try Ubuntu out.  If I could use WINE to run some necessary apps well I may be able to make an eventual switch.  My main questions are:
[LIST=1]
[*]Does WINE work well with Photoshop, Illustrator & the like?  Or is it hit & miss depending on the specific program?  I read one post that indicated the PS on WINE was sloooooow.
[*]Is using the command line similar to Windows' command prompt?  (and yes, I can definitely copy/paste.  Very well in fact ;-))
[*]The ATI driver stuff looks daunting.  Will good copy/paste skills suffice?  I don't play games much, but I love working at 1680x1050.
[/LIST]

Thank y'all very much!

Arphaus

---

### Post by rdbeamer on 2007-04-21
Hi:
Ran across your post while looking for info on "cross over" which is based on wine.  It is available in the newest release.  From how it reads, most of the adobe products should work well with it.  Hope that helps and makes your migration easier.

---

### Post by arphaus on 2007-04-21
Do you mean Codeweaver's Crossover?  If so, their site has Photoshop CS 2 listed as 'untested.'  Could you provide a link to the info you've found?

---

### Post by arphaus on 2007-04-21
I'm extremely impressed.  Very much so.  I realize that some things were slow since it was running off a cd, but overall it was pretty snappy, even with the wobbly window stuff turned on.  Quick things I noticed:

[LIST]
[*]it's elegant (at least the human theme, I only took brief glances at the others)
[*]it's well organized - it took me a couple of minutes to get my bearings
[*]terminal doesn't look as scary as I thought it might
[*]my screen resolution was correct
[*]it seems to be what I hoped to get from shell replacements before
[/LIST]

I couldn't test my wireless settings as I'm at location that requires a vpn client (cisco to be precise), but things seemed pretty positive overall.  Now I'm piqued enough to make a partition for a dual boot and look into moving my settings from my PC installs of Firefox & the like.  And test out WINE and see what happens.  Woot!

---

### Post by adewale on 2007-04-21
well i've tried photoshop with wine but didn't go well. you can try inkscape, it  makes my work easier also there is xara xtreme([http://www.xaraxtreme.org/)](http://www.xaraxtreme.org/)). There are many graphic tools out there you just have to search

---

### Post by kyphi on 2007-04-21
Several Photoshop versions work with CodeWeavers CrossOver Linux.  They are listed under P (not A for Adobe) in the Compatibility List.  I have found other Windows programmes to work well with CrossOver but to get these recognised is a difficult task.  I don't think that CrossOver have the staff to update information regularly.  The best thing to do is to experiment yourself.

You might also like to have a look at InnoTek VirtualBox which will let you run Windows with all its programmes on top of Linux.  That way you can access your Windows programmes with a mouseclick without dual booting.  Another programme that will perform a similar service is VM Ware ... there are others.

I run PhotoImpact in Windows via VirtualBox on Ubuntu 6.06.

---

### Post by arphaus on 2007-04-21
I'd be interested to try Inkscape & Xara for personal use, but being able to exchange psds & ais is a must.  If Photoshop performance is really poor, than a dual-boot would be best option for now.  Or perhaps vmware, though I'm not sure how productive that would be with a single core cpu.

I will give it a go over the next few weeks and see how things play out.  Regardless, I'm quite excited about Ubuntu overall!

---

### Post by adewale on 2007-04-22
i just used inkscape to create and export in ai (adobe illustrator) format and Gimp was able to import it successfully

---

### Post by arphaus on 2007-04-22
That's pretty cool.  I'm still skeptical as to how cross-compatible the apps are, but I'll do some testing and see how it goes.  I'll start prepping my hard drive for a proper install today - my wifi test at home went nice and smooth :)

---

