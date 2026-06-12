---
title: "d3a icons question"
date: 2005-01-31
forum: Art &amp; Design
---

### Post by Campitor on 2005-01-31
Hello all:

    I hope this is the place to ask this question...so here it goes.  I have been using the d3a theme with d3a icons.  It looks great, but some of the icons included in the theme are not working, specially the msword icon.  Application files such as mspowerpoint, msexcel are changed to the cool looking silver d3a icon, but my word files (which I regreatfully still have to use because I share a lot of files with windoze using people) still has the gnome icon.  Do I have to do something special in order to get this icon to change?

  I installed the theme using the GUI, but the icons I installed by unziping the tarball into my ~/.icons/ folder.  I imagine I can just copy the d3a msword icon over the gnome one, but I'm afraid I will destroy something.  

Thx for the help

Camp

---

### Post by bvc on 2005-01-31
They probably just need the right name. Look at the default or maybe
[http://users.ossm.org.mk/~tome/wp-uploads/Ewegant.tar.gz](http://users.ossm.org.mk/~tome/wp-uploads/Ewegant.tar.gz)
or
[http://gnome-look.org/index.php?xcontentmode=190](http://gnome-look.org/index.php?xcontentmode=190)

I'm not at home on linux to be able to look right now.

---

### Post by bvc on 2005-01-31
They probably just need the right name. Look at the default or maybe the icon theme here
[http://gnomesupport.org/forums/viewtopic.php?t=8515&highlight=icons](http://gnomesupport.org/forums/viewtopic.php?t=8515&highlight=icons)
or here
[http://gnome-look.org/index.php?xcontentmode=190](http://gnome-look.org/index.php?xcontentmode=190)

I'm not at home on linux to be able to look right now.

---

### Post by bvc on 2005-01-31
copy gnome-mime-application-msword.png to another place and name it gnome-mime-application-vnd.msword.png and put it back in the mimetypes dir.
log out and back in or killall nautilus or reset the icon theme.

does it work?

---

### Post by bvc on 2005-01-31
just checked....mine show up w/o any mods to the theme. wonder why yours doesn't?

---

### Post by Campitor on 2005-02-01
[QUOTE=bvc]just checked....mine show up w/o any mods to the theme. wonder why yours doesn't?[/QUOTE]


I modified the ~/.icons/d3a-icons/128x128/mimitypes file as you mentioned and still have problems with the *.doc files.  I've included a screenshot so you can see this.  I tried changing to a different icon theme, and apparently the problem is common to all icons...Word files show up in their original format.  So this leads me to believe that it is something related to my gnome or nautilus set up.

[IMG]Screenshot.png[/IMG]

I'm not sure how to post  the screenshot, but I attached the file.

Thanks for the help

Camp.

---

### Post by Campitor on 2005-02-01
I think I just fixed the problem.  For some reason, my *.doc files are listed in nautilus as: vnd-ms-word files, and the d3a icons are set up as:  vnd-msword files.  So I just added a little hyphen (-) to the icon definition, and "presto" I have the icons I needed.  Thanks for paying attention to my inquiry, and congrats on some fantastic Icons.  Do you know if you're planning to include icons for Abiword and Gnumeric?  

Campitor

---

### Post by bvc on 2005-02-01
glad it's fixed!

they're not my icons, I only ported them from windows/iconpackager. So no, it's done.

Oh, there's a kde version as well. There's a lot of other goodies at the creators (Milo) website. Links are at the d3a icons post on gnome-look.

---

### Post by knappen on 2005-02-02
I had the same problem but I had to add vnd as well. The hyphen was also missing.

---

