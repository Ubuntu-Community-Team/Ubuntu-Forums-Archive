---
title: "Configure Script Error (intltool)"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-08-14
I was trying to install the latest nimbus theme from [http://dlc.sun.com/osol/jds/downloads/extras/](http://dlc.sun.com/osol/jds/downloads/extras/) .

My problem is that, when I ran the configure script, there was an error message. Here is the end of the configure script.

```
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for intltool >= 0.23... awk: cmd. line:1: fatal: cannot open file `./intltool-update.in' for reading (No such file or directory)
awk: cmd. line:1: fatal: cannot open file `./intltool-update.in' for reading (No such file or directory)
 found
./configure: line 3649: test: : integer expression expected
configure: error: Your intltool is too old.  You need intltool 0.23 or later.

```

What should I do to fix this?

---

### Post by 5-HT on 2007-08-14
Looks like either your intltool version is too old or you do not have it installed, you'll need to install intltool  >= 0.23. Funny, because all versions of Ubuntu since Dapper have included a more recent version. May have to grab it from upstream.
cheers,

---

### Post by wersdaluv on 2007-08-14
> **5-HT said:**
> Looks like either your intltool version is too old or you do not have it installed, you'll need to install intltool  >= 0.23. Funny, because all versions of Ubuntu since Dapper have included a more recent version. May have to grab it from upstream.
cheers,

I have intltool and intltool-debian installed. Actullay, I have version 0.32.5 installed.

---

### Post by 5-HT on 2007-08-14
Could be a Debianism/Ubuntuism with the package, or with the config script not looking in the right place for intltool-update.in. Is there an option in the config script to allow specifying the path to intltool-update.in? Is the file there? If so, you _could_ try to just remove that integer check for intltool from the config script: not sure if that would do it though if there's still an issue with the expected paths.

---

### Post by wersdaluv on 2007-08-14
I found a perfect thread for this but the problem is that, it is in Chinese.

See [http://forum.ubuntu.org.cn/about66238.html&sid=8469a24d5dba5221e5711a6f64fa59a2](http://forum.ubuntu.org.cn/about66238.html&sid=8469a24d5dba5221e5711a6f64fa59a2)

The poster, junsuck said something about the errors with the configure script of the nimbus theme. 

Can you somewhat understand the solutions he gave from his post? He gave code's there but I can hardly relate because of my lack of familiarity.

---

### Post by schorsch on 2007-08-14
Weird, 

the configure scripts expects some intltool-files in the actual directory with the nimbus sources:

```
ln -s /usr/share/intltool/intltool-update.in intltool-update.in
ln -s /usr/share/intltool/intltool-extract.in intltool-extract.in
ln -s /usr/share/intltool/intltool-merge.in intltool-merge.in

```

In addition to that you have to install the package "icon-naming-utils"; after that configure and make are running smoothly

---

### Post by wersdaluv on 2007-08-14
I found a good source on installing the nimbus theme, but it was in some other language. I think it's Italian.

Here it is [http://pollycoke.wordpress.com/2007/03/06/gnome-installare-il-tema-predefinito-di-solaris-su-ubuntu-howtodeb/](http://pollycoke.wordpress.com/2007/03/06/gnome-installare-il-tema-predefinito-di-solaris-su-ubuntu-howtodeb/)

I hope there would be someone to translate the instructions for us.

---

### Post by 5-HT on 2007-08-14
> **schorsch said:**
> Weird, 

the configure scripts expects some intltool-files in the actual directory with the nimbus sources:


 ```
cannot open file `./intltool-update.in' 
```Argh, missed that: thanks!
[quote=[wersdaluv]]("http://ubuntuforums.org/member.php?u=202558") found a good source on installing the nimbus theme, but it was in some other language. I think it's Italian.

Here it is [http://pollycoke.wordpress.com/2007/...untu-howtodeb/]("http://pollycoke.wordpress.com/2007/03/06/gnome-installare-il-tema-predefinito-di-solaris-su-ubuntu-howtodeb/")

I hope there would be someone to translate the instructions for us. [/quote]
You can use google's translate feature for the whole page.
Just making sure you install the required dependencies, and running the install commands (using the autogen.sh script instead of the configure script) will get the job done. Though  [schorsch]("http://ubuntuforums.org/member.php?u=99540") gave a nice workaround for the configure script. Not sure about prefixing it to /usr though, perhaps /usr/local is more appropriate?
cheers,

---

### Post by wersdaluv on 2007-08-14
> **schorsch said:**
> Weird, 

the configure scripts expects some intltool-files in the actual directory with the nimbus sources:

```
ln -s /usr/share/intltool/intltool-update.in intltool-update.in
ln -s /usr/share/intltool/intltool-extract.in intltool-extract.in
ln -s /usr/share/intltool/intltool-merge.in intltool-merge.in

```

In addition to that you have to install the package "icon-naming-utils"; after that configure and make are running smoothly

What are those codes supposed to do? Please enlighten me. They worked, but I don't understand what they did.

:KS

---

### Post by schorsch on 2007-08-14
The configure script searches in the actual directory for the three mentioned files and does not look in the directory where they really are. So i just created three so called symlinks in the directory with the sources to the real files so that the configure scripts just followed these links. It is a little bit of betraying .... :-)

---

### Post by wersdaluv on 2007-08-14
After successfully installing the theme, it was not in the list of themes in my "Theme Preferences"

How do I choose the nimbus theme?

---

### Post by 5-HT on 2007-08-14
> **wersdaluv said:**
> After successfully installing the theme, it was not in the list of themes in my "Theme Preferences"

How do I choose the nimbus theme?

How did you install it? It's best to directly unpack into ~/.themes rather than doing it the GUI way
Is the theme listed in ~/.themes ? If you go into customize for a theme, are Nimbus controls and window borders there?
Is there an index.theme file in it's top-level directory? If not, you'll need to make one (just copy of another one from a different theme and edit accordingly).

---

### Post by wersdaluv on 2007-08-14
> **5-HT said:**
> How did you install it? It's best to directly unpack into ~/.themes rather than doing it the GUI way
Is the theme listed in ~/.themes ? If you go into customize for a theme, are Nimbus controls and window borders there?
Is there an index.theme file in it's top-level directory? If not, you'll need to make one (just copy of another one from a different theme and edit accordingly).

I installed it by sudo make installing from the folder I extracted from nimbus-0.0.8.tar.bz2.

Under my .themes folder, nimbus-0.0.8 is there, but the nimbus-0.0.8 folder contains only and "icons" folder. 

If I customize a theme, the nimbus controls and window borders are not there.

I do not see an index.theme file under themes/nimbus-0.0.8. Is themes/nimbus-0.0.8 the top-level directory that you were referring to?

Edit: 

I copied my index.theme file from the folder of my custom "Tango Clearlooks" theme, but I still did not see nimbus as a choice theme from "Theme Preferences."

Thank you so much for your help, by the way!!! :)

---

### Post by wersdaluv on 2007-08-14
I had a folder where I extracted the nimbus-0.0.8 tar.bz2. I copied that folder to my .themes folder. After that, nimbus became one of the choices in "Theme Preferences" but the nimbus controls theme and the window decoration theme still wasn't there.

---

### Post by 5-HT on 2007-08-14
> **wersdaluv said:**
> I had a folder where I extracted the nimbus-0.0.8 tar.bz2. I copied that folder to my .themes folder. After that, nimbus became one of the choices in "Theme Preferences" but the nimbus controls theme and the window decoration theme still wasn't there.

Hmmm, I don't use nimbus so I can't say for sure, but perhaps the install didn't go as planned. Do you see the engine in /usr/lib/gtk-2.0/2.10.0/engines (or whichever path is used on your system--I'm not on a Ubuntu box right now).

---

### Post by wersdaluv on 2007-08-14
I copied my /usr/local/share/themes/nimbus folder to /home/user/.themes/nimbus. 

This time, I already have the nimbus window decoration and icons, but not the controls. WHat can I do to have the nimbus controls?

Under my /home/user/.themes/nimbus/ folder, I have a gtk-2.0 folder, metacity-1 folder, and an index.theme file.

---

### Post by wersdaluv on 2007-08-14
> **5-HT said:**
> Hmmm, I don't use nimbus so I can't say for sure, but perhaps the install didn't go as planned. Do you see the engine in /usr/lib/gtk-2.0/2.10.0/engines (or whichever path is used on your system--I'm not on a Ubuntu box right now).

I have a /usr/lib/gtk-2.0/2.10.0/engines folder with a lot of files on it.

---

### Post by 5-HT on 2007-08-14
> **wersdaluv said:**
> I copied my /usr/local/share/themes/nimbus folder to /home/user/.themes/nimbus. ...
Under my /home/user/.themes/nimbus/ folder, I have a gtk-2.0 folder, metacity-1 folder, and an index.theme file.
Looks like you have all the proper direcotries there, not sure what's going on (BTW, if the theme's in /usr/local/share/themes there shouldn't be a need to install it on a per-user basis in ~/.themes)

> **wersdaluv said:**
> I have a /usr/lib/gtk-2.0/2.10.0/engines folder with a lot of files on it.
the nimbus engine should be called something like 'libnimbus.so' or similar.

---

### Post by wersdaluv on 2007-08-14
> **5-HT said:**
> Looks like you have all the proper direcotries there, not sure what's going on (BTW, if the theme's in /usr/local/share/themes there shouldn't be a need to install it on a per-user basis in ~/.themes)


the nimbus engine should be called something like 'libnimbus.so' or similar.

I did not see any libnimbus or anything similar.

What do you think could be the problem why I do not have the libnimbus installed?

---

