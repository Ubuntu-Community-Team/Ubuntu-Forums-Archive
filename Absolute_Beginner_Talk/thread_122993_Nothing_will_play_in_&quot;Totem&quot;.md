---
title: "Nothing will play in &quot;Totem&quot;"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by Rock Lobstah on 2006-01-28
Well, "Totem", the default media player that came with my Ubuntu won't play anything.

No matter what I try it just says..

"Totem could not play '_________'.

There were no decoders found to handle the stream, you might need to install the corresponding plugins"

But how do I know what to install?

Thanks.

---

### Post by dueY on 2006-01-28
Try getting the w32codecs.  They might be in backports.

---

### Post by Rock Lobstah on 2006-01-28
[QUOTE=dueY]Try getting the w32codecs.  They might be in backports.[/QUOTE]

Linky? Can't find them.

Well, I take that back. I found a download, but the archiver didn't support the file type. (.rpm?)

---

### Post by Patrick-Ruff on 2006-01-28
yeah I was just about to ask you to clarify.

---

### Post by Madpilot on 2006-01-28
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) has info on enabling all the formats in Ubuntu, in ways Totem can use. w32codecs is in the section called "The Codecs" there.

Note that Ubuntu doesn't natively use RPMs, but .deb files for installing. 99% of the time you'll never even handle the .deb directly but use Add Applications or Synaptic to do the installation from Ubuntu's online repositories.

The w32codecs are one of the few exceptions to that rule, because Ubuntu can't legally include them in their repos or on the CDs.

---

### Post by Rock Lobstah on 2006-01-29
Why won't my archiver support .deb?

[http://img53.imageshack.us/img53/6158/deb5bk.jpg](http://img53.imageshack.us/img53/6158/deb5bk.jpg)

---

### Post by psomas on 2006-01-29
get automatix...it will install all the codecs you need and many more....
you'll find it in the 'Customization Tips & Tricks' section of the form... ;)

---

### Post by dueY on 2006-01-29
[QUOTE=Rock Lobstah]Why won't my archiver support .deb?

[http://img53.imageshack.us/img53/6158/deb5bk.jpg](http://img53.imageshack.us/img53/6158/deb5bk.jpg)[/QUOTE]

Go to the directory the file is in with terminal and type this:
```
sudo dpkg -i [file.deb]
```

---

### Post by Rock Lobstah on 2006-01-29
> **psomas]get automatix...it will install all the codecs you need and many more....
you'll find it in the 'Customization Tips & Tricks' section of the form...  said:**
> 

It says it's not supported on AMD64s (I have a 3700) :(

[QUOTE=dueY]Go to the directory the file is in with terminal and type this:
```
sudo dpkg -i [file.deb]
```

"Go to the directory the file is in?"

I tryed to use "open with Archive Manager".. so is it even really saved to my computer?

---

### Post by psomas on 2006-01-29
[QUOTE=Rock Lobstah]It says it's not supported on AMD64s (I have a 3700) :(



"Go to the directory the file is in?"

I tryed to use "open with Archive Manager".. so is it even really saved to my computer?[/QUOTE]
you can either try the chroot solution,and get a 32bit version of ubuntu inside the 64bit(so you can install automatix and everything will be much simpler) 
or open the terminal and type:
cd [the directory,where you've downloaded the file]
sudo dpkg -i [filename.deb]

(if you want to try chroot, search in the forum and you'll find a how-to)

---

### Post by dueY on 2006-01-29
[QUOTE=Rock Lobstah]

"Go to the directory the file is in?"

[/QUOTE]

Use the terminal and the cd command.

---

### Post by Rock Lobstah on 2006-01-29
[QUOTE=psomas]you can either try the chroot solution,and get a 32bit version of ubuntu inside the 64bit(so you can install automatix and everything will be much simpler) 
or open the terminal and type:
cd [the directory,where you've downloaded the file]
sudo dpkg -i [filename.deb]

(if you want to try chroot, search in the forum and you'll find a how-to)[/QUOTE]

```
********:cd ~/Desktop
********:~/Desktop$ sudo dpkg -i w32codecs_20050412-0.0_i386.deb
Password:
dpkg: error processing w32codecs_20050412-0.0_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 w32codecs_20050412-0.0_i386.deb
```

:( ?

---

