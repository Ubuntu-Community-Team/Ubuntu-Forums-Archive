---
title: "Lilypond music notation"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by WebDrake on 2006-06-26
I've just been checking out the Lilypond music notation package.  Seems quite interesting---very different, obviously, from Finale/Sibelius/etc. but I suspect in many ways superior.

Anyway, I noticed that in Ubuntu only version 2.6.3 is available whereas the current stable version, according to the website, is 2.8.5.  Why such a big discrepancy, and is there an Ubuntu-compatible package available to install the up-to-date version?

Many thanks,

     -- Joe

---

### Post by Brunellus on 2006-06-26
discrepancy is probably due to the fact that the package mainainter hasn't gotten around to packaging the latest for ubuntu yet.  If there are features/fixes in the latest version that are absolutely critical, you can always compile from source.

---

### Post by jazzmuzik on 2006-06-26
Don't install the Ubuntu version. This isn't the usual advice I would give but for Lilypond it is correct. Download the latest prepackaged version of Lilypond -- either the stable or development release -- and run the installation program as non-root. It will set up everything you need to run and it will run from your user account. Works great.

Go here:
[http://lilypond.org/web/install/](http://lilypond.org/web/install/)

And get either the "2.8 stable branch Any/x86" or the "2.9 development branch Any/x86" package. I've used both with success. Then run package from the terminal like this:

```
sh lilypond-2.9.10-1.linux.sh
```

That's all it takes for the installation. Type "lilypond -v" to check the version and see if it's working.

---

### Post by WebDrake on 2006-06-26
Thanks very much for the advice! :D

[QUOTE=jazzmuzik]Don't install the Ubuntu version. This isn't the usual advice I would give but for Lilypond it is correct. Download the latest prepackaged version of Lilypond -- either the stable or development release -- and run the installation program as non-root. It will set up everything you need to run and it will run from your user account. Works great.
[/QUOTE]
It's installed, but the ~/lilypond/usr/bin directory has not been added to the PATH variable.

I tried adding the following lines to .bash_profile
```

if [ -d ~/lilypond/usr/bin ] ; then
    PATH=~/lilypond/usr/bin:"${PATH}"
fi

```
but it didn't work: can anyone advise?

One more thing: I've noticed that some applications automatically associate with certain file types even from the command line, e.g. if I type acroread and start typing a filename, it will automatically work out that I want a file ending in .pdf and eliminate other alternatives when I press the tab key to complete filename.  How do I set the same thing up for lilypond and .ly files?

BTW for the musical people on this site I thought I'd share my reason for being so impressed with Lilypond.  Half-jokingly I tried entering a time signature of 7/10 (yes, it exists).  Lilypond produced a warning, but accepted it: not only that, but it understood its musical meaning too.  Very nice! 8)

---

### Post by jazzmuzik on 2006-06-26
Ubuntu is broken in this regard. See [this thread.](http://ubuntuforums.org/showthread.php?t=200876) To fix it add the following to .bashrc:

```
# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
```

---

### Post by jazzmuzik on 2006-06-27
Okay, maybe "broken" is too strong a word.

---

### Post by Gustav on 2006-06-27
This is the thing I like least about lilypond, it changes the syntax too much between versions. I have to learn a lot of stuff again for avery new version (although the syntax always gets better for each version :))

Other than that it's really great!

---

### Post by jazzmuzik on 2006-06-27
[QUOTE=Gustav]This is the thing I like least about lilypond, it changes the syntax too much between versions. I have to learn a lot of stuff again for avery new version (although the syntax always gets better for each version :))

Other than that it's really great![/QUOTE]


When you get a new version of Lilypond don't forget to run convert.ly on your old source files. It will update your lily code to the newer version and you won't have to worry about learning new things as much. But still lilypond is definitely a moving target.

```
convert.ly music.ly music-new.ly
```

---

