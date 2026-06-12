---
title: "Error on screenshot from term"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by fobnicat on 2007-04-11
I went to terminal and entered

```
gnome-screenshot
```

when i did, it took the screen shot but I got a bunch of errors 

```
fobnicat@fobnicat-desktop:~$ gnome | screenshot
bash: screenshot: command not found
bash: gnome: command not found
fobnicat@fobnicat-desktop:~$ gnome-screenshot

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel-screenshot:19292): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
handle_transfer_vfs_error!
fobnicat@fobnicat-desktop:~$ 

```

any ideas?

---

### Post by fobnicat on 2007-04-11
ok so I thought that it saved the screenshot but i tried it again and realized that after i name the file and try to save it that is when 
```
handle_transfer_vfs_error!
fobnicat@fobnicat-desktop:~$
```
shows up...

---

### Post by LaurelLynn on 2007-04-11
Dear fobnicat,

According to this link:

[http://www.macewan.org/2006/11/19/gtk-warning-unable-to-locate-theme-engine-in-module_path-pixmap/](http://www.macewan.org/2006/11/19/gtk-warning-unable-to-locate-theme-engine-in-module_path-pixmap/)

You are missing one dependancy which should be loadable with the command:

sudo apt-get install gtk2-engines-pixbuf

This was on a different forum, but should work because the post was from someone also using  Edgy.

---

### Post by fobnicat on 2007-04-11
awesome...

well that got rid of the GTK WARNING.. but I am still getting th error
```
handle_transfer_vfs_error!
fobnicat@fobnicat-desktop:~$
```

---

### Post by LaurelLynn on 2007-04-11
Dear fobnicat,

When I Googled that error, all the pages were source code patches. That says to me there is or was a known problem in Gnome. By now the patch is probably in the latest version.

I would try upgrading Gnome, and if that didn´t work I would upgrade all the installed packages. Take notes, as this is useful stuff to know  (I got it from the Linux Cookbook, which I keep close at hand):

# apt-get update                          (updates the list of available packages)

# apt-get  -u  upgrade gnome      ( upgrades, but does not remove any packages to resolve dependancies)

or 

# apt-get  -u  dist-upgrade  gnome    (removes or installs new packages, as needed, to resolve dependancies)

The -u  prompts you before making changes, which could be a bit tedious, so it is optional.

To do the same thing for every package installed, just remove the ¨gnome¨ from the commands (with -u this would could get **really** tedious).

Hopefully getting the lattest version will resolve the problem.

---

### Post by fobnicat on 2007-04-11
when you say packages, what do you mean?

---

### Post by LaurelLynn on 2007-04-11
That is an interesting question?

Package really just reffers to a bundle of that stuff that is zipped up into one ¨.deb¨ file and posted to a repository.

Sometimes it is a whole application, sometimes it´s just a library, some header files, or the documentation for an application.

When someone tells to:

$  sudo apt-get  install  something

¨something¨ is known as the package name.  The power of ¨apt-get¨ is that it will usually figure out if any other pacakes are needed and get them too.

In the command I gave you ¨gnome¨ is the name for your overall desktop. It will have many other dependancies that apt-get will upgrade at the same time.

Synaptic,  which is run from the top bar   System->Administration->Synaptic Package Manager
Is a graphical front-end for apt-get.

Now that I think of it,  Synapatic has this nice little button  ¨Mark all Upgrades¨.  Hitting that and then the ¨Apply¨ button when it is ready should upgrade all the software you have installed to their lattest version.

That might solve a lot of your problems.

---

### Post by fobnicat on 2007-04-11
awesome! ill give it a shot and let you know! thanks for your help!

---

### Post by fobnicat on 2007-04-11
interesting.. nothign was marked..
 guess iw ill have to try it the old way...

could it have somethign to do with having fluxbox installed although I am not running it? i also have pypanel istalled and still ahve a few bugs with it that I am hoping to work out soon....

---

### Post by LaurelLynn on 2007-04-12
There could be some conflict, but I don´t know the inner working of screenshot, so I would only be guessing at what it could be. You could always unistall programs you think might conflict, and see it works.  Reinstalling if not. Repeat...Repeat...  It´s an option but a very time consuming one with a low probabilty of success.

As I said before, it looks like it is a known problem, and there are source code patches available.  If upgrading hasn´t solve the problem, then unfortunately it would seem that the fix has not yet filtered through system to the repositories yet.  

Unless you are prepared to download the source, apply the patches and recompile the program. You either have to wait for the patch to reach the repositories.  Or go to Gnomes website to load the most recent version from the source.  Or look for other screen capture programs, I´m sure linux has several.

At least those are all the options that come to mind...Sorry :(

---

### Post by fobnicat on 2007-04-12
oh welll... thanks for your help! I atleast learned a few things...

---

### Post by RedSquirrel on 2007-04-13
In Fluxbox, you can use Imagemagick. [Here]("http://ubuntuforums.org/showthread.php?t=406662") is another thread discussing screenshots in Fluxbox.

---

