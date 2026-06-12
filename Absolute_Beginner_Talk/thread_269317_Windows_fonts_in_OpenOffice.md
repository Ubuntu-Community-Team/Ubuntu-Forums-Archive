---
title: "Windows fonts in OpenOffice"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by feap on 2006-10-01
I'm currently applying for jobs and writing my resume in OpenOffice. Therefore what I see on my OO screen has to absolutely, positively match whatever the recruiter sees. I have to export the files to .doc format and any Linux-specific fonts get replaced by something else, formatting goes out the window and I don't get the job.

While perfect match might be too much to ask (is it?), is it possible to install Windows TrueType fonts (specifically Times New Roman) and use it in OO? That way I could work with the fonts and hopefully get similar results. It seems that I still would need to use another (windows) computer to verify that it looks good (*sigh*).

And no, it's not always possible to use .pdf.

---

### Post by coffeecat on 2006-10-01
Open Synaptic Package Manager (I think you need Universe and possibly Multiverse repositories enabled) and select and download msttcorefonts. That'll give you Times New Roman and others.

A word of warning. Even if you save as a .doc file you'll almost certainly find that page breaks occur in different places with different machines running different OSs configured for different printers. The only way round this I know is to export your file as a .pdf. You can do this from the file menu in OOo.

**Edit** - sorry, just noticed your comment about pdf files, but I'll let mine stand. This business of page breaks can occur (I believe) even between different Windows computers running different printers which is why pdf files (if you can use them) are useful.

---

### Post by feap on 2006-10-01
Thank you for the quick reply! Yes, I'd prefer using .pdf for various reasons, but for some reason many sites don't accept them. And yeah, I know that pagination and formatting changes even across Word installs, but now that I have the windoze fonts it should at least alleviate the problem :)

---

### Post by coffeecat on 2006-10-01
Best of luck with the job applications.

There's a quick and easy way of installing .ttf fonts if you have the .ttf files handy. This is for the Gnome desktop. Be warned that you may be falling foul of the law if you use copyrighted font files.

Go to System > Preferences > Font. A Font Preferences window opens. Click on the Details button. In the new window click on the 'Go to font folder button'. This opens a Nautilus Window that is a virtual folder of all the fonts installed on your system. Simpy drag and drop the .ttf file(s) into the window. Restart the xserver with ctr-alt-backspace or a reboot and your new fonts will now be available for use. If you have KDE or want a more geeky (i.e. difficult :wink:) way of doing it, suggest you search these forums. There have been several threads.

---

### Post by Dale61 on 2006-12-07
In my experiences with OO (going back to v1.0.0), I've found that retaining the same format is difficult unless the recipient is also using OO, even if saving an OO document to .doc.

If it's important to retain formatting, you can either print off your original and forward it via fax, export it as a .pdf (who doesn't have at least a pdf reader these days?), or send a copy of the original via snail mail.

Alternatively, you could always include a disclaimer stating that your resume was created using OpenOffice, and that some formatting may differ than that of the original.  Point out that a copy of the original can be forwarded if needed.

Then again, if a recruiter is more concerned about the formatting of the document as opposed to what you have written, is the job really worth it?

---

