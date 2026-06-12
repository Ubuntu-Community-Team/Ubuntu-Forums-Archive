---
title: "Howto share Macromedia Flashplayer with browsers?"
date: 2005-05-26
forum: Absolute Beginner Talk
---

### Post by dj.shenzou on 2005-05-26
I installed Flashplayer to Firefox. Later I installed Opera browser, since it has one very good feature; I love to configure it so, that on startup it automatically starts from the last session (I hope to see this feature in Firefox in future).  Of course Opera wants to download its own version of Flashplayer. I hate to have double copies of such (needed) crap, so is there anyway in Ubuntu  that I could point Opera to use same Flasplayer than Firefox?? If you dont know, please tell at least in which folder is installed Flash that Firefox uses?

---

### Post by Stealth on 2005-05-26
Well, I'm not sure of the exact directory, but in Windows I know that in the plugins folder,, under the Firefox directory, a file called "NPSWF32.dll" is put in, and thats your Flash plugin I believe. I'm pretty sure you can't just swap it around with other browsers though. :( However, I know of an extension which you can get for Firefox, which adds a whole bunch of awesome tab features, including that restore session feature. Its called Tab Mix and you can get it [here](http://www.extensionsmirror.nl/index.php?showtopic=2291&). Just look at the extension's preferences and you'll find the session feature. :)

---

### Post by jobezone on 2005-05-27
In my system the flash plugin is installed in /usr/lib/mozilla-firefox/plugins
but it may also appear in /usr/lib/mozilla/plugins

---

### Post by Whistler on 2005-05-27
I installed the "swfdec" (a free clone of Flash player) in Debian, using the official Debian package and it works with all the browsers (Konqueror, Mozilla and Firefox).

I haven't tried Opera as I don't want to install more non-free programs

---

### Post by BobSongs on 2005-12-17
Time to revive this thread.

Okay. Firefox does a disappearing act. I click a link: any and all running copies of Firefox suddenly and mysteriously disappear.

Well, I figure I've got a choice of a variety of browsers. Let me try Opera.

Current version installed: 8.51

I downloaded Flashplayer from Macromedia. As far as I understand I've installed it to work under both Firefox and Opera. Here's a list of files. Should be self explanatory:
```
[COLOR="Black"]
bob@edubuntu:~$ cd /usr/lib/opera/plugins
bob@edubuntu:/usr/lib/opera/plugins$ ls -l -h
total 2.3M
-rwxr-xr-x  1 root root  856 2005-12-16 23:06[/COLOR] [COLOR="SeaGreen"]flashplayer.xpt[/COLOR]
[COLOR="Black"]-rwxr-xr-x  1 root root 2.0M 2005-12-16 23:06[/COLOR] [COLOR="#2e8b57"]libflashplayer.so[/COLOR]
[COLOR="Black"]-rw-r--r--  1 root root  65K 2005-11-14 08:47 libnpp.so
-rwxr-xr-x  1 root root  76K 2005-11-14 08:47[/COLOR] [COLOR="#2e8b57"]operamotifwrapper-2[/COLOR]
[COLOR="#000000"]-rwxr-xr-x  1 root root  76K 2005-11-14 08:47[/COLOR] [COLOR="#2e8b57"]operamotifwrapper-3[/COLOR]
[COLOR="#000000"]-rwxr-xr-x  1 root root 6.8K 2005-11-14 08:47[/COLOR] [COLOR="#2e8b57"]operaplugincleaner[/COLOR]

```
So, Flash is installed.

However no Flash item appears. homestarrunner.com, for example, gives me a large, black page.

What am I doing wrong? Has anyone else encountered this?

Bob

[**Edit**: Okay. That was weird. I know I opened homestarrunner and nothing showed up. Okay. So the initial page does appear. But clicking anything won't work. I suppose that's not Ubuntu's fault. Probably an Opera thing. Oh well. The logo doesn't appear on my website. Still, it's 1/2 working. Thanks anyways.]

---

