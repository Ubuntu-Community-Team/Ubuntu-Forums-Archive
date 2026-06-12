---
title: "Unable to install 6.10 64bit and 32bit versions"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Zylos on 2007-03-11
I posted this in the 64bit forums, when I thought I was in the beginners forums.  I apologize for the double posts.

I'm a Linix/Unix noob here so please bare with me.

I have downloaded and burned both the 64bit version and 32bit version (AMD 64 3700+) of Ubuntu. The 64bit version and 32bit version will bring up the menu. (install with GUI or Safe GUI, memory test etc...) but with the 64bit version, I get the the first 5 screenshots that is on this page.

[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

However, Once I hit <OK> on the 5th SS, instead of all the information that comes up on the 6th shot, i just get a blank black screen with the cursor in the upper left hand corner. i've attempted to type sudo dpkg-reconfigure xserver-xorg but nothing happenes. I'm able to type stuff, but nothing happens. If i just press enter, it will bring up the splash screen, and ask me to take the CD out of the CD Tray.

The 32bit version acts a little differently. It brings up the same menu, and it doesnt matter which install i attempt, it brings up the ubuntu splash screen with the progress bar (unlike the 64bit version, this splash screen is in color). Then it has a solid green line (1 pixel in height) run straight across the screen under the progress bar.

I'm at a loss here. I'm not sure what to do. Here are my computer specs

Windows XP SP2
AMD 64bit 3700+
2gigs of Corsair XMS ram
ATI x850 XT
Sound blaster audigy 2
I'm using the VGA port on my video card instead of the DVI port.
19" Viewsonic LCD monitor.

The links I used to get both the 64bit version and 32bit version are as follows:

[http://www.gtlib.gatech.edu/pub/ubun...nate-amd64.iso](http://www.gtlib.gatech.edu/pub/ubun...nate-amd64.iso)

[http://www.gtlib.gatech.edu/pub/ubun...rnate-i386.iso](http://www.gtlib.gatech.edu/pub/ubun...rnate-i386.iso)

Any help would be appreciated.

---

### Post by Kateikyoushi on 2007-03-11
It is because of your video card, you can solve it by following these instructions. [LINK]("http://www.ubuntuforums.org/showpost.php?p=2193083&postcount=3")

---

### Post by mrmonday on 2007-03-11
Choose the option on the menu to check the cd, does it give any errors?

Try downloading the iso's form [here]("http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download")

It gives clear instructions on which one to go for, and how to install, troubleshooting etc.

---

### Post by Zylos on 2007-03-11
I will try that once I get home.  I'll let you know if that fixes my issue.

Thanks for the reply and the help :)

---

### Post by Zylos on 2007-03-11
> **mrmonday said:**
> Choose the option on the menu to check the cd, does it give any errors?

Try downloading the iso's form [here]("http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download")

It gives clear instructions on which one to go for, and how to install, troubleshooting etc.

Thats where I got them from (i chose the Georgia link to down load them)

---

### Post by Zylos on 2007-03-11
> **Kateikyoushi said:**
> It is because of your video card, you can solve it by following these instructions. [LINK]("http://www.ubuntuforums.org/showpost.php?p=2193083&postcount=3")

That worked Katei :)  ty for your help.

---

