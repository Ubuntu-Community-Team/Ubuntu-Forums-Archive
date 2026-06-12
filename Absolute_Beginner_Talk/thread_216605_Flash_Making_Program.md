---
title: "Flash Making Program"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2006-07-15
Is there a free program for Linux similar to Macromedia Flash MX?

---

### Post by gThree on 2006-07-15
Someone mentioned this the other day ... looks like a start.

[http://ktoon.toonka.com/]("http://ktoon.toonka.com/")

---

### Post by loell on 2006-07-15
the debian package of ktoon has an unsatifiable depency

---

### Post by mikeoh on 2006-07-15
There is Flash for Linux though I don't know how useable it is.  

[http://f4l.sourceforge.net/]("http://f4l.sourceforge.net/")

---

### Post by shendric on 2006-07-16
> **loell said:**
> the debian package of ktoon has an unsatifiable depency

Yeah, I had that same problem.  Hopefully, someone will be able to create an Ubuntu package for it soon.

---

### Post by mostwanted on 2006-07-16
Might I ask what you need it for? If it's for school or something like that, I can understand. I needed Flash MX myself in my last term for my programming class (I learned all the tricks with that app back in ye olden days, so I also owned everyone on the course despite using Linux and not Windows hehe).

If you want it for making websites or something like that, realise that Macromedia/Adobe has no wish for an open, great web, they simply want to lock web developers to their platform using their binary, proprietary format and closed-source plugin which is only regularly updated for Windows and Mac. I used to make a lot of stuff in Flash, but I got smarter over the years.

Attached is a screenshot of Macromedia Flash MX running on my Ubuntu. It runs pretty much perfectly in WINE. If you just need Flash MX it will run, but MX 2004 and 8 don't run in Linux.

---

### Post by amcavoy on 2006-07-17
That would be fine.  How do I set it up like you have it?

Thank you.

---

### Post by mostwanted on 2006-07-18
Get an installer for Flash MX (trial or full version), it's an exe file. Make sure you have installed wine (it should be in multiverse or universe, if you're unsure how to install software, take a look at my guide).

Open a terminal, navigate to the folder where the file is and run that file with wine like this:

```
wine flash_mx_installer.exe
```

That will launch the installer, finish installing and then look up the hidden folder .wine/drive_c/ in your home directory. Flash wil be installed to the Program Files folder. Find the exe and run it using wine once again like this:

```
wine "/home/$USER/.wine/drive_c/Program Files/Macromedia/Flash MX/Flash.exe"
```

Then make a launcher on your desktop or on your panel, download the attached icon and drag and drop it onto the icon box in the "Create launcher"  window.

---

### Post by Stealth on 2006-07-18
Flash 8 DOES work in Linux, as I have it running ;) The only thing is my tablet won't work, and obviously you can't publish your Flash stuff in version 8 (just set it to Flash 7) until we get the player...

---

### Post by mostwanted on 2006-07-18
> **Stealth said:**
> Flash 8 DOES work in Linux, as I have it running ;) The only thing is my tablet won't work, and obviously you can't publish your Flash stuff in version 8 (just set it to Flash 7) until we get the player...

It does!? Were there any special steps into getting it working?

I didn't suspect that Flash 8 would work in Linux, since I tried WINEing Flash MX 2004 only a few months ago to no success.

---

