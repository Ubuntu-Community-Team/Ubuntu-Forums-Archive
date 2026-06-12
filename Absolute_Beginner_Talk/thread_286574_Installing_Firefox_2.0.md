---
title: "Installing Firefox 2.0"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by bobmorris on 2006-10-27
Ok, I've downloaded Firefox2.0.gz.tar.

I can't figure out how to install it...

The archive manage asks where to unpack it to, I tried usr/lib/firefox, it said I didn't have rights.

What am I missing?

---

### Post by KnoTHavok on 2006-10-27
> **bobmorris said:**
> Ok, I've downloaded Firefox2.0.gz.tar.

I can't figure out how to install it...

The archive manage asks where to unpack it to, I tried usr/lib/firefox, it said I didn't have rights.

What am I missing?
I believe this is what you should do.
someone please correct me if I'm wrong.
```

sudo tar -xzvf firefox2.0.tar.gz /usr/lib/firefox

```
Hope that helps

---

### Post by AdonisV on 2006-10-27
I downloaded it too and can't make it work. why won't anyone just post the whole procedure? this is so annoying in forums coz when you ask someone how to bake a cake people will just say you'll need flour but not teach the whole step.. :-k

---

### Post by bobmorris on 2006-10-27
Still not working, I get

bob@Bob-Ubuntu-desktop:~/transit$ sudo tar -xzvf  firefox-2.0.tar.gz /usr/lib/firefox
tar: /usr/lib/firefox: Not found in archive
tar: Error exit delayed from previous errors

Ideas?

---

### Post by bobmorris on 2006-10-28
I agree. 

I am a geek. Installing FireFox just shouldn't be this complicated...

---

### Post by slimdog360 on 2006-10-28
```
sudo tar xvfz firefox2.0.tar.gz /usr/lib/firefox
```. very close though you just had the letters mixed up. I think KnoTHavok meant -zxvf

[http://simplythebest.net/info/unix/untar.html]("http://simplythebest.net/info/unix/untar.html")
[http://www.freebsddiary.org/untar.php]("http://www.freebsddiary.org/untar.php")

I havent tried to install it but Im guessing there is a .bin file in the folder to where you untar it. You will just have to change the links in your icons, menus etc to that link. example, if you have a firefox icon in your panel, right click on it and go to properties. change the link to ```
/usr/lib/firefox/firefox
```. But I couldnt be sure if that would work

---

### Post by Matt Yun on 2006-10-28
1. tar xvzf firefox-2.0.tar.gz

This unpacks a 'firefox' directory

2. sudo mv firefox /opt/firefox-2.0

/opt is where third-party software packages go (ie. not from your distro's package management scheme).  You can also use /usr/local/opt

3. sudo ln -s /opt/firefox-2.0/firefox /usr/local/bin/firefox

It's better to create the symlink in /usr/local/bin rather than /usr/bin because you are installing this software independent of Ubuntu's package management.

4. Create a menu item or a shortcut for 'Firefox2'; application to execute is /opt/firefox-2.0/firefox

So far, I'm using it with no problems.

---

### Post by HareBall on 2006-10-28
> **slimdog360 said:**
> ```
sudo tar xvfz firefox2.0.tar.gz /usr/lib/firefox
```. very close though you just had the letters mixed up. I think KnoTHavok meant -zxvf

[http://simplythebest.net/info/unix/untar.html]("http://simplythebest.net/info/unix/untar.html")
[http://www.freebsddiary.org/untar.php]("http://www.freebsddiary.org/untar.php")

I havent tried to install it but Im guessing there is a .bin file in the folder to where you untar it. You will just have to change the links in your icons, menus etc to that link. example, if you have a firefox icon in your panel, right click on it and go to properties. change the link to ```
/usr/lib/firefox/firefox
```. But I couldnt be sure if that would work
I tried this and it didn't work for me. Here is what I got when I tried:
larry@larry-desktop:~$ sudo tar xvfz firefox2.0.tar.gz /usr/lib/firefox
tar: firefox2.0.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: /usr/lib/firefox: Not found in archive
tar: Error exit delayed from previous errors
What next?

---

### Post by slimdog360 on 2006-10-28
sorry that should have been a capital F on firefox there. Mat yun's way should work though.

---

### Post by glotz on 2006-10-28
> **AdonisV said:**
> I downloaded it too and can't make it work. why won't anyone just post the whole procedure? this is so annoying in forums coz when you ask someone how to bake a cake people will just say you'll need flour but not teach the whole step.. :-k

Are we being a little helpless here? **Search** the wiki and the forums for 'firefox' or for 'firefox 2.0'. You will find the general 'nextVersion' wikipage and multiple howto threads in these very forums. That's what you guys are supposed to do always prior to posting. It helps also keeping this place from becoming a mess.

---

### Post by A2A on 2006-10-28
Folks, this *might* help.
[http://everythingelse.wordpress.com/2006/07/15/howto-install-firefox-20-bon-echo-in-ubuntu/](http://everythingelse.wordpress.com/2006/07/15/howto-install-firefox-20-bon-echo-in-ubuntu/)

Regards,

---

### Post by woedend on 2006-10-28
or, to not even use the command line, make a folder in your home directory, lets say call it .firefox2(to make it hidden and unobstructive).  extract contents to said folder, and double click(make launcher to) the file "firefox"(a shell script).
hth

---

### Post by towsonu2003 on 2006-10-28
this should work: [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

note: I recently changed references to Fx 1.5 in that page to Fx2, so be careful while typing the commands and tell us how it went.

---

### Post by glotz on 2006-10-28
Nice job bringing the wiki up to date. On the wiki page it says that the mozilla build is faster. Has somebody actually got some numbers to prove it or is it just FUD?

---

### Post by bobmorris on 2006-10-28
I searched multiple sites, found info, tried them and they didn't work. Then found a link that said Easy Eft has FireFox 2.0 installed, so I just upgraded to that.

Admittedly, a convoluted way of doing it!

---

### Post by chickengirl on 2006-10-28
> **woedend said:**
> or, to not even use the command line, make a folder in your home directory, lets say call it .firefox2(to make it hidden and unobstructive).  extract contents to said folder, and double click(make launcher to) the file "firefox"(a shell script).
hth

That's pretty much how I do it except I do it from the command line and I don't make the folder hidden. (Ooooh! Living on the edge! :twisted: )

---

### Post by towsonu2003 on 2006-10-28
> **towsonu2003 said:**
> this should work: [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

note: I recently changed references to Fx 1.5 in that page to Fx2, so be careful while typing the commands and tell us how it went.

> **glotz said:**
> Nice job bringing the wiki up to date. On the wiki page it says that the mozilla build is faster. Has somebody actually got some numbers to prove it or is it just FUD?

It was a known bug for Dapper's firefox (which was pango enabled) so it's not fud. at worst, it not-up-to-date info.

---

### Post by esaym on 2006-10-28
hehe: [http://getswiftfox.com/installer.htm](http://getswiftfox.com/installer.htm)


if you want the desktop icon you will have to copy it from the default install location of /usr/share/applications/swiftfox.desktop and copy it over to /home/user/desktop


:-D

---

