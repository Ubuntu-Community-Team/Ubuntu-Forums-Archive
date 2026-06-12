---
title: "HOWTO: Use Webshots on Xubuntu Wallpaper"
date: 2007-06-05
forum: Art &amp; Design
---

### Post by crazy25000 on 2007-06-05
Hello, 

Ive only been using Linux for about 2 weeks now. I use Webshots a lot and so do many other people. I could not figure out how to use Webilder on Xubuntu, so I figured a way around it, its not perfect, but it worked for me , so I thought yall would like it as well. 

1. Download Webilder at [www.webilder.org](www.webilder.org)
2. After you install, open Webilder by opening a terminal: Applications>>Accessories>>Terminal.
3. Type "webilder_desktop" in the terminal and Webilder should open. 
4. Import your Webshots files by clicking on File>>Import Webshots files in Webilder or you can press Control+I.
5. After you import your files, in Webilder, click on Tools>>Advanced.
6. Copy that directory that is listed, it is where all your Webshots files are located.
7. Right click on your Desktop and click on Desktop Settings.
8.Where it says Image and right under it is File:.....paste the Webilder directory here and then click on the icon next to the directory to choose the pictures. 

Hope this helps!!!! Please let me know if there are any problems

---

### Post by johnmbradford on 2007-07-14
It didn't work.  At line 3 the error message bash: webilder_desktop: command not found appears.
I've downloaded webilder, it's on the desktop.  It's called Webilder-0.6.2.tar.gz
John

---

### Post by maruchan on 2007-07-14
> I've downloaded webilder, it's on the desktop. It's called Webilder-0.6.2.tar.gz

That's only the download. And it's the wrong download. You want the section on the [download page]("http://www.webilder.org/download.html") that says "On Ubuntu or Debian." Or just do this:

Type Alt+F2, and then type "gksudo gedit /etc/apt/sources.list"

Then paste this text into the bottom of that file **if you are using Ubuntu Feisty**. If not, replace "feisty" with "edgy" or "dapper":

```
 
deb http://debian.websterwood.com/ feisty main
deb-src http://debian.websterwood.com/ feisty main
```

Then save the file and close the text editor.

Next, open up Synaptic from the system administration menu. Tell it to reload/refresh once it's open. Then search for webilder. Install webilder and webilter-gnome by right-clicking each and clicking "install", then click the "apply" button at the top of the Synaptic screen.

After this is finished, **then** Webilder is installed and you can complete the rest of this howto.

---

### Post by Mathrim on 2007-10-29
is there allready an installation procedure for the gutsy gibbon?

---

### Post by Ptero-4 on 2007-11-12
for gutsy the procedure is the same except that you'll need to compile webilder from sources since it haven't been packaged for gutsy yet.

---

