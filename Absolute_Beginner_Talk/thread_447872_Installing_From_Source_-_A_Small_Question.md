---
title: "Installing From Source - A Small Question"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Ghostlove on 2007-05-18
At first I was scared to post this because I was afraid I'd sound really, really stupid. Then I realised that when it comes to Ubuntu and Linux in general for that matter, I *am* really, really stupid... and the only way to reduce my stupidity is to ask questions and pay attention to the answers. So here goes.

I am currently installing Pidgin from source after some silliness with the .deb file I tried. Everything is going surprisingly well, but just so I don't make a huge cock-up - is it okay for me to delete the folder of source files that I extracted, from my Home folder? Once it's been installed, does that folder need to stay where it is, or is it safe for me to get rid of it?

Thanks in advance!

---

### Post by Cypher on 2007-05-18
You can delete the sources once you've installed the program and it's functioning well. Even if you wanted to remove the extracted sources, you can leave the binary tarball for later use. Or if you know where to get it again, delete it to save some space.

---

### Post by Ghostlove on 2007-05-18
That was quick - thanks very much! :D

---

### Post by Ghostlove on 2007-05-18
Hmm now. Any idea how to *uninstall* something I have installed from source? :oops:

---

### Post by steve.horsley on 2007-05-18
Hmm. Some packages allow you to do **make uninstall** I believe. Of course, you can't do that after deleting the source directories with the make scripts in them. If you don't know where the install put the files, you will have a problem tracking them down.

---

### Post by carlosqueso on 2007-05-18
If you kept the source directory, you should be able to go to that directory and type ```
sudo make uninstall
```  If you didn't, you're gonna have to find where it put the stuff, or reinstall it from source and use the make uninstall from there.   In the future, install the checkinstall package, and anywhere instructions call for "make install", substitute "checkinstall" and you'll be able to remove it like any other program.  It'll also create a nice deb file for you.

---

### Post by Ghostlove on 2007-05-18
How do I know if it has actually uninstalled?

I am actually blushing right now with how silly I sound... :/

---

### Post by gigaferz on 2007-05-18
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

for your next installations

hey!,

I also have some questions like that, they sound silly but they are important .

so far i tried to unistall gaim , and guess what ?? it is still there!!!!

i even tried synaptic package manager!!!

---

### Post by carlosqueso on 2007-05-18
you can always type ```
sudo updatedb
``` and then ```
locate <program name>
``` to see what files from it are left on your system.  It's not foolproof, but a start.

---

### Post by Rui Pais on 2007-05-18
> **Ghostlove said:**
> At first I was scared to post this because I was afraid I'd sound really, really stupid. Then I realised that when it comes to Ubuntu and Linux in general for that matter, I *am* really, really stupid... and the only way to reduce my stupidity is to ask questions and pay attention to the answers. So here goes.
Chinese have a saying taht goes more or less like: those who ask look stupid for a minute, those who don't will be stupid for ever :)

just want to reinforce something on a link on a previous post, that may be not much obvious on 1st sight. 
Use checkinstall _always_ to see if it can automatically make a nice deb for you (that can easily be uninstalled and easily allow you to see what and where stuff is installed).
```
sudo apt-get install checkinstall
```
and then after the *make* step, instead of *sudo make install*, do:
```
sudo checkinstall -D
```
sometimes it fails to make a deb, but in most cases it works and make our lives soooo much easy.

---

### Post by zvacet on 2007-05-18
To **gigaferz**


```
sudo apt-get --purge remove file_name
```

if this doesn´t work

```
whereis gaim
```

and you will see all directories wich contens gaim files.You have to go in each of them with cd and when you are inside remove file with 

```
sudo rm -r file_name
```

---

### Post by steve.horsley on 2007-05-18
> **Ghostlove said:**
> How do I know if it has actually uninstalled?

You really just have to take it on faith that the uninstaller sis what it said it did, no mre and no less. Unless you keep records of every file on the system, which is unlikely.

If you deleted the installer/uninstaller, you either need very good file records, or to download the installer again to uninstall.

---

### Post by gigaferz on 2007-05-19
Helo!

Thanks for your reply,
however, when I executed the purge command, it removed ubuntu-desktop(?)

Now, my question is is this supposed to happen?

ohh, dont worry I can reinstall from    cl...if anything goes wrong

---

### Post by Rui Pais on 2007-05-19
> **gigaferz said:**
> ...
however, when I executed the purge command, it removed ubuntu-desktop(?)

Now, my question is is this supposed to happen?

yes, cause gaim is a dependency of ubuntu-desktop.

ubuntu-desktop it's a meta-package, an empty packages with a list of packages as dependencies to be installed. It's a way to bunch a lot of apps to installed under a single name. It's safe to remove, It's only useful for dist-upgrades. 
If you want to use other versions of a certain packages or remove some stuff, to make gnome lighter or because you prefer another default app (like the case evolution/thunderbird) you will have to remove it anyways.

And as you say you can always install it again... if you plan to dist-upgrade instead of fresh install in a future release.

---

