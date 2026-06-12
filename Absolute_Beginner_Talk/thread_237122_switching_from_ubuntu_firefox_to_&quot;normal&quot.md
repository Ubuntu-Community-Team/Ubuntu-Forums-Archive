---
title: "switching from ubuntu firefox to &quot;normal&quot; release"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by shoagun on 2006-08-15
i would like to switch to mozilla-firefox instead of using the firefox that came with ubuntu.  is there a way to do this without losing my current settings (ie bookmarks, plugins, extensions)?

---

### Post by meng on 2006-08-15
Umm, forgive my ignorance, but what's the difference? I always thought mozilla firefox WAS firefox. I know that mozilla is not firefox, but mozilla firefox?

---

### Post by skale on 2006-08-15
Extentions and plugins might be tough, as for bookmarks, look for a bookmarks-something in .mozilla/firefox

I believe the Ubuntu version is 0.0.2 versions behind. Is there a specific problem you have with the ubuntu firefox?

---

### Post by flaak_monkey on 2006-08-15
are you reffering to Swiftfox?

---

### Post by xinix on 2006-08-15
I think the OP means switching from the firefox included with the distro to the one you get from mozilla.org.  It's no big deal just download the file and uncompress it.  To run it just open the folder and fun the script "firefox".  You'll need to make links for your current plugins in the plugins folder in your new FF Folder.  Your extension should work just fine unless you are switching to the Beta2 version.

---

### Post by shoagun on 2006-08-15
Sorry I wasn't clear.  I wasn't sure what the appropriate termnology was.  Anyway, xinix got my question right. 

Anyway, I was interested in figuring out how this all works, so I played around with it a bit.  It turns out pretty much all settings are saved separately from the install.  So I uninstalled the FF that came with Ubuntu.  I downloaded the FF on the Mozilla site, and opend it.  My bookmarks and my extensions were unchanged.  To save plugins, I simply had to copy plugins from the old FF folder to the new FF folder.  

Now, the only problem is that I've lost my convinient quicklaung icon.  To start firefox, I have to go to the FF directory and type ./firefox
This is a little annoying.  Anyone know how to get that nice icon back?

---

### Post by meng on 2006-08-15
Right click the GNOME panel (top or bottom, your choice), select Add to Panel ..., Custom Launcher, then you'll probably enter /usr/bin/firefox, or maybe just firefox.

---

### Post by steve.horsley on 2006-08-15
Not too hard to do.

Download the firefox tar.gz from mozilla.com. Open a command prompt and do this:
> cd /opt
sudo tar xfz /home/whoever/wherever/firefox-1.5.0.6.tar.gz
sudo rm /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox

To update this new installation of firefox when a new version comes out you will need to use the command **gksudo firefox** and the menu Help->Check for updates. 

When Ubuntu updates its version of firefox you will need to run this command again:
> sudo rm /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox

---

### Post by shoagun on 2006-08-15
Hey Steve, thanks a bunch!  One question though.  Are you saying that I should move the FF directory that I unpack to /opt ?  Right now I have it in my home directory, and I suppose I could create the link between /home/me/firefox/firefox and /usr/bin/firefox but would it be better to put it in /opt ?  I noticed that Ubuntu had the FF directory in /Usr/lib I think.  I'm not sure if it matters.

---

### Post by Frank Golden on 2006-08-15
Still don't answer Meng's question. WHY?
The version that came with my Ubuntu works just fine.
Should I be looking for a real or percieved problem/difference?

---

### Post by msak007 on 2006-08-15
Some people don't want to wait for the repo maintainers to release a new package for it to upgrade. The repo version is usually 1-2 releases behind (from what I've noticed). New versions usually have bug fixes or minor enhancements, and there's usually no hurry to update the repo version unless it's some critical security fix so it takes a while for an update. Also, some people tend to notice that the downloaded version is faster than the one included in Ubuntu (there's always Swiftfox). Personally, I opted to download it from Mozilla rather than use the repo version.

---

### Post by Frank Golden on 2006-08-15
> **msak007 said:**
> Some people don't want to wait for the repo maintainers to release a new package for it to upgrade. The repo version is usually 1-2 releases behind (from what I've noticed). New versions usually have bug fixes or minor enhancements, and there's usually no hurry to update the repo version unless it's some critical security fix so it takes a while for an update. Also, some people tend to notice that the downloaded version is faster than the one included in Ubuntu (there's always Swiftfox). Personally, I opted to download it from Mozilla rather than use the repo version.
That makes sense. I did notice that the option to update firefox does't exist in the Ubuntu version. Does the manual update option exist in the "normal" version and if it does is it seamless. By that I mean do I have to jump through hoops to install the updates.

---

### Post by msak007 on 2006-08-15
Yes, it does exist. It's normally grayed out if you start Firefox as a normal user, but if you start it using gksudo (in Gnome) or kdesu (in KDE), then that option is available. If an update is available, it downloads it and upon a restart it installs it. Very seamless, very easy, and no need to download or install anything manually again after the initial install. The only thing about doing it this way is that you have to know that there is an update to run Firefox as root.

---

### Post by shoagun on 2006-08-16
Steve,

I reread your post and realized that you untarred the directory into /opt.  So I assume keeping it here is the desired option.  Creating the link worked in that now I can just type firefox into the commandline to open firefox, but I still would like an icon quicklaunch.  I lost the original when I uninstalled ubuntu's firefox.  

It's a pretty n00b question, but anyone know how I can make quicklaunch icon?

---

### Post by shoagun on 2006-08-16
Nevermind.  I realized the best thing to do was to reinstall ubuntu's firefox and then to simply replace /usr/lib/firefox with the firefox directory unpacked from the tarball available at the FF website.

---

### Post by steve.horsley on 2006-08-16
Glad you got it working. The reason I don't say to untar the file locally and then **move** it to /opt is because that would leave  the installation owned by you and it should be owned by root. Copying the local untarred folder is OK I think, because copying changes the owner. 

Apart from the fact that you cannot use the online update in the Ubuntu version, for some reason they change (downgrade) the version of javascript being used to an earlier version than the real firefox. I have no idea why.

---

