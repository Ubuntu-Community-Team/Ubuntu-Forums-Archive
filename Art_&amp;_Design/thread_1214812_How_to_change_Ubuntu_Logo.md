---
title: "How to change Ubuntu Logo"
date: 2009-07-16
forum: Art &amp; Design
---

### Post by rawfool on 2009-07-16
Can I change the Ubuntu Logo which lies beside **Applications** tab? I want to change it to Gnome Logo which has a foot print on it. I'm a newbee to Linux environment, so I thought of not manipulating anything without any advice. Please help me with this.
Thnx.

---

### Post by raronson on 2009-07-16
Hi.

go to ~/.icons/<icon theme directory>/scalable (or 24x24)/places/

and replace the "start-here.png" (or "start-here.svg") with the new logo.  Rename the new logo to "start-here.png" or "start-here.svg" depending on file type.

Here's a couple for you:

---

### Post by HotForLinux on 2009-07-16
I don't know which one:

/usr/share/icons/HighContrastLargePrintInverse/48x48/places/start-here.png
/usr/share/icons/Human/22x22/places/start-here.png
/usr/share/icons/Human/24x24/places/start-here.png
/usr/share/icons/Human/48x48/places/start-here.png
/usr/share/icons/Human/scalable/places/start-here.svg
/usr/share/icons/Tangerine/16x16/places/start-here.png
/usr/share/icons/Tangerine/22x22/places/start-here.png
/usr/share/icons/Tangerine/24x24/places/start-here.png
/usr/share/icons/Tangerine/32x32/places/start-here.png
/usr/share/icons/Tangerine/scalable/places/start-here.svg
/usr/share/icons/gnome/16x16/places/start-here.png
/usr/share/icons/gnome/22x22/places/start-here.png
/usr/share/icons/gnome/24x24/places/start-here.png
/usr/share/icons/gnome/32x32/places/start-here.png
/usr/share/icons/gnome/scalable/places/start-here.svg


but I like the Ubuntu logo

(Hard Heroin)

---

### Post by oblivian516 on 2009-07-16
Lol, replace the one of the theme you are using! (I'm guessing 24x24)

---

### Post by rawfool on 2009-07-21
It helped me. Thnx Everyone. :popcorn:

---

### Post by adhika_rexuss on 2009-08-24
> **raronson said:**
> Hi.

go to ~/.icons/<icon theme directory>/scalable (or 24x24)/places/

and replace the "start-here.png" (or "start-here.svg") with the new logo.  Rename the new logo to "start-here.png" or "start-here.svg" depending on file type.

Here's a couple for you:

Hi Raronson, 

How do you know that it was 24x24 that is being used by ubuntu?
Is there any configuration file that I can modify to change from 24x24 to 16x16 for example.

Thank you,
Adhika

---

### Post by rawfool on 2009-08-25
**@ adhika_rexuss - ** You have to create logos of all sizes and just follow **@ HotForLinux** post in this thread. This will replace all the Ubuntu icons with your customized icon. Logo cannot be fixed to particular size because, every theme use different logo sizes. So this way you can have your customized logo in all the themes.
P.S: There may not be *start-here.png* for some sizes/themes, so you need not paste for your customized logo for those.
Cheers !

---

### Post by adhika_rexuss on 2009-08-25
Hi rawfool, basically, **HotForLinux** way was to replace any of those logo with the logo that we want to have. However we actually don't know which folder will be used for the start-here.png file. I was wondering if this is something we can check from a configuration. I have no idea at all on the configuration file that needs to be checked.

**HotForLinux**, may be you have any idea about my curiousity?

Thank you,
Adhika

---

### Post by rawfool on 2009-08-28
In Ubuntu there are many themes and each theme uses different size for the icon. You can manually check those folders if it has *start-here.png* file. To find the location, just follow the paths given **@ HotForLinux**'s post. For example, if you want to change the icon in Human theme with size 22, then you just paste your file to ***/usr/share/icons/Human/22x22/places***. 
For example, if you have your customized start-here.png on desktop, then the following should be executed in 'Terminal'.
> *cp /home/username/desktop/start-here.png /usr/share/icons/Human/22x22/places/start-here.png*

This will copy your customized file into the Human(Theme)/22x22(Size of icon)/places(folder which contains icon)
Note: You should be root to execute the following.
Shoot a reply if you have any doubts.

---

