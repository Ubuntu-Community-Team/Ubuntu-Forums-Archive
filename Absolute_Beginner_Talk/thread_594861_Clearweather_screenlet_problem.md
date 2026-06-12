---
title: "Clearweather screenlet problem?"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by Octavgmail.come on 2007-10-28
I installed the Clearweather screenlet with the following

 "wget [http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg](http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg) -O- | sudo apt-key add -"

 echo "deb [http://hendrik.kaju.pri.ee/ubuntu/](http://hendrik.kaju.pri.ee/ubuntu/) gutsy screenlets" >> /etc/apt/sources.list

"sudo apt-get update && sudo apt-get install screenlets"

So now my screenlet manager shows up but when i go to import the clearweather into it it does not see the ClearWeatherScreenlet.py , Really what i want to do is to have this run on startup anyone know how to resolve this?

---

### Post by Octavgmail.come on 2007-10-28
anyone?

---

### Post by lizerazu on 2007-10-28
If you've installed the [screenlets core]("http://www.screenlets.org/index.php/Home") then if you put the screen lets in your /home/(user)/.screenlets directory then all you need to do is run screenlets-manager (also found in the Admin menu) and there you can set it to start on launch.

---

