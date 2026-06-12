---
title: "Can someone talk me through AutoMatrix?"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by MacDonagh on 2006-08-12
I'm having trouble following the instructions they've set out. Can someone show me the way?

---

### Post by MacDonagh on 2006-08-12
Anyone out there that can help me?
Don't be shy. 
Just tell me what to do, in English.

---

### Post by John.Michael.Kane on 2006-08-12
Since you don't list what issue is. this a shot in the dark.

1: **sudo gedit /etc/apt/sources.list**

2: **Add the following to your sources.list **
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

3:In Terminal **Copy paste**
wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc) gpg --import key.gpg.asc
**Then CopyPaste this**
gpg --export --armor 521A9C7C | sudo apt-key add -

4:Run This in Terminal
sudo apt-get update

5:Followed by 
sudo apt-get install automatix


Heres a list of [**[COLOR="Red"]Software and Tweaks[/COLOR]**]("http://www.getautomatix.com/wiki/index.php?title=Software_and_Tweaks") included with automatix



**[COLOR="Red"]Next time you post please be more specific about your problem/s[/COLOR]**

---

### Post by Greycloak on 2006-08-12
Have you looked here?

[http://www.ubuntuforums.org/showthread.php?t=190025](http://www.ubuntuforums.org/showthread.php?t=190025)

Just open terminal and follow the instructions.  Once it's installed just type 'automatix' and it should start up.  From that point you can choose which items you need installed.

LOL...SD-Plissken beat me to it.

---

