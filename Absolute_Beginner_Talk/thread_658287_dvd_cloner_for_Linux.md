---
title: "dvd cloner for Linux?"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by new2gutsy on 2008-01-04
I am wondering about is my dvd burning,I got a burning application installed,burned a kvcd as a cue sheet to a cdr and worked flawlessly already
but I'm looking for a program like I used in windows "dvd cloner"? So I can completely copy the contents of one disc then copy it to another
is there nething like that for Ubuntu?

---

### Post by steeleyuk on 2008-01-04
You could try [Brasero]("apt://brasero") which does 1:1 disc burning. Though, I don't know if it allows you to copy commerical DVD's.

---

### Post by gn2 on 2008-01-04
There are a few, I use K9Copy.

---

### Post by LowSky on 2008-01-04
gnomebaker should make 1:1 DVDs also K3b, K9Copy should too

---

### Post by new2gutsy on 2008-01-04
Great
Thank you,will check these out when I get home from work
I assume I can get these from the add/remove programs or the sympatic (sp) update manager thingy?

---

### Post by steeleyuk on 2008-01-04
Yes, you can get them through either.

---

### Post by Paulmd on 2008-01-04
> **new2gutsy said:**
> I am wondering about is my dvd burning,I got a burning application installed,burned a kvcd as a cue sheet to a cdr and worked flawlessly already
but I'm looking for a program like I used in windows "dvd cloner"? So I can completely copy the contents of one disc then copy it to another
is there nething like that for Ubuntu?

Commercial or home brew? 

If commercial, are they video or Data?


Commercial Video DVDS are almost always copy - protected. On top of that, there is too much data for a dvd-r. Copying those involves breaking the copy protection and re-encoding the video at a lower quality (which takes up less space). The movie industry has aggressively went after sites that host programs to do this.

Data dvds are generally not copy protected. Though most game cds and dvds are (they use different forms of copy protection).

k3b is a common burning program that handles non-copy protected cds and dvds.

---

### Post by LowSky on 2008-01-04
some movies fit on standard 4.7 GB disc, while some need Dual layer disc that hold 9.4Gb.

Copy Protection is sometimes annoying, but there are ways around it

---

### Post by DishBreak on 2008-01-04
xDvdShrink seems to do the job you're looking for. easiest way to do it is to install via automatix

[www.getautomatix.com](www.getautomatix.com) 
look for "Installing with APT" under the Install wiki. 

Hopefully this helps

---

### Post by Hallvor on 2008-01-04
DVD95 will shrink a dvd9 to a regular dvd5.

*sudo apt-get install dvd95*

---

### Post by new2gutsy on 2008-01-04
I would say Homebrews then....I would fully copy some movies from the Movie Gallery and Blockbuster on Windows,could always override the copy protection with the add on "anydvd"
But I'm not really looking for that I'd be happy just getting a cloning program to do homebrews
much quicker cloning one rather then burning it a 2nd time if I'm making a copy for a friend or sumthing like that


> **Paulmd said:**
> Commercial or home brew? 

If commercial, are they video or Data?


Commercial Video DVDS are almost always copy - protected. On top of that, there is too much data for a dvd-r. Copying those involves breaking the copy protection and re-encoding the video at a lower quality (which takes up less space). The movie industry has aggressively went after sites that host programs to do this.

Data dvds are generally not copy protected. Though most game cds and dvds are (they use different forms of copy protection).

k3b is a common burning program that handles non-copy protected cds and dvds.

---

### Post by Paulmd on 2008-01-04
> **new2gutsy said:**
> I would say Homebrews then....I would fully copy some movies from the Movie Gallery and Blockbuster on Windows,could always override the copy protection with the add on "anydvd"
But I'm not really looking for that I'd be happy just getting a cloning program to do homebrews
much quicker cloning one rather then burning it a 2nd time if I'm making a copy for a friend or sumthing like that


You do know you can't legally copy rentals, don't you?

You can make a backup copy of dvds you actually own. (But you can't turn around and sell them).

I think I had better not venture further help on this topic.

---

### Post by new2gutsy on 2008-01-04
LOL no I'm not selling them or nething
I know I can't LEGALLY do it,just alot of times when I burn a movie I make a copy for a friend

---

### Post by steeleyuk on 2008-01-04
That's illegal too ;)

---

### Post by Paqman on 2008-01-04
> **DishBreak said:**
> xDvdShrink seems to do the job you're looking for. easiest way to do it is to install via automatix

[www.getautomatix.com](www.getautomatix.com) 
look for "Installing with APT" under the Install wiki. 

Hopefully this helps

Using Automatix isn't such a good idea. It has a pretty cavalier attitude to packaging standards, and can therefore introduce a lot of instability into your system. Compiling from a tarball isn't really that hard, and if you use [checkinstall](http://packages.ubuntu.com/gutsy/admin/checkinstall) you'll even be able to uninstall through Synaptic

---

### Post by Hallvor on 2008-01-05
> **steeleyuk said:**
> That's illegal too ;)

That depends where you are, I guess. It is perfectly legal to give copies of music albums and movies to friends and family here in Norway. And probably in many other countries as well. Fair use.

---

### Post by Paulmd on 2008-01-05
> **Hallvor said:**
> That depends where you are, I guess. It is perfectly legal to give copies of music albums and movies to friends and family here in Norway. And probably in many other countries as well. Fair use.

In the US, fair use is more restrictive. You can make a backup copy of a movie or cd, transfer it to an ipod or whatever, but you can't make copies for all of your family and friends. Lots of people DO anyway, and it's not heavily enforced until there's monetary gain, or some volume, but that's not really the point.

---

