---
title: "Unable to update Firefox"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Janset on 2007-08-25
Hi all.

I warn you, I am EXTREMELY new to Ubuntu     :(

I have set up UNBUNTU on my other computer (this one is Windows XP) to run UBUNTU Ver 6.06.1 and on that I am running the bog standard Firefox that came with that version.

The other day I tried to update Firefox to the latest version but was unable as the "Update Firefox" section in the drop down "Help" Menu is greyed out.

I the tried to update from within Firefox from it's home page and still no joy.

Can anyone please explain why this is happening and talk me through the update process? 

I do not have any problems with Windows, but Ubuntu may as well be another planet.

Regards   :confused:

---

### Post by forestpixie on 2007-08-25
Firefox updates do turn in the normal update way from Ubuntu, but if you want to you can use [Ubuntuzilla]("http://ubuntuzilla.wiki.sourceforge.net/"). Have a look

---

### Post by mikeyphi on 2007-08-25
I guess you are using the correct version of Firefox for your version of Ubuntu.
The latests versions are probably based on later linux kernels which are available in the latest releases of Ubuntu.

The choice is yours - you stay with the long term support version of ubuntu with the installed programs that you 'know' will carry on working
or - you upgrade to the later versions of ubuntu , with newer features, that don't carry the same long term support.

---

### Post by alienexplorers on 2007-08-25
I just downloaded the tar file for Firefox 2.0.0.6 and untared it to my home directory. I setup a shortcut to it and it runs like a champ.  You can even import your add-ons and bookmarks to the new .mozilla profile file.
> [http://kb.mozillazine.org/Migrating_settings_to_a_new_profile](http://kb.mozillazine.org/Migrating_settings_to_a_new_profile)

---

### Post by Lord Illidan on 2007-08-25
> **mikeyphi said:**
> I guess you are using the correct version of Firefox for your version of Ubuntu.
The latests versions are probably based on later linux kernels which are available in the latest releases of Ubuntu.


Actually this is incorrect. There's no such thing as Firefox depending on a particular linux kernel...if anything it would depend on the 2.6 kernel which is shared by Breezy, Dapper, Edgy, Feisty, and Gutsy...

To update firefox : press alt+f2 type> gksudo firefox
use the firefox help> update to update it than close it after its done, don't browse with a root firefox.

---

### Post by bme on 2007-08-25
when you enable security updates in synaptics,firefox usually is included. this is where I update firefox.whenever a new firefox version is available from the repos it will be included in the available updates...

---

### Post by Janset on 2007-08-25
Hi Guys.

Thank you for your replies.  Will give your suggestions a go later on today hopefully.

As for general updates. I did click something but can't remember exactly what, but I was advised that I need to install/update 27 items. This I did and if I remmeber correctly, Firefox was one of the updates. But when I opened up Firefox after the updates were installed, it still showed the original outdated version with the update function stillgreyed out.

Lord Illidan, I will give your suggestions a go, in the mean time, what do you mean "do not browse with a root firefox" ?  

Regards.   :?

---

### Post by aysiu on 2007-08-25
> **forestpixie said:**
> Firefox updates do turn in the normal update way from Ubuntu, but if you want to you can use [Ubuntuzilla]("http://ubuntuzilla.wiki.sourceforge.net/"). Have a look
I would vouch for this suggestion.

---

### Post by frayalejandro on 2007-08-25
Follow the instructions on this link. That will make it.

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

Reboot your computer after that.

---

### Post by Lord Illidan on 2007-08-26
>  "do not browse with a root firefox" ?

When browsing as root, there is an increased probability of breaking your entire system, while browsing as user is limited to your own home directory.

---

### Post by Dr Small on 2007-08-26
If you are on Dapper or Edgy, you can use this simple shell script to upgrade your firefox to the newest version.

Download this:
[http://php.8ez.com/drsmall/blog/wp-content/installnewfirefox.sh](http://php.8ez.com/drsmall/blog/wp-content/installnewfirefox.sh)

And then run this in the terminal:
```
sh installnewfirefox.sh
```

Dr Small

---

### Post by Acglaphotis on 2007-08-26
Or, you can download the tar.gz from mozilla.com, uncompress it on /opt and just change the icons to /opt/firefox/firefox. 

Just adding alternatives ;).

---

### Post by nanotube on 2007-08-26
> **Dr Small said:**
> If you are on Dapper or Edgy, you can use this simple shell script to upgrade your firefox to the newest version.

Download this:
[http://php.8ez.com/drsmall/blog/wp-content/installnewfirefox.sh](http://php.8ez.com/drsmall/blog/wp-content/installnewfirefox.sh)

And then run this in the terminal:
```
sh installnewfirefox.sh
```

Dr Small

hi,
you're linking to a /really/ old installnewfirefox script (back from 2006). the newest version now lives on the ubuntuzilla project site.

it might still be functional... but there's no guarantee it will stay that way, if mozilla changes site layout, e.g. 

so i'd recommend that you point people to the ubuntuzilla project site. 

but thanks for posting that... that's version 2.14, before i even started using cvs and the sf.net file release system, so i didn't even have that version on hand anymore. i'll put that out on the file release system for archival purposes. :) (oldest version currently out on the ubuntuzilla frs is 3.1.0)

if you find any more old versions, let me know. pieces of ubuntuzilla history. :)

---

