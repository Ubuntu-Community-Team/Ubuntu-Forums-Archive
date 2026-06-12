---
title: "After installation"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by bobetko on 2007-09-05
After I install something through synaptic manager, sometime (almost all the times) I don't have idea where file is installed. For example, I installed John-the-ripper and all I know that I can run john now. But, I would like to read some help files which are probably located in the application's folder, but don't have idea how to find them. I tried search (available through GNOME) but it does not work or, I don't know how to use it (it has all together 2 options). It is impossible that there is no file named john anywhere on the disk.
I have feisty ubuntu. Thanks.

---

### Post by hoges on 2007-09-05
It really depends on the software you're installing.

Usually, it will end up with a shortcut to the ap in the applications toolbar.

Otherwise, it may be a terminal job. For example, if you wanted to run firefox in the terminal, you would type "firefox" (without quotes) and it would boot. For a manual on firefox, you'd type man firefox.

Usually what's in these is on a website if you want a more elegant html/pdf copy.

Hope this helps

---

### Post by bobetko on 2007-09-05
Thanks for response.

On the website they would usually tell me something like: config file is saved in your installation folder, ...etc.... Problem is, I can't find my installation folder.

---

### Post by hyper_ch on 2007-09-05
you can also check if there are man(ual) pages for it:

```

man program_name

```

I guess most GUI programs don't have man pages anymore but terminal programs do have.

---

### Post by RomeReactor on 2007-09-05
Hi. The file and directory structure of Linux is different than that of windows, so one program makes entries in several directories. Try [this site]("http://www.comptechdoc.org/os/linux/commands/linux_crfilest.html") for an overview of Linux's directory structure.

To find documentation for a program, you could try reading its man page, which means a manual read from the command line; for that, you need to know the name of the program's executable, so search in Synaptic for your program, highlight it and press the **Properties** button; go to the **Installed Files** tab, and look for an entry in **/usr/bin**.

For example, looking for totem-gstreamer in Synaptic shows this entries in /usr/bin:
```
/usr/bin/totem
/usr/bin/totem-video-thumbnailer
/usr/bin/totem-video-indexer
```

so I open a terminal (Applications->Accessories->Terminal), and enter the following to see the manual:
```
man totem
```

---

