---
title: "Where's the GUI?"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by jsheldon on 2007-05-11
I downloaded Ubuntu 7.0 Server because I wanted to play around with the LAMP server components among other things.

The system boots in command line and my UNIX commands are ok but would like to adventure around the system more visually.

How can I enable the gui for ubuntu server?

Thanks

---

### Post by aysiu on 2007-05-11
Servers don't come with GUIs.

Do you need one? If so, I or someone else can help you install a minimalist one.

---

### Post by compmodder26 on 2007-05-11
Server edition is command line only by default.  On a production system the GUI is considered a resource waste and can potentially introduce security holes.  In your case, you don't seem to want to run a production server so a gui won't hurt you.  In that case you have two options.  Install the Desktop version instead, or simply type this command at the command prompt:

```
sudo apt-get install ubuntu-desktop
```

edit:  aysiu has a good idea as well.  You might want to inquire a bit more about a minimalistic gui without the unneeded desktop applications

---

### Post by jsheldon on 2007-05-11
Talk about reducing unnecessary system processing!

Ok I will download the desktop to play around there until I refresh my UNIX skills thanks

---

### Post by aysiu on 2007-05-11
> **jsheldon said:**
> Talk about reducing unnecessary system processing!

Ok I will download the desktop to play around there until I refresh my UNIX skills thanks
Wait... you don't need to reinstall or download another ISO. You can install a GUI right on top of what you have right now.

Did you, in fact, want to install a home user desktop? Or did you want a server with a GUI for server administration?

---

### Post by Seisen on 2007-05-11
That's basically what I did. I did a server install then installed fluxbox, firefox and some other programs.

---

### Post by aysiu on 2007-05-11
I doubt a Server would need Firefox, but I re-read the first post, and if jsheldon wanted LAMP, I'm assuming it's going to be a Server with a GUI and not a home desktop.

In that case, do this:

Log in.

Type ```
sudo nano -B /etc/apt/sources.list
``` Uncomment (i.e., remove the # sign from the beginning of) any line that looks like a web address. Then save (Control-X, Y, Enter). Finally ```
sudo apt-get update
sudo apt-get install wdm icewm xterm menu xorg gksu synaptic rox-filer
sudo /etc/init.d/wdm start
```

---

### Post by Seisen on 2007-05-11
What I did was the minimalist install, thats why I added firefox.

---

### Post by RedSquirrel on 2007-05-11
> **aysiu said:**
> I doubt a Server would need Firefox, but I re-read the first post, and if jsheldon wanted LAMP, I'm assuming it's going to be a Server with a GUI and not a home desktop.

In that case, do this:

Log in.

Type ```
sudo nano -B /etc/apt/sources.list
``` Uncomment (i.e., remove the # sign from the beginning of) any line that looks like a web address. Then save (Control-X, Y, Enter). [/code]





If the server was installed from a CD then the sources.list is already setup correctly, with the following exception:

I would recommend that lines that have **cdrom:** be commented out (put a # at the beginning), otherwise one will be prompted to put the CD in each time one wants to install packages. ;)

[note: sources.list has the backports repository commented out by default, but one may not want that repository anyway.]

PS - fluxbox is another light window manager you could use.

---

