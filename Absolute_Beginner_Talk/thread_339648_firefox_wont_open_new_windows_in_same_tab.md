---
title: "firefox wont open new windows in same tab?"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2007-01-16
i just installed edgy and now fire fox wont open windows in the same tab. there aint even that option under preferences. 

also using about:config to edit the preference browser.link.open_external and setting to the value
1
   ( Open links from other programs in the current tab)

nothing happens...

any help would be great

---

### Post by ajmorris on 2007-01-16
There is an option under Edit > preferences and the "tabs" tab.

Attatched is a screenshot of the option.

---

### Post by Quillz on 2007-01-16
> **ajmorris said:**
> There is an option under Edit > preferences and the "tabs" tab.

Attatched is a screenshot of the option.
Oddly enough, even with that option checked, links still tend to open in new windows as opposed to a new tab in the current window.

---

### Post by jinxjinx on 2007-01-16
-_^

---

### Post by ajmorris on 2007-01-16
> **Quillz said:**
> Oddly enough, even with that option checked, links still tend to open in new windows as opposed to a new tab in the current window.

it depends on the configuration of the website.

---

### Post by Win2Mac2Linux on 2007-01-16
> **Quillz said:**
> Oddly enough, even with that option checked, links still tend to open in new windows as opposed to a new tab in the current window.


Agreed...I am a first tiime linux user trying Ubuntu.  I have the latest version of Firefox with the "tab" option checked and links, etc. always open in a new window.  I have yet to have something open in a new tab.  I hope it gets corrected soon.  I love that feature!!!

---

### Post by durus on 2007-01-16
uncheck open window in the same tab, save , restart firefox, then check open window in the same tab. This worked for me.

---

### Post by Win2Mac2Linux on 2007-01-16
> **durus said:**
> uncheck open window in the same tab, save , restart firefox, then check open window in the same tab. This worked for me.

I wish I had the same luck as you did.  I don't even get new windows opening.  The current open window updates to the link I click on.  Hmmm...  :-k 

Thanks though.  :)

---

### Post by Win2Mac2Linux on 2007-01-16
> **durus said:**
> uncheck open window in the same tab, save , restart firefox, then check open window in the same tab. This worked for me.

Now, all of a sudden, links are opening up in tabs!!!  Hmmm...
Well, whatever!!!  As long as it's working now...

I've been up all night.  Maybe I rebooted or something and wasn't paying attention and that helped...

---

### Post by jinxjinx on 2007-01-16
i have the opposite problem I DONT want tabs or new windows....but i cant find the option for this....

---

### Post by Win2Mac2Linux on 2007-01-16
> **jinxjinx said:**
> i have the [http://sports.yahoo.com/nhl/standingsopposite](http://sports.yahoo.com/nhl/standingsopposite) problem I DONT want tabs or new windows....but i cant find the option for this....

As far as I know, when you edit "Preferences" in Firefox you have to choose between opening in a new tab or window.  I'm not sure if there is an option just to constantly update the currently open window.  It is the same under System>Preferences>Preferred Applications options.   There are also preference settings for tab or window.  I think (in your case) you might have to pick the lesser of two evils.  Maybe someone more knowledgeable than I might know a way.  Good luck.

---

### Post by jinxjinx on 2007-01-17
yeah i cant believe this. the older version of firefox had this option.

it just seems more intuitive to me...

---

### Post by Kimos on 2007-11-02
Win2Mac2Linux has the right idea. In Gnome:

[LIST]
[*]Menu through: System -> Preferences -> Preferred Applications
[*]Click on the Internet tab
[*]Select Firefox for the web browser
[*]Select Open Link in New Tab
[/LIST]

It'll fill the command to something like: firefox -remote "openurl(%s,new-tab)"

Honesly, I don't know why you have to set this in two places, one of them being outside the app. Took me a while to figure this out.

---

### Post by stchman on 2007-11-02
Very easy fix:

[http://www.stchman.com/tweaks.html](http://www.stchman.com/tweaks.html)

Look at open links in new tabs.  Strange is that it is the default for Firefox on Windows.

---

### Post by alienexplorers on 2007-11-02
Have you tried Tab Mix Plus which gives you more control of what opens where.  It can be found at:
> [https://addons.mozilla.org/en-US/firefox/addon/1122](https://addons.mozilla.org/en-US/firefox/addon/1122)

---

