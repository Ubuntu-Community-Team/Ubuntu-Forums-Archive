---
title: "Thunderbird opening wrong browser"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-09-14
Hi, I use thunderbird for my rss feeds because for me it works best, however I use Flock as my browser but used to use firefox, now what I want is for when I click on links in thunderbird it to open them in Flock not Firefox, Flock is the default browser on my system but it seems that thunderbid keeps pointing to firefox, can I change this?

Calv

---

### Post by mitch.c on 2006-09-14
Create a file called user.js (if it doesn't already exist in your Thunderbird profile directory), and add these lines:
```
user_pref("network.protocol-handler.app.http", "/path/to/flock");
user_pref("network.protocol-handler.app.https", "/path/to/flock");
user_pref("network.protocol-handler.app.ftp", "/path/to/flock");
```
Your user profile dir is located in:
~/.mozilla-thunderbird/profilename/
where profile name is some random char string + .profile name: ie, plg7c2yj.default

---

### Post by calvinthomas on 2006-09-14
I added this as said and changed the part at the end to where flock was on my system but it still opens things up in firefox, I tried rebooting just incase that was necessary but it didn't help. Do I need to tell it to use those settings somehow?

Calv

---

### Post by mitch.c on 2006-09-14
That's odd. I can change those lines to any browser on my system and Thunderbird will open that browser regardless of the Gnome default. Try this (Thunderbird):
1. In the Edit menu, click Preferences.
2. Select the Advanced tab, and click Config. Editor.
3. Type network.protocol-handler.app.http in the filter and verify the path to flock.
If it is not correct, then you may have more than one profile on your system in which case you need to make the changes to the correct profile.

You said flock is your default browser, how did you set it?

Does flock appears as an alternative in the output of these two commands?
```
update-alternatives --display x-www-browser
update-alternatives --display gnome-www-browser
```

---

### Post by calvinthomas on 2006-09-14
In 3) I don't have that at all in config editor! there is none at all!

Also, the entry is not right from a terminal I get:

calvin@calvin-laptop:~$ update-alternatives --display x-www-browser
x-www-browser - status is auto.
 link currently points to /usr/bin/opera
/usr/bin/firefox - priority 70
 slave x-www-browser.1.gz: /usr/share/man/man1/firefox.1.gz
/usr/bin/opera - priority 80
Current `best' version is /usr/bin/opera.
calvin@calvin-laptop:~$ update-alternatives --display gnome-www-browser
No alternatives for gnome-www-browser.

I said, set as default in flock, to set as default

Calv

---

### Post by mitch.c on 2006-09-14
> **calvinthomas said:**
> In 3) I don't have that at all in config editor! there is none at all!
Are you saying the network.protocol-handler.app.http value is empty or that  network.protocol-handler.app.http doesn't exist?

Either way, that means the values in user.js aren't being read. What is the output of
```
ls ~/.mozilla-thunderbird
```

> **calvinthomas said:**
> Also, the entry is not right from a terminal I get:

calvin@calvin-laptop:~$ update-alternatives --display x-www-browser
x-www-browser - status is auto.
 link currently points to /usr/bin/opera
/usr/bin/firefox - priority 70
 slave x-www-browser.1.gz: /usr/share/man/man1/firefox.1.gz
/usr/bin/opera - priority 80
Current `best' version is /usr/bin/opera.
calvin@calvin-laptop:~$ update-alternatives --display gnome-www-browser
No alternatives for gnome-www-browser.

Well, your X browser is set to Opera. Adding flock to your alternatives would probably be a good idea.
```
sudo update-alternatives --install /usr/bin/x-www-browser x-www-browser /path/to/flock 70
sudo update-alternatives --install /usr/bin/gnome-www-browser gnome-www-browser /path/to/flock 70

```
And then select flock for each of these:
```
update-alternatives --config x-www-browser
update-alternatives --config gnome-www-browser
```

> **calvinthomas said:**
> I said, set as default in flock, to set as default
AFAIK, this won't do anything in linux. Set here instead (gnome menu):
System -> Preferences -> Preferred Applications

---

### Post by calvinthomas on 2006-09-14
Simply selecting custom in system > preferences > preferred applications and selecting web browser to custom and changing it to flock fixed the problem in thunderbird!

Thanks for your help!

Calv

---

