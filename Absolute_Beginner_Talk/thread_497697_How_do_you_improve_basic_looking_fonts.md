---
title: "How do you improve basic looking fonts?"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by cdgeorge1 on 2007-07-10
Hi all, this is my very first post and very first step away from XP - so be gentle with me.

I have successfully installed Ubuntu Feisty and really do not like those basic baby looking fonts you get on the desktop. Please help me seriously improve the look of these fonts - this is where Windows XP score highly.

Warning - if you are going to lead me somewhere to install a so called 'package' then you will have to hold my hand on my first install. For example, I could download something onto the Feisty desktop - then not know how to run the equivalent XP 'setup.exe' - because I understand it's not as easy as that with Linux. I am prepared to learn though.

So anyway, on with seriously improving the default desktop that comes with Feisty - and that font rendering. If I show this off to friends - I don't want to be embarrassed by such a childish look and feel.

---

### Post by Sbarton on 2007-07-10
Have a look at this you may find something useful:
[http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694)
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
regards

---

### Post by cdgeorge1 on 2007-07-10
Thanks for getting back to me so quickly - I was concerned that I would have to wait a while for a response while I sit here drumming my fingers trying to make Ubuntu look more XP like.

I am not really looking to change splash screens or seek glassy effects etc (I have already worked out the basics of this) - its just the font, and only the font.

I think this URL will lead me to fix the problem: [http://ubuntuguide.org/wiki/Ubuntu:Feisty/EyeCandy](http://ubuntuguide.org/wiki/Ubuntu:Feisty/EyeCandy)
Look down and find 'How to improve sub-pixel font rendering for Feisty'

The trouble is, this takes me to a directory on the Internet, where I have downloaded a file (and I am not even sure if it's the right file), and I have not got a clue what to do with this file. Am I going in the right direction here?

If indeed I have found the right thing (David Turner's sub-pixel rendering patches) - how do I install it to make it work?

---

### Post by moredhel on 2007-07-10
ok, with that guide.

go into applications > accessories > terminal

then type

```
gksudo gedit /etc/apt/sources.list
```

*whenver it asks you for your password, type it in, but nothing will show up, simply type it then press enter*

and add either 

http://www.telemail.fi/mlind/ubuntu[/url] feisty fonts
deb-src http://www.telemail.fi/mlind/ubuntu[/url] feisty fonts

or for 64bit feisty (if you don't know then do the 32bit instructions)

deb http://ubuntu.moshen.de[/url] feisty experimental
deb-src http://ubuntu.moshen.de[/url] feisty experimental

to the bottom (just copy and paste it)

save that, then close it.

depending on if you are 32bit or 64bit feisty, type either:

32bit:
```
gpg --keyserver subkeys.pgp.net --recv-keys 937215FF
```

then 

```
gpg --export --armor 937215FF | sudo apt-key add -
```

or for 64 bit:

```
*

wget http://ubuntu.moshen.de/2F306651.gpg -O- | sudo apt-key add -

```

then in terminal type:

sudo apt-get update

wait for that. Then type:

sudo apt-get install libfreetype6 libcairo2 libxft2

type 'y' or 'yes' if it wants you to.

then type

sudo dpkg-reconfigure fontconfig-config

and you might get some options thing, and do the following:

Native, Automatic, No bitmapped fonts.





then type:

sudo dpkg-reconfigure fontconfig.

---

### Post by cdgeorge1 on 2007-07-10
Whoa, I would never have worked that out on my own!

It's not a simple setup which I am used to doing - perhaps because this is an exceptional thing I am asking to do.

I will let you know how I get on.....

---

### Post by cdgeorge1 on 2007-07-10
I guess this does not help...

chris@chris-desktop:~$ sudo apt-get update
E: Type ‘http://www.telemail.fi/mlind/ubuntu[/url]’ is not known on line 57 in source list /etc/apt/sources.list
chris@chris-desktop:~$ 

I have followed your instructions precisely - sorry to be a pain!

I guess if I understood half of it I may be able to work out how to solve it.

---

### Post by alienexplorers on 2007-07-10
You could add the mscorefonts which seem to look better than the faons the system came with.

---

### Post by cdgeorge1 on 2007-07-10
I am up for anything in order to change the default font style - if I need to use mscorefonts then so be it.

How would I implement the mscorefonts?

Although I was trying to implement something else beforehand, but I got an error so was unable to see the results.

---

### Post by smbm on 2007-07-10
> **moredhel said:**
> ok, with that guide.

go into applications > accessories > terminal

then type

```
gksudo gedit /etc/apt/sources.list
```

*whenver it asks you for your password, type it in, but nothing will show up, simply type it then press enter*

and add either 

http://www.telemail.fi/mlind/ubuntu[/url] feisty fonts
deb-src http://www.telemail.fi/mlind/ubuntu[/url] feisty fonts

or for 64bit feisty (if you don't know then do the 32bit instructions)

deb http://ubuntu.moshen.de[/url] feisty experimental
deb-src http://ubuntu.moshen.de[/url] feisty experimental

to the bottom (just copy and paste it)

save that, then close it.

depending on if you are 32bit or 64bit feisty, type either:

32bit:
```
gpg --keyserver subkeys.pgp.net --recv-keys 937215FF
```

then 

```
gpg --export --armor 937215FF | sudo apt-key add -
```

or for 64 bit:

```
*

wget http://ubuntu.moshen.de/2F306651.gpg -O- | sudo apt-key add -

```

then in terminal type:

sudo apt-get update

wait for that. Then type:

sudo apt-get install libfreetype6 libcairo2 libxft2

type 'y' or 'yes' if it wants you to.

then type

sudo dpkg-reconfigure fontconfig-config

and you might get some options thing, and do the following:

Native, Automatic, No bitmapped fonts.





then type:

sudo dpkg-reconfigure fontconfig.

I believe there are some typo's in this, as far as I know the correct repo's are:

deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts
deb-src [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts

Apart from that I've scanned over the steps above and they seem correct.

Good luck.

---

### Post by cdgeorge1 on 2007-07-10
Yes that process seems to have worked now - as you said, it must have been a typo.

However, saying that, the default install of Firefox still renders the font for Google's search page awfully! I don't know if any of you have experienced this but the circular radio buttons (to select between Search: 'the web' or 'pages from the UK') - by the way I have this selection because I am using google.co.uk and not google.com - but to carry on... the circular radio buttons do not complete a full circle (like XP does) and the edges graphics for the circular radio buttons are ragged to say the least!

But is this just a problem with Firefox? I must definitely have this solved before I am happy!

---

### Post by cdgeorge1 on 2007-07-10
In fact this poor guy [http://ubuntuforums.org/showthread.php?p=1966543](http://ubuntuforums.org/showthread.php?p=1966543) has the same problem, and nobody has replied.

---

### Post by Incie83 on 2007-07-10
Indeed, this is a problem with the Linux version of FF, I believe. You will find a solution to your eye-candy problem [_here_]("http://ubuntuforums.org/showthread.php?t=369596"). The script has recently been updated with a GUI, so you shouldn't have any trouble with the installation.

---

### Post by stchman on 2007-07-10
> **cdgeorge1 said:**
> Hi all, this is my very first post and very first step away from XP - so be gentle with me.

I have successfully installed Ubuntu Feisty and really do not like those basic baby looking fonts you get on the desktop. Please help me seriously improve the look of these fonts - this is where Windows XP score highly.

Warning - if you are going to lead me somewhere to install a so called 'package' then you will have to hold my hand on my first install. For example, I could download something onto the Feisty desktop - then not know how to run the equivalent XP 'setup.exe' - because I understand it's not as easy as that with Linux. I am prepared to learn though.

So anyway, on with seriously improving the default desktop that comes with Feisty - and that font rendering. If I show this off to friends - I don't want to be embarrassed by such a childish look and feel.

I personally like XP's fonts and such.  You can transform your Ubuntu desktop to an XP look:

[http://www.stchman.com/ms_fonts.html](http://www.stchman.com/ms_fonts.html)

---

### Post by cdgeorge1 on 2007-07-10
> **Incie83 said:**
> Indeed, this is a problem with the Linux version of FF, I believe. You will find a solution to your eye-candy problem [_here_]("http://ubuntuforums.org/showthread.php?t=369596"). The script has recently been updated with a GUI, so you shouldn't have any trouble with the installation.

You guys are quick! I did actually find this thread before reading this answer - I ended up just doing the following  as instructed by the thread:

wget [http://home.comcast.net/~tehdnite/linux/prettywidgets_firefox2_linux.tar.gz](http://home.comcast.net/~tehdnite/linux/prettywidgets_firefox2_linux.tar.gz)
sudo cp -r /usr/lib/firefox/res/ /usr/lib/firefox/res_original
tar -xvvzf prettywidgets_firefox2_linux.tar.gz
sudo mv ./prettywidgets_firefox2_linux/* /usr/lib/firefox/res/

And this improved things dramatically on its own!

---

