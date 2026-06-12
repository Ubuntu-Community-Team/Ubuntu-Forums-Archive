---
title: "Mozilla Firefox - No Such File or Directory"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by Clay85 on 2006-05-12
I just re-installed Ubuntu. The first time I installed it I updated Mozilla Firefox from 1.08 to 1.5.0.3 no problem. This time I'm having really bad luck.

I'm using this script:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

which seems simple enough. This is what's happening:
```
 enzo@reboot:~/Desktop$ chmod +x installnewfirefox.sh
enzo@reboot:~/Desktop$ ./installnewfirefox.sh
bash: ./installnewfirefox.sh: /bin/sh^M: bad interpreter: No such file or directory
enzo@reboot:~/Desktop$ ls
firefox-1.5.0.3.tar.gz  installnewfirefox.sh  removenewfirefox.sh
enzo@reboot:~/Desktop$

```

I tried looking in the Synaptic Package Manager, but I couldn't find 1.5.0.3 there.

---

### Post by aysiu on 2006-05-12
That's weird. I'm looking at the source file, and I don't see a /bin/sh^M: ```
**#!/bin/sh**
echo "Updating repositories list
"
sudo apt-get update
echo "
Making sure libstdc++5 and the old Firefox are installed
"
sudo apt-get -y install firefox libstdc++5
echo "
Backing up old Firefox preferences
"
cp -R ~/.mozilla ~/.mozilla_backup
echo "
Changing to home directory
"
cd
echo "
Downloading Firefox from the Mozilla site
"
wget -c http://ftp-mozilla.netscape.com/pub/mozilla.org/firefox/releases/1.5.0.3/linux-i686/en-US/firefox-1.5.0.3.tar.gz
echo "
Unzipping the .tar.gz file
"
sudo tar -C /opt -x -z -v -f firefox-1.5.0.3.tar.gz
echo "
Removing the unzipped .tar.gz
"
rm firefox-1.5.0.3.tar.gz
echo "
Linking plugins
"
cd /opt/firefox/plugins/
sudo ln -s /usr/lib/mozilla-firefox/plugins/* .
echo "
Linking launcher to new Firefox
"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
echo "
The new Firefox is installed."
``` Is there a way for me to know if there's a ^M in there?

---

### Post by aysiu on 2006-05-12
Could you do me a favor and re-download the file (clear your Firefox cache first) from the website and try again? See if you still get the ^M error.

Just so you know, I've modified the script since the first time you used it. The original download mirror died, so I put in an active mirror, and I may have inadvertently put in some kind of strange invisible character after the first line...

---

### Post by Clay85 on 2006-05-12
Delete the installnewfirefox.sh file and redownload it? I can do that. Do you want me to post the innards of the file, too?
Where is the firefox cache?

redownloaded file:
```
#!/bin/sh

echo "Updating repositories list

"

sudo apt-get update

echo "

Making sure libstdc++5 and the old Firefox are installed

"

sudo apt-get -y install firefox libstdc++5

echo "

Backing up old Firefox preferences

"

cp -R ~/.mozilla ~/.mozilla_backup

echo "

Changing to home directory

"

cd

echo "

Downloading Firefox from the Mozilla site

"

wget -c http://ftp-mozilla.netscape.com/pub/mozilla.org/firefox/releases/1.5.0.3/linux-i686/en-US/firefox-1.5.0.3.tar.gz

echo "

Unzipping the .tar.gz file

"

sudo tar -C /opt -x -z -v -f firefox-1.5.0.3.tar.gz

echo "

Removing the unzipped .tar.gz

"

rm firefox-1.5.0.3.tar.gz

echo "

Linking plugins

"
```

---

### Post by Clay85 on 2006-05-12
Now I get:
```
enzo@reboot:~$ cd Desktop
enzo@reboot:~/Desktop$ chmod +x installnewfirefox.sh
chmod: cannot access `installnewfirefox.sh': No such file or directory
enzo@reboot:~/Desktop$

```

That's the same thing I was getting before, but now at the first command instead of the second command.
I'm not sure how I'm failing a two step process. Of course, leave it to me to fail at a two step process.
1.) chmod +x installnewfirefox.sh
2.) ./installnewfirefox.sh

---

### Post by aysiu on 2006-05-12
[QUOTE=Clay85]
```
enzo@reboot:~$ cd Desktop
enzo@reboot:~/Desktop$ chmod +x installnewfirefox.sh
chmod: cannot access `installnewfirefox.sh': No such file or directory
enzo@reboot:~/Desktop$

```[/quote] When you're at this part, can you do ```
ls
``` the way you did the first time around to see what's in the Desktop folder?

The first time, I think some kind of weird hidden character may have snuck into the script itself (after #!/bin/sh). The second time, I'm not 100% sure you downloaded it to your desktop.

In other words, the first time, it was looking for a directory that the script was specifying.
The second time, it was looking for the script itself.

---

### Post by Clay85 on 2006-05-12
```

enzo@reboot:~$ cd Desktop
enzo@reboot:~/Desktop$ chmod +x installnewfirefox.sh
enzo@reboot:~/Desktop$ ./installnewfirefox.sh
bash: ./installnewfirefox.sh: /bin/sh^M: bad interpreter: No such file or directory
enzo@reboot:~/Desktop$ ls
firefox-1.5.0.3.tar.gz  installnewfirefox.sh  removenewfirefox.sh
enzo@reboot:~/Desktop$
```

Now I'm back where I started. Is there a different script I can try?

---

### Post by Clay85 on 2006-05-12
ahh you were right. Some character had gotten in there somehow. It's in the original file. I opened Gedit with F2 and pasted my text in there, backspaced after the /sh at the start of the script, then hit enter. Then I did those two commands and it's downloading now. :)

---

### Post by aysiu on 2006-05-12
[QUOTE=Clay85]```

enzo@reboot:~$ cd Desktop
enzo@reboot:~/Desktop$ chmod +x installnewfirefox.sh
enzo@reboot:~/Desktop$ ./installnewfirefox.sh
bash: ./installnewfirefox.sh: /bin/sh^M: bad interpreter: No such file or directory
enzo@reboot:~/Desktop$ ls
firefox-1.5.0.3.tar.gz  installnewfirefox.sh  removenewfirefox.sh
enzo@reboot:~/Desktop$
```

Now I'm back where I started. Is there a different script I can try?[/QUOTE] There's Automatix, but that will install more than just Firefox, and it'll change your sources.list.

You could try ```
nano installnewfirefox.sh
``` Delete the first line and then type in ```
#!/bin/sh
``` That way the ^M probably won't be in there.

I'm going to have to work on fixing this script. If you can wait a few hours, I can probably get it just right again.

---

### Post by aysiu on 2006-05-12
[QUOTE=Clay85]ahh you were right. Some character had gotten in there somehow. It's in the original file. I opened Gedit with F2 and pasted my text in there, backspaced after the /sh at the start of the script, then hit enter. Then I did those two commands and it's downloading now. :)[/QUOTE] Sorry. The text got corrupted somehow because I edited it in Windows using Wordpad (during my lunch break at work), and I think some weird formatting crept in. I'll have to edit it again with Ubuntu when I get home.

---

### Post by Clay85 on 2006-05-12
Well the terminal downloaded and unzipped the file.
```
100%[====================================>] 8,453,871    206.23K/s    ETA 00:00

16:19:50 (203.46 KB/s) - `firefox-1.5.0.3.tar.gz' saved [8453871/8453871]



Unzipping the .tar.gz file

```
...lots of files being unzipped...
```

Removing the unzipped .tar.gz

Linking plugins

enzo@reboot:~/Desktop$ firefox
plugin_get_value 1
plugin_get_value 2
*** loading the extensions datasource
*** loading the extensions datasource
enzo@reboot:~/Desktop$

```

But firefox is still 1.08

I think I give up today. My brain is melting. I'll put this post in my bookmarks and check it later. 
Thanks for your help, I was **so** up the creek without a paddle. :) Now I have a paddle, but it's a really tough creek!

---

### Post by aysiu on 2006-05-12
Yeah, give me a few hours to work out the kinks, test it a bit. I'll post back here when the script is good. Thanks for your patience. I'll never edit the script in Windows again!

---

### Post by aysiu on 2006-05-12
Okay. The script should be good now. I tested it out on a live Hoary and it worked.

The important thing to do is clear your Firefox cache, though, before re-downloading the script. If you don't clear you cache, when you "download" the script, Firefox will just give you the same script you downloaded before. It won't download the script from the Psychocats server.

Can you also check--since the script *appeared* to work--/usr/bin? Right-click on the *firefox* file and select *properties*. See if it points to /opt/firefox/firefox or not.

---

### Post by aysiu on 2006-05-12
Okay. I've tried the script on Hoary and Dapper. I'm 100% it works in its current form. Thanks for catching that weird character glitch. Please try the script again if you have the patience for it.

---

### Post by Clay85 on 2006-05-15
Location: /opt/firefox

Well, that's not right. :(
To clear the firefox cache I go to Edit, Preferences, Privacy, Cache and hit the Clear button?

---

### Post by Clay85 on 2006-05-15
It worked. Thanks for your help. :D

---

