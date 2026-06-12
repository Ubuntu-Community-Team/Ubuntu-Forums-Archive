---
title: "Does Evolution Support Auto-Complete when entering in a contact?"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-09-17
I like this in Thunderbird where

[LIST=1]
[*]you type in a contact and it gets added to your contact list (except when you type the name      wrong, tha's annoying)
[*]when you start type in the "To:" feild and it begins to auto-complete and give you suggestions,                         this really helps.
[/LIST]
Anybody know how I can do this in Evolution? (Or I could just go ahead and download thunderbird...)

Static Void

---

### Post by philinux on 2007-09-17
Autocomplete works in evolution too.

Just by typing a name same as TB. I use TB because of the webmail extension so I get hotmail.

---

### Post by staticvoid on 2007-09-20
maybe I imported my contacts list wrong....how did u do it?
sv

---

### Post by tombott on 2007-09-20
Auto complete works with me as well in Evo, but my contact come from a Exchange server and one's i have manually added.

Can I ask your reasons from switching from Thunderbird to Evo?

I use Evo to connect to my works exchange server and use Thunderbird for my personal email.

I can't see any advantage using Evo over Thunderbird unless you want Exchange / GroupWise support.

The Lighting add-on in Thunderbird is great for Calendar / To Do

---

### Post by staticvoid on 2007-09-21
I could never get 2.0.0.6 thunderbird to install, only 1.5 which I do not like... I just go the latest version and I'm trying to get it working. I ran the "thunderbird" script. I hope it will work.

sv

---

### Post by rahimveron on 2007-09-21
Open your /etc/apt/sources.list as root
```
sudo gedit /etc/apt/sources.list
```
Add the following two lines at the end of the sources.list file and save
```
deb http://ubuntu.iuculano.it feisty thunderbird
deb-src http://ubuntu.iuculano.it feisty thunderbird
```
Open the terminal and update```
sudo apt-get update
```
Now to install thunderbird, enter in the terminal
```
sudo apt-get install thunderbird
```
for more details use this link
[http://ubuntu.iuculano.it/dists/feisty/thunderbird/]("http://ubuntu.iuculano.it/dists/feisty/thunderbird/")

---

### Post by staticvoid on 2007-09-21
Thanks,
I should have waited for you rahimveron, I've allready got it installed. I added the repositories to the source list and then just went to Add and Remove..

I hope some one finds your tutorial to there benifit. Very clear and srtaight forward :D.
How to install thunderbird 2 new version :)

Static V.

p.s. How can I intergrate Pidgin with Thunderbird? It says "Plugin for intergration with Evolution".

---

