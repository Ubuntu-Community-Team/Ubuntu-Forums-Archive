---
title: "How can I get .tff fonts to work in OpenOffice?"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by RhynoWoody on 2008-03-16
If I was to say download Sidewalk from [here]("http://www.dafont.com/sidewalk.font"), could I get it to work in OpenOffice?  How can I accomplish this?

---

### Post by HereInOz on 2008-03-16
You may find this thread useful

[http://ubuntuforums.org/showthread.php?t=275202](http://ubuntuforums.org/showthread.php?t=275202)

---

### Post by Arthur Archnix on 2008-03-16
Download it to your desktop, and extract it. Then, open a terminal and change into the directory containing the font. Then make a new directory under /usr/share/fonts/truetype/. Then copy your new font to the new directory. Then regenerate the font cache.

That's the basic steps. If you can download it to your desktop and extract it and then open a terminal and change directories, these commands should take you the rest of the way:
```
sudo mkdir /usr/share/fonts/truetype/myfonts
```That makes a directory where you can put all your custom fonts.
```
 sudo cp ~/Desktop/FOLDER/*.ttf /usr/share/fonts/truetype/myfonts
```
That copies the fonts from a folder on your desktop (replace FOLDER with the actual name of your folder) to the newly created folder.
```
sudo fc-cache -fv
```That regenerates your font cache. Now you should be able to restart openoffice and use the fonts.

---

### Post by Oldsoldier2003 on 2008-03-16
> **RhynoWoody said:**
> If I was to say download Sidewalk from [here]("http://www.dafont.com/sidewalk.font"), could I get it to work in OpenOffice?  How can I accomplish this?

[http://www.openoffice.org/FAQs/fontguide.html](http://www.openoffice.org/FAQs/fontguide.html)

> Adding fonts

To install fonts for all OpenOffice.org applications it is sufficient that they can be found in the filesystem. OpenOffice.org searches the following directories for fonts:
  	Solaris 	Linux
1 	The directories /usr/openwin/lib/X11/fonts/Type1 and /usr/openwin/lib/X11/fonts/Type1/sun 	The directory /usr/X11R6/lib/X11/fonts/Type1
2 	Locale dependend directories found in the file /usr/openwin/lib/locale/"your_locale"/OWfontpath 	The output of the command /usr/sbin/chkfontpath or chkfontpath
3 	The fontpath as returned by XGetFontPath() 	Same as Solaris
4 	Directories given by the environment variable SAL_FONTPATH_PRIVATE, usually this variable is set by the soffice script to "openoffice_dir"/share/fonts/truetype 	Same as Solaris

If the fonts are installed in one of the above mentioned directories they should be available for OpenOffice.org. The fontpath is a comma separated list of directories that is searched for fonts by the XServer. Please note that as given in (4) OpenOffice.org searches this path and therefor examines the same font files as the XServer, if the XServer is running on the same machine. Therfore setting up the font for your local XServer is enough.

If you want to add fonts that are used exclusively in OpenOffice.org (i.e. not by the XServer) use the spadmin utility and add the fonts to your OpenOffice.org installation (to the directory openoffice_dir/share/fonts/truetype). Adding fonts with spadmin is described in the setup guide.

The same is true if you want to make sure that your fonts are available on a remote display connection. Since the fontpath is only valid on the machine the XServer is running on you are better off installing the fonts locally on your machine or on a directory that is shared between the XServer and OpenOffice.org.

Most home user will run their XServer locally. They only need to add the fonts to the local fontpath.

---

### Post by durand on 2008-03-16
Or...you could put the fonts in fonts:/// with nautilus. Then just restart open office.

---

### Post by John Jason Jordan on 2008-03-17
> **durand said:**
> Or...you could put the fonts in fonts:/// with nautilus. Then just restart open office.
I can't find any such folder in Nautilus.

---

### Post by forrestcupp on 2008-03-17
Open Nautilus in your user directory and click View and check the 'Show hidden files' box.  If there's not already a folder called .fonts, make a new folder called .fonts.  Make sure the '.' is in front.  That makes it a hidden folder.

Then you should be able to place your font files in that directory and it should work.

---

### Post by durand on 2008-03-17
Yeah, do what forrestcupp said....fonts:/// used to work....not sure why it doesn't anymore.

---

### Post by John Jason Jordan on 2008-03-17
> **durand said:**
> Yeah, do what forrestcupp said....fonts:/// used to work....not sure why it doesn't anymore.
OK. I already knew about the ~/.fonts folder. I was trying to use fonts:/// in Nautilus, but there is no place to type "fonts:///" in a Nautilus window, nor could I find a folder with that name.

What I could really use is a simple drag and drop way to install a font in the system for all users without having to refresh the font cache and stuff. It seems to me that a little utility to do this should be pretty simple to program. Maybe it exists but I just never found it.

---

### Post by durand on 2008-03-18
That was what fonts:/// was for.....I really don't know why it disappeared.

---

### Post by Arthur Archnix on 2008-03-18
> **John Jason Jordan said:**
> What I could really use is a simple drag and drop way to install a font in the system for all users without having to refresh the font cache and stuff. It seems to me that a little utility to do this should be pretty simple to program. Maybe it exists but I just never found it.

Here's something [http://packages.ubuntu.com/gutsy/utils/fontypython](http://packages.ubuntu.com/gutsy/utils/fontypython)

This seems to me to be much more complicated than created a folder, copying fonts to that folder, then regenerating the font cache.

But to each their own.

---

### Post by Martje_001 on 2008-03-18
> **John Jason Jordan said:**
> OK. I already knew about the ~/.fonts folder. I was trying to use fonts:/// in Nautilus, but there is no place to type "fonts:///" in a Nautilus window, nor could I find a folder with that name.
Click this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=62976&stc=1&d=1205844490[/IMG]

---

### Post by durand on 2008-03-18
thats not what i meant.

---

### Post by John Jason Jordan on 2008-03-18
> **Martje_001 said:**
> Click this:
I'd love it if my Nautilus windows looked like that. Here is what mine look like:

I've poked all over Nautilus but can't find any options to make it look like yours. I'm on gutsy x86_64, Gnome 2.20.1, 10/17/2007.

---

### Post by Martje_001 on 2008-03-18
Go to *view* and check the first four thing you can check. I think that's it ;)

---

### Post by John Jason Jordan on 2008-03-18
> **Martje_001 said:**
> Go to *view* and check the first four thing you can check. I think that's it ;)
It turns out that what I needed to do was go to Edit > Preferences, then the Behavior tab and change it to Always Open in Browser Windows. That made it give me the location bar. And typing "fonts:///" in the location bar gives me a view of all my installed fonts. Dragging new fonts into the window makes them work. This is on Gutsy 7.10 with Gnome 2.20.1.

---

