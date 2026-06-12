---
title: "How to install progys?"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by 3wells on 2008-02-23
nOOb here...

I'd like to install flas, adobe & quicktime. I have the packages - now what?

/home/ross/Desktop/install_flash_player_9_linux.tar.gz

/home/ross/Desktop/QuickTime741_Leopard.dmg

/home/ross/Desktop/AdobeReader_enu-8.1.2-1.i486.rpm

3

---

### Post by nsimeone2000 on 2008-02-23
[http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually)

That link should help you out, also if you are using firefox, you can download the flash player automatically using the add-ons device, and then click on plugins.  then you should click the box next to the flash player and you should be in business.

Quicktime is another plugin you can install directly, and the Adobe reader I am unsure of, but it might be in there as well, here is a link to the addons in Firefox

[https://addons.mozilla.org/en-US/firefox/](https://addons.mozilla.org/en-US/firefox/)

Hope this helps......

Edit, you can install all those plugins in firefox under the second link, the first link is simply FYI if you cannot find it any other way.

---

### Post by PeterJS on 2008-02-23
> **3wells said:**
> nOOb here...

I'd like to install flas, adobe & quicktime. I have the packages - now what?

/home/ross/Desktop/install_flash_player_9_linux.tar.gz

Tar balls aren't incompatable, but usually aren't the best option. Flash is in the repositories under the name of flashplugin-nonfree, and is also a part of the ubuntu-restricted-extras package.

> 
/home/ross/Desktop/QuickTime741_Leopard.dmg

That's a Mac package and isn't even going to begin to work. Quicktime codecs for ubuntu media players are available under the name libquicktime1 in the repositories.

> 
/home/ross/Desktop/AdobeReader_enu-8.1.2-1.i486.rpm


RPMs are red hat packages and can be converted to Deb packages with alien, generally it doesn't work very well but is usable as a last resort. As for adobe reader it's available in Medibuntu:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

