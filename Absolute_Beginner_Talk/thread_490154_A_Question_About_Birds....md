---
title: "A Question About Birds..."
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by tcoffeep on 2007-07-02
Not birds, specifically, but Pidgin :)

Sorry, that was lame.

Anyways, I was trying to figure out how to update my version of GAIM to Pidgin, and from the tutorials on some sites, it says all I basically have to do is

> sudo apt-get update
sudo apt-get install pidgin

But when I attempt to do that, alas, no pidgin package found. Uhm, is there any ideas on this?

---

### Post by Brucevdk on 2007-07-02
Pidgin isn't in the repositories, apt-get works by fetching packages from repositories you have defined (Ubuntu provided ones are main, universe and multiverse) although I believe it can also be used for different purposes (no hands-on experience with that though). Sometimes packages are backported from the upcoming release (e.g. Gutsy), which you can see as releasing an update. From what I can tell this doesn't happen very often and it certainly hasn't been the case for Pidgin.

I'm not aware of a repository that contains Pidgin, though you'll probably find one mentioned in one of the many threads in this forum. However, you can get the Debian package from [GetDeb]("http://www.getdeb.net/release.php?id=1045") or compile it from source. A reminder here is probably appropriate: always remember to be very careful about the software you install and who to trust.

---

### Post by Malibu Illusion on 2007-07-02
[http://pidgin.im/pidgin/home/](http://pidgin.im/pidgin/home/)

Download, execute:

```
./configure
make
sudo make install
```

Alternatively, if you don't fancy compiling from source, follow the simple instructions here:

[http://www.debuntu.org/pidgin-2.0.0-deb-ubuntu-feisty-fawn](http://www.debuntu.org/pidgin-2.0.0-deb-ubuntu-feisty-fawn)

I believe you've missed out the addition of the required repositories from what you're saying.

---

### Post by tcoffeep on 2007-07-02
Thank you very much. Pidgin is installed, and working.

---

### Post by Malibu Illusion on 2007-07-02
Something to note that I've just realised actually, the .deb that I linked to is a backport of the 2.0.0 version.  Pidgin is currently 2.0.2 so if you explicitly want the very latest version you'll have to check out the GetDeb page that Brucevdk linked, if you didn't do so already, or compile from the source tarball.

---

### Post by RomeReactor on 2007-07-02
Hi. If you decide to compile [Pidgin]("http://pidgin.im/pidgin/download/source/") (as I did), you'll need the following libraries to enable MSN compatibility:
```
sudo apt-get install libgtk2.0-dev libxml2-dev gettext libnss-dev libnspr-dev
```
once you download the file and the libraries are installed, put your **pidgin-2.0.2** folder in your home directory and rename it as **.pidgin-2.0.2** (notice the dot before the name ) to hide it; now open a terminal, and enter:
```
cd .pidgin-2.0.2
```
then
```
./configure
```
next
```
make
```
and finally
```
sudo make install
```
to make an icon for it, right-click on the menu (Applications Places System), select "Edit Menus", highlight "Internet" on the left and press "New Item". Fill it out like this:

*Type: Application
*Name: Pidgin Internet Messenger
*Command: pidgin
*Comment: Send instant messages over multiple protocols

The icon is located in **/home/YOUR_USER_NAME/.pidgin-2.0.2/pidgin/pixmaps/pidgin.ico**

EDIT: I'm too slow...

---

### Post by Brucevdk on 2007-07-02
> **RomeReactor said:**
> Hi. If you decide to compile [Pidgin]("http://pidgin.im/pidgin/download/source/") (as I did), you'll need the following libraries to enable MSN compatibility:

You could probably also use:
```
sudo apt-get build-dep gaim
```

---

