---
title: "Complete newbie questions"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Toroxor on 2007-10-19
Hello, I just installed Ubuntu for the very first time, and I am very excited and willing to learn about it.  I have a few problems I cant seem to solve for myself, so I am asking for you're help.
In order to run certain HTML based programs I need something called Gecko, I am not sure what it is, But I tried to install it automatically but it needs Internet Explorer.  Whenever I try to install Internet Explorer it gives me the error "Unable to find a volume for extraction.  please verify that you have proper permissions".

My question is, Is there any way to install Gecko without internet explorer,  maybe in terminal?  The program I am trying to use here is Veoh TV.  (Yes I have installed wine).

On to my other question.  I read somewhere that Ubuntu 7.10 comes with compiz fusion.  How do I enable this?

All help will be greatly appreciated, thanks in advance. :)

---

### Post by jayaramk on 2007-10-19
is u need a hmtl editor... uu have screem and blue fish the best html editors availabl... give a chance of using them and u'll definitely find them intresting!!!!

---

### Post by Toroxor on 2007-10-19
Can you be a little more specific please?  This is my first time using Ubuntu so I am not sure what those programs are.  How do I open them?  What do I need to do with them/

Thanks.

---

### Post by mivo on 2007-10-19
Gecko is "only" a browser engine that i.e. Firefox uses. What exactly are you looking for? What programs are you having problems with?

Compiz-Fusion is installed by default. In the Preferences menu you can change the level of effects. For more, and more control, you need to install the Compiz Settings Manager (search for this in Synaptic -- highly recommended). You can also type this:

```
sudo apt-get install compizconfig-settings-manager
```

Welcome to Ubuntu! :)

---

### Post by mlentink on 2007-10-19
> **Toroxor said:**
> In order to run certain HTML based programs I need something called Gecko, I am not sure what it is,.....
My question is, Is there any way to install Gecko without internet explorer,  maybe in terminal?  The program I am trying to use here is Veoh TV.  (Yes I have installed wine).


Gecko is a rendering engine used in many browsers, notably the Mozilla-based browsers like Firefox. It is standard in Ubuntu, so you do not need to install IE (nor should you). 
Please browse around to find Linux alternatives for your streaming video Veoh-TV, which there should be quite a few. Veoh seems to be Windows and Mac only, you may be able to get it to run under Wine, but I doubt it. You be better off wit a Linux-alternative

---

### Post by dhruva023 on 2007-10-19
the veoh tv will not work under wine ( not for me ).

i would say, just watch the movie online.

---

### Post by Toroxor on 2007-10-19
Wow, thanks so much guys.  Can you recommend me an alternative to Veoh TV?

---

### Post by yabbies on 2007-10-19
instead of Veoh TV why not check out Myth TV?
go to applications>add/remove

click top right corner and check all applications or something like that

then you can look up MythTV in the add/remove 
just check the box and click the apply button to install

To enable compiz goto System>Preferences>Appearances 

click on the last tab, I think it says desktop effects or something like that
check the appropriate box to enable effects.

---

### Post by SadaraX on 2007-11-09
Toroxor, this may not be exactly what you wanted, but there is a project that allows you to download the full videos from Veoh. It has to be compiled, but that is not too hard.

Dependencies (on ubuntu feisty 7.04/ gutsy 7.10):
```
build-essential
libssl-dev
subversion
libsqlite3-dev
```

And to build it:
```

svn co [https://veohlin.svn.sourceforge.net/svnroot/veohlin](https://veohlin.svn.sourceforge.net/svnroot/veohlin) openveoh
cd openveoh/
make sockets
make all
sudo make install

```

There is both a console app called vget and there is a new beta gui called kvget. When I tried 'make install' my system complained about my firefox. But it actually created the programs in

For kvget: ./openveoh/src/attic/
For vget: ./openveoh/src/tools/vget

Hope that helps

---

