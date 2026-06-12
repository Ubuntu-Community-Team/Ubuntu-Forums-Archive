---
title: "Ubuntu Font Rendering on Debian"
date: 2013-05-14
forum: Any Other OS
---

### Post by buzzingrobot on 2013-05-14
I'm considering a long-term project that will require long-term use of a desktop distribution.  Ubuntu's 9-month release cycle looks to be too short for my purposes, and 12.04.02 LTS doesn't offer what I need.

So, I'm looking at Debian.  I did a test installation of the new 7 release (Wheezy).  

Font rendering, though, is the issue.  It is better out of the box than on earlier releases.  But, I won't use it unless I can tweak it to duplicate the font rendering on Ubuntu 13.04, which I'm using at the moment.

Now, how to get Ubuntu font rendering on Debian is a perennial question, and not too popular at the Debian forum. But, I have searched high and low and have not found a decent answer.  

By "decent", I mean instructions on applying the Ubuntu patches to Debian code. Presumably, Cairo, fontconfig and freetype need to be patched. (I could handle patching source in conventional fashion, but have no experience patching and building debs the 'Debian Way'.)

If those instructions are not out there, then perhaps pointers to up-to-date patched debs for Wheezy?

I have seen lots of advice to edit ~/.fonts.conf and/or copy Ubuntu's fontconfig files.  That's all well and good, but the Ubuntu patches need to be applied, too.

Are those answers out there?  Have I been looking in the wrong places?

---

### Post by BubuXP on 2013-06-12
From the answers received, I guess you're looking in the wrong place :)
The easier way to get what you need is installing directly the ubuntu packages responsible of the font rendering in debian, and those are libfreetype6, libfontconfig1, fontconfig and fontconfig-config (libcairo and xft are not necessary anymore), plus you can also install ttf-ubuntu-font-family.
Use the apt-pinning from ubuntu repos or install the packages manually with gdebi (or dpkg). Packages locations:
[http://archive.ubuntu.com/ubuntu/pool/main/f/freetype/](http://archive.ubuntu.com/ubuntu/pool/main/f/freetype/)
[http://archive.ubuntu.com/ubuntu/pool/main/f/fontconfig/](http://archive.ubuntu.com/ubuntu/pool/main/f/fontconfig/)
[http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-font-family-sources/](http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-font-family-sources/)

Everything works fine here, I'm using Sid (if you have dependencies issues in wheezy try using older versions of the libraries).

---

### Post by buzzingrobot on 2013-06-12
> **BubuXP said:**
> From the answers received, I guess you're looking in the wrong place :)
The easier way to get what you need is installing directly the ubuntu packages responsible of the font rendering in debian, and those are libfreetype6, libfontconfig1, fontconfig and fontconfig-config (libcairo and xft are not necessary anymore), plus you can also install ttf-ubuntu-font-family.
Use the apt-pinning from ubuntu repos or install the packages manually with gdebi (or dpkg). Packages locations:
[http://archive.ubuntu.com/ubuntu/pool/main/f/freetype/](http://archive.ubuntu.com/ubuntu/pool/main/f/freetype/)
[http://archive.ubuntu.com/ubuntu/pool/main/f/fontconfig/](http://archive.ubuntu.com/ubuntu/pool/main/f/fontconfig/)
[http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-font-family-sources/](http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-font-family-sources/)

Everything works fine here, I'm using Sid (if you have dependencies issues in wheezy try using older versions of the libraries).

Thanks.  I rebuilt the patched Ubuntu (Raring) packages for Wheezy. Didn't pin anything because the version numbers are higher than anything that's likely to ever  roll out in Wheezy updates.

For whatever reason, though, I thought the resulting display in Wheezy had weaknesses that I don't see in Raring.  I spent a busy few days checking out several distributions using the Ubuntu patches or Infinality.  In the end, I decided 13.04 delivers the best presentation on my equipment.  I've reconfigured my multi-disk partitioning scheme and my backups to try to lend some stability despite the short Raring life cycle.

---

### Post by BubuXP on 2013-06-12
If the ubuntu repo is added in source.list then I think one should use the pinning to give lowest priority to that repo, or it could end in a mess (but I don't tried it, so I don't know what really happens in such situation).

If you recompile the packages in Debian from Ubuntu sources, have you used the dev packages from Ubuntu or from Debian? Maybe that's the cause for not obtaining the same results.
I checked the dependencies and those libraries won't install in Wheezy:amd64 because they need libc6 >= 2.14 and in Wheezy it's 2.13. Strangely, the i386 version of these libraries need libc6 >= 2.11 so these will install in Wheezy:i386

I think I will make some comparative screenshots between original Lubuntu live desktop and Debian Sid with Ubuntu's libraries and settings.

---

### Post by buzzingrobot on 2013-06-12
> **BubuXP said:**
> 
If you recompile the packages in Debian from Ubuntu sources, have you used the dev packages from Ubuntu or from Debian? Maybe that's the cause for not obtaining the same results.
I checked the dependencies and those libraries won't install in Wheezy:amd64 because they need libc6 >= 2.14 and in Wheezy it's 2.13. Strangely, the i386 version of these libraries need libc6 >= 2.11 so these will install in Wheezy:i386

Could be.  I just used "apt-get -f install" to pull in the dependencies when the build complained. Although I don't believe I pulled in a new libc6.  That I would have noticed. I didn't compare the dev sources.

---

### Post by BubuXP on 2013-06-12
The Ubuntu packages won't install directly on Wheezy:amd64 because of different libc6 versions, that's because it needs to be recompiled.
The dev libraries requested when compiling are libfreetype6-dev, libfontconfig1-dev and others, but I think those should came from Ubuntu to be sure that the result is the same as original (these don't seem to need a specific libc6 version so the Wheezy libc6 will be fine).
But if the system you need to setup will use a 32bit Wheezy, you can directly install the ubuntu packages.

---

### Post by BubuXP on 2013-06-12
I take the screenshots, but I haven't compared them yet.

Debian is Sid with LXDE and Ubuntu font hinting packages.
Lubuntu is vanilla, with default settings (only changed default theme).

File manager and desktop:
Debian: [http://www.mediafire.com/view/3bcyrxyw1e9wfs3](http://www.mediafire.com/view/3bcyrxyw1e9wfs3)
Lubuntu: [www.mediafire.com/view/shf4vgqy2tfuz7f](www.mediafire.com/view/shf4vgqy2tfuz7f)

Terminal (font DejaVu Sans Mono 12):
Debian: [http://www.mediafire.com/view/y1t19p2c8dqt7n4](http://www.mediafire.com/view/y1t19p2c8dqt7n4)
Lubuntu: [http://www.mediafire.com/view/j4oxjz8581j8hip](http://www.mediafire.com/view/j4oxjz8581j8hip)

Synaptic:
Debian: [http://www.mediafire.com/view/rb0c03w804jy59y](http://www.mediafire.com/view/rb0c03w804jy59y)
Lubuntu: [http://www.mediafire.com/view/9gmdcm9ovrada6y](http://www.mediafire.com/view/9gmdcm9ovrada6y)


All the following fonts have size 11

Ubuntu Condensed
Deb: [http://www.mediafire.com/view/1n7yws609n7sbce](http://www.mediafire.com/view/1n7yws609n7sbce)
Lubu: [http://www.mediafire.com/view/1n7yws609n7sbce](http://www.mediafire.com/view/1n7yws609n7sbce)

DejaVu Sans
Deb: [http://www.mediafire.com/view/gvn69dlh7022kno](http://www.mediafire.com/view/gvn69dlh7022kno)
Lubu: [http://www.mediafire.com/view/fdi9u54cbkm3fzi](http://www.mediafire.com/view/fdi9u54cbkm3fzi)

DejaVu Serif
Deb: [http://www.mediafire.com/view/xq9z8c5hw5qw9y5](http://www.mediafire.com/view/xq9z8c5hw5qw9y5)
Lubu: [http://www.mediafire.com/view/2z46fo133wnoeaq](http://www.mediafire.com/view/2z46fo133wnoeaq)

FreeSerif
Deb: [http://www.mediafire.com/view/zhz4oow3h1rpxkw](http://www.mediafire.com/view/zhz4oow3h1rpxkw)
Lubu: [http://www.mediafire.com/view/ayceb3intj421bw](http://www.mediafire.com/view/ayceb3intj421bw)

FreeSans
Deb: [http://www.mediafire.com/view/bj9imly67du0uvx](http://www.mediafire.com/view/bj9imly67du0uvx)
Lubu: [http://www.mediafire.com/view/5zveb129q8v8bd8](http://www.mediafire.com/view/5zveb129q8v8bd8)

Ubuntu Mono
Deb: [http://www.mediafire.com/view/2nu6n5i7mob51jb](http://www.mediafire.com/view/2nu6n5i7mob51jb)
Lubu: [http://www.mediafire.com/view/2t6sp8adj9tt7fy](http://www.mediafire.com/view/2t6sp8adj9tt7fy)

Other Debian:
[http://www.mediafire.com/view/4cfvewqa48kxhij](http://www.mediafire.com/view/4cfvewqa48kxhij)
[http://www.mediafire.com/view/8itjhu7r3ik3yho](http://www.mediafire.com/view/8itjhu7r3ik3yho)

What do you think? Until now I only noted a fatter ubuntu font on the windows titlebar, but they are the same font and size.

EDIT: comparing the first two pic at 400% I noted that the fonts are the same, but in Debian the spacing between glyphs is less. Looking at the icon named "Desktop" it's almost impossible to caught but the space between the **D** and the **e** and between the **t** and the **o** is less in Debian.
What packages take care of font spacing apart those that I used before? Maybe it's the desktop environment? I will check other pics tomorrow, now it's too late.

EDIT2: on the side panel of the file manager the fonts are exactly the same, even spacing. And I could say that the tightened words in Debian look almost better than the original? :D

---

### Post by buzzingrobot on 2013-06-13
Interesting.  On my monitor, they all look good, and it's difficult to see any differences.  (I haven't blown them up.) 

When I compared 13.04 with patched Debian, I thought character edges on Debian were a tiny bit less distinct, and that rounded characters on Debian -- o's, a's, r', etc. -- often showed stray gray pixels inside the loops, while those in 13.04 did not.

I've decided that the sharpness setting of a monitor has a lot to with how fonts appear.  I can adjust mine in a range that goes from an extreme of totally smudgy characters to the other extreme of quite visible individual pixels.

Ambient lighting is also important, something I learned from working with photos. Text and images look better on my screen in indirect natural light, especially morning light. They look worse in the evening with artificial lighting, so much so that I won't do photo work at night.

---

### Post by BubuXP on 2013-06-15
For the information I found the cause for the different spacing. It's because I used Saucy fontconfig (2.10.93) instead of Raring (2.10.2) and it could be an upstream improvement.
BTW I compiled (hopefully right) the Raring source in Debian, so they can be used even in Wheezy without problems, but I'm still testing them.
I found that no particular patches are applied in freetype (it's just newer than Debian), so probably "Ubuntu's magic touch" resides only in the fontconfig packages.
If someone is interested I can link them and provide instruction for a clean install.

---

### Post by touil1976 on 2013-12-06
> **BubuXP said:**
> For the information I found the cause for the different spacing. It's because I used Saucy fontconfig (2.10.93) instead of Raring (2.10.2) and it could be an upstream improvement.
BTW I compiled (hopefully right) the Raring source in Debian, so they can be used even in Wheezy without problems, but I'm still testing them.
I found that no particular patches are applied in freetype (it's just newer than Debian), so probably "Ubuntu's magic touch" resides only in the fontconfig packages.
If someone is interested I can link them and provide instruction for a clean install.

BubuXP, I would be very much interested in knowing what you did to get debian fonts look exactly like in Ubuntu. Could you please post or send me a step by step guide for doing it ?

Thank you very much in advance.

---

### Post by BubuXP on 2013-12-06
> **touil1976 said:**
> BubuXP, I would be very much interested in knowing what you did to get debian fonts look exactly like in Ubuntu. Could you please post or send me a step by step guide for doing it ?

In the previous posts I said to install the ubuntu packages in debian to get the same rendering, but it's incorrect. From Wheezy, the font rendering packages are the same as Ubuntu, no more custom patches except that Ubuntu change the *fontconfig* configuration to enable certain option by default (where Debian instead use the upstream bare configuration).

To enable the same Ubuntu font aspect, first install the Ubuntu font with [the official package]("http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-font-family-sources/ttf-ubuntu-font-family_0.80-0ubuntu6_all.deb").
Then create the system default configuration with:
**sudo nano /etc/fonts/local.conf**
and paste the following:

```
<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
    <match target="pattern">

<!-- Font rasterization converts vector font data to bitmap data so that it
     can be displayed. The result can appear jagged due to aliasing.
     Anti-aliasing increases the apparent resolution of font edges. -->
        <edit mode="append" name="antialias">
            <bool>true</bool>
        </edit>

<!-- Using normal hinting, TrueType hinting instructions in the font are
     interpreted by freetype's Byte-Code Interpreter. This works best for
     fonts with good hinting instructions. -->
        <edit mode="append" name="hinting">
            <bool>true</bool>
        </edit>

<!-- Auto-discovery for hinting. This looks worse than normal hinting for
     fonts with good instructions, but better for those with poor or no
     instructions. The autohinter and subpixel rendering are not designed
     to work together and should not be used in combination. -->
        <edit mode="append" name="autohint">
            <bool>false</bool>
        </edit>

<!-- Hint style is the amount of influence the hinting mode has. Hinting
     can be set to: "hintfull", "hintmedium", "hintslight" and "hintnone".
     With BCI hinting, "hintfull" should work best for most fonts.
     With the autohinter, "hintslight" is recommended. -->
        <edit mode="append" name="hintstyle">
            <const>hintslight</const>
        </edit>

<!-- Subpixel rendering effectively triples the horizontal (or vertical)
     resolution for fonts by making use of subpixels. The autohinter and
     subpixel rendering are not designed to work together and should not
     be used in combination. Most monitors manufactured today use the
     Red, Green, Blue (RGB) specification. Fontconfig will need to know
     your monitor type to be able to display your fonts correctly.
     Values are "rgb" (most common), "bgr", "vrgb" (vertical), "vbgr",
     "unknown" or "none". -->
        <edit mode="append" name="rgba">
            <const>rgb</const>
        </edit>

<!-- When using subpixel rendering, you should enable the LCD filter,
     which is designed to reduce colour fringing. The "lcddefault" filter
     will work for most users. Other filters are available that can be
     used in special situations: "lcdlight"; a lighter filter ideal for
     fonts that look too bold or fuzzy; "lcdlegacy", the original Cairo
     filter; "lcdnone" to disable it entirely. -->
        <edit mode="append" name="lcdfilter">
            <const>lcddefault</const>
        </edit>

<!-- Fontconfig should be able to detect DPI parameters as discovered
     by the Xorg server. You can check Xorg's automatically discovered
     DPI with the command 'xdpyinfo | grep resolution'
     Uncomment the following to activate customized DPI -->
<!--
        <edit mode="append" name="dpi">
            <double>96</double>
        </edit>
-->

<!-- Some scalable fonts have embedded bitmap versions which are rendered
     instead, mainly at smaller sizes. Force using scalable fonts at all
     sizes by disabling embedded bitmap. -->
        <edit mode="append" name="embeddedbitmap">
            <bool>false</bool>
        </edit>

    </match>

<!-- Reject bitmap fonts in favour of Truetype, Postscript, etc. -->
    <selectfont><rejectfont><pattern>
        <patelt name="scalable"><bool>false</bool></patelt>
    </pattern></rejectfont></selectfont>


<!-- Use font substitution to set your preferred fonts the default
     serif, sans-serif and monospace fonts. You can also substitute
     a specific font not installed on the system (e.g. Arial) with
     an installed one (e.g. FreeSans) by adding other aliases like
     these. This only works if the original font is not on the system. -->
    <alias>
        <family>serif</family>
        <prefer><family>DejaVu Serif</family></prefer>
    </alias>
    <alias>
        <family>sans-serif</family>
        <prefer><family>Ubuntu</family></prefer>
    </alias>
    <alias>
        <family>monospace</family>
        <prefer><family>Ubuntu Mono</family></prefer>
    </alias>
<!--
    <alias>
        <family>Arial</family>
        <prefer><family>FreeSans</family></prefer>
    </alias>
-->


<!-- Fixes for Ubuntu family:
    - Medium variant is used instead of Regular on Qt apps:
      https://bugs.launchpad.net/ubuntu-font-family/+bug/744812
    - Medium and Bold looks the same in certain applications:
      https://bugs.launchpad.net/ubuntu/+source/gnome-specimen/+bug/813373
-->
<match target="scan">
    <test name="fullname" compare="eq">
        <string>Ubuntu Light</string>
    </test>
    <edit name="family" mode="assign">
        <string>Ubuntu</string>
    </edit>
    <edit name="style" mode="assign">
        <string>Light</string>
    </edit>
</match>

<match target="scan">
    <test name="fullname" compare="eq">
        <string>Ubuntu Light Italic</string>
    </test>
    <edit name="family" mode="assign">
        <string>Ubuntu</string>
    </edit>
    <edit name="style" mode="assign">
        <string>Light Italic</string>
    </edit>
</match>

<match target="scan">
    <test name="fullname" compare="eq">
        <string>Ubuntu Medium</string>
    </test>
    <edit name="family" mode="assign">
        <string>Ubuntu</string>
    </edit>
    <edit name="style" mode="assign">
        <string>Medium</string>
    </edit>
    <edit name="weight" mode="assign">
        <const>demibold</const>
    </edit>
</match>

<match target="scan">
    <test name="fullname" compare="eq">
        <string>Ubuntu Medium Italic</string>
    </test>
    <edit name="family" mode="assign">
        <string>Ubuntu</string>
    </edit>
    <edit name="style" mode="assign">
        <string>Medium Italic</string>
    </edit>
    <edit name="weight" mode="assign">
        <const>demibold</const>
    </edit>
</match>

</fontconfig>
```

Exit saving the file, do **fc-cache -fv** with **sudo** and without, and then reboot (or logout/login).
The comments in the config file could help you changing settings.

You should also change the font appearance options of you desktop environment (Gnome, Xfce, LXDE, etc.) to match the above settings, because those DE usually ignore some of the fontconfig settings.

Tell me if it works fine for you or if you find any problem.

EDIT: Using the Ubuntu font you could get [bold fonts in some applications]("https://bugs.launchpad.net/ubuntu-font-family/+bug/744812") (like in VLC for example) but I found how a workaround and put the fix on the above configuration.

---

