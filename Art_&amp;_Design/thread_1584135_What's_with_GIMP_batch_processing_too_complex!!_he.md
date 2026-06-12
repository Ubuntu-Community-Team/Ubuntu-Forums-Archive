---
title: "What's with GIMP batch processing? too complex!! help please?!"
date: 2010-09-28
forum: Art &amp; Design
---

### Post by youbuntu on 2010-09-28
Hey chaps! What's with all the futzing and schmutzing around with scripts and config files in GIMP, when **all** I want to do is batch process some JPEGs, **not learn ANOTHER computer language!**

Help, if it doesn't involve a degree in scripting language, please! (how do NON geeks get by?! artistic types?!)

---

### Post by SeijiSensei on 2010-09-28
> **glossywhite said:**
> Hey chaps! What's with all the futzing and schmutzing around with scripts and config files in GIMP, when **all** I want to do is batch process some JPEGs, **not learn ANOTHER computer language!**

Help, if it doesn't involve a degree in scripting language, please! (how do NON geeks get by?! artistic types?!)

What do you want to do with those JPEGs?  I'd suggest you take a look at [ImageMagick]("http://www.imagemagick.org/script/index.php").  It's available from the Ubuntu repositories by the usual means.  Runs on other platforms like Windows and OS X as well.

---

### Post by youbuntu on 2010-09-28
Thanks, but you miss the point - I'm using GIMP

[EDIT]: Done it:

```
sudo aptitude install gimp-plugin-registry
```

---

### Post by SeijiSensei on 2010-09-28
OK, but ImageMagick is an excellent alternative to using the GIMP for batch processing.  The command-line "convert" program has an amazing array of options to resize, crop, etc., etc., almost any graphic, and you can easily script it from the bash shell.

Part of this is a "philosophy" issue.  Unix was built on using simple command-line programs with a specific purpose.  ImageMagick is a stellar example of this philosophy.

---

### Post by youbuntu on 2010-09-29
> **SeijiSensei said:**
> OK, but ImageMagick is an excellent alternative to using the GIMP for batch processing.  The command-line "convert" program has an amazing array of options to resize, crop, etc., etc., almost any graphic, and you can easily script it from the bash shell.

Part of this is a "philosophy" issue.  Unix was built on using simple command-line programs with a specific purpose.  ImageMagick is a stellar example of this philosophy.

Maybe re-reading my opening post will help in clarifying things (again). Thanks.

---

