---
title: "Terminal Question"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by krit86lr on 2006-04-23
Hi all :) 

I just installed ubuntu yesterday.  So far I really like it.  Thanks for taking the time to make this OS, and provide help to end users like myself.

I am trying to update Fire Fox.  So far I have downloaded it to my desktop and extracted it to my desktop, but that didn't work.

I read this in another thread: "Just follow these instructions. They may look involved, but it's simple copy and paste into the terminal"
_[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)_

My question is what is the terminal and where do I find it? :confused: Sorry if this is a stupid question, but I am only familiar with Windows.  A little guidance takes me a long way.  I am a fast learner.  Please be patient with me in the beginning. ;) 

Thank you in advance for your patience and assistance.

---

### Post by gr0kzer0 on 2006-04-23
You'll find the Terminal under Applications -> Accessories -> Terminal.

It's kind of like the DOS prompt in Windows (kind of...) You can type instryctions in, and hit Enter to make them happen.

---

### Post by aktiwers on 2006-04-23
When you find your terminal, like descriped above, I would really advice you to install these 2 programs. They will help you set up a lot of programs (also firefox), very very easy (easyer than windows!). Im new to Ubuntu/Linux too, and these helped me alot!

[http://ubuntuforums.org/showthread.p...ight=automatix]("http://ubuntuforums.org/showthread.php?t=138405&highlight=automatix")

and 

[http://easyubuntu.freecontrib.org/]("http://easyubuntu.freecontrib.org/")

---

### Post by aysiu on 2006-04-23
[QUOTE=gr0kzer0]You'll find the Terminal under Applications -> Accessories -> Terminal.[/QUOTE] Or if you happen to be using Kubuntu: KMenu > System > Konsole.

By the way, I wrote a script that automates the Wiki instructions for you, so you don't have to copy and paste all those commands: [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by skinnygmg on 2006-04-23
here's a list of bash commands

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

very useful

---

### Post by krit86lr on 2006-04-23
Wow!  Thanks for all of the helpful responses. :) 

I installed FF v1.5, but the browser link is still v1.0.8.  I then used the following commands to make v1.5 the default version.  Did I do this correctly?

I copied this first into Terminal and pressed enter: # First, /usr/bin/firefox
 sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
 sudo ln -s /opt/firefox/firefox /usr/bin/firefox

Then I copied this into Terminal and pressed enter: # Then, /usr/bin/mozilla-firefox, used as the default gnome browser
 sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
 sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox


Is this similar to Windows, and maybe I need to reboot for the changes to take effect?  Because it didn't work. :( Thanks again everyone!

---

### Post by 5-HT on 2006-04-23
[quote=krit86lr]Wow!  Thanks for all of the helpful responses. :) 

I installed FF v1.5, but the browser link is still v1.0.8.  I then used the following commands to make v1.5 the default version.  Did I do this correctly?

I copied this first into Terminal and pressed enter: # First, /usr/bin/firefox
 sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
 sudo ln -s /opt/firefox/firefox /usr/bin/firefox

Then I copied this into Terminal and pressed enter: # Then, /usr/bin/mozilla-firefox, used as the default gnome browser
 sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
 sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox


Is this similar to Windows, and maybe I need to reboot for the changes to take effect?  Because it didn't work. :( Thanks again everyone![/quote] 
Did you get any error messages?
When you type the following in a terminal
```
 file /usr/bin/firefox 
``` and
```
 file /usr/bin/mozilla-firefox
``` are they pointing to /opt/firefox/firefox?

If not, it would be best to do these one at a time:

```
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox 
``` ```
sudo ln -s /opt/firefox/firefox /usr/bin/firefox 
```  ```
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox 
``` ```
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox 
``` 
Hope that helps.

---

