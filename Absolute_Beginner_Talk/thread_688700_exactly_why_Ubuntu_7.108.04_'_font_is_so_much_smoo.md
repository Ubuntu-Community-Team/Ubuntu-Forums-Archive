---
title: "exactly why Ubuntu 7.10/8.04 ' font is so much smoother than other linux distroes?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by clevin on 2008-02-05
at same settings. ubuntu 710/804's font looks so much smoother than fedora/mandriva?

how come?

My Old laptop is very slow running ubuntu 710, so I installed mandriva 2008.0, with freetype 2.3.5, plf non-free font library, but fonts still looks edgy.

---

### Post by vinutux on 2008-02-05
itz answer in ur question because it is UBUNTU not mandriva and fedora :)

anyway don't know technically check out system -> preferenses -> appearence and font tab (change font displa ie lcd etc)

---

### Post by dcstar on 2008-02-05
> **vinutux said:**
> 
.......
anyway don't know technically check out system -> preferenses -> appearence and font tab (change font displa ie lcd etc)

Yep, just because Ubuntu may turn on things like font hinting by default, it doesn't mean other distros will also enable theses things in the install (even though they are capable of them).

There are hundreds (thousands?) of turn on/off options that a distro package has to have configured, some are wanted by people, others maybe not.

You will see posts saying 'distro "X" does this for me but Ubuntu doesn't!, why?', and the only real answer is **because they are different**.

If these distros were all almost identical, then there would be little point in having most of them.

---

### Post by clevin on 2008-02-06
lol, my friend, Im not that noob, I set up everything exactly the same:

96dpi
LCD subpixel, RGB, hinting full/light, font size 10

Im saying, with exactly same settings, ubuntu font is smoother. anybody knows why?

---

### Post by jordanmthomas on 2008-02-06
Ubuntu compiles libxft, freetype2, cairo, and fontconfig with some extra patches that many (most) distros don't use.
I actually used these patches and recompiled all these on Arch.

You should be able to get these patches with apt somehow, but my debian-ese is failing me.

---

### Post by clevin on 2008-02-06
thats what I thought, anywhere I can find a detailed list of what I need?

---

### Post by papuccino1 on 2008-02-06
I guess :P

---

### Post by mohbana on 2008-02-25
can someone point me in the right direction i would like my fedora installation to use the same fonts ubuntu does, ubuntu's fonts are clearly in my opinion way better.  

Take a look at this thread, its not that long.  I am experiencing the same thing as that user.  I've tried what he suggested.  As in [http://forums.fedoraforum.org/forum/showpost.php?p=872101&postcount=7](http://forums.fedoraforum.org/forum/showpost.php?p=872101&postcount=7).  Copying the fonts from ubuntu didn't have any effect.  The only thing that had any effect on the fonts and made it better was [http://forums.fedoraforum.org/forum/showpost.php?p=871456&postcount=5](http://forums.fedoraforum.org/forum/showpost.php?p=871456&postcount=5).

I would really like to get this resolved.  Thanks in advance for the help

---

### Post by AdamWill on 2008-02-25
The patches referred to are these, I think:

[http://www.freetype.org/freetype2/patches/rogue-patches.html](http://www.freetype.org/freetype2/patches/rogue-patches.html)

I'm checking through Ubuntu's diffs to see exactly what you guys have.

The only patches in the Ubuntu freetype package which affect font rendering simply change the settings of three build-time configuration options:

-#define TT_CONFIG_OPTION_UNPATENTED_HINTING
+/* #define TT_CONFIG_OPTION_UNPATENTED_HINTING */

-/* #define FT_CONFIG_OPTION_SUBPIXEL_RENDERING */
+#define FT_CONFIG_OPTION_SUBPIXEL_RENDERING

-/* #define TT_CONFIG_OPTION_BYTECODE_INTERPRETER */
+#define TT_CONFIG_OPTION_BYTECODE_INTERPRETER

I do not know the legal basis on which Ubuntu as a project believes it's legally okay to have these settings, but most other distros have the "unpatented" settings - TT_CONFIG_OPTION_UNPATENTED_HINTING enabled, FT_CONFIG_OPTION_SUBPIXEL_RENDERING disabled, TT_CONFIG_OPTION_BYTECODE_INTERPRETER disabled - as they consider it legally problematic to use the "patented" settings of these options.

There is no actual *code* patched in Ubuntu's freetype package which affects font rendering at all. The only changes that affect rendering are the changes to these three upstream configuration settings.

For libxft2, Ubuntu has an updated version of [http://www.freetype.org/freetype2/patches/libXft-2.1.7-lcd-filter-2.patch](http://www.freetype.org/freetype2/patches/libXft-2.1.7-lcd-filter-2.patch) named libXft-2.1.10-lcd-filter-3.patch. This makes libxft2 use Freetype's built-in LCD color filtering feature.

For fontconfig, Ubuntu includes a patch named 03_lcd_filter_freedesktop_bug13566.patch, which adds configuration options fore Freetype's subpixel filtering capabilities. This is planned to go upstream to fontconfig with version 2.6: see [https://bugs.freedesktop.org/show_bug.cgi?id=13566](https://bugs.freedesktop.org/show_bug.cgi?id=13566) .

For cairo, Ubuntu includes a patch named 02-lcd_filter_freedesktop_bug10301.dpatch , which basically does the same as the Xft patch, only for Cairo (which is what a lot of modern apps actually use for their font rendering). Freedesktop.org bug is - duh - 10301: [https://bugs.freedesktop.org/show_bug.cgi?id=10301](https://bugs.freedesktop.org/show_bug.cgi?id=10301) . Long discussion of the history of these patches is there. Apparently, at least this one actually originates with SUSE.

So, yeah, that's basically what's going on. I suspect all the other patches are irrelevant unless FT_CONFIG_OPTION_SUBPIXEL_RENDERING is enabled in freetype, but I may be wrong there.

---

### Post by jordanmthomas on 2008-02-25
> **AdamWill said:**
> Every time anyone points at these supposed patches, it's always the same set, which were applied to upstream Freetype quite a long time ago...

Well, Arch doesn't have it by default I don't think, seeing as these exist in AUR:
[http://aur.archlinux.org/packages.php?ID=14440](http://aur.archlinux.org/packages.php?ID=14440)
[http://aur.archlinux.org/packages.php?ID=14438](http://aur.archlinux.org/packages.php?ID=14438)
[http://aur.archlinux.org/packages.php?ID=14437](http://aur.archlinux.org/packages.php?ID=14437)
[http://aur.archlinux.org/packages.php?ID=14439](http://aur.archlinux.org/packages.php?ID=14439)

It seems to me Ubuntu does *something* special to its fonts, because my fonts look way better after installing these than they did beforehand.  Had these patches been applied upstream, wouldn't they find their way into Arch?

---

### Post by AdamWill on 2008-02-25
yep, I edited my post, see above. Some of the old set of patches that is usually referred to has since gone upstream or been made obsolete, but some (apparently with some kind of legal issues attached), not.

---

### Post by mohbana on 2008-02-26
thanks AdamWill for the reply

could someone using fedora 8 please outline the steps they took to get fonts ubuntu use. thanks

---

### Post by jordanmthomas on 2008-02-26
> **mohbana said:**
> thanks AdamWill for the reply

could someone using fedora 8 please outline the steps they took to get fonts ubuntu use. thanks

Perhaps that would be better asked on Fedora's forums or in other OS talk?
Not trying to run you off, but you're likely to get more responses there, seeing as this is an Ubuntu forum.

---

### Post by jordanmthomas on 2008-02-26
> **mohbana said:**
> thanks AdamWill for the reply

could someone using fedora 8 please outline the steps they took to get fonts ubuntu use. thanks

Also, if you think the fonts in my screenshot attached look like what you're after you can read the PKGBUILDs at the links I provided earlier.  Basically, what's inside them is the patching process and what options were used when compiling.

You can use them as a guide to compile them your way.

Hope this at least gets you started.  Good luck.  :)

---

### Post by AdamWill on 2008-02-27
as a quick follow up, our (Mandriva's) font guy tells me that as far as our legal advice is concerned, the options in question all enable code that is considered subject to patents and thus we cannot safely ship Mandriva with those options set the way Ubuntu sets them. We have no idea why Ubuntu does not consider this to be a problem or is ignoring it, but I'm sure there's a mailing list where you could ask.

---

### Post by mohbana on 2008-03-12
I recompiled the freetype with the **bytecode interpreter** and **subpixelrendering**, i couldn't find **unpantented hinting**.  Here is the actual post [http://forums.fedoraforum.org/forum/showpost.php?p=977255&postcount=2](http://forums.fedoraforum.org/forum/showpost.php?p=977255&postcount=2), your going to need **freetype-2.3.5-3.fc8.src.rpm** i suggest you google it.

---

