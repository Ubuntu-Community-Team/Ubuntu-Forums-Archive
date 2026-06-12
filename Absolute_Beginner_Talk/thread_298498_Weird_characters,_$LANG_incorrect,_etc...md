---
title: "Weird characters, $LANG incorrect, etc.."
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by JaRoLLz on 2006-11-12
I'm sorry if this thread has been posted before, but I've got a problem...

When I type:

[FONT="Courier New"]man ls[/FONT]

to view the manual for ls, the terminal display this message:

[FONT="Courier New"]man: can't set the locale; make sure $LC_* and $LANG are correct[/FONT]

The manual did show, but there are weird characters which looks like this: **<?>**

Also when doing apt-get, the terminal always shows this at the end of its operation:

[FONT="Courier New"]
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
[/FONT]

What should I do to get rid of this problem? Pls HELP!

---

### Post by kewldude606 on 2006-11-12
Type the following into the terminal and post the results:
```
echo $LANG
``````
echo $LC_*
```

Get to the terminal by Applications-->Accessories-->Terminal (If on Ubuntu, not Kubuntu, etc.)

---

### Post by JaRoLLz on 2006-11-12
echo $LANG
en_US.UTF-8

echo $LC_*
1 Desktop Documents Download Examples GoogleEarthLinux.bin PicasaDocuments Ubuntu Guide automatix.key google-earth googleearth jriddell.key loadlog quinn1.key quinn2.key workspace

---

### Post by JaRoLLz on 2006-11-12
Sorry for double-posting.

I think my problem is with the locale. Is there anyway to set it? The terminal always says that it can't set the locale.

---

### Post by NT4usB on 2006-11-19
I have the same issue.
I'm sure it has to do with my using some Edgy bits to update MythTV to 0.20 in Dapper.
I followed the steps from [http://ubuntuforums.org/showpost.php?p=1586072&postcount=310](http://ubuntuforums.org/showpost.php?p=1586072&postcount=310)
And although Mythtv workes perfect, it's borked some other stuff.
No big deal for me since it's only a PVR box and that works fine. May give some clues as to what causes the locals problem.

---

### Post by x1a4 on 2006-12-20
Try this:

Fire-up Synaptic, search for 'locale', then download all the locales you want from the list of available locales.  

After downloading your locales, you might want to try setting language environment variables in your favourite shell's rc file.  

For tcsh you'd do it like this: 

Using your favourite text editor, open ~/.tcshrc then add/modify these lines: 

```

setenv LANGUAGE 'en_US;en_GB;en'
setenv LANG           'en_US;en_GB;en'
setenv LC_ALL        'en_US;en_GB;en'

```

Hope this helps.

---

### Post by x1a4 on 2006-12-20
PS: You might also try running 
% sudo /usr/sbin/locale-gen

---

### Post by x1a4 on 2006-12-20
PPS This might also work

apt-get install locales
dpkg-reconfigure locales 

Come to think of it you might want to try this first.

---

