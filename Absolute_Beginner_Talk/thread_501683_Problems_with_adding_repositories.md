---
title: "Problems with adding repositories"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by kitty500cat on 2007-07-15
I had to reinstall Ubuntu and now I'm having problems adding the universe and multiverse repositories.

I tried adding them all to /etc/apt/sources.list, but when I tried $ sudo apt-get update it would hang at *Waiting for headers*.  If I went into Synaptic and tried to reload the list, it always failed at downloading Translation-en_US packages.  So I cleared and saved sources.list, did $ sudo apt-get update again, and then went to system->administration-software sources, where I added the universe and multiverse packages.  The only problem is, when I close it, it needs to download certain files.  It always fails to download the Translation-en_US packages, so it just sits there until I press the Cancel button.

Does it have anything to do with the /etc/environment file?  Here are its contents:

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US-utf8"
```

Thanks in advance for your help.

---

### Post by clitmaster on 2007-07-15
my first thort is that its to do with ur sources.list file....i had the same sorta thing, it was having issues connecting with a specific repo...but i was on a shaped internet connection, so maybe it was timing out from slow dataflow ?

otherwise, post ur sources.list up here, and some1 can double-check it for ya

---

### Post by kitty500cat on 2007-07-15
My sources.list file:

```
deb http://us.archive.ubuntu.com/ubuntu/ feisty main universe restricted multiverse
```

I just tried $ sudo apt-get update, and it worked.  But when I opened Synaptic and tried to reload, it claimed it couldn't connect to us.archive.ubuntu.com.

Now the downloads are simply failing.

Any ideas?  Thanks for your help so far.

---

### Post by MPH on 2007-07-15
When I needed an additional repository for Synaptic, I went to the Synaptic Menu Bar, clicked on **Settings** -> **Repositories** and a panel popped-up.  Click on the **Third-Party Software** tab and click the **Add...** button.  Enter your **deb** line there.

Worked the first time for me... maybe I was just lucky for once. :)

---

### Post by kitty500cat on 2007-07-16
I used the GUI (either in Synaptic like MPH said, or in system->administration->software sources, I don't remember which) to modify my sources.list file.  The first time some of the repository downloads failed; I tried again, then left for a couple of hours; when I came back, I had all of the files I needed.

Thanks a lot! :)

---

