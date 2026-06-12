---
title: "Installing fonts"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by Torquemada28 on 2006-06-23
As far as I can tell, you can install a font in Ubuntu by right-clicking on the font file  and choosing Actions=>Install. The problem is, I have over 1200 fonts that I want to install but if I select them all and right-click, the Install option no longer appears in the Actions sub-menu.
Is there a program I can use to install multiple fonts or a method that would be suitable for installing so many fonts at once?

I have another question regarding fonts.
In Windoze, when you install a font, that font is immediately available for use in applications such as Photoshop, Word and Dreamweaver.
Is this the same in Ubuntu? Will GIMP allow me to use any font I have installed on the OS, or does it (and other applications) maintain their own font libraries seperate from the OS?

Thanks in advance.

---

### Post by _infinity on 2006-06-23
Open your home folder and make sure that "Show Hidden Files"  from the view menu is checked.Create a new folder called ".fonts" and open it.Drag and drop all your fonts to this folder.You will probably need to restart any applications that use fonts in order for them to be registered,or you can alternatively log out and then back in.

---

### Post by Torquemada28 on 2006-06-23
[QUOTE=_infinity]Open your home folder and make sure that "Show Hidden Files"  from the view menu is checked.Create a new folder called ".fonts" and open it.Drag and drop all your fonts to this folder.You will probably need to restart any applications that use fonts in order for them to be registered,or you can alternatively log out and then back in.[/QUOTE]

Thanks, but it didn't work.
I followed your instructions but neither Open Office or GIMP allowed me to use the fonts I copied over.

---

### Post by Torquemada28 on 2006-06-24
*bump*

Come on. Someone must know something about this issue.

---

### Post by robotron2084 on 2006-06-25
Run:
sudo fc-cache -f -v
And this should rebuild your font cache and it will be available. You will probably have to restart your program.

---

### Post by gingermark on 2006-06-25
This is nice and easy in Kubuntu, do the following:

K-Menu --> System Settings --> Font Installer, then click "Administrator Mode".

Now click "Add Fonts". navigate to your folder with your 1200 fonts and press 'Ctrl'+'A', then click "Open" (you may need to click it twice).

The fonts should then be available the next time you open any application you need them in.

---

### Post by perrin on 2006-06-30
Hi Torquemada28

I'm not sure if you solved this one yet?
This is for Ubuntu - may also work in Kubuntu, but I would use a different approach myself.
What I do is I copy all of my fonts that I want into a folder I create (e.g myfonts) under /usr/share/fonts (so mine is /usr/share/fonts/myfonts)
I run a terminal with the command "sudo nautilus" since I need administrator priviledges to copy the fonts to the folder.
Depending on the number of fonts you are going to copy, it may take some time.  I have around 3200 fonts, which takes around ten to twenty minutes.

I'd love to hear what the others think too.

---

### Post by vasimakhtar on 2006-07-03
Hi.
I did the same and able to read all FONTS IN GUJARATI language. Wonderful job..
thanks


[QUOTE=perrin]Hi Torquemada28

I'm not sure if you solved this one yet?
This is for Ubuntu - may also work in Kubuntu, but I would use a different approach myself.
What I do is I copy all of my fonts that I want into a folder I create (e.g myfonts) under /usr/share/fonts (so mine is /usr/share/fonts/myfonts)
I run a terminal with the command "sudo nautilus" since I need administrator priviledges to copy the fonts to the folder.
Depending on the number of fonts you are going to copy, it may take some time.  I have around 3200 fonts, which takes around ten to twenty minutes.

I'd love to hear what the others think too.[/QUOTE]

---

### Post by dangermouse28 on 2006-07-05
Hi

I too have a font problem...

I've installed fonts into /usr/share/fonts/truetype and done the fc-cache thing. The fonts show up in everything but openoffice. Why doesn't openoffice see them?:confused: 

Thanks

---

### Post by TorxT3D on 2006-07-05
create the .fonts folder, put them in there and use this command

sudo fc-cache -f -v

works for me and i added tahoma, can now be used in openoffice, etc..

---

### Post by markfasano on 2006-07-06
[QUOTE=perrin]Hi Torquemada28

I'm not sure if you solved this one yet?
This is for Ubuntu - may also work in Kubuntu, but I would use a different approach myself.
What I do is I copy all of my fonts that I want into a folder I create (e.g myfonts) under /usr/share/fonts (so mine is /usr/share/fonts/myfonts)
I run a terminal with the command "sudo nautilus" since I need administrator priviledges to copy the fonts to the folder.
Depending on the number of fonts you are going to copy, it may take some time.  I have around 3200 fonts, which takes around ten to twenty minutes.

I'd love to hear what the others think too.[/QUOTE]

Solid technique. This works. Thanks.

---

### Post by dangermouse28 on 2006-07-06
Hi markfasano

Do the fonts show up in Openoffice?

---

