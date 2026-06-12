---
title: "Skins - why don't they show up?"
date: 2005-08-18
forum: Absolute Beginner Talk
---

### Post by mikeb on 2005-08-18
I've download skins for xmms and placed them in the ~/.xmms/Skins directory, however, when I restart xmms, the new skins don't show up in the "skins browser" window. I also copied the skins (all .bmp files) to the ~/.bmp/Skins directory and they don't show up there either.

What am I doing wrong? How can I fix this? Thanks.

---

### Post by mikeb on 2005-08-18
Certainly some _must_ have done this successfully. How about some help please?

---

### Post by xmastree on 2005-08-18
Basically, if you download a theme called foo, when you extract all the BMPs etc. they should end up in .xmms/Skins/foo/

Where do you find good skins?

---

### Post by xmastree on 2005-08-18
From [this page](http://www.neowin.net/forum/lofiversion/index.php/t136494.html) > 2. XMMS creates a hidden directory in your account root folder. For the superuser this would generally be /root/.xmms
For a normal user with a home directory /home/harry it would mostly be /home/harry/.xmms

3. This folder in turn would have a folder called Skins ( /root/.xmms/Skins ). Inside this folder you could copy all your Winamp skins and all of them would work with XMMS.

Note : The skins have to be in .zip format. The newer Winamp skins are available in .wsz format, rename these to .zip before using them with XMMS.

I haven't tried that approach yet.

---

### Post by mikeb on 2005-08-18
[QUOTE=xmastree]Basically, if you download a theme called foo, when you extract all the BMPs etc. they should end up in .xmms/Skins/foo/

Where do you find good skins?[/QUOTE]

If you go here: [http://www.gnome-look.org/](http://www.gnome-look.org/) you will find xmms skins, wallpaper, themes, everything you need to make gnome look like you want.

---

### Post by mikeb on 2005-08-18
[QUOTE=xmastree]From [this page](http://www.neowin.net/forum/lofiversion/index.php/t136494.html) 

I haven't tried that approach yet.[/QUOTE]

The skins were, of course, downloaded in a zip archive. When I expanded the archive, it was filled with images with .bmp extension and a few text files that seems to be instructions used by xmms. I guess I could try renaming the *.bmp to *.zip and see what happens, but I still find this strange.

Anyhow thanks for your help.

---

### Post by xmastree on 2005-08-18
> The skins were, of course, downloaded in a zip archiveJust put the zip file in .xmms/Skins
It really is that simple. xmms will unzip it as needed.

I just tried getting some from winamp.com

So long as you stick to the .wsz files, put the file in Skins/ and remane it .zip and they works just fine.

---

### Post by mikeb on 2005-08-18
[QUOTE=xmastree]Just put the zip file in .xmms/Skins
It really is that simple. xmms will unzip it as needed.

I just tried getting some from winamp.com

So long as you stick to the .wsz files, put the file in Skins/ and remane it .zip and they works just fine.[/QUOTE]


Many thanks for your kind help!

---

