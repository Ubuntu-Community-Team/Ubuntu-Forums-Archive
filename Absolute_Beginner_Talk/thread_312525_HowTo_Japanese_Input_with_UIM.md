---
title: "HowTo: Japanese Input with UIM"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by k0rv3n on 2006-12-04
Hi.

I noticed a lot of pepole, including myself just a while ago, have trouble getting Japaneses input to work on ubuntu so I thought I would setup this howto on how I got mine to work.

I have Ubuntu 6.10 (Edgy) and I used this howto as guideline [https://help.ubuntu.com/community/JapaneseInput](https://help.ubuntu.com/community/JapaneseInput)

First we need to install some packages:

```
sudo apt-get install uim-applet-gnome uim-xim uim-anthy uim-gtk2.0 im-switch
```
You need to have the UniversePackages repository configured.

Now the other howto tells you to do the following command, which only gives an error:
```
im-switch -s uim_anthy
```

Like everyone else I got this error: 
```
Error: no configuration file "uim_anthy" exists.
Error: No action taken.
```

Instead type:
```
uim-pref-gtk
```
This will bring up the graphical interface for uim.
Here I did the following changes:

1) In the global section I changed the "Input meta toggle key" to "<Shift>space", this I my liking and to follow the other guide ;) 

2) Change "Alternative input method" to Anthy.

3) Now in the Anthy section I changed "Default input mode" to Hiragana.

Now you should be able to change between writing with you standard letters and to typing hiragna! &#12420;&#12387;&#12383;&#65281;&#12288;:D 

To get a useful toolbar type:
```
uim-toolbar-gtk
```

or, if you want it in the systray:
```
uim-toolbar-gtk-systray 
```

The latter one I got at startup cause it changes as I change to typing style.

Hope this helps. Cheers!

---

### Post by Stambo00 on 2006-12-21
Thank you, this worked great!

---

### Post by zetsumei on 2006-12-21
thank you, it worked i love typing in japanese...

---

### Post by Wnutt on 2007-01-07
&#12354;&#12426;&#12364;&#12392;&#12372;&#12374;&#12356;&#12414;&#12375;&#12392;&#65281;
That was perfect. Thanks a lot. It will help a lot for my japanese courses.

---

### Post by k0rv3n on 2007-01-08
Glad to hear its working for you guys!!!

---

### Post by lanig on 2007-01-09
It didn't work for me and for good reason I think :
There is a [bug (missing file)]("https://launchpad.net/ubuntu/+source/uim/+bug/70484") in the uim_anthy package.

This file has the following content```

XIM=uim
XIM_PROGRAM=/usr/bin/uim-xim
XIM_ARGS=
GTK_IM_MODULE=uim
ENGINE=anthy

if [ -r "$HOME/.uim" ]; then
  TMPFILE=$(mktemp) || exit 1
  if [ "$(grep "; IM-SWITCH VALUE" $HOME/.uim)" ]; then
    sed "s/(define default-im-name '[^)]*) ; IM-SWITCH VALUE/(define default-im-name '$ENGI
NE) ; IM-SWITCH VALUE/" < $HOME/.uim > $TMPFILE
  else
    cat $HOME/.uim > $TMPFILE
    if [ "$(grep -E "^\(define[[:space:]]+default-im-name[[:space:]]" $HOME/.uim)" ]; then
      echo "; (define default-im-name '$ENGINE) ; IM-SWITCH VALUE" >> $TMPFILE
    else
      echo "(define default-im-name '$ENGINE) ; IM-SWITCH VALUE" >> $TMPFILE
    fi
  fi
  mv $TMPFILE $HOME/.uim
else
  echo "(define default-im-name '$ENGINE) ; IM-SWITCH VALUE" > $HOME/.uim
fi

```

Create the file /etc/X11/xinit/xinput.d/uim_anthy, put the above content inside, set the perms to world readable, and it is OK.
Alternatively, I tried also [this tip]("http://ubuntuforums.org/showthread.php?t=306133") and it worked mostly well but I had minor annoyances with french only special characters in QT based apps.

---

### Post by seetho on 2007-04-17
[COLOR=Black]I finally got japanese input working by following the solutions in this thread - thank you all. &#12354;&#12426;&#12364;&#12392;&#12290;

However it was not all that easy.  Following kOrv3n's step above allowed me to input japanese on the command line terminal but not anywhere else.  So I decided to try lanig's steps in adding in the missing file.  This worked out well and I got input for ooffice and gedit but not terminal, thunderbird or firefox.  After a restart everything works!

I still have an irritating problem of having to type "+<space> to get the double quote character and '+<space> to get the quote.  Still looking for a solution for this.  Otherwise everything works fine.


[/COLOR]

---

### Post by OsakaWilson on 2007-04-23
> **lanig said:**
> 

Create the file /etc/X11/xinit/xinput.d/uim_anthy, put the above content inside, set the perms to world readable, and it is OK.
Alternatively, I tried also [this tip]("http://ubuntuforums.org/showthread.php?t=306133") and it worked mostly well but I had minor annoyances with french only special characters in QT based apps.

Forgive my ignorance, but how do you "create a file"? Also, what are "perms" and how do I set them to "world readable".

---

### Post by OsakaWilson on 2007-04-23
I tried putting it into a text file and saving it under the name and pathway listed, but it told me that I don't have permission to save there.

---

### Post by k0rv3n on 2007-04-23
> **OsakaWilson said:**
> I tried putting it into a text file and saving it under the name and pathway listed, but it told me that I don't have permission to save there.

I'm not sure what that file does since it work for without it but I guess you need to use "sudo" to be able to write the file.

---

### Post by HokkaidoHillbilly on 2007-04-23
Also, if anybody's interested, setting up Japanese in Feisty was a whole heckuva lot easier for me.  Not sure how it'd work on a US/English keyboard as I've gotta JP106 w/ the &#21322;&#35282;&#12539;&#20840;&#35282; button, but all I had to do was install Japanese language support from System->Administration->Language Support and I was in business.

Alternatively, you could also just d/l & burn the Japanese version of Feisty and set default language to English so that you're ready to go out of the box.

---

### Post by Najand on 2007-06-19
> **HokkaidoHillbilly said:**
> Also, if anybody's interested, setting up Japanese in Feisty was a whole heckuva lot easier for me.  Not sure how it'd work on a US/English keyboard as I've gotta JP106 w/ the &#21322;&#35282;&#12539;&#20840;&#35282; button, but all I had to do was install Japanese language support from System->Administration->Language Support and I was in business.

Alternatively, you could also just d/l & burn the Japanese version of Feisty and set default language to English so that you're ready to go out of the box.

Well, Feisty installs SCIM, not UIM... People are talking about UIM here.

---

### Post by zazen666 on 2007-08-17
Hi, 
I follwed the above instructions and I have japanese in firefox, but not Abiword or OPENOFFICE. Does anyone know how to fix this?

---

### Post by thestig_992 on 2008-03-19
thank yo so much for all the help, the only problem is that i cant seem to get it to appear in my top bar...some help please?

---

### Post by Lobinho on 2008-05-29
Hi all.  Love the UIM but was wondering if there is any plan for UIM to support transparency.  It's the only opaque item on my Gnome panel!  Is that a simple thing to implement?

Thanks!

---

