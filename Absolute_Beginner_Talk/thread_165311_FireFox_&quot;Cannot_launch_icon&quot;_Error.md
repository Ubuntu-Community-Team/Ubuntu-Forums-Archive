---
title: "FireFox &quot;Cannot launch icon&quot; Error"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by krit86lr on 2006-04-24
Hi all :) I am starting a new thread so that my other thread doesn't get too far off topic.

I just installed ubuntu 2 days ago.  I used automatix to install a lot of software including FireFox 1.5.0.2.  The browser link was still 1.0.8 so I tried to make 1.5 the default by doing the following.

**I copied this first into Terminal and pressed enter:** # First, /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox

**Then I copied this into Terminal and pressed enter:** # Then, /usr/bin/mozilla-firefox, used as the default gnome browser
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox

I did not receive any errors until I rebooted and clicked the FireFox launch icon.
[I][B]Cannot launch icon
Details: Failed to execute child process "firefox" (No such file or directory)[/B][/I]

Does anyone know how to resolve this error? :confused:  Thank you in advance for your time.

---

### Post by krit86lr on 2006-04-24
I am thinking that maybe I should just reinstall Ubuntu and start over.  Is there a link that I can use to search for errors btw?

---

### Post by xenmax on 2006-04-24
The error basicaly means that it was not able to find any executable file called 'firefox' in any of paths in your $PATH
You can check if this is indeed case with ```
which firefox
```
Also, if /opt/firefox/firefox exists and it works(launch /opt/firefox/firefox and check), then you can right click on firefox icon -> Properties and change Command field to /opt/firefox/firefox instead of firefox as a temporary fix.

---

