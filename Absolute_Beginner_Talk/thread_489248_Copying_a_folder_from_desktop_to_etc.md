---
title: "Copying a folder from desktop to /etc/"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Beatbreaker on 2007-07-01
i've recently downloaded Thunderbird 2 - it's given me the folder with all the working files in it (no install file)  i got it fro here: [http://www.mozilla.com/en-US/thunderbird/](http://www.mozilla.com/en-US/thunderbird/)

i wanted to copy it to my /etc/ folder but sudo/gksudo cp won't do it, what am i doing wrong?

---

### Post by Raineer on 2007-07-01
What exactly are you typing?  I assume this is from the console?

As you state, this is a list of files in directories...you may want to try:

**sudo cp -r /home/me/thunderbird  /etc**

Just ensure the directory name is correct for the top of the thunderbird "tree"

---

### Post by Brucevdk on 2007-07-01
Did you execute just *cp SOURCE DEST*? You'd probably have gotten the error *cp: omitting directory `foobar'*. You can't copy directories just using *cp*, you'll have to use *cp* with the recursive option, that is.
```

cp -R SOURCE DEST

```

***However***, you should put it either in */opt* or in your home directory, as far as I know */etc* is mostly for configuration files.

You can just start Nautilus using gksudo and then open the archive with your file manager and extract to /opt.
```

gksudo nautilus

```

---

### Post by Beatbreaker on 2007-07-01
ah the -r worked the treat! thanks very much! 

...although i did back out of the idea once i got it working, i found a repo for Thunderbird 2 (it amazes me why its not on fiesty in the first place, it'll be in Gutsy won't it?) 

anyway many thanks for the tips

- can someone let me know now how to do a delete with sudo? ... or maybe point me to a site with heaps of connamds on it?

---

### Post by Raineer on 2007-07-01
If you just mean to delete files, the command is **rm**

You can type **man rm** to see all the options, press 'q' when you're done reading to get back to the command line.

If you have a package you need to delete it can be done in your package manager, or with 'apt-get remove'

---

### Post by RomeReactor on 2007-07-01
Hi. I think [LinuxCommand]("http://www.linuxcommand.org/") is a good place to start learning the command line.

---

### Post by _simon_ on 2007-07-01
If you're lazy like me then install nautilus scripts via Automatix.

You'll then get a root-nautilus-here option on your right click menu.

You also get a gedit-root and search-here option.

---

### Post by Beatbreaker on 2007-07-01
> **RomeReactor said:**
> Hi. I think [LinuxCommand]("http://www.linuxcommand.org/") is a good place to start learning the command line.

that guide is gold, thanks very much!

---

