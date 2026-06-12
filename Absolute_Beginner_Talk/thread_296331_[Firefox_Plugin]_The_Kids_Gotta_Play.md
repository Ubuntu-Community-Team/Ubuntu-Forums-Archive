---
title: "[Firefox Plugin?] The Kids Gotta Play"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Belgatom on 2006-11-09
I upgraded to firefox 2.0 recently and for all I knew everything worked fine. Untill I introduced the kids to the linux machine. I am running Linux at home as a trial to see if my (and clearly their) daily needs can be filled. 

Up to now, I have got everything to do what I want it to do. 

Thrust the kids to burst my bubble of course. 

My son recently visited his uncle where he introduced him to a site. [http://www.spele.be]("http://www.spele.be"). It's a gamesite with flash games and java games and wotnot... The first thing he clicks on refuses to play. I get the screen loaded alright but the input doesn't seem to work. 

The link to the game is [here]("http://www.spele.be/games/alexingevaar.html"). 

Can any of you play it? 

And if so, what kind of plugin do I need? 

And finally, how do I install said plugin?

---

### Post by picpak on 2006-11-09
I can play it. You need [Flash 9](http://ubuntuforums.org/showthread.php?t=279990&highlight=flash+9).

---

### Post by Lord Illidan on 2006-11-09
Yes, I can play it. You need the Flash 9 beta plugin.

---

### Post by bulldog on 2006-11-09
I can play it without an error in Edgy.

---

### Post by Belgatom on 2006-11-09
Weird stuff. I followed the instruction in the link but no succes. 

Let me tell you how it goes:

Before this thread, the game loads but the little dude doesn't move when I use the keyboard.

I then install the Flash plugin according to the link. 

I restart Firefox and go to the game. Game doesn't load but Firefox points out that I am missing a plug-in. Aha, me says. I click on the wizard and 9 seconds later, the plug-in is installed, the game loads and again, I can't move the little guy.

I repeat the process with exactly the same results. After install of above plug-in, Firefox tells me it's missing and installs it and we are back to square one.


***edit***

Hmmm, most of the games seem to have the same effect. Keyboard doesn't seem to register in the flashgame.

---

### Post by bulldog on 2006-11-09
I installed flash9 with automatix2,maybe you can give that a try?

---

### Post by picpak on 2006-11-09
This is gonna sound really stupid but...


Did you click within the Flash game?



For me, that usually helps.

---

### Post by Lord Illidan on 2006-11-09
Strange. Try re-installing flash as per the howto. Then go on this link : [http://www.adobe.com/products/flash/about/](http://www.adobe.com/products/flash/about/)

what is your flash version?

---

### Post by Belgatom on 2006-11-09
> **bulldog said:**
> I installed flash9 with automatix2,maybe you can give that a try?

Installed Automatix, selected Flash player. Same result as before. After Automatix install Flashplayer, the game refuses to load and suggests install missing plug-in. I can't do anything but agree. I agree.
And back to square one...

> **picpak said:**
> This is gonna sound really stupid but...
Did you click within the Flash game?
For me, that usually helps.

No suggested however unusual can be regarded as stupid. Alas, I had done it, did it again to make sure, but no results. 

> **Lord Illidan said:**
> Strange. Try re-installing flash as per the howto. Then go on this link : [http://www.adobe.com/products/flash/about/](http://www.adobe.com/products/flash/about/)
what is your flash version?

Will do. Currently it says: "You have 7,0,68,0"

Extra: I am a little worried that it might not have to do with Flash because it works fine on my Windows laptop and when I hit the adobe page on that one, it says: "You have 7,0,19,0". Are you guys running Firefox 2.0?

---

### Post by Belgatom on 2006-11-09
Alas, did the same thing but still get the same result as before. 

Anybody have more suggestions how to get Flash 9 installed?

---

### Post by Lord Illidan on 2006-11-09
> **Belgatom said:**
>  
Will do. Currently it says: "You have 7,0,68,0"

Extra: I am a little worried that it might not have to do with Flash because it works fine on my Windows laptop and when I hit the adobe page on that one, it says: "You have 7,0,19,0". Are you guys running Firefox 2.0?

Strange. I am using Firefox 2.0 and flash 9 on Edgy Eft...and it works perfectly.

---

### Post by arnieboy on 2006-11-09
If you upgraded to Firefox 2.0, you need to tell us where you installed Firefox 2.0. If Automatix2 does not know where you installed FF 2.0, there is no way it can install the flash plugin for you in that location.
So please tell us the location where FF 2.0 is installed.

---

### Post by CarpKing on 2006-11-09
Well, if all else fails, you can install the Windows version of Firefox in Wine.  That's what I used to get better Flash performance before the Flash 9 beta plugin came out.  Odd that it seems to work with Flash 7 in Windows, though.

---

### Post by Belgatom on 2006-11-09
> **CarpKing said:**
> Well, if all else fails, you can install the Windows version of Firefox in Wine.  That's what I used to get better Flash performance before the Flash 9 beta plugin came out.  Odd that it seems to work with Flash 7 in Windows, though.

A nice suggestion but that would be admitting defeat. And defeat is not an option. This machine is currently set up as a learning experience. And learning can be a painfull experience, but in the end, it brings enlightment. 

> **arnieboy said:**
> If you upgraded to Firefox 2.0, you need to tell us where you installed Firefox 2.0. If Automatix2 does not know where you installed FF 2.0, there is no way it can install the flash plugin for you in that location.
So please tell us the location where FF 2.0 is installed.

I was thinking the same thing. Unfortunately Upgrading FF 2.0 was one of the first things I did, using a script I found on the internet. And as you imagine, I had (still haven't) no idea what I was doing, really. And guess what, I dumped the script. 

Is there some way to find this out? Some command?

---

### Post by bulldog on 2006-11-09
locate firefox
whereis firefox

To name a few.

---

### Post by IYY on 2006-11-09
Get flash 9 here: [http://www.adobe.com/go/fp9_update_b1_standalone_linux](http://www.adobe.com/go/fp9_update_b1_standalone_linux)

The game worked for me.

---

### Post by Belgatom on 2006-11-09
> **bulldog said:**
> locate firefox
whereis firefox

To name a few.

When I do that, I do get quit a lot of stuff back. I think I need to find out where the program itself is located. What is the .exe equivalent of Linux? Anyway, did a locate firefox.* and got the following. 

> belgatom@belgatom-desktop:~$ locate firefox.*
/var/lib/dpkg/info/firefox.conffiles
/var/lib/dpkg/info/firefox.list
/var/lib/dpkg/info/firefox.md5sums
/var/lib/dpkg/info/firefox.postinst
/var/lib/dpkg/info/firefox.postrm
/var/lib/dpkg/info/firefox.preinst
/var/lib/dpkg/info/firefox.prerm
/home/belgatom/.icons/stilllife/16x16/apps/mozilla-firefox.png
/home/belgatom/.icons/stilllife/24x24/apps/mozilla-firefox.png
/home/belgatom/.icons/stilllife/32x32/apps/mozilla-firefox.png
/home/belgatom/.icons/stilllife/48x48/apps/mozilla-firefox.png
/home/belgatom/store/Icons/Firefox/firefox.ico
/home/belgatom/store/Icons/Firefox/firefox.png
/home/belgatom/store/Icons/PNG/Real_Stuff/Real Stuff/PNG/firefox.png
/home/belgatom/store/Icons/PNG/Real_Stuff/Real Stuff/ICO/firefox.ico
/home/belgatom/store/Icons/PNG/PNG/Software/firefox.png
/home/belgatom/store/Icons/PNG/Ico/softwear/divers/firefox.ico
/etc/firefox/pref/firefox.js
/etc/gre.d/firefox.conf
/opt/firefox/defaults/pref/firefox.js
/usr/bin/firefox.ubuntu
/usr/bin/mozilla-firefox.ubuntu
/usr/lib/firefox/extensions/langpack-en-GB@firefox.mozilla.org
/usr/lib/firefox/extensions/langpack-en-GB@firefox.mozilla.org/chrome
/usr/lib/firefox/extensions/langpack-en-GB@firefox.mozilla.org/chrome/en-GB.jar
/usr/lib/firefox/extensions/langpack-en-GB@firefox.mozilla.org/uninstall
/usr/lib/firefox/extensions/langpack-en-GB@firefox.mozilla.org/uninstall/Uninstall
/usr/lib/firefox/extensions/langpack-en-GB@firefox.mozilla.org/chrome.manifest
/usr/lib/firefox/extensions/langpack-en-GB@firefox.mozilla.org/install.rdf
/usr/lib/firefox/firefox.cfg
/usr/share/app-install/desktop/firefox.desktop
/usr/share/applications/firefox.desktop
/usr/share/doc/mozilla-thunderbird/mozilla-firefox.js.tmpl
/usr/share/firefox/defaults/pref/firefox.js
/usr/share/man/man1/firefox.1.gz
/usr/share/man/man1/mozilla-firefox.1.gz
/usr/share/pixmaps/firefox.png
/usr/share/pixmaps/mozilla-firefox.png
/usr/share/pixmaps/mozilla-firefox.xpm
/usr/share/ubuntu-docs/ubuntu/menus/C/firefox.xml
/usr/share/gdesklets/Displays/gnomebar/gfx/firefox.png


Can if figure out where Firefox is installed through this? 

@IVY: That's for the stand alone, will that work when I open something flash in Firefox?

---

### Post by bulldog on 2006-11-09
Think yours is in /opt.

I did take a look where mine is and /opt didn't showed up in the list.

---

### Post by fog on 2006-11-10
Try this [deb]("http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb"), works fine here.

---

