---
title: "Anonymous Surfing &amp; SwiftFox"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-10-17
Does anyone have experience with setting up SwiftFox for anonymous surfing?

---

### Post by aktiwers on 2006-10-17
What do you mean with Anonymous surfing?
Do you mean like installing the extention Tor?

Search for it, it sounds like what you are looking for.

---

### Post by Arevos on 2006-10-17
I have experience with setting up Firefox for anonymous surfing, and as Swiftfox is just an optimised build of Firefox, the techniques should be the same.

First, I used [this guide](http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian) to install the latest version of Tor. As per the guide's instructions, I added these two repositories to /etc/apt/sources.list:

```
deb http://mirror.noreply.org/pub/tor dapper main
deb-src http://mirror.noreply.org/pub/tor dapper main
```

I then opened a terminal and added the key to verify these packages to apt:
```
$ gpg --keyserver subkeys.pgp.net --recv 94C09C7F
$ gpg --fingerprint 94C09C7F
$ gpg --export 94C09C7F | sudo apt-key add -
```

I installed Tor and Privoxy with apt-get:
```
$ sudo apt-get update
$ sudo apt-get install tor privoxy
```

Next, I followed [this guide](http://tor.eff.org/docs/tor-doc-unix.html.en) in order to configure Privoxy and to check Tor was working properly. As per the guide, I added this line to /etc/privoxy/config:

```
forward-socks4a / localhost:9050 .
```

And commented out these three lines:

```
logfile logfile
jarfile jarfile
debug 1
```(Remember to restart Tor and Privoxy for the changes to take hold! "sudo /etc/init.d/tor restart" and "sudo /etc/init.d/privoxy restart")

To integrate Tor with Firefox, I use [TorButton](https://addons.mozilla.org/firefox/2275/). I also used [Stealther](https://addons.mozilla.org/firefox/1306/) to provide some measure of local privacy.

---

### Post by Mark_in_Hollywood on 2006-10-19
I did:

mark@Lexington:~$ sudo  gpg --keyserver subkeys.pgp.net --recv 94C09C7F
gpg: WARNING: unsafe ownership on configuration file `/home/mark/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
mark@Lexington:~$

What happened?

---

### Post by Mark_in_Hollywood on 2006-10-21
SUCCESS!!

Tor/Privoxy is up and running.

---

