---
title: "Installing Synce 0.10 (or gimme some .deb)"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by ffoletti on 2007-05-11
[SIZE="2"]Hi everybody! 
I read that a new version of synce/syncekonnector has been released, so I flew to synce website ([http://sourceforge.net/projects/synce/](http://sourceforge.net/projects/synce/) )  to immediately get it and check if it works on Feisty, while older version seems not to work (I think it's kinda bug...)
but as the noob I am, I coudln''t install, I think I'll need some help.... I download those files and then? I am still trying to understand what went wrong with my ./configure and make - make install commands, but it seems like I miss something to get this working ("recursive errors" comes out.. make doesn'work at all).... 
were there a .deb package... this would be better...  in the meanwhile, somebody could tell me how to do this? 
Thank you all [/SIZE]

*noob*ody said it was easy :lolflag:

---

### Post by Seisen on 2007-05-11
Can you post what kind of errors you are getting and also did you install build-essential?

```
sudo apt-get install build-essential
```

---

### Post by ffoletti on 2007-05-12
Well, I missed some libraries, but I think I miss some more, or I'm not doing it properly...
after configure, make shows me this output:
(this was while trying to install librapi2-0.10.0)

make  all-recursive
make[1]: Entering directory `/home/francesco/SYNCE/librapi2-0.10.0'
Making all in src
make[2]: Entering directory `/home/francesco/SYNCE/librapi2-0.10.0/src'
Making all in support
make[3]: Entering directory `/home/francesco/SYNCE/librapi2-0.10.0/src/support'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/francesco/SYNCE/librapi2-0.10.0/src/support'
Making all in rapi
make[3]: Entering directory `/home/francesco/SYNCE/librapi2-0.10.0/src/rapi'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/francesco/SYNCE/librapi2-0.10.0/src/rapi'
Making all in rapi2
make[3]: Entering directory `/home/francesco/SYNCE/librapi2-0.10.0/src/rapi2'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/francesco/SYNCE/librapi2-0.10.0/src/rapi2'
Making all in config
make[3]: Entering directory `/home/francesco/SYNCE/librapi2-0.10.0/src/config'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/francesco/SYNCE/librapi2-0.10.0/src/config'
make[3]: Entering directory `/home/francesco/SYNCE/librapi2-0.10.0/src'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/francesco/SYNCE/librapi2-0.10.0/src'
make[2]: Leaving directory `/home/francesco/SYNCE/librapi2-0.10.0/src'
Making all in script
make[2]: Entering directory `/home/francesco/SYNCE/librapi2-0.10.0/script'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/francesco/SYNCE/librapi2-0.10.0/script'
Making all in tools
make[2]: Entering directory `/home/francesco/SYNCE/librapi2-0.10.0/tools'
Making all in man
make[3]: Entering directory `/home/francesco/SYNCE/librapi2-0.10.0/tools/man'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/francesco/SYNCE/librapi2-0.10.0/tools/man'
make[3]: Entering directory `/home/francesco/SYNCE/librapi2-0.10.0/tools'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/francesco/SYNCE/librapi2-0.10.0/tools'
make[2]: Leaving directory `/home/francesco/SYNCE/librapi2-0.10.0/tools'
Making all in tests
make[2]: Entering directory `/home/francesco/SYNCE/librapi2-0.10.0/tests'
Making all in CeRapiInvoke
make[3]: Entering directory `/home/francesco/SYNCE/librapi2-0.10.0/tests/CeRapiInvoke'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/francesco/SYNCE/librapi2-0.10.0/tests/CeRapiInvoke'
Making all in rapi
make[3]: Entering directory `/home/francesco/SYNCE/librapi2-0.10.0/tests/rapi'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/francesco/SYNCE/librapi2-0.10.0/tests/rapi'
make[3]: Entering directory `/home/francesco/SYNCE/librapi2-0.10.0/tests'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/francesco/SYNCE/librapi2-0.10.0/tests'
make[2]: Leaving directory `/home/francesco/SYNCE/librapi2-0.10.0/tests'
Making all in python
make[2]: Entering directory `/home/francesco/SYNCE/librapi2-0.10.0/python'
Making all in tests
make[3]: Entering directory `/home/francesco/SYNCE/librapi2-0.10.0/python/tests'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/francesco/SYNCE/librapi2-0.10.0/python/tests'
make[3]: Entering directory `/home/francesco/SYNCE/librapi2-0.10.0/python'
pyrexc ./pyrapi2.pyx -o ./pyrapi2.c
/bin/bash: pyrexc: command not found
make[3]: *** [pyrapi2.c] Error 127
make[3]: Leaving directory `/home/francesco/SYNCE/librapi2-0.10.0/python'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/francesco/SYNCE/librapi2-0.10.0/python'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/francesco/SYNCE/librapi2-0.10.0'
make: *** [all] Error

what's this caused by? I know I must be doing something the wrong way, but I don't know what...
thanks

---

### Post by adwatkin19 on 2007-05-14
Hi, i am getting more or less the exact same thing when i try to install synce 0.10 it would be nice to have this working as i need my wm5 device for work purposes.

By the way, where should the files from the synce website be downloaded to?

thanks to anyone who can help with this

adwatkin

---

### Post by beow on 2007-05-23
You have to install python-dev and python-pyrex:

sudo apt-get install python-dev python-pyrex

Bengt

---

### Post by wersdaluv on 2007-05-27
I have a good news!

After Googling, I saw this --> [http://www.nabble.com/Re:-SynCE-0.10.0-Debian-Packages-t3780467.html](http://www.nabble.com/Re:-SynCE-0.10.0-Debian-Packages-t3780467.html)

> Add the following lines to your /etc/apt/sources.list:

deb [http://jonnylamb.com](http://jonnylamb.com) debian/
deb-src [http://jonnylamb.com](http://jonnylamb.com) debian/

---

### Post by serhito on 2007-11-26
I am new to Ubuntu 7.10 and love it so far...
I am having a real hard time to setup my pocket PC to sync with Evolution.
I went through several methods that i found (lengthy ones), I still can't make it work.
Some methods sends you back and forth to different websites and then i get confused.
Besides there are some older ones that i don't know if they still apply.

Could someone point me towards one that is recent ?
Thanks

---

