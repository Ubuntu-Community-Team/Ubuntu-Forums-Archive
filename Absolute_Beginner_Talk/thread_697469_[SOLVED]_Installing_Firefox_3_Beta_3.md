---
title: "[SOLVED] Installing Firefox 3 Beta 3"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by The Hunt For Ida Wave on 2008-02-15
Being relatively new to Ubuntu I've not yet grasped how to install applications that aren't from the repos. Can anyone give me instructions to install the beta of firefox 3?

---

### Post by Kileak on 2008-02-15
The easiest way (if I'm not mistaken) is to not install it, just download this file:

[http://www.mozilla.com/products/download.html?product=firefox-3.0b3&os=linux&lang=en-US]("http://www.mozilla.com/products/download.html?product=firefox-3.0b3&os=linux&lang=en-US")

(you should close down Firefox before doing the rest)

unzip it (say to your desktop) and run the file 'firefox' inside the folder. (a simple double click, run, should do).

This won't trash your old Firefox install, and your old bookmarks etc will be used, but you should make sure you don't have any instances of your old Firefox running.

You can create a launcher for this file easy enough:

(say on the desktop)

right click >> Create Launcher...
Type : Application
Name : Firefox 3 Beta 3
Command : /home/{user}/Desktop/firefox/firefox
replace {user} above with your user name...
choose an icon if you like
click OK

Done.

Edit: I am using Feisty, so YMMV

---

### Post by bollix47 on 2008-02-15
You can use synaptic to install it.

Firefox 3.0 is in the universe repository and b3 is in gutsy-backports.

To activate the universe open synaptic and go to settings>repositories.
To activate backports ... settings>repositories>updates.

Place check next to universe and gutsy-backports. Save and reload, then search for firefox.

Edit: To include backports for b3 version.

---

### Post by Joeb454 on 2008-02-15
I think the version in the Universe Repo is slightly older...last time I checked it was an alpha build...yep...synaptic lists Firefox 3 as being Alpha 8.

I think we can say that is some way behind Beta 3 :)

---

### Post by bollix47 on 2008-02-15
> **Joeb454 said:**
> I think the version in the Universe Repo is slightly older...last time I checked it was an alpha build...yep...synaptic lists Firefox 3 as being Alpha 8.

I think we can say that is some way behind Beta 3 :)

Yes you are correct.  To get b3 version you have to activate the backport repository.

Synaptic > Settings > Repositories > Updates

Check the gutsy-backports entry.

Close and Reload.

---

### Post by Kosimo on 2008-02-15
> **bollix47 said:**
> Yes you are correct.  To get b3 version you have to activate the backport repository.

Synaptic > Settings > Repositories > Updates

Check the gutsy-backports entry.

Close and Reload.

The current Firefox Beta 3 availbe in gutsy-backports isn't the newest one. Cuz is still the PRE-Beta3.

---

### Post by The Hunt For Ida Wave on 2008-02-16
Thank you Kileak, got it. :)

---

### Post by billgoldberg on 2008-02-16
For future reference, this is how I installed it:

Download the file [here]("http://en-us.www.mozilla.com/en-US/firefox/all-beta.html") (save it on the desktop)

Just copy past this into the terminal.

   ```
 sudo tar -C /opt -jxvf /home/username/Desktop/firefox-3.0b3.tar.bz2

```
```
    cd /opt/firefox/plugins/
```

```
    sudo ln -s /usr/lib/firefox/plugins/* .
```

    ```
cd
```

```
    sudo dpkg-divert –divert /usr/bin/firefox.ubuntu –rename /usr/bin/firefox
```

```
    sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

```
    sudo dpkg-divert –divert /usr/bin/mozilla-firefox.ubuntu –rename /usr/bin/mozilla-firefox
```

```
    sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
```


I had to add firefox to the “applications -> internet” again.

Move your mouse above “applications” and right click it. Choose to “edit menu”, select”internet” on the left, then select “new item”on the right. Fill this in:

- Firefox 3 beta 3
- firefox
- web browser

Then hit ok. The icon picture should be added by default.

If you had java and flash support in firefox 2, you’ll have it in ff3.

---

### Post by The Hunt For Ida Wave on 2008-02-16
What does the "cd /opt/firefox/plugins/" command do?

I'm trying to install flash player but I get this error everytime "Firefox could not install this item because "install-if5..rdf" (provided by the item) is not well-formed or does not exist. Please contact the author about this problem."

I have Flash/Java in FF2 but it seems not to have been implemented into FF3.

---

### Post by The Hunt For Ida Wave on 2008-02-16
I just downloaded and used the tar.gz installer instead. Working fine now. :)

---

