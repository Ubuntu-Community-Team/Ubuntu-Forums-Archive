---
title: "Firefox &amp; TB in Linux &amp; Win use same profile?"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by Danny Boy on 2006-04-22
I already have a FAT32 parition automounted at boot in Breezy. Can I some how make Firefox and Thunderbird access the same profile and settings in both windows & linux by copying a few files to the partition? 

The reason why I ask is I've downloaded my mail in TB a couple time in Win and need it in Linux, I normally don't leave mail on the server due to webspace restrictions. Rebooting into Win is a time waster and PIA. :p

My thinking is since it's the same program on in both OS they should be able to read each others settings and stuff like that.

Thanks in advance for your ideas, 

Dan

---

### Post by PriceChild on 2006-04-22
For firefox, i use a little wonder extension called "Own Area"

I signed up early so its free for me, but you'd probably have to pay.

It basically stored all your bookmarks and settings in a central database, so you can log on anywhere with your username and p/w to retrieve them.

Don't know how to help with thunderbird though sorry.

check out glaxstar.com for ownarea.

Pricey

---

### Post by Kimm on 2006-04-22
If you have a spare FAT32 partion you could probably make it work.
If you install the windows thunderbird there and have the partion mount at bootup, you might be able to create symlinks to your Linux profile, thus using the same data, all wound be stored on the FAT32 disk.

But you need to fix file prvelages, but you could have a script run when Ubuntu starts, doing something like:

chown -R <user>:<user> <path>

I guess that could work...

Edit:
Or if you can get the windows thunderbird to store the files on the FAT32 disks, you might be able to use the Thunderbird profile directory as a mountpoint...

---

### Post by AndyCooll on 2006-04-22
This isn't as straightforward as you might think, and I'm not sure it's actually possible (for Firefox anyway, not sure about Thunderbird). 

The problem is that the Linux and Windows versions of Firefox are fundamentally different. And your profile contains more than just your bookmarks. It also includes programming language about your extensions, your layout of FF etc. And FF interacts with each OS differently to make your extensions work or achieve the layout you set. You can tell this simply by the fact that if you download a plugin you usually have to select your OS version. 

Even within the same version of FF there are differences between the Linux and Windows versions. The standard "Preferences" is found in a different place depending on whether it's Linux (edit-->preferences) or Windows (tools-->preferences).   

:cool:

---

### Post by tuxcantfly on 2006-04-22
for thunderbird

**ln -s /media/windows/Documents\ and\ Settings/yourusername/Application\ Data/Thunderbird**
**rm -rf .mozilla-thunderbird**
**mv Thunderbird .mozilla-thunderbird**

/media/windows is assumed to be the mountpoint for the fat32 partition, change it accordingly

for firefox

**ln -s /media/windows/Documents\ and\ Settings/yourusername/Application\ Data/Mozilla**
**rm -rf .mozilla**
**mv Mozilla .mozilla**

warning: this will get rid of all your existing bookmarks and mail stored on the ubuntu partition!

---

### Post by tuxcantfly on 2006-04-22
basically, the bookmarks and mail will be transferred over, but the plugins (like flash and acrobat) you'll have to manually reinstall. Most extensions should also work.

---

### Post by Danny Boy on 2006-04-22
[QUOTE=tuxcantfly]basically, the bookmarks and mail will be transferred over, but the plugins (like flash and acrobat) you'll have to manually reinstall. Most extensions should also work.[/QUOTE]

thank you very much! I'm not to worried about extensions. I have the fat partion mounted in media/windows my windows system (ntfs) is mounted to /media/windows/nfts so this is what I entered:
```
ln -s /media/windows/nfts/Documents\ and\ Settings/dan/Application\ Data/Thunderbird
```

I'ml having a problem though:

```
dan@DeuceCoupe:~$ rm .mozilla-thunderbird
rm: cannot remove `.mozilla-thunderbird': Is a directory

```

---

### Post by Kimm on 2006-04-23
rm .mozilla-thunderbird

should be

rm -rf .mozilla-thunderbird

---

