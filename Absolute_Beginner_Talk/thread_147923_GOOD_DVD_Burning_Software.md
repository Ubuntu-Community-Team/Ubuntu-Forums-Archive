---
title: "GOOD DVD Burning Software"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by d-x on 2006-03-21
Whats good DVD Burning Software? I have some files that need to be burnt to DVD and be able to work on a win32 machine. I have no idea what is good in ubuntu hence why I'm asking.

---

### Post by nocturn on 2006-03-21
K3B is great, though it is a KDE app.

You can get it via synaptic.

---

### Post by trent dillman on 2006-03-21
K3B is good, although I've grown quite fond of GnomeBaker. Also, Nero makes a Linux version which I believe is a ripoff of gtoaster (but I may be mistaken on that one).

Try:

sudo apt-get install k3b gnomebaker gtoaster

and pick which suits you best.

---

### Post by frodon on 2006-03-21
K3b is the more complete burning software i think, however gnomebaker and graveman works really well, all that softwares are in the repositories.
I use k3b with GNOME personnally.

---

### Post by _simon_ on 2006-03-21
Gnomebaker has never worked for me but k3b worked first time.

---

### Post by taurus on 2006-03-21
If you follow this forum for the last few days, some people are having problems with gnomebaker so I would recommand k3b also.  And just so you know, nerolinux IS not free!  You need to enter a key for it but if you have a copy for Windows (version 6 or above), you can use the same key...

---

### Post by patrick295767 on 2006-03-21
K3B is the very very best.
  
If you cannot burn DVD (burnign fails) , try the Option 'IGNORE' 
that can make it !
  
I got such error depending on the type of dvd burner hardware u are using.

Greetz

---

### Post by jrcmuniz on 2006-03-21
Try NeroLinux!!!! very good one!!

Cheers

Joao Renato.

---

### Post by az on 2006-03-21
For dvdauthoring, I find tovid is great.   You can easily make a dvd with all of your kids videos from your digital camera with it.

It is not in the repos, AFAIK...

---

### Post by patrick295767 on 2006-03-21
[QUOTE=jrcmuniz]Try NeroLinux!!!! very good one!!

Cheers

Joao Renato.[/QUOTE]
  
Very easy one, ... 
  I tried it, and I have doubts concerning its capacities compared to the brother under windows.
  
(After using nerolinux, you'll certainly change to k3b, but it's worth a try)

---

### Post by jtpratt on 2006-03-22
You mentioned K3B, which is very good but can not natively convert video of prepare the proper format for a DVD at all.  It can burn a DVD from .iso if you have it already created and the proper xml file and folder structure to go along with it.

Tovid is also good, but has it's share of problems on many machines.  There is a new one called DeVeDe that I've not been able to get to work at all.  Because of these any many other issues, I've documented how I convert video and create dvd's on my Ubuntu box in my <a href="http://smorgasbord.net/convert_video_linux" target="_blank">convert to video in linux guide</a>.

Hopefully some of the tips there may help you.

---

### Post by steve.horsley on 2006-03-23
Every time I install Ubuntu, I give gnomebaker another chance. And every time, I eventually give up and go back to k3b. To be honest, I'm astonished that the gnomebaker authors can bring themselves to release something that unreliable. Not that I'm claiming that I could do better.

* It fails to write to re-writable CDs (without giving a reason) unless you blank the old contents off first. Just brain-dead. k3b asks if you want it erased.
* When you insert a blank CD that it just asked for, nautilus pops up a window asking if you want to burn to the CD you just inserted. Right on top of the OK button in the gnomebaker "please insert" dialog box! K3b, which is a KDE app, manages to suppress that popup in gnome. Gnomebaker, a gnome app, doesn't.

Those I was trying to live with. Then I tried to burn a data DVD this evening...

* It failed to write a blank data DVD for no obvious reason
So then I tried to format it in case that was the problem...
* It failed to format a blank data DVD, and the cdrecord mentioned an invalid command

I gave up and installed k3b. Perfect burn first time. It's a shame - it would be nice if gnome had a reliable burner as well as KDE.

This kind of turned into a rant about gnomebaker. Sorry, but I needed to get it off my chest. It's sad to see something so nearly finished, nearly very good, but apparently just abandoned.

---

