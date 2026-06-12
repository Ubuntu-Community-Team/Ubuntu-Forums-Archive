---
title: "Mozilla Prism available for Linux"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by wildkarde on 2007-11-02
There is a working Prism "release" for Linux.  

It has not been announced yet by Mozilla which could only mean it's not final yet on the 0.8 release.

Nevertheless, for your goodness here it is.

[http://starkravingfinkle.org/projects/webrunner/prism-0.8-linux.tar.bz2](http://starkravingfinkle.org/projects/webrunner/prism-0.8-linux.tar.bz2)

---

### Post by FredB on 2007-11-02
Well, it is like xulrunner in a way. So what's the interest of it ?

---

### Post by wildkarde on 2007-11-02
Formerly known as webrunner, you can now run web apps as seaminly desktop apps.  

> Prism isn&#8217;t a new platform, it&#8217;s simply the web platform integrated into the desktop experience. Web developers don&#8217;t have to target it separately, because any application that can run in a modern standards-compliant web browser can run in Prism. Prism is built on Firefox, so it supports rich internet technologies like HTML, JavaScript, CSS, and <canvas> and runs on Windows, Mac OS X, and Linux.

More on this here.  [http://labs.mozilla.com/2007/10/prism/](http://labs.mozilla.com/2007/10/prism/)

---

### Post by FredB on 2007-11-02
Ok. I made a mistake. I mixed webrunner and xulrunner which are in some ways identical... Even twins, one is for local apps, the other for remote apps.

---

### Post by Leonivek on 2007-11-02
Awesome!  I actually installed Webrunner last week, but how do I install this new version??  For Webrunner, all I had to do was extract the folder and run webrunner, but this tarball is different.  Doesn't look like I can 'configure' or 'make install' either... Or am I insane and suffering from lack of coffee??  :)

---

### Post by Leonivek on 2007-11-02
bump

---

### Post by wildkarde on 2007-11-02
There's no need to compile anything with this.

All you have to do is extract the files and double click on prism.

That's all :)

if you already have webapps you want to run, you can run them by running the following command.

```
prism -webapp gmail.webapp
```

assuming it's in the same folder anyway.

Let me know.

---

### Post by Leonivek on 2007-11-03
That's what I thought, just like 'webrunner'... but that's the problem, there is no 'prism' to double-click on....

Oh never mind... as I was writing this I double-checked the extracted folder and for some reason, only the folders were extracted and 'prism' and 'application.ini' were ignored.

You see?  Lack of coffee was the reason!

---

### Post by keen3tix on 2007-11-26
I have some installation problems:

I put it in /opt/prism. I can start the programm with "/opt/prism/prism", but not with just "prism" - it says "bash: prism: command not found"

Also I am not sure where to put the webapp packages to make it work.

---

### Post by de_valentin on 2007-11-26
Looks cool, gonna try it tonight

---

### Post by wildkarde on 2007-11-26
> **keen3tix said:**
> I have some installation problems:

I put it in /opt/prism. I can start the programm with "/opt/prism/prism", but not with just "prism" - it says "bash: prism: command not found"

Also I am not sure where to put the webapp packages to make it work.

/opt/prism is not on your $PATH, and therefore it is not showing.  

Rather than doing something like that, try this instead.

```
gksu gedit /usr/share/applications/prism.desktop
```

and paste this

[Desktop Entry]
Encoding=UTF-8
Name=Prism
Comment=Prism
Exec=/opt/prism/prism
Icon=/opt/prism/chrome/icons/default/webrunner48.png
Terminal=false
Type=Application
Categories=Application;Network;
StartupNotify=true

---

### Post by keen3tix on 2007-11-27
Hi, thanks - works. Now I have an icon which starts Prism, but still: where do I have to install the packages for the webapp and how can I make icons for them?

---

### Post by ryphix on 2007-11-27
What are the advantages of Prism right now?
So far, I've only managed to make bookmarks on my desktop.

---

### Post by wildkarde on 2007-11-28
> **keen3tix said:**
> Hi, thanks - works. Now I have an icon which starts Prism, but still: where do I have to install the packages for the webapp and how can I make icons for them?

You can either start prism and put whatever URL you want, or you can use the webapps following this format.

```
/opt/prism/prism -webapp webapp/gmail.webapp
```

This is assuming that you have downloaded the webapps to a directory inside /opt/prism called webapps.  For these, you can go to the lower right corner and click "Install to desktop".

> What are the advantages of Prism right now?
So far, I've only managed to make bookmarks on my desktop.

The main selling point is that Firefox or whatever your browser of preference is sometimes crashes.  If you were composing an email or chatting (meebo/gmail), that can be an annoying.  So you can run website applications as if they were stand alone applications.

---

### Post by wildkarde on 2007-12-17
Attached is a small script I made for anyone who wants to get prism but doesn't want to download or create the icon.

It's very simple.  I'll try to keep it updated for future versions.


EDIT: Added a "Done" message to the script.

---

### Post by airtonix on 2008-01-02
> The main selling point is that Firefox or whatever your browser of preference is sometimes crashes. If you were composing an email or chatting (meebo/gmail), that can be an annoying.
Definitley, but this was more of a problem for me when using windows and IE(any version)....whereas firefox, just takes friggn long time to load, laggs & or freezes other tabbed pages when loading new tab page.

> So you can run website applications as if they were stand alone applications.How does this address the freezing or crashing issue?

Edit: if this is the sucessor to webrunner, where is the one for xulrunner? or have they both merged in to prism?

---

### Post by anojrs on 2008-03-29
If anyone is still facing any issues installing Prism on Gutsy, you can read my walkthrough.
[Installing Prism on Gutsy]("http://anojrs.blogspot.com/2008/03/installing-mozilla-prism-on-ubuntu.html")


Regards
Anoj
([http://anojrs.blogspot.com](http://anojrs.blogspot.com))

---

