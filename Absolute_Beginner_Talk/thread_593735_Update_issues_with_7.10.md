---
title: "Update issues with 7.10"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Exedus on 2007-10-27
I'm a brand new Linux user and I've just installed 7.10 of Ubuntu. I tried the live disk first and then installed under second partition and dual booting with Windows XP. I've decided to get rid of Windows all together as my laptop is a MAC and I reinstalled Ubuntu and got rid of Windows all together. When I installed under a dual boot I received updates to Ubuntu automatically. But after the re-install it seems I cant get auto updates. I even went to the updates manager and refreshed and still nothing. Firefox is still at 2.0.6 and I know there are other updates that were available as well. Anyone have any ideas? I'd love to keep my system up to date.

---

### Post by overdrank on 2007-10-27
> **Exedus said:**
> I'm a brand new Linux user and I've just installed 7.10 of Ubuntu. I tried the live disk first and then installed under second partition and dual booting with Windows XP. I've decided to get rid of Windows all together as my laptop is a MAC and I reinstalled Ubuntu and got rid of Windows all together. When I installed under a dual boot I received updates to Ubuntu automatically. But after the re-install it seems I cant get auto updates. I even went to the updates manager and refreshed and still nothing. Firefox is still at 2.0.6 and I know there are other updates that were available as well. Anyone have any ideas? I'd love to keep my system up to date.

You can try to update in the terminal
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
You can replace apt-get with aptitude if you prefer.

---

### Post by Exedus on 2007-10-27
More info: it seems that I'm having the same problem installing new apps. I tried installing VLC and it kept asking me to refresh every time I tried to check it. My new connection obviously works fine since I'm able to post here. I'm so confused. 

Also,,,,holy crap a response already! You guys work fast here. Could somebody explain what the above suggestion does. As I said I'm a real Linux Noobie.

---

### Post by perlluver on 2007-10-27
As for the firefox updating, try this site ubuntuzilla.wiki.sourceforge.net/.  Helped me out a lot.

---

### Post by overdrank on 2007-10-27
> **Exedus said:**
> 
Also,,,,holy crap a response already! You guys work fast here. Could somebody explain what the above suggestion does. As I said I'm a real Linux Noobie.

I was merely suggesting updating through the terminal if you would like. You can also link those commands together also like ```
sudo apt-get update && sudo apt-get upgrade
```
the terminal located under applications, accessories, terminal

---

### Post by Exedus on 2007-10-27
Thanks for all the help. Any explainations on why it was working while dual booting and now that I've done a full install nothing?

---

### Post by overdrank on 2007-10-27
> **Exedus said:**
> Thanks for all the help. Any explainations on why it was working while dual booting and now that I've done a full install nothing?

If you have just download and install the you probably have the latest installation. :KS
Edit if you do not see any errors with the commands then I would say you are up to date .

---

### Post by Exedus on 2007-10-27
Tried the terminal command and says everything is up to date. I guess I'm just confused as to why the first time I installed I had updates available, like Firefox, but this time nothing. Doesn't really make sense.

EDIT: Also it doesn't explain why I can't install new applications as well.

---

### Post by Exedus on 2007-10-27
bump?

---

### Post by Exedus on 2007-10-27
I still don't believe that my system is up to date no matter what Ubuntu is telling me as I still can't seem to download and install apps. I think the two are related.

---

### Post by Exedus on 2007-10-27
OK I just did a complete re-install and still nothing. Please can somebody help? I really would like to continue using Linux as things did work great when I was dual booting. I really don't want to have to re-install XP. I still can't see updates and I still can't download and install apps. Please help.

---

### Post by Exedus on 2007-10-27
I think I found the problem. All of the sources in the software sources were unchecked. Once I checked I few of them the updates popped up. I'm still not sure why I didn't have to do this the first time.

---

