---
title: "replacement for Dreamweaver"
date: 2008-12-21
forum: Art &amp; Design
---

### Post by terry@softreq.com on 2008-12-21
Is there software I could use in Ubuntu that would (sort of) replace Dreamweaver?

ie. a WYSIWYG html editor with a built in FTP client?

Thanks, Terry

---

### Post by jrusso2 on 2008-12-21
Really there is nothing like Dreamweaver for Linux.  Kommander is about the closest to it.

The rest of them are on WYSISYG, but they are Web page editors.

---

### Post by terry@softreq.com on 2008-12-21
jrusso2, 

Thanks for your response.

Would Kommander be the best of the bunch?

I'd only use it to pull down web pages off a server, do some HTML edits, and FTP the page back to the server. 

Thanks, Terry

---

### Post by kayosiii on 2008-12-21
Kompozer is probably your best bet - but FTP integration at the filesystem level (on KDE at least) means that specific support for uploading to FTP is not necessarily needed - ie you can work directly with the files on your ftp server

---

### Post by terry@softreq.com on 2008-12-21
Okay, I will give Komposer a shot thanks!

---

### Post by !nkubus on 2008-12-21
I would try aptana studio, it's based on eclipse and is absolutely fantastic, there is a lot of plugins also availabe for it.

Hope it helps :)

---

### Post by Peter76 on 2008-12-22
I use bluefish for this; it is an editor, so no wysiwyg, but it can open remote documents ( ie on an ftp server ) and save them there. I think you need to use Gnome to use this though.

---

### Post by simonbanyard on 2008-12-22
At the risk of sounding like an arrogant techie type, learn to code by hand. That way you only ever need Vi or Emacs or Kate or GEdit or <insert favorite text editor here>. You get far more satisfaction and its surprisingly easy too! I can recommend the excellent Head First HTML & CSS as a staring point.

---

### Post by terry@softreq.com on 2008-12-22
Simon,

I do 90 percent of my coding by hand - I just use the WYSIWYG editor to check the work a bit. 

If I don't need the WYSIWYG view, does that open more options?

The main thing to be able to edit code, run the html on my PC, and then FTP to/from the server.

I could probably use any "notepad" style editor I suppose, and download a separate FTP client.

Given all the above, does this change anyone's recommendation?

Thanks again! 

Terry

---

### Post by alex.rayu on 2008-12-22
Terry is you do most of the coding by hand I suggest running geany or, more textate-like Komodo Edit. And preview in browser. 

I user DreamWeaver when I were learning, and when I learned the right clean way of coding, I switched to a lighter program.

---

### Post by AJB2K3 on 2008-12-24
In my experience on both windows and linux, no WYSIWYG has ever rendered it the same way as it appears online so I have FF+opera open to preview/test pages.

Yep I use the text editior.

WYSIWYG = Amaya by the W3C.

---

### Post by namdung on 2008-12-24
Dreamweaver works fine under WINE. Does it give 100% functionality is a question. But I'd recommend a FOSS software like Seamonkey.

---

### Post by hessiess on 2008-12-25
Learn HTML and CSS, then use any half decent text editor, like Vim or EMACS. Visual editiors output terrable code.

---

### Post by macintosh on 2008-12-26
KompoZer is the nearest I found!

---

### Post by dannytatom on 2008-12-26
> **AJB2K3 said:**
> In my experience on both windows and linux, no WYSIWYG has ever rendered it the same way as it appears online so I have FF+opera open to preview/test pages.

Yep I use the text editior.

WYSIWYG = Amaya by the W3C.

+1

Any text editor, preferably with colorful syntax, is best.

---

### Post by turezky on 2008-12-26
Somebody mentioned it above, but it went unnoticed.
Try Aptana. It has WYSIWIG, code suggest (for most languages e.g. html, php and I think CSS), integration with the javascript libraries and loads more.
I can surely say it's a fair replacement for Dreamweaver if you value features mentioned above...

---

### Post by Sand &amp; Mercury on 2008-12-26
I used Kompozer when I started out after I was still a bit sore from having no Dreamweaver around (While it is compatible with Wine, if I want to develop legally on my own it is not compatible with my budget). It does work very well, if you want something whipped up very quickly. It's not quite as rich as Dreamweaver, but it is quite complete for producing HTML and CSS. While I do most of my layouts by hand with gedit, I still use Kompozer to do a few things when I can't get my head around them properly. The good thing about WYSIWYG editors is that they generate a lot of your code very quickly, even if it's not as clean as doing it by hand, that can be cleaned up on your part afterwards.

---

### Post by wheezer on 2009-01-02
> **!nkubus said:**
> I would try aptana studio

Ink,

I've used Aptana studio for years, and love it. There's nothing even close. (Handcoding may be fine for simple HTML webpages, but robust ajax, rails, php and other develpment need a lot of IDE help that Aptana provides).

Anyway, so now I have upgraded to Ubuntu Intrepid, and I cannot start the Aptana workbench at all without getting cryptic errors about "SWT errors." I think it's the old internal browser blowing up.  Are you running under intrepid ok? Any idea what my fix might be? Aptana hasn't responded, and if experience is my guide, it could be days.


Thanks

---

### Post by wheezer on 2009-01-02
This was the fix. You need an earlier xulrunner
1. Install xulrunner 1.8.1.16 with Synaptic
2. Start aptana with the attached shell script (copy to aptana directory). I run it with a shell in the aptana directory because it expects to find AptanaStudio in the current directory. You can change it to the absolute path to where AptanaStudio is stored.

---

### Post by Niva on 2009-01-05
Wow someone wants to go back to dreamweaver.  I hated that package and everything I had to build with it with a passion.  

Honestly, frontpage was so much more pleasant for me to work with.

Best thing you can do is get away from all of it.  Use wordpress and surrender your soul to PHP and CSS, I've done it now, I'm never going back to any of those bloated useless packages.

---

### Post by littlemog on 2009-01-05
At its current form, DW is hardly close to any comparsion to Frontpage anymore though... talk about the FP days... FP used to churn out the worst code. :(

> **Niva said:**
> Wow someone wants to go back to dreamweaver.  I hated that package and everything I had to build with it with a passion.  

Honestly, frontpage was so much more pleasant for me to work with.

Best thing you can do is get away from all of it.  Use wordpress and surrender your soul to PHP and CSS, I've done it now, I'm never going back to any of those bloated useless packages.

---

### Post by hessiess on 2009-01-08
> **Niva said:**
> Wow someone wants to go back to dreamweaver.  I hated that package and everything I had to build with it with a passion.  

Honestly, frontpage was so much more pleasant for me to work with.

Best thing you can do is get away from all of it.  Use wordpress and surrender your soul to PHP and CSS, I've done it now, I'm never going back to any of those bloated useless packages.

Frountpage outputs absolutely diabolical code ;)

---

### Post by sav2005 on 2009-01-10
> **terry@softreq.com said:**
> Is there software I could use in Ubuntu that would (sort of) replace Dreamweaver?

ie. a WYSIWYG html editor with a built in FTP client?

Thanks, Terry

Install Quanta with synaptic. It's more like HomePage than Dreamweaver but has some basic WYSIWYG features and FTP built in. It uses the Kommander editor and Konqueror so it installs some KDE libraries. I use it a lot and like it, it is more feature rich than Bluefish and organises your projects better.

Laurie

---

