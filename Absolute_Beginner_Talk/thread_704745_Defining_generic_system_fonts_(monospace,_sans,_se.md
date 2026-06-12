---
title: "Defining generic system fonts (monospace, sans, serif, etc.)?"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by duesen on 2008-02-22
How do I specify which fonts correspond to generic fonts in Ubuntu? (serif, sans, monospace, etc.) :confused:

TIA!

---

### Post by bwhite82 on 2008-02-22
Could you clarify your question please?

---

### Post by duesen on 2008-02-22
> **Soldierboy said:**
> Could you clarify your question please?

Well, if you go to System > Preferences > Appearance > Fonts, you will see that there are generic font names available in the font list: Sans, Monospace, Serif. Similarly, in Firefox font settings (Edit > Preferences > Content > Font & Colors) you will see similar generic names.

These names are not real font names, but rather generic aliases. How do I know which actual fonts are used in their place? How do I change these assignments?

Thanks!

---

### Post by iris-n on 2008-06-07
Hi duesden.

Hope's not to late to be useful, i've found the answer. Run ```
fc-match <alias>
``` in the terminal to see to what font they resolve. In my machine, they were all defaulting to DejaVu. As to how to change it, don't have a clue, seems it's hardcoded.

---

### Post by qns8dn3 on 2008-06-09
Edit the XML file ~/.fonts.conf (create it first if not exist) to change default fonts for Sans, Serif and Monospace. 

Here is the content of my custom ~/.fonts.conf file. 

```
<?xml version="1.0"?><!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

 <alias>
	 <family>sans-serif</family>
	 <prefer>
		 <family>Lucida Grande</family>
		 <family>Malgun Gothic</family>
	 </prefer>
 </alias>

 <alias>
	 <family>monospace</family>
	 <prefer>
		 <family>Lucida Console</family>
		 <family>Malgun Gothic</family>
	 </prefer>
 </alias>


</fontconfig>
```

This sets English texts with Sans font to be rendered with Lucida Grande font and Korean texts to be rendered with Malgun Gothic font. (Because Lucida Grande doesn't support Korean text, Korean text falls back to the second one Malgun Gothic) And sets English texts with Monospace font to be rendered with Lucida Console and korean texts with Monospace font to be rendered with Malgun Gothic.

To edit an XML file such as .fonts.conf, use any text editor or an XML editor such as [XML Copy Editor](http://xml-copy-editor.sourceforge.net/). Before saving an edit, validate it to be sure of no mistakes. 

You may need to enter "sudo fc-cache -f -v" in a terminal or restart X to see the change.

For an easy overview of installed fonts and comparison, install gnome-specimen from Synaptic Package Manager and access Applications > Graphics > Specimen Font Previewer. This is useful when deciding which fonts to use for generic fonts.

---

