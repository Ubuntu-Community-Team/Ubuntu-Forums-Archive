---
title: "UBUNTU/Debian: Intsalling Inckscape - any help appreciated."
date: 2008-12-17
forum: Art &amp; Design
---

### Post by Paulzy on 2008-12-17
Hi Guys

Trying to install Inscape for Hardy Hedon Ubuntu. The distribution file is inkscape-0.46.tar.bz2 for debian packages. Niether package manager under Ubuntu 8.0.41 HH LTS has Inkscape in it's library, so I was left to install/built manually.

I've been pulling my hair out. I've been trying to compile inkscape (the newest version available as of Nov '08) but I keep on running into seemingly infinite dependencies. I've downloaded about 70MB worth of GTK libraries, but each time one library requires another, which requires another, which requires one where that library's latest available version is apparently incompatible with one of the previous ones... so I start again. This is happening over and over, I just never seem able to get the right combinations of versions that will live with each other and eventually with the tip of the iceberg - inkscape itself.

Is there a guide / howto anywhere that lists the CORRECT versions of ALL required GTK libraries to get inkscape to compile? Since as far as I can determine, it will NOT (or one of its huge set of dependencies, if you try latest versions of the GTK libraries) compile - unless you have EXACTLY the right versions of GTK libraries - libraries that will allow inkscape to compile against them, BUT ALSO allows "each other" (as regards GTK libraries) to compile...

I just can't seem to find the right version mix... The inkscape compile guide as I understand it merely states that GTK dev libraries are required.

I'm really -really- stuck in version hell with this... fixing one incompatible library merely hatches two or other more incompatibilities "upstream" and sometimes "downstream" in the compile chain for a particular library - version incompatibilities are cascading up and down and I simply can't get the right "mix" to eventually be able to get inskscape to even start compliling. (I suspect if I do that, I'll just run into "inkscape itself" issues again...)

Anybody got ANY advice to give?

Nirvana would be a list of versions of GTK libraries (there apparently are dozens of versions available of each major component - glib, pango, atk etc. etc.!) that will allow inkscape to compile...

---

### Post by Samhain13 on 2008-12-17
Inkscape 0.46 should be available (in 8.04) through:

```
sudo apt-get install inkscape
```

---

### Post by Paulzy on 2008-12-18
> **Samhain13 said:**
> Inkscape 0.46 should be available (in 8.04) through:

```
sudo apt-get install inkscape
```

I thought I had tried this -- oh wait, no it was for one of the dependencies because I downloaded inkscape from their website mirror. That's why I didn't "apt-get" it. Thanks, after building about four of the libraries it seems installing via apt-get I only needed the ImageMagik 10 & it's depends. Thanks :popcorn:

Paul ):P

---

### Post by glotz on 2008-12-18
Welcome to the forums Paulzy! Glad your issue is solved. Now, it would be polite towards other users of these forums to mark this thread as solved. You can do it via the thread tools link at the top of the page. Also, if you found Samhain13's reply particularly useful, you could click the little yellow icon in his post's lower right corner to thank him. The package manager is your friend! Welcome to the land of the penguin! :)

---

