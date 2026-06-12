---
title: "Finding where  new programs are installed"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by DrewB on 2007-02-08
Hello,
I recently took the plunge and switched from using Windows to Ubuntu Linux.

One of the things I find difficult is how to know where new programs have been installed. Windows highlighted newly installed programs in the Start menu and you usually choose during insatall the directory you want to install it to.

However this is not the case in Ubuntu when using  Synaptic or Automatix.

For instance I recently installed Archiving Tools which provides additional archiving tools (rar, unrar, ace 7zip,etc) using Automatix. However once the install had finished I couldn't find the new Archiving Tools anywhere and I can't open 7z files.

My question is how do I find out where the new Archiving Tools were installed so I can use them? And how do I find where programs are installed in general in Ubuntu Linux?

Thanks a lot
Andrew

---

### Post by Dr Small on 2007-02-08
Your new "Archiving Tools" may have went under Applications -> System Tools.
And to open 7z files, try going to Properties on that file, go over to the Open With tab, and find the name of your Archiving Tools to open it.

Try that, as it may help.

Dr Small

---

### Post by shareMenaPeace on 2007-02-08
Those windows archives are now added to the rightlick on archive "extract" function.
So to extract an archive just rightlick and choose "extract" it will figure which archiver to use byitself.

Well and finding stuff is a little diffrent i still learning this to. But basicly when i search something i open the terminal and type

```
locate filename
```

or

```
which filename

```

To run a application it has to be a binary and those are in the /bin folders. But im confused as there are many diffrent /bin all over /root but the above command helps at least to track this down.

Cheers

---

### Post by DrewB on 2007-02-08
> **Dr Small said:**
> Your new "Archiving Tools" may have went under Applications -> System Tools.
And to open 7z files, try going to Properties on that file, go over to the Open With tab, and find the name of your Archiving Tools to open it.

Hi I've checked in Applications -> System Tools and its not there. I've looked everywhere under Applications and System menus but can't find Archiving Tools anywhere. The only thing I have is Archive Manager under Applications -> Accessories. However this does not open 7zip files.
Automatix does say that Archiving Tools is installed but god knows where!
Thanks
Andrew

---

### Post by bruenig on 2007-02-08
Archiving tools isn't an application. Although I don't use automatix, rar and unrar and the like are not graphical applications. Some graphical applications may be able to use them like the archive manager and such, but they are command line programs. Being a windows convert, one thing to remember is that programs aren't necessarily graphical.

This is one of the problems with automatix, that being that it by design allows people to remain ignorant and so when they have a problem, they don't know what exactly to do.

---

### Post by DrewB on 2007-02-08
> **shareMenaPeace said:**
> Those windows archives are now added to the rightlick on archive "extract" function.
So to extract an archive just rightlick and choose "extract" it will figure which archiver to use byitself.


If i right-click on the 7z archiive and select "Extract Here" an error dialog is displayed saying "Archive type is not supported"

> 
Well and finding stuff is a little diffrent i still learning this to. But basicly when i search something i open the terminal and type

```
locate filename
```

or

```
which filename

```


Thanks. Using 'locate filename' i was able to find p7zip in /usr/bin and this works from the command line on the 7z archive file.  Whether this is part of the Archiving Tools that Automatix installed I've no idea.

---

### Post by lambros on 2007-02-08
Hi Andrew,

I, too, have noticed that a lot of programs don't seem to install shortcuts into the menus.  In those cases, I generally just run them from the Terminal.  For example, I installed a package called "sgt-puzzles" - it's in Synaptic in the Universe repository.  This didn't seem to create any menu entries, so I had to find out what the executable files were.

You can easily find out what files are installed by a particular package in Synaptic.  Run Synaptic, highlight a package you've already installed, then go to Package->Properties and click on the "Installed Files" tab.  That shows you a list of files - the interesting ones are those beginning /usr/bin/... or (if you're like me!) /usr/games/...  If you want, you can get a complete list of these "bin" folders by running this command in the terminal:

```
echo $PATH
```

For my example "sgt-puzzles" package, I can see these entries in the list:

/usr/games/blackboxgame
/usr/games/bridges
/usr/games/cube
/usr/games/dominosa
..etc..

So I immediately know I can type in any of those commands (blackboxgame, bridges...) into the Terminal, and they will actually do something! :)  If you don't like using the Terminal, you could always create your own Launchers (desktop shortcuts) afterwards.  Hint: my own favourites are: loopy, netgame and bridges :-)

Hope that helps,
Lambros

---

### Post by shareMenaPeace on 2007-02-08
> **DrewB said:**
> Thanks. Using 'locate filename' i was able to find p7zip in /usr/bin and this works from the command line on the 7z archive file.  Whether this is part of the Archiving Tools that Automatix installed I've no idea.

I forgott this

```
whereis filename
```

---

