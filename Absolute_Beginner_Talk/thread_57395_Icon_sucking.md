---
title: "Icon sucking"
date: 2005-08-16
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-08-16
Anyone know of an app that can be used to suck icons out of Linux? Prefereably one that can scan a complete filesystem, suck out icons and save them in a folder. Would be great if it can suck icons from Windows as well.

---

### Post by KingBahamut on 2005-08-16
Hmmmm....Put Linux Icons in Windows? 

This might be admireable.....best way to do that would be to take all the .xpm's out of /usr/share/pixmaps convert them to .ico's and then change away. 

Of course, your talking about using a Windows machine afterwards, in which case Id never support that. 

So , there you go. 

=)

---

### Post by dcraven on 2005-08-16
[QUOTE=GrootBrak]Anyone know of an app that can be used to suck icons out of Linux? Prefereably one that can scan a complete filesystem, suck out icons and save them in a folder. Would be great if it can suck icons from Windows as well.[/QUOTE]

Not that I'm aware of. The only way I could see that an application could identify icons is by location as icons, on Linux anyways, are typically PNG or SVG files just like any other image or vector graphic on the filesystem.

Normally, icons are kept in /usr/share/icons/ under directories named after the icon theme. SVG iconsets are kept in a subdirectory there called "scalable" since they can be scaled to any size without losing sharpness, and bitmap (PNG) icons are kept in a subdirectory according to their sizes (eg. 32x32).

A simple script can be used to scrape the /usr/share/icons/ directory and its subdirectories for all images of these formats. Here is an example in Python that may need some adjustment to do what you want, but it's a start. It will put all files of extension .png and .svg in the current directory. A caveat is that if the file already exists, it is overwritten. This is a problem given that, for example, the firefox icon is named the same thing in each theme. Your requirements are a little vague as to how this should be handled, so I leave you with the script to edit it as you see fit.

```

#!/usr/bin/env python

import os,shutil

for root, dirs, files in os.walk('/usr/share/icons/'):
    for file in files:
        path = os.path.join(root, file)
        print path
        if path.endswith('png') or path.endswith('svg'):
            shutil.copyfile(path, './%s' % file)

```

Cheers,
~djc

EDIT: As was pointed out in the post above mine, there are other locations and formats that do exist. Keep that in mind when scraping the filesystem for all icons.

---

### Post by dcraven on 2005-08-16
[QUOTE=KingBahamut]...best way to do that would be to take all the .xpm's out of /usr/share/pixmaps convert them to .ico's and then change away. 
[/QUOTE]

You are right.. There are lots of icons there too! How are these things organized? By the looks of it, in /usr/share/pixmaps there are the default, GNOME specific icons. Some of these have a png and xpm version in that directory. So I suppose in the /usr/share/icons directory there are only third party themed icons? Although some of those themes (eg. hicolor) I think also come out of the box with GNOME.

I'm confused now.

~djc

---

### Post by KingBahamut on 2005-08-16
The logic of the data schema for unix/linux makes sense only after youve looked at it day in and day out for a number of years dcraven. 

Trust me, I know.

---

### Post by GrootBrak on 2005-08-17
[QUOTE=KingBahamut]The logic of the data schema for unix/linux makes sense only after youve looked at it day in and day out for a number of years dcraven. 

Trust me, I know.[/QUOTE]
 Darn GPRS access went down before I posted. Will reply later, I'm still at work now.

---

### Post by GrootBrak on 2005-08-17
[QUOTE=GrootBrak]Darn GPRS access went down before I posted. Will reply later, I'm still at work now.[/QUOTE]
 > Hmmmm....Put Linux Icons in Windows? 

The other way around! The DLL's in Windowy programs held some great icons, I want some of those. Even if it means logging in to windows, extract icons, save to a file and use them in Linux. Problem is windows use .ico files.

Another thing that propably confuse me, the Linux icons is often marked as .png. Now in the "other" world, .png is for portable network graphics, meaning to me, lossless pictures. Is this the same thing? If that is true, can I convert any small picture to an .png and use it as an icon? (unlike the other that has to be .ico?)

>  SVG iconsets are kept in a subdirectory there called "scalable"
I don't have such a directory, thanks for the code. I know very little programming, so "tweaking" would be a bit of an overstatement.

> I'm confused now.
join the club. But thanks for the tip to look in there. I never realised the other folders would hold icons. (Never bothered to look there...) I have the notion that icons are created in the equivalent of dll's. For instance, many games and apps in universe don't have any icons associated, nor do they link to the menu. Smeg won't add it either as a command. Every time I re-open smeg, it won't show any changes

---

### Post by xmastree on 2005-08-17
[QUOTE=GrootBrak] can I convert any small picture to an .png and use it as an icon?[/QUOTE]Best way to find out is try it. You may be pleased with the result.  :) 

32 x 32 is a good size to aim for, transparency works, too.

This is a PNG:

[IMG]http://www.xmastree.34sp.com/ubuntu/xnshot.png[/IMG]


> The other way around! The DLL's in Windowy programs held some great icons, I want some of those. Even if it means logging in to windows, extract icons, save to a file and use them in Linux. Problem is windows use .ico files.

One way I can think of, although it's a complete PITA, is to make shortcuts on your Win desktop, (a plain background would help) using the icons you like (do them all at once), then take a screenshot, and one by one cut the icons from that and paste into a new 32x32 file then save it as a PNG.

---

### Post by cwaldbieser on 2005-08-17
There are lots of demoware/shareware programs for Windows you can use to convert .ico files to other graphic file formats.  Just google for "Icon Editor" or "ICO converter".

In *NIX, icons tend to be in PNG (portable network graphics) and XPM format, but they are sometimes in other graphics format as well.  So if you can just convert your ICO files to PNGs, you should probably be set.

---

### Post by GrootBrak on 2005-08-18
[QUOTE=cwaldbieser]There are lots of demoware/shareware programs for Windows you can use to convert .ico files to other graphic file formats.  Just google for "Icon Editor" or "ICO converter".

In *NIX, icons tend to be in PNG (portable network graphics) and XPM format, but they are sometimes in other graphics format as well.  So if you can just convert your ICO files to PNGs, you should probably be set.[/QUOTE]
 Thanx for all the info, will try it out real soon, I hope! 

Hey cwalbieser, you seen my avatar? I love bugs like you!!! (That is, like in eating them!) Next thing is getting my avatar as an icon...

---

### Post by Cordate on 2005-12-18
I brought some of my off-the-net .ico icons that I used to use under windows with me when I moved to Ubuntu, and they work fine here :) No need to convert them unless you want to do graphic work on them.

---

