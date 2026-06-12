---
title: "Installing from downloaded package"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by myke on 2005-11-22
OK -- I downloaded Thunderbird directly from the Mozilla website.  I know I can install it thru the package manager but I want to be able to learn to do so with direct downloads so I thought I'd try it with Thunderbird.  I've got it decompressed in it's own folder.  Now how do I install it?

---

### Post by narcolept on 2005-11-22
if you've extracted it, there should be an install script or a bin file that you can run with ./filename form a terminal.

---

### Post by myke on 2005-11-22
ok.  i opened up the terminal and typed:    /home/myke/Desktop/Downloads/thunderbird/thunderbird

this brings up a small menu that asks if i wan t to run the program or run it in the terminal.  either way, you can then launch the program.  that is fine but i want to have an icon to just to just launch the program directly.  what's my course of action?

---

### Post by Brunellus on 2005-11-22
you can make a launcher.  If you're in gnome, that's Applications>System Tools>Applications Menu Editor. 

now that you've done it, however, let me suggest that you delete it and reinstall via apt-get--that way you'll be able to get updates automatically.  The value of this is not to be underestimated.

---

### Post by myke on 2005-11-22
excellent.  i feel a bit on the dumb side of life.  i did create the launcher pointed toward the thunderbird shell script and it launched the program nicely.  i suppose that means that once i deflated the tarball, it was installed and just needed a launcher.  easier than i thought!  and yes, i'm on gnome now. i started with kde but switched to gnome as i find it a bit more polished.

i'll take your suggestion and reinstall via the package manager so as to get updates easier.  thanks for the tip!

---

### Post by Brunellus on 2005-11-22
in the future, try to use the repositories before resorting to downloading and installing individual .debs.  it makes the whole system that much easier to administer.

---

### Post by kperkins on 2005-11-22
[QUOTE=Brunellus]in the future, try to use the repositories before resorting to downloading and installing individual .debs.  it makes the whole system that much easier to administer.[/QUOTE]
While true on one level, he explicitely said that he did this as a learning experience.  There are many good reasons to install packages other than the official .debs, and it's good to learn how.
This isn't Windows, we're here for the freedom to do what we want with our computers, and we can't do that unless we learn how.
(and, myke, it's not always that easy :D, sometime it really sucks installing a program via a tar, because of dependencies.  Most source archives have an INTALL or README in them telling how to install the program, though.)

---

### Post by eaglescout1984 on 2005-12-11
[QUOTE=Brunellus]let me suggest that you delete it and reinstall via apt-get--that way you'll be able to get updates automatically.[/QUOTE]

I tried that and it tells me it can't find thunderbird. Is there a specific way I have to type thunderbird to download it? I had a similar problem with just Ubuntu packages, but that's fixed now.

---

### Post by aysiu on 2005-12-11
If you want to learn other ways to install stuff, the Mozilla .tar.gzs may not be the best way to go, as they use an installer script. Most .tar.gzs will require you to ./configure make make install.

---

### Post by eaglescout1984 on 2005-12-11
That's not helping me, this is exactly how I typed it ito the terminal:

sudo apt-get install thunderbird

It gave me:
E: Couldn't find package thunderbird

Any ideas?

---

### Post by aysiu on 2005-12-11
[QUOTE=eaglescout1984]
Any ideas?[/QUOTE] ```
sudo apt-get install mozilla-thunderbird
```

---

### Post by eaglescout1984 on 2005-12-11
Thanks, that did it. Now I just need to visit my school's website on setting up an account on thunderbird, again.

---

