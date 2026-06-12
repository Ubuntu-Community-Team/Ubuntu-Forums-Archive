---
title: "accessing the source/build options of packages (think Arch PKGBUILD, or gentoo ebuild"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by jf/ on 2007-08-18
hi guys, as per subject. Is there any way to get at how the packages that i'm downloading or using were built? Reason being, of course, that i would like to know, and possibly modify if necessary. I've searched the forums, and even the official docs already (help.ubuntu.com), but found nothing to answer this question. If this is not exactly the best place to get an answer, pls feel free to shift this question someplace else (but i hope i can know where it shifted to!!!) - the reason why i'm putting it here is cos i'm new to Ubuntu...

---

### Post by jf/ on 2007-08-18
ok, I found packages.ubuntu.com, although, it doesn't seem to provide the build options for the packages...

One question to the mods - am i posting in the correct section here? would i be better served posting somewhere else instead?

---

### Post by wirelessmonkey on 2007-08-18
You can generally download the package sources if you have the deb-src repositiories enabled, and depending on the application, you can generally find their creators' sites and get the sources there. i.e. apache == [www.apache.org](www.apache.org), various others can be found on [www.sourceforge.net](www.sourceforge.net)

---

### Post by bodhi.zazen on 2007-08-18
Well, I would not consider this a new user question, but you are fine :)

See if this link helps :

[http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html)

---

### Post by jf/ on 2007-08-18
> **bodhi.zazen said:**
> Well, I would not consider this a new user question, but you are fine :)

See if this link helps :


:) well i'm new to the whole ubuntu/debian thing. But thanks.

---

### Post by bodhi.zazen on 2007-08-18
> **jf/ said:**
> :) well i'm new to the whole ubuntu/debian thing. But thanks.

Well, welcome to Ubuntu ;) 

I am a fan of Arch Linux also as are several other Ubuntu community members

---

### Post by jf/ on 2007-08-18
> **bodhi.zazen said:**
> Well, welcome to Ubuntu ;) 

I am a fan of Arch Linux also as are several other Ubuntu community members

:) thanks. I'm coming from Arch, but hope that Ubuntu will be able to satisfy my needs from now on... Let's hope everything works out! It's going to be a change, no doubt, but i hope to be able to have the same easy access to source, + package building possibilities if possible...

Btw, i've just tried downloading the source (with 'apt-get source') for one package, and i get some pretty strange errors that sort of indicate that things arent properly set up (I've highlighted those errors in bold). why is that?

```
$ apt-get source dwm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 23.0kB of source archives.
Get:1 http://sg.archive.ubuntu.com feisty/universe dwm 2.7-1 (dsc) [566B]
Get:2 http://sg.archive.ubuntu.com feisty/universe dwm 2.7-1 (tar) [17.6kB]
Get:3 http://sg.archive.ubuntu.com feisty/universe dwm 2.7-1 (diff) [4834B]
Fetched 23.0kB in 0s (116kB/s)
**gpg: can't open `/gnupg/options.skel': No such file or directory**
gpg: Signature made Thursday 14,December,2006 04:28:41 PM SGT using DSA key ID 4B2B2B9E
**gpg: Can't check signature: public key not found**
dpkg-source: extracting dwm in dwm-2.7
dpkg-source: unpacking dwm_2.7.orig.tar.gz
dpkg-source: applying ./dwm_2.7-1.diff.gz

```

The first error with '/gnupg/options.skel', as i've discovered, can be gotten rid of if you just run gpg, and let it create ~/.gnupg. But still, it's not exactly a very helpful message to see... Especially since /gnupg does not exist at all!

the 2nd error, though, I cant help thinking about. Why cant the public key be already imported? So how should i import this?

Lastly, how do i interpret the files in "/debian" in the unpacked directory? am i to assume that 'rules' is the new makefile?

---

### Post by bodhi.zazen on 2007-08-19
Yea, the gpg error messages are not so easy to decipher :twisted:

If need be, you can ignore them, you will just get an "error message' complaining about untrusted sources.

Now some of the how-to's around here include commands for how to import the relevant key ;)

Otherwise, see if this helps : [https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

sudo apt-get build-dep <application> # Installs dependencies needed to compile an application.
sudo apt-get source <application>    # Download application's source code to current directory.

Then ./configure && make && sudo checkinstall

check install will make a .deb package from the source code which makes it easier to manage in the future, but it does not always work.

After you download the source code you can edit or apply patches if needed.

The rules is not the makefile ...

I just DL dwm to take a look. The makefile is in dwm-4.3 (same directory as the debian directory)

*Note : I am looking at this on Gutsy so I have a higher version ;)

Those rules are the build options

See if these links help you :

[http://www.debian.org/doc/debian-policy/ch-source.html](http://www.debian.org/doc/debian-policy/ch-source.html) (section 4.9)

[https://help.ubuntu.com/6.06/ubuntu/packagingguide/C/basic-scratch.html](https://help.ubuntu.com/6.06/ubuntu/packagingguide/C/basic-scratch.html) (See the rules section)

> The rules file is an executable Makefile that has rules for building the binary package from the source packages.

HTH :)

---

### Post by kakao on 2008-06-15
Hi there.

> **jf/ said:**
> ok, I found packages.ubuntu.com, although, it doesn't seem to provide the build options for the packages...

Since I was looking for an answer to this exact same question and it hasn't been answered here as far as I understand it (and cannot seam to find it elsewhere, either)... How DO I find the build options for a .deb I'm donwloading via aptitude/apt-get? I.e. how it has been configured prior to compilation?

In my case I'm trying to find out wheather GnuCash had ```
$ ./configure --enable-hbci
```.

Cheers.

---

