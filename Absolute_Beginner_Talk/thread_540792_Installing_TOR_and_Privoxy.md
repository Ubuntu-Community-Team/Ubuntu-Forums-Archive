---
title: "Installing TOR and Privoxy"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-09-02
Hi,  I went into the Repositories and download / installed Tor and Privoxy.
but there are extra instructions that I don't understand.

Here is a link to the instructions that I am trying to follow.
[https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

I don't understand this part.

**You will need to add the following repositories to your /etc/apt/sources.list file:**

**Ubuntu 7.04 (Feisty Fawn):**
```
deb http://mirror.noreply.org/pub/tor feisty main
deb-src http://mirror.noreply.org/pub/tor feisty main
```

This can be done by using nano, gedit or another text editor of your choosing. Before moving on be sure
to get the PGP keys for the new repositories and do an update / upgrade using the following commands:

```

$ gpg --keyserver subkeys.pgp.net --recv 94C09C7F
$ gpg --fingerprint 94C09C7F
$ gpg --export 94C09C7F | sudo apt-key add -
$ sudo apt-get update
$ sudo apt-get upgrade

```

I think I did it completely wrong.
I'm thinking I should have done the above before
I installed Tor and privoxy,
I didn't find the Directions til after the fact.
Should I uninstall both program before I try to do the above?
I really need some help on this.....

Thank you.

---

### Post by SOULRiDER on 2007-09-02
To install them you will have to add those 2 lines to your repo list. To do so you have to add them to a file which happens to be /etc/apt/sources.list. To edit the file press alt + f2 and type

```
gksu gedit /etc/apt/sources.list
``` type in your password and add ```
deb http://mirror.noreply.org/pub/tor feisty main
deb-src http://mirror.noreply.org/pub/tor feisty main
``` at the bottom.

Once youre done, in a console copy and paste these commands:
```
$ gpg --keyserver subkeys.pgp.net --recv 94C09C7F
gpg --fingerprint 94C09C7F
gpg --export 94C09C7F | sudo apt-key add -
sudo apt-get update
sudo apt-get upgrade
```

Once you dot hat finally type
```
sudo aptitude install tor privoxy
```

Good luck!

---

### Post by Orbital75 on 2007-09-02
Thank you......  I wasn't sure what the source list stuff was.

I have already install Tor &  Privoxy should I uninstall them
first or is it ok to go ahead and follow your directions.

One more thing, Will Tor &  Privoxy start up with Ubuntu
or will I need to start them manually. 
Will there be icons in my Applications tray?

Thanks again.   :KS

---

### Post by SOULRiDER on 2007-09-02
Well, if you follow my directions they will get reinstalled (maybe a new version). Im not sure about the other questions sice i havnt installed them, just check out the wiki, it seems to cover a lot.

Good luck!

---

### Post by Orbital75 on 2007-10-11
I now have both tor and privoxy installed but no Icons were put any where in my menu.
I'd like to create some launchers for both of them so I can activate them
and use Tor button in firefox. Could someone show me how with the commands
to run them.  I know how to make a launcher but don't know the commands to
run them.  thank you.  :)

---

### Post by Orbital75 on 2007-10-13
No Takers  :)

---

### Post by Countryboy123 on 2007-10-13
Hi, 
I can help a little. I know something about Privoxy. My Ubuntu did not have a Gui for Privoxy. I had to edit a file  in the etc folder. I believe it was: file sytem/ etc/ privoxy /user.action. On the positve side I only use it to bypass specific sites, so their is not a lot of need for editing. Priivoxy has alot of help files on its site I would look there for more details . 

You will need root access to edit your user.action file. I like to use Drag & Drop sudo. Here is a link: [https://help.ubuntu.com/community/RootSudo#head-c863a1b669260ba6af02fa652d7f8fe5e6828042](https://help.ubuntu.com/community/RootSudo#head-c863a1b669260ba6af02fa652d7f8fe5e6828042)

---

