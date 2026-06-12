---
title: "web fonts and ubuntu"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by -Ghost9- on 2007-07-21
I tried doing a search but couldn't find what i was looking for. I notice that in ff in ubuntu some webpages get messed up. I know this is because ubuntu is rendering the fonts differently, but I'm wondering if there isn't a font pack or something to download so that web pages show up as they were designed to...

So is there a way to fix it?

---

### Post by mlentink on 2007-07-21
Are you referring to the Microsoft Core Fonts? Verdana et al.?

Those are easlily installed with:
```
$sudo apt-get install msttcorefonts
```
Please make sure you have universe repo's enabled

---

### Post by Steve1961 on 2007-07-21
> **-Ghost9- said:**
> I tried doing a search but couldn't find what i was looking for. I notice that in ff in ubuntu some webpages get messed up. I know this is because ubuntu is rendering the fonts differently, but I'm wondering if there isn't a font pack or something to download so that web pages show up as they were designed to...

So is there a way to fix it?


sudo apt-get install msttcorefonts

Sorry mlentink, looks like we posted at the same time

---

### Post by -Ghost9- on 2007-07-21
> **mlentink said:**
> Are you referring to the Microsoft Core Fonts? Verdana et al.?

Those are easlily installed with:
```
$sudo apt-get install msttcorefonts
```
Please make sure you have universe repo's enabled

Is it supposed to use that $ symbol?
it worked without it but i got an error with it.

---

### Post by mlentink on 2007-07-21
> **-Ghost9- said:**
> Is it supposed to use that $ symbol?
it worked without it but i got an error with it.
No. Sorry, The $ was meant to represent your prompt, you don't type it in.
What error did you get? this should work if you have universe repositories enabled

---

### Post by -Ghost9- on 2007-07-21
> **mlentink said:**
> No. Sorry, The $ was meant to represent your prompt, you don't type it in.
What error did you get? this should work if you have universe repositories enabled

it just said this:
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

but i got it to work and now my webpages look correct. Thanks a lot! I appreciate it.

---

### Post by mlentink on 2007-07-21
> **-Ghost9- said:**
> but i got it to work and now my webpages look correct. Thanks a lot! I appreciate it.

Did you use 'sudo'? 
Anyhow, glad it works.

---

### Post by crimesaucer on 2007-07-21
Now here is another way to have smooth fonts on your notepad app (don't copy and paste from the wiki page because the quotes are wrong, copy and paste the code I wrote below): [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_smooth_fonts](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_smooth_fonts)

just use your Terminal to open this file with this command:

```
gedit ~/.fonts.conf
```


Just copy and paste the part below, over the entire page, then save it:


```

<?xml version="1.0" ?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
<edit name="autohint" mode="assign">
<bool>true</bool>
</edit>
</match>
</fontconfig>

```

your .fonts.conf should look exactly like the part above.


...also...

I don't know about ubuntu, but in xubuntu, I use these settings in my User Interface Preferences:

You will make these checked: 

"Use anti-aliasing for fonts"
"Use hinting"
 "Use sub-pixel hinting".

you can also adjust the RGB and Slight, Medium, and Full settings to display fonts differently.


Most of those settings above will give you smoother fonts in your menubars of all apps like Firefox, and in your ubuntu panels.

---

### Post by -Ghost9- on 2007-07-21
> **mlentink said:**
> Did you use 'sudo'? 
Anyhow, glad it works.

yeah. i used the command line you gave me without the $

---

