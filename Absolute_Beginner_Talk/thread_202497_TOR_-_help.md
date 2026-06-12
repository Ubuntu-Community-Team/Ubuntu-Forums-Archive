---
title: "TOR - help?"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by Iesos on 2006-06-23
Hi, I'm having trouble with TOR. Just installed it, and got it working (sort of) for a little while. I had the following problem before:

If a ran a program like:
$ torify gnome-btdownload
and then started one just like it. Then only one of them seemed to work. What have I setup wrong to get problem?

If I run:
$ torify traceroute [www.piratpartiet.se](www.piratpartiet.se)
(or some other page) then the trace would get very long and wierd right? But It doesn't. So I think my TOR setup is wrong.

Someone on this forum (can't the thread again) said that one can restart the TOR-deamon with:
$ killall tor
$ $ sudo /etc/init.d/tor start
But then I get the following error:
```
 * Starting tor daemon (tor)... Jun 23 20:11:46.800 [notice] Tor v0.1.0.16. This is experimental software. Do not rely on it for strong anonymity.
Jun 23 20:11:46.854 [notice] options_validate(): Your ContactInfo config option is not set. Please consider setting it, so we can contact you if your server is misconfigured or something else goes wrong.
Jun 23 20:11:46.854 [warn] resolve_my_address(): Address 'totoro' resolves to private IP '127.0.0.1'. Tor servers that use the default DirServers must have public IP addresses.
Jun 23 20:11:46.854 [err] tor_init(): Reading config failed--see warnings above. For usage, try -h.
                                                                                                                                  [fail]

```
And I don't have a clue what anything of that means...

So, any TOR user that can help me?

---

### Post by Iesos on 2006-06-23
Ok, solved the problem...
All I need an answer to now is when can I use torify and when does it not have any effect?

---

### Post by airzer0 on 2006-06-24
sudo apt-get privoxy 
configure that by sudo gedit /etc/privoxy/config
then uncomment(place a #)
in front of jar jar line 
and place (#) in front of logfile logfile
then configure your web browser i use firefox 1.5 so go to tools option and click extensions and search for torbutton and install 
there you go

---

### Post by airzer0 on 2006-06-24
sudo apt-get install privoxy

---

### Post by j-strap2 on 2006-06-24
'torify' is just a shell script that calls tsocks. tsocks is used for applications that can't be configured to talk to a proxy themselves - tsocks catches the network calls and passes them to a specified proxy. In this case, torify uses tsocks to route an application's traffic through Tor. 

However, torify in some Tor packages is broken and does not work correctly.

---

### Post by heman on 2006-06-25
I'm very new to Ubunutu, but the privoxy package doesn't show up when I apt-cache search in Dapper.  Am I doing something wrong?

---

### Post by DCM36 on 2006-06-26
Do you have the extra repositories enabled? Go [here]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories") for the command-line way or [here]("http://ubuntuguide.org/wiki/Dapper#How_to_apt-get_the_easy_way_.28Synaptic.29") for the GUI way. This should enable you to download privoxy with apt-get. 

Also, if you haven't taken a look at [this]("http://tor.eff.org/docs/tor-doc-unix.html.en"), it helps a lot with setting up Tor and Privoxy.

---

