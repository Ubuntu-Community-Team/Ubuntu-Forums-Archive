---
title: "Migrating from Windows - usability questions"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by robfuller on 2008-01-01
I've just installed Ubuntu 7.10, and am really impressed. Unlike when I first tried to use Ubuntu about 18 months ago (I think that was Dapper Drake), almost everything is working straight away. I have a few questions about how to set things up in Ubuntu. These are minor issues, but they do affect how likely I am to switch to Ubuntu from Windows.

Sorry in advance that these are stupid questions, but I really have tried searching for the answers. I'm kind of overwhelmed by documentation on the various Ubuntu sites.

(1) How do I mount my Windows partition automatically when Ubuntu starts? At the moment I have to manually open the file browser, double-click on the Windows partition, then enter my password.

(2) Everything on the Gnome desktop (using the standard theme) appears larger than in Windows: the window borders, icons, etc, all take up more of my screen space in Gnome, even though I'm using the same monitor resolution (1280 x 800) as in Windows. I've reduced the font sizes using System > Preferences > Appearance, but that doesn't change the size of everything else.

(3) In Firefox for Windows, the backspace key has the same effect as clicking the "back" arrow - and I use it all the time. In Firefox in Ubuntu, backspace is doing a "page up" instead. How can I change that?

(4) Is there any way to implement simple key shortcuts for accented characters? (eg. in MS Word, typing <ctrl>+' then e gives an é) I know there are extensions to do that in Firefox, but is there any way to do across all applications?

(5) Why is that I can use the Times New Roman and Arial fonts in OpenOffice or for viewing PDFs, but I can't set them as my default fonts for the desktop or for Firefox?

Thanks in advance for any help you can give me.....
Rob

---

### Post by HermanAB on 2008-01-01
My tuppence worth:

(1) How do I mount my Windows partition automatically:
Configure it in /etc/fstab

2) Everything on the Gnome desktop (using the standard theme) appears larger than in Windows
Use a higher screen resolution.

3) In Firefox for Windows, the backspace key has the same effect as clicking the "back" arrow
The program you need is called xmodmap.  See this guide: [http://aeronetworks.ca/eeepc-howto.html](http://aeronetworks.ca/eeepc-howto.html) down towards the bottom about the Right-hand Control Key.

(4) Is there any way to implement simple key shortcuts for accented characters?
In Kubuntu, that is a function of KDE, on Ubuntu, you may need to use xmodmap.

(5) Why is that I can use the Times New Roman and Arial fonts in OpenOffice or for viewing PDFs
Fonts are embedded in PDF files to make them portable.  You should install the Redhat Freedom Fonts - they are equivalent to the popular Microsoft fonts.

Hope that helps!

Herman

---

### Post by robfuller on 2008-01-01
Thanks, Herman, that does help a lot. I've managed to work out auto-mounting with /etc/fstab, and I will explore xmodmap. I already have the display resolution in the Gnome desktop set to the actual resolution of my laptop's screen, so I can't go any higher - it just seems that all the desktop "furniture" takes up more of my screen space than it does in Windows. Anyway, that's a very small quibble....

Rob

---

### Post by Mazza558 on 2008-01-01
> **robfuller said:**
>  I already have the display resolution in the Gnome desktop set to the actual resolution of my laptop's screen, so I can't go any higher - it just seems that all the desktop "furniture" takes up more of my screen space than it does in Windows. Anyway, that's a very small quibble....

Rob

Gnome takes up more screen space than Windows, but you'll get used to it. It's actually easier to use when you have more space for the interface. It's similar to what happens if you try a Mac.

---

### Post by jken146 on 2008-01-01
Alt+Left Arrow is the default kb shortcut for going back in Firefox.

---

### Post by dcstar on 2008-01-01
> **robfuller said:**
> I've just installed Ubuntu 7.10, and am really impressed. Unlike when I first tried to use Ubuntu about 18 months ago (I think that was Dapper Drake), almost everything is working straight away. I have a few questions about how to set things up in Ubuntu. These are minor issues, but they do affect how likely I am to switch to Ubuntu from Windows.

Sorry in advance that these are stupid questions, but I really have tried searching for the answers. I'm kind of overwhelmed by documentation on the various Ubuntu sites.

(1) How do I mount my Windows partition automatically when Ubuntu starts? At the moment I have to manually open the file browser, double-click on the Windows partition, then enter my password.
.......
Thanks in advance for any help you can give me.....
Rob

Install the **pysdm** package, then System-Administration-Storage Device Manager to set up the access.

---

### Post by ARhere on 2008-01-01
Geeze!

The competition for answering questions is getting tough!  This post is only a few minutes old and all questions are answered.

Yeah for Ubuntu..  Booo for my chances to a high rating! hehehe

-AR

---

### Post by rubenvb on 2008-01-17
About the backspace key in Firefox... Is there an easy way (I know, installing an application isn't that hard...) to change the action executed when pressing the backspace key (like in about:config, there is an option that changes the action when the backspace key is pressed, but I don't know what it does...)
Thanks

---

### Post by Joeb454 on 2008-01-17
What do you want to change it to?

---

### Post by an93l on 2008-01-17
if you stil want to reduce the size of the top and bottom panels you can do so if you right click on each of them and then click properties there is a size box you can reduce this and the bars will get thinner, the window title bars ect are controled by the theme that you installed you can get different ones from gnome-look.org. i hope this is what you ment.

---

### Post by philinux on 2008-01-17
Firefox address bar

```
about:config
```

Filter = browser.backspace-action

change the entry from 1 to 0.

---

### Post by rubenvb on 2008-01-17
I'd like to change the backspace button to go back in the browser (ie the green arrow in the topleft)

---

### Post by Joeb454 on 2008-01-17
Like in Windows you mean?

*yes I just said Windows & spelt it correctly ;) :lolflag:*

---

### Post by masher_oz on 2008-01-18
> **philinux said:**
> Firefox address bar

```
about:config
```

Filter = browser.backspace-action

change the entry from 1 to 0.


Fixed my problem!  :)

---

### Post by BatsotO on 2008-02-11
> **robfuller said:**
> Thanks, Herman, that does help a lot. I've managed to work out auto-mounting with /etc/fstab, and I will explore xmodmap. I already have the display resolution in the Gnome desktop set to the actual resolution of my laptop's screen, so I can't go any higher - it just seems that all the desktop "furniture" takes up more of my screen space than it does in Windows. Anyway, that's a very small quibble....

Rob

I put all the "furnitures" in one panel and delete the other panel

---

