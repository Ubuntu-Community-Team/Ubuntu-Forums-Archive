---
title: "remove firefox 2"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by fasoulas on 2006-12-04
I want to remove firefox 2 from my ubuntu because it is highly unstable and it hangs all tha time espesially when i have 6-7 tabs open
It has a big deference from my firefox 2 on windows that one is much faster and i rerly face any problems i don't now the reason maybe it doesn't perform well on ubuntu

when i try to close a tab i have to wait for about 10s for it and see the next tab

I want firefox 1.5 back 

I installed it from a site with istructions that i don't remember...
Is there a way to remove it 

I tried a search in the synaptic and i found some packages of firefox 1.5.8 installed but i use firefox 2 

Msybe if i remove firefox 2 the old firefox will come back

HELP ME!!!!!!

---

### Post by kakalaky on 2006-12-04
```
man apt-get
```

---

### Post by jordanmthomas on 2006-12-04
You really need to find out how you did it, but if you remember anything involving symlinks this should help

I'm not sure how you installed firefox 2, but this should fix it so you use firefox 1.5.0.8

First, look to make sure you do in fact have 1.5.0.8 installed
```
ls /usr/lib/firefox-1.5.0.8 | grep firefox
```
If firefox and firefox-bin show up, then you should be ok.

Then, rename your current firefox symlink so if it doesn't work you can name it back and go back to firefox 2
```
sudo mv /usr/bin/firefox /usr/bin/firefox.backup
```
Then, create a new link back to firefox 1.5
```
sudo ln -s /usr/lib/firefox-1.5.0.8 /usr/bin/firefox
```
see if it works after closing any open firefoxes
```
firefox
```

If for some reason it doesn't, you can do this to switch back to firefox 2 until you can get another solution.
```
sudo mv /usr/bin/firefox.backup /usr/bin/firefox
```

---

### Post by fasoulas on 2006-12-04
> **jordanmthomas said:**
> You really need to find out how you did it, but if you remember anything involving symlinks this should help

I'm not sure how you installed firefox 2, but this should fix it so you use firefox 1.5.0.8

First, look to make sure you do in fact have 1.5.0.8 installed
```
ls /usr/lib/firefox-1.5.0.8 | grep firefox
```
If firefox and firefox-bin show up, then you should be ok.

Then, rename your current firefox symlink so if it doesn't work you can name it back and go back to firefox 2
```
sudo mv /usr/bin/firefox /usr/bin/firefox.backup
```
Then, create a new link back to firefox 1.5
```
sudo ln -s /usr/lib/firefox-1.5.0.8 /usr/bin/firefox
```
see if it works after closing any open firefoxes
```
firefox
```

If for some reason it doesn't, you can do this to switch back to firefox 2 until you can get another solution.
```
sudo mv /usr/bin/firefox.backup /usr/bin/firefox
```

 ```
ls /usr/lib/firefox-1.5.0.8 | grep firefox
```

When i put this command i see this 

ls /usr/lib/firefox-1.5.0.8 | grep firefox
ls: /usr/lib/firefox-1.5.0.8: No such file or directory

i think i installed it with apt-get

---

### Post by kakalaky on 2006-12-04
Just adapt the instructions here for the version of Firefox you want:

[https://help.ubuntu.com/community/FirefoxNewVersion]("https://help.ubuntu.com/community/FirefoxNewVersion")

---

### Post by jordanmthomas on 2006-12-04
> **fasoulas said:**
> ```
ls /usr/lib/firefox-1.5.0.8 | grep firefox
```

When i put this command i see this 

ls /usr/lib/firefox-1.5.0.8 | grep firefox
ls: /usr/lib/firefox-1.5.0.8: No such file or directory

i think i installed it with apt-get

That's just where it was on my system.  I actually use Fedora, and I assumed the location would be the same.  Basically, you'd have to find where it is installed and updated the symlinks.  

Since it's not the exact same, I'd suggest following the link kakaly provided.

---

### Post by fasoulas on 2006-12-05
#

 # First, /usr/bin/firefox
 sudo rm /usr/bin/firefox
 sudo dpkg-divert --rename --remove /usr/bin/firefox
 # Then, /usr/bin/mozilla-firefox, used as the default gnome browser
 sudo rm /usr/bin/mozilla-firefox
 sudo dpkg-divert --rename --remove /usr/bin/mozilla-firefox
 

#

Restore your old profile:

 cd
 mv .mozilla .mozilla-20
 mv .mozilla.ubuntu .mozilla
 

#

(optional) Delete the firefox directory

 sudo rm -r /opt/firefox
 
i made these steps from the link that kakalaky posted 
There are under the Removing option 

Have i deleted all the files of firefox???

And after i installed Swiftfox 1.5 from automatix 

And now i don't have any problems but have i deleted all the files of the other firefox with the commands i have putted??

---

### Post by Ben Sprinkle on 2006-12-05
```

sudo apt-get install -u firefox2.0

```
Or:
```

sudo apt-get uninstall firefox2.0

```
Can't remember which, if says no program try firefox-2.0 or just firefox.

---

