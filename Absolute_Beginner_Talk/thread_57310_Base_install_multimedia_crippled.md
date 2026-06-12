---
title: "Base install multimedia crippled?"
date: 2005-08-16
forum: Absolute Beginner Talk
---

### Post by pattison on 2005-08-16
I just installed ubuntu, and can't seem to find any mp3, mpg or avi libraries included in the dist. No music will play using the supplied player (don't know what it is, i used to use xine) and no video or dvd will play with totem.
Apt-get is no good because my ubuntu machine is isolated from the internet. Is there some trick I should know, or a problem with my install, or am I just out of luck? It was surprising that I couldn't play mp3's at least, but then again, the mandrake I used to use came on 2 disks.

---

### Post by TristanMike on 2005-08-16
Hi, I assume you haven't edited your sources.list yet. The things like mp3 and dvd can't be included in a free distribution by defualt so you must enable the repositories.

This website [http://ubuntuguide.org](http://ubuntuguide.org) has all of the commands you will need. All you need to is run the commands from a terminal but first edit your sources.list explained on the webpage here [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

From there you can install the w32 codecs [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs) and others, just browse the list and pick what you like. If you have any other questions or I was completely off then post back or smack me in the face with a trout, respectively.

EDIT: Oh, just noticed, no internet, well, in the face with a trout it is *SMACK* well, that's what you would do if you could get access to the internet.

---

### Post by poofyhairguy on 2005-08-16
[QUOTE=pattison]I just installed ubuntu, and can't seem to find any mp3, mpg or avi libraries included in the dist. No music will play using the supplied player (don't know what it is, i used to use xine) and no video or dvd will play with totem.
Apt-get is no good because my ubuntu machine is isolated from the internet. Is there some trick I should know, or a problem with my install, or am I just out of luck? It was surprising that I couldn't play mp3's at least, but then again, the mandrake I used to use came on 2 disks.[/QUOTE]

No...its not a problem with your install. All of those codecs are illegal to distribute in many nations, so they are not included in Ubuntu for legal reasons (we don't want a lawsuit). Its a pain, but its one we have to live with.

The way around it is unfortunately apt-get. 

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

Or this Cd:

[http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)

If there is no way to touch any internet....you have one option. Ask someone with internet to download and give (or mail) you that CD. (so yes, at some point internet is needed)

---

### Post by jmcnaught on 2005-08-16
hello,

ubuntu doesn't include support for multimedia codecs that are patented by companies who could sue.

you can easily get support for multimedia codecs from a thirdparty.  the easiest way is to add the ubuntu backports repository.  instructions for adding multimedia support and lots more can be found at [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) 

cheers,

jeremy mcnaughton

---

### Post by pattison on 2005-08-16
[QUOTE=poofyhairguy]
Or this Cd:

[http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)

If there is no way to touch any internet....you have one option. Ask someone with internet to download and give (or mail) you that CD. (so yes, at some point internet is needed)[/QUOTE]

From that link:
"Ubuntu Addon Zip (for Ubuntu 5.04 i386) selectively installs the following apps without an internet connection:
Java, flash-player + firefox plugin, adobe reader + firefox plugin, gFTP, multimedia codecs, mplayer (xmms is installed if you install mplayer), dvdplayback, xine, realplayer 10, thunderbird, gnomebaker, firestarter, nvidia 3D driver, samba server, ssh server, Japanese and Chinese input (see guide below)."


 That is an excellent link, thanks. I didn't say I don't have internet access, just that my Ubuntu machine can't touch the internet. So anything I can dl to a usb stick is great. 115 MB is a reasonable size dl to "fix" the base install. Thanks again for the quick help.

---

