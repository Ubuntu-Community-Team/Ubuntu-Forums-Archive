---
title: "[SOLVED] Tor -"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by al.adab on 2008-03-20
hello,

I installed TOR (sudo apt-install tor) and can't find it anywhere on the menu.I then checked [https://help.ubuntu.com/community/TOR#head-ccba4382b2ec0a1f923f783fdb6b0b9a1d57df3c](https://help.ubuntu.com/community/TOR#head-ccba4382b2ec0a1f923f783fdb6b0b9a1d57df3c) and found out I should've downloaded the repositories, except that this page doesn't mention Gutsy. 

question 1) how can I download the reps for Gutsy?
question 2) what does "This can be done by using nano, gedit or another text editor of your choosing. Before moving on be sure to get the PGP keys for the new repositories and do an update / upgrade using the following commands" (found at the paragraph "Installing TOR", same page) mean? Can you tell me exactly what I should type in terminal? 

Thanks for your help.

---

### Post by fedex1993 on 2008-03-20
well tor is not going to be on the menu it runs at startup and you can run it in a terminal
edit: One of my friends has a tutorial on tor hold on getting link

---

### Post by jordanmthomas on 2008-03-20
```
apt-get install tor
```
Gets files from repositories.  I'm guessing tor just wasn't in Feisty's or Edgy's repositories, which is why you would have to type in the extra commands to grab PGP keys and add new repos.  Tor isn't something that has a GUI, so it won't show up in your menus.
```
ps -A | grep tor
```
will show yo u if it's running.

You will also want to install privoxy.
The instructions on the page regarding privoxy look like they should work fine.
If you don't know how to use nano, replace **sudo nano** with **gksudo gedit**

After you've installed tor and privoxy (and have started them) you will need to configure any program you want to use tor to use a proxy server.  

For example, setting up firefox to use tor:  
Go to Edit -- Preferences -- Advanced and click on "Settings" for the connection and configure it like in my screenshot.

There's also a firefox extension to turn it on and off.  Just look up tor firefox extension on google and you'll find it.

Good luck and happy anonymous browsing.

---

### Post by al.adab on 2008-03-20
thanks so much jordanmthomas  

...I'm still a bit confused...sorry! Could you please clarify the following: 

*Gets files from repositories.* > does this mean I type in terminal 

[I]deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) feisty main
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) feisty main[/I] 

each of them preceded by...*sudo*  and I ignore the *PGP key command* ?

*...and configure it like in my screenshot* sorry, where?

Thanks again for your patience.

---

### Post by jordanmthomas on 2008-03-20
You already have tor installed, so ignore the part about adding those lines and ignore the PGP commands.  Skip down to the part about privoxy because the stuff about tor you've already taken care of.

You don't have to add those lines because tor is already in gutsy's repositories.  It was not there for edgy or feisty, so you had to add them.

Woops, forgot the screenshot.  Sorry about that.

Also, I'm sorry about the delayed response.  I had to go to class.

---

### Post by al.adab on 2008-03-20
Many thanks jordanmthomas for your help. I really appreciate this. I've followed your directions and those at [https://help.ubuntu.com/community/TOR#head-ccba4382b2ec0a1f923f783fdb6b0b9a1d57df3c](https://help.ubuntu.com/community/TOR#head-ccba4382b2ec0a1f923f783fdb6b0b9a1d57df3c). 

The first part seems to work, doesn't it?

~$ sudo /etc/init.d/tor start
[sudo] password for daniel:
Raising maximum number of filedescriptors (ulimit -n) to 8192.
Starting tor daemon: tor...
done.
daniel@al-Adab:~$ sudo /etc/init.d/privoxy start
Starting filtering proxy server: privoxy.
daniel@al-Adab:~$ netstat -a | grep 9050
tcp        0      0 localhost:9050          *:*                     LISTEN    

I've just tried this out hoping it'd confirm that TOR is running and I got the following: 
 
daniel@al-Adab:~$ ps -A | grep tor
 5371 ?        00:00:00 hald-addon-stor
 5453 ?        00:00:00 tor

Does this look ok? For some reason, if I type TOR in terminal I get the following: 

daniel@al-Adab:~$ tor
Mar 21 00:06:07.658 [notice] Tor v0.1.2.17. This is experimental software. Do not rely on it for strong anonymity.
Mar 21 00:06:07.661 [notice] Initialized libevent version 1.3b using method epoll. Good.
Mar 21 00:06:07.661 [notice] Opening Socks listener on 127.0.0.1:9050
Mar 21 00:06:07.661 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Mar 21 00:06:07.661 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
Mar 21 00:06:07.661 [err] Reading config failed--see warnings above.

Does this mean that something went wrong? Also does TOR start automatically at re-boot (and all I have to do it to enable it on firefox> the add-on is installed (green=on/red=off) and I modified the firefox proxies configuration as you suggested. 

Thanks again.

---

### Post by jordanmthomas on 2008-03-20
Once you've done
```
sudo /etc/init.d/tor start
sudo /etc/init.d/privoxy start
```
tor is running and ready.  Also, it (and privoxy) should automatically start when you reboot, and be usable by turning it on / off in firefox or whatever program you're using.

You don't need to run tor on its own by just typing tor.  Note when you did that it mentioned that it is already running?

You can see if tor is working right by disabling it in firefox and going to 
[http://whatismyip.com](http://whatismyip.com)
Note your IP.
Then, enable tor and reload the page.  If your IP doesn't change, then something is wrong with your configuration.

---

### Post by al.adab on 2008-03-20
Fantastic. It works. A very last question (hoping I'm not turning into a bore): now that I've done the configuration on Firefox, shall I also do it on Evolution mail? Just in case...thanks again.

---

### Post by jordanmthomas on 2008-03-20
I don't have evolution installed, so I can't say exactly what you need to do.
Generally, you just tell programs to use your proxy of localhost:9050 or localhost:8118

Keep in mind that you **may** not want to send personal data like e-mails over the tor network.  I believe there's been reports of people harvesting data by hosting tor nodes and capturing information coming through it.  Unless you have a real need to use tor for your e-mail, I would personally not do it.  I'd at least ensure the data is encrypted with SSL or something similar.

---

