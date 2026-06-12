---
title: "envy, maximum resolution, and what is beryl?"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by nicklikesfire on 2008-01-06
Hello,

So I debated for a while about asking this, because I'm sure the answer is out there somewhere. After numerous tries, and half a dozen reinstalls, I've run out of ideas.

How do I go about increasing my screen resolution?

I'm running an ATI x1650 pro graphics card, Acer 22 inch 2216w monitor.

I ran Envy, and I have no idea if it worked or not. I installed compiz-fusion, but I have no idea what it does, and I'm not sure what beryl is. Yes, I am at the very lowest rung of anyone running ubuntu, in terms of skills.

If anyone can help me get my resolution up to 1680 x 1050, that would be great. I'm absolutely new at this, so unfortunately I really need step by step instructions. If there's other info you need before figuring this out, please let me know.

Thanks so much for anything anyone can tell me.

-Nick

---

### Post by wheredidrealitygo on 2008-01-06
Beryl and Compiz-fusion are both window decorators, they can do advanced desktop effects like the cube, wobbly windows, etc. The default window decorator in Ubuntu is called Metacity.

Compiz-fusion is technically newer, as it is a combination of Compiz and Beryl.

[http://www.compiz-fusion.org/]("http://www.compiz-fusion.org/") for more info on Compiz-fusion.

---

### Post by nicklikesfire on 2008-01-06
> **wheredidrealitygo said:**
> Beryl and Compiz-fusion are both window decorators, they can do advanced desktop effects like the cube, wobbly windows, etc. The default window decorator in Ubuntu is called Metacity.

Compiz-fusion is technically newer, as it is a combination of Compiz and Beryl.

[http://www.compiz-fusion.org/]("http://www.compiz-fusion.org/") for more info on Compiz-fusion.

Cool, yeah, I've been there, and installed compiz-fusion. I guess that means that I don't need beryl?

Any help on the resolution thing? Checking if Envy worked?

---

### Post by wheredidrealitygo on 2008-01-06
If you've installed Compiz-fusion then no you don't need Beryl.

Instead of using Envy, have you tried downloading and installing ATI driver directly from the ATI website?

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.443.1-x86.x86_64.run]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.443.1-x86.x86_64.run")

That is a direct link to the 32-bit installer of the ATI driver, I would read the documentation that accompanies it on the website ([http://ati.amd.com/support/driver.html]("http://ati.amd.com/support/driver.html")), as I've only installed an ATI driver once or twice, but when you download the driver you should be able to right click it, go to properties, make sure under the permissions tab that it's "executable", and then execute it either from a terminal with ```
sudo sh ati-driver-installer-8.443.1-x86.x86_64.run
``` or you may be able to do it graphically, by double-clicking it and clicking "run".

You can shorten the code when you navigate to the directory by doing ```
sudo sh ati-driv*.run
``` which will fill in the blanks on it's own.

---

### Post by nicklikesfire on 2008-01-07
Found a solution here: [http://ubuntuforums.org/showthread.php?p=4092316#post4092316](http://ubuntuforums.org/showthread.php?p=4092316#post4092316)

Thanks for all the help!

---

