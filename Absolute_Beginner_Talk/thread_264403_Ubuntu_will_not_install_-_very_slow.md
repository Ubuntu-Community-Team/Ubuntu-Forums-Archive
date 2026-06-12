---
title: "Ubuntu will not install - very slow"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by souperdoo on 2006-09-24
Hi  

I am trying to install Ubuntu on a Compaq Armada laptop. This is a P3 500MHz with 192 Mb of RAM.

When I boot from the Ubuntu disk (which I created from a download and burned an ISO image as recommended) I can get the desktop to come up. Takes a long time, but it comes up.

When I click on the "Install" icon it EVENTUALLY gets to the menu where I am to select the language. After selecting "English" it takes a LONG time for the "Forward" button to activate. 

Once it does and I click that button nothing ever happens again. I've even waited overnight, but no joy.

I used this CD to install Ubuntu on a desktop at work and it all ran very quickly and that installation is working well.

Any thoughts?

Thanks,

Tom

---

### Post by xyz on 2006-09-24
Did you check the integrity of your CD?
```
md5sum -c file.iso.md5
```
in a console to make sure nothing wrong while burning or that there are no corrupted files.

---

### Post by souperdoo on 2006-09-24
> **xyz said:**
> Did you check the integrity of your CD?
```
md5sum -c file.iso.md5
```
in a console to make sure nothing wrong while burning or that there are no corrupted files.

Hi - 

I'm not experienced enough to know exactly what the above means. I don't understand what a "console" is in this context.

I did try, in XP, clicking on "Run" and entering "D: md5sum -c file.iso.md5" That didn't do anything.

So, I rebooted the system and did the disk check from the Ubuntu menu.

It reported that "0 checksums failed", so I think the CD is OK.

Thanks,

Tom

---

### Post by xyz on 2006-09-24
Sorry about that!
At the top of your screen, go to Application > Accessories > Terminal

But let's keep it simple for now. Did you burn the image with k3b?
I'm asking because ,before burning the image, it verifies if what you are going to burn on the CD has defects or not.
Am i making any sense?

---

### Post by souperdoo on 2006-09-24
> **xyz said:**
> Sorry about that!
At the top of your screen, go to Application > Accessories > Terminal

But let's keep it simple for now. Did you burn the image with k3b?
I'm asking because ,before burning the image, it verifies if what you are going to burn on the CD has defects or not.
Am i making any sense?

Hi - 

OK, I would have to reboot and let Ubuntu run before I could try the "Application > Accessories > Terminal" thing. I will try that, but it takes a long time to get there. Might be an hour before I get back here. [-o< 

I used CDBurnerXP Pro 3 to burn the CD.

thanks,

Tom

---

### Post by souperdoo on 2006-09-24
> **souperdoo said:**
> Hi - 

OK, I would have to reboot and let Ubuntu run before I could try the "Application > Accessories > Terminal" thing. I will try that, but it takes a long time to get there. Might be an hour before I get back here. [-o< 

I used CDBurnerXP Pro 3 to burn the CD.

thanks,

Tom

OK, I got to the Terminal.

When I ran this command: md5sum -c file.iso.md5

I got "No such file or directory"

I tired different permutations of that command; none of them gave me anything except "No such file or directory".

Tom

---

### Post by bulldog on 2006-09-24
Well your RAM is the limit to use the live cd.

You could concider the 'alternate cd' which uses a textbased install instead of a GUI.
It uses less resources so the install should be a lot quicker.

And you could even concider to **not** install ubuntu but xubuntu instead which will perform a little better on your system

The live cd will install only Ubuntu,but the alternate has all the flavors on it if I'm well informed,so it's wurth to download the alternate cd.

---

### Post by souperdoo on 2006-09-24
> **bulldog said:**
> Well your RAM is the limit to use the live cd.

<snip>

The live cd will install only Ubuntu,but the alternate has all the flavors on it if I'm well informed,so it's wurth to download the alternate cd.

Thanks for that tip - I'll try the alternate and see if it works better.

thanks,

Tom

---

### Post by souperdoo on 2006-10-13
Thanks - 

the alternate cd approach worked just fine.

Now I can't get the wireless card to work. Off to search for a solution.

tom

---

