---
title: "Mactel Support from Command Line Wont Install"
date: 2010-05-11
forum: Apple Hardware Users
---

### Post by oscargodson on 2010-05-11
I don't get it... i've been following the instructions for the Mactel team and they say to put this into the terminal:
```
sudo add-apt-repository ppa:mactel-support && apt-get update
```But it always gives me this:
```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 7A6BC20C4FE04DADD10837608DB7F87A2B97B7B8
gpg: requesting key 2B97B7B8 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory
```I really need this because i believe this fixes a lot of driver issues. Im running the latest MacBook Pro (intel i5 / MBP 6th Gen).

I'm having severe driver issues, i think these fixes these, right?
- No sound
- Special buttons like brightness, sound, etc show up on Ubuntu when pushed but nothing actually happens. Same with the Eject button. Shows a status bubble in the top right that it's ejecting, but doesn't do anything.
- The touchpad, as it has no buttons on the Mac, is nearly not useable, but they say it works out of the box...

Also, side question... can you change control to be cmd? Like, swap them to match the Mac's layout?

haven't used Ubuntu since 6.04, so I'm super excited... anyone know how to help?!

---

### Post by linuxopjemac on 2010-05-11
do you have synaptic package manager open at the same time ?

---

### Post by linuxopjemac on 2010-05-11
just add
```
deb http://ppa.launchpad.net/mactel-support/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/mactel-support/ppa/ubuntu lucid main
```

to /etc/apt/sources.list (I suppose you have Lucid, otherwise replace lucid with your Ubuntu version)

```
sudo apt-get update
```

You will have to then get the gpg key, google a bit

---

### Post by oscargodson on 2010-05-11
Thanks, but, I still dont think I get what to do:

I got a gpg key:
```
gpg: /home/oscar/.gnupg/trustdb.gpg: trustdb created
gpg: key  B51AEF85 marked as ultimately trusted
public and secret key created  and signed.

gpg: checking the trustdb
gpg: 3 marginal(s)  needed, 1 complete(s) needed, PGP trust model
gpg: depth: 0  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 1u
pub    2048R/B51AEF85 2010-05-11
      Key fingerprint = C24F E0AD C1E0  9D6F 548F  1395 2F07 79C3 B51A EF85
uid                  Oscar Godson  (Oscar Godson) <[EMAIL="oscargodson@gmail.com"]oscargodson@gmail.com[/EMAIL]>
sub   2048R/0B0D379D 2010-05-11

```

After getting the key I went ahead and did the ```
sudo apt-get update
``` and it went through it, updated it, and said it was done and also gave me this error at the end:
```
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8DB7F87A2B97B7B8
```

Even with the error, I went ahead and tried to the mactel thing again, and same error :(

---

### Post by newbie80 on 2010-05-11
I had the same problem. In my case the problem was that my wireless network was not connected, I had to connect to net via ethernet and then was able to install mactel support. I got the same messages as you posted when I tried first. Sorry if this is not the case with you.

---

### Post by oscargodson on 2010-05-11
Seems to be working now, sweet. It looks like i had topick out the packages manually and install them each separate

---

