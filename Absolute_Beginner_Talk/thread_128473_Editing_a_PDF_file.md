---
title: "Editing a PDF file"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2006-02-11
I would like to fill out a form which is in a PDF format.  How can I do this?  Please give me a step by step approach for installing programs if necessary.

Thanks

---

### Post by atoponce on 2006-02-11
You can open, edit and save the pdf in OpenOffice.org.

---

### Post by aysiu on 2006-02-11
KWord also can edit and export PDFs.

To install KWord, Alt-F2 and then type ```
gnome-terminal
``` for Gnome or ```
konsole
``` for KDE. Then type these two commands ```
sudo apt-get update
sudo apt-get install kword
```

---

### Post by engla on 2006-02-11
[QUOTE=aysiu]KWord also can edit and export PDFs.

To install KWord, Alt-F2 and then type ```
gnome-terminal
``` for Gnome or ```
konsole
``` for KDE. Then type these two commands ```
sudo apt-get update
sudo apt-get install kword
```[/QUOTE]
I don't understand why we keep throwing shell commands at beginners.

Yes, those commands always work, but there is a nice way to install programs: 

Synaptic is a great tool for managing packages. It's quite simple and you find it in the System menu: System > Administration > Synaptic Package Manager. Search for the package kwin, mark it for installation, and click apply

---

### Post by Bartender on 2006-02-11
racer -
Go to Applications>Office>OpenOffice.orgWriter & left-click

Start writing

When you're done, go to File>Export as PDF & left-click.  A new window comes up, you give your file a name.  Desktop is the default location.  Click Export.  I haven't made sense of the Linux file system yet so don't know how to move the file to some specific folder.

BTW, I stumbled onto directions for hastening OpenOffice's startup.  On my PIII 450 it useta take over a half minute.  Less than ten seconds now.

**Please note!! This is only if you have at least 512MB or more of RAM!  If you have less bump these values up a little bit at a time or pick some value roughly proportional to the values given below.  In other words, for 256 of total RAM try 50 for "Use for OpenOffice" and 10 for "Memory per object"**

Open OpenOffice.orgWriter.  Go to Tools>Options.  Is the first entry in the directory tree expanded?  It was when I first went there.  That's where you'll find "Memory".  Click on that.  Under Graphics Cache, bump the "Use for OpenOffice.org" MB value up to 100 or so.  
Now go to "Memory per object".  Nudge that up to 20 or thereabouts.  
Click OK, back out, close OO, see if that helps any.

If you've got more than 512, you can push these numbers higher, though there's probly a point at which nothing more is gained.

EDIT:  Whoopie  The OP asks how to fill out a pdf form, not create one.  Jeez, I gotta read these things more carefully

---

### Post by annsachd on 2006-02-11
You are misinformed atoponce.

OO software is not intended to read or edit PDF files.

---

### Post by atoponce on 2006-02-11
[quote=annsachd]You are misinformed atoponce.

OO software is not intended to read or edit PDF files.[/quote]

Oh really?  Then why did the developers include it in the software?  Why does it handle PDFs just fine?  Just curious.

---

### Post by aysiu on 2006-02-12
[QUOTE=engla]I don't understand why we keep throwing shell commands at beginners.[/QUOTE] Because I'm not physically standing behind these beginners. In a *written* forum, the easiest way to convey instructions is shell commands that can be *graphically* copied and pasted into the terminal.

It also leaves less room for error.

I don't want to say, "Open up this thing. Click on that icon. Then, you see the thing to left of that... blah blah blah" when I can just say, "Copy and paste these commands."

---

### Post by aysiu on 2006-02-12
[QUOTE=atoponce]Oh really?  Then why did the developers include it in the software?  Why does it handle PDFs just fine?  Just curious.[/QUOTE] Can you post a screenshot of how you import PDFs into OpenOffice? I haven't found that feature. Does it need a special plugin?

I've attached a screenshot of KWord's PDF import process--no plugins needed.

---

### Post by Estariel on 2006-02-12
> Can you post a screenshot of how you import PDFs into OpenOffice? I haven't found that feature. Does it need a special plugin?

As far as I know, OOo cannot open it. It can open PS files just fine, but it lacks PDF support. Kword however can do it.

I hope that KDE4's kpdf will have proper pdf handling (i.e. highlighting/marking and basic editing) - at least this is in its roadmap :)

---

### Post by aysiu on 2006-02-12
Maybe by "handle," atoponce meant just *exporting* to PDF? I haven't found an import PDF option in OpenOffice. I've poked around, too. That's why I asked if there was a special plugin.

---

### Post by atoponce on 2006-02-12
[quote=Estariel]As far as I know, OOo cannot open it. It can open PS files just fine, but it lacks PDF support. Kword however can do it.

I hope that KDE4's kpdf will have proper pdf handling (i.e. highlighting/marking and basic editing) - at least this is in its roadmap :)[/quote]

I stand corrected and I appologize for my quickness to judge.  I work with OpenOffice.org 2.0 at work every day, and regularly export plain text and Word Documents to PDFs.  Becuse of it's export capabilities, I figured it could import too, although I have never tried.  After trying, I see that PDFs are not listed in the filters.  How unfortunate.  As much as I love OpenOffice.org, I am becoming increasingly dissapointed as I stumble across things like this.

---

### Post by gingermark on 2006-02-12
[QUOTE=racermike1967]I would like to fill out a form which is in a PDF format.  How can I do this?  Please give me a step by step approach for installing programs if necessary.

Thanks[/QUOTE]

If you just want to fill out the form, ie just write "on-top" of it, without changing the formatting of the pdf at all, use The GIMP. If you are using Ubuntu you should already have that, in Kubuntu run Adept, search for it's entry, right click and select install, and then click "commit changes".

You have to open each page individually, but you can then use the text box option to write "on-top" of the pdf. It works quite well.

KWord does work, but I find it messes around with the pdf's formatting.

There is also a program called flpsed, which is soley intended for this purpose, but it's currently alpha software and I wouldn't recommend it. One to keep an eye on for the future though.

Hope that's what you were after.

---

