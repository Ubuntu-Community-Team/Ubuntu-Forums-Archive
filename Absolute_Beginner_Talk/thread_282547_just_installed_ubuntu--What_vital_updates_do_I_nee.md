---
title: "just installed ubuntu--What vital updates do I need?"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by bugalugs on 2006-10-22
Help, I have just installed ubuntu and I know I need to download to install vital program bits and pieces.  The problem is I am limited to 500meg before they start charging me 15cents a meg.  What installs are vital to read media files ie music and dvds, and what do i need to recognise usb flash drives as I cant currently access my flask disk(could be something to do with ntfs format?) I would also like to transfer my music, media files and word processer files (and maybe some other stuff) how can I do this? I tryed to mount windows partition which is observable as 196.1 GB volume but it wont allow it.:(

---

### Post by d3v1ant_0n3 on 2006-10-22
Ok, a good place to start for getting all the media related things you'll need is automatix...it's a program that will allow you to easily download and installed many popular programs and utilities etc that aren't supplied with ubuntu...you can find it [here](http://www.getautomatix.com/) 

Opinions are divided about Automatix-for newcomers it's great, because it makes life much easier, but by the same token, learning how to actually install all the components manually is a great learning experience. Me, I loved it:p 

[This](http://www.psychocats.net/ubuntu/mountwindows) link should help you with mounting your windows volume...aysiu does some wonderful howto's- They've helped me out greatly!

As to how much of the updates you should download, well I'm not sure- I doubt there's 500mb of updates, although this really depends on how old the disc you used to install is, or if you'r etrying to upgrade to edgy, for instance.

---

### Post by reacocard on 2006-10-22
For your Windows partition and the flash drive, you need to install the ntfs-progs package to add support for reading ntfs. If you want to be able to write to that partition/drive, you'll need something like ntfs-3g (search the forums for details). As for media, see [this wiki page]("https://help.ubuntu.com/community/RestrictedFormats").

---

### Post by bugalugs on 2006-10-22
what is 'edgy' automatix says i need it to install codecs

---

### Post by IMC_TKB on 2006-10-22
when i try to install, it says to add things to the Sources.list. when i do linux says its a read only file and wont let me edit it

---

### Post by bugalugs on 2006-10-22
Automatix is now on the sys tools menu, remember, I have the raw out of box ubuntu, I dont have any add ons.  how do i get 'edgy'

---

### Post by Madpilot on 2006-10-22
I'd recommend avoiding Automatix, it's too good at breaking Ubuntu installs.

Head for [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats") to get MP3/WMV/other media stuff working, and explore the rest of the Ubuntu documentation for other issues - see the linkes in my sig just below.

---

### Post by Qrk on 2006-10-22
Edgy is the next release of Ubuntu, it is scheduled for next week. (This will be a more than 500 meg download, so you may not wish to upgrade)



Editing your sources.list
To edit a root owned file, you need to use sudo:

```
sudo gedit /etc/apt/sources.list
```


[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by IMC_TKB on 2006-10-23
i used sudo, and it opened the sources.list but when i tried to save it wouldnt let me,

---

### Post by tubasoldier on 2006-10-23
> **Madpilot said:**
> I'd recommend avoiding Automatix, it's too good at breaking Ubuntu installs.

Head for [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats") to get MP3/WMV/other media stuff working, and explore the rest of the Ubuntu documentation for other issues - see the linkes in my sig just below.

I personally found the Ubuntu Guide more helpful. [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

