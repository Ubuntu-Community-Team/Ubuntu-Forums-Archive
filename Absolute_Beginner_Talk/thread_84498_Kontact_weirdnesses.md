---
title: "Kontact weirdnesses"
date: 2005-10-31
forum: Absolute Beginner Talk
---

### Post by editrix on 2005-10-31
I started with Ubuntu, then installed Kubuntu for the KDE apps. At first, I ran Kontact under Ubuntu/Gnome, then switched to Ubuntu/KDE using GDM, then entirely to Kubuntu, using KDM. Don't know if this swtiching caused the problems, but: 

When Kontact starts, or if I do anything that takes time, I still see the Gnome wheel, rather than the KDE bouncing whatever.

As well, the Contacts/Address book has multiple entries for the same person, but if I delete one, they all go.

My std.vcf files are breeding all by themselves. Last time I looked I had 5, today I have 7:

/home/wolfgang/.kde/share/apps/kabc/std.vcf
/home/wolfgang/.kde/share/apps/kabc/std.vcf_3
/home/wolfgang/.kde/share/apps/kabc/std.vcf_1
/home/wolfgang/.kde/share/apps/kabc/std.vcf_4
/home/wolfgang/.kde/share/apps/kabc/std.vcf_2
/home/wolfgang/.kde/share/apps/kabc/std.vcf_5
/home/wolfgang/.kde/share/apps/kabc/std.vcf_6

Today I tried deleting (by renaming) the extras, but then Kontact crashed completely--i.e., won't open at all. And renaming them to the old names didn't help :( 

I have the main list of contacts, plus 2 distribution lists. One DL shows up as a file in KDE Resources, the other doesn't. Don't know if that's relevant. 

The main list of contacts, other than the duplications, seems to work fine. But if I hit Select in the composer window, I get many, many repetitions of the same name, all with different email addresses taken from other names.

The std files seem to be identical. They all begin as one would expect, but then about 6 names down I get this: (I have fudged them to protect others' privacy)
BEGIN:VCARD
CATEGORIES:List of Emails
CLASS:PUBLIC
EMAIL;TYPE=PREF:XXzadam@sympatico.ca
EMAIL:XXWritten@shaw.ca
EMAIL:Burgess <XXoton@magma.ca>
EMAIL:Glenn <XXntact_aglenn@hotmail.com>
EMAIL:] <XXaker@analecta.com>
EMAIL:XXldry@shaw.ca

it goes on for what looks like every person, ending with:

EMAIL:XXcchiato <XXtchvee@infinet.net>
EMAIL:XXscosi <XXviscosi@adelphia.net>
FN:XXamitz, Elizabeth
N:XXamitz;Elizabeth;;;
REV:2005-10-28T13:25:38Z
UID:6ZhB1UWth7
VERSION:3.0
END:VCARD

And then resumes normal-type entries for the rest of the file.

Note, too, that that 1st entry in this weird section
EMAIL;TYPE=PREF:XXzadam@sympatico.ca 
is the same person as the last one(s) 
FN:XXamitz, Elizabeth
N:XXamitz;Elizabeth;;;

Now that it seems I can't start Kontact at all, I'm reluctant to try anything else. Any advice would be most appreciated.

---

### Post by Manny C on 2005-10-31
The fact that you have this many files in kabc subfolder is normal. This is what I have:
```
 ls ~/.kde/share/apps/kabc/
lock/      std.vcf    std.vcf_1  std.vcf_2  std.vcf_3  std.vcf_4  std.vcf_5  std.vcf_6  std.vcf_7
```

What is in the lock/ subfolder of kabc?

---

### Post by editrix on 2005-10-31
Hi Manny:

Thanks for being so quick.

[QUOTE=Manny C]The fact that you have this many files in kabc subfolder is normal. [/QUOTE]

Okay, but you have to admit it looks weird :-)

> What is in the lock/ subfolder of kabc?

It's empty.

BTW, I discovered the cause--but not the cure--for part of my problem. The Kontact icon that sits in the panel belongs to root (how did that happen?) but I can open Kontact from the menu.

Does this mean I have 2 versions of Kontact configured, or just that the icon/link is owned by root?

---

### Post by Manny C on 2005-10-31
The fact that root owns the icon is also not suprising. In fact I have the same here. But I don't have these problems. Ok...try the following:
```
 sudo dpkg-reconfigure kontact korganizer kaddressbook kdepim 
```

You may not have the last package installed (which isn't really a huge problem as it is a metapackage).

---

### Post by editrix on 2005-11-01
Hi Manny:

Well, I'm making progress.

The icon now loads Kontact, but I'm still getting the Gnome wheel instead of the bouncing KDE thingy (I mention this only because it may somehow relate to the other problems).

However, I still have all those duplicates, and when I delete one, the others go as well. I noticed that, when I deleted one, std.vcf and std.vcf2 had the new modified date, the others didn't. So, what are they? Backup files? I used one to reinstate the deleted address, anyway.

I hope this doesn't sound like too petty a problem. I'm always concerned that what looks trivial now will turn out to be major later on. Also, as a trained librarian, the messy input goes against the grain.

Thanks for your help.

---

