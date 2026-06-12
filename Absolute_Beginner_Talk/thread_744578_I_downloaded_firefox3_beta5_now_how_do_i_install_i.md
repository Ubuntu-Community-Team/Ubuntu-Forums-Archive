---
title: "I downloaded firefox3 beta5 now how do i install it? using the terminal"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by Brii on 2008-04-03
its saved to /home/brii/Desktop
and is named firefox-3.0b5.tar.bz2

also asking this so i could install other programs too

---

### Post by privaterolf on 2008-04-03
> Install Firefox 3 Beta 5
Let&#8217;s install Firefox now. This one command downloads the Firefox archive, and extracts it to a folder called firefox in your home directory. Copy and paste it (one line) into your terminal to install.
```
wget -O - http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0b5/linux-i686/en-US/firefox-3.0b5.tar.bz2 | tar xj -C ~

```
Run Firefox 3 Beta 5
Before running Firefox 3, close Firefox 2. Double-click the firefox file inside the firefox folder in your home directory, or run this command:
```
~/firefox/firefox

```
You can add Firefox 3 to your GNOME Applications menu using the menu editor in System->Preferences->Main Menu.

Missing plugins?
Firefox 3 may not see browser plugins like Flash. If you&#8217;re missing plugins, you can copy them from /usr/lib/firefox/plugins to ~/firefox/plugins.

[http://tombuntu.com/index.php/2008/04/03/install-firefox-3-beta-5-in-ubuntu-with-one-command/](http://tombuntu.com/index.php/2008/04/03/install-firefox-3-beta-5-in-ubuntu-with-one-command/)

Check out the back-up profile section on that page as well.

---

