---
title: "Can i use terminal to email/surf the web?"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by wannaBeHacker on 2007-01-04
Hey guys,

I'm trying to find out if i can surf the web or check email, if so can you please tell me how, and/or link me too.

Thanks

-two time poopware

---

### Post by oyvindaa on 2007-01-04
There are some terminal-based e-mail clients, one of them is called mutt.

```
sudo apt-get install mutt
```

There are also some other packages, like 

```
muttprint - Pretty printing of mails
muttprint-manual - Manual for muttprint
muttprofile - a utility to choose profiles in Mutt
```

To browse the web you can use w3m.

Just type in the terminal:

```
w3m www.ubuntu.com
```

---

### Post by darrenm on 2007-01-04
you may also like fetchmail. It gets mail from a remote server and drops it your queue.

edit /etc/default/fetchmail and change daemon to yes

edit /etc/fetchmailrc and put the following info in:

```
poll remote.pop3.server with protocol pop3
  user your.remote.username password your.remote.password is your.local.user
```

then restart fetchmail /etc/init.d/fetchmail restart

---

### Post by scrooge_74 on 2007-01-04
w3m is a very interestinh way to surf the net, and I find it to be a very good program, I just use it to have some fun.

Haven't use mutt since I am to hook into thunderbird

---

### Post by wannaBeHacker on 2007-01-04
thanks guys,

how do i leave a webpage after i enter it, i am stuck, like what do u push or enter that is equvilant to hitting the X in winodws

---

### Post by encompass on 2007-01-04
read the manuals only about how it all works... but trust me... it is one of the best ways to surf the net when everything else breaks... did you know you can chat too?

---

### Post by RajivNair on 2007-01-04
you can also try "lynx"

  sudo apt-get install lynx

---

### Post by RajivNair on 2007-01-04
you can also try "lynx"

  sudo apt-get install lynx

To quit w3m,just press the "Q" button.

---

### Post by scrooge_74 on 2007-01-04
> **RajivNair said:**
> you can also try "lynx"

  sudo apt-get install lynx

To quit w3m,just press the "Q" button.

I have use w3m a couple of times, but never actually try to post to the forums using it LOL

i think I just did

---

### Post by wannaBeHacker on 2007-01-04
btw just to let you guys know i am trying to become completely gui independent

---

### Post by darrenm on 2007-01-04
Really not that difficult to do. Everything works so much quicker too. :)

---

### Post by mcduck on 2007-01-04
I recommend links2 instead of lynx/w3c..

---

### Post by Sukarn on 2007-01-04
> **mcduck said:**
> I recommend links2 instead of lynx/w3c..
Its w3m, not w3c

---

### Post by bapoumba on 2007-01-04
> **wannaBeHacker said:**
> btw just to let you guys know i am trying to become completely gui independent
Well, then try [CenterICQ]("http://centericq.de/docs/readme.php") for jabber client (among other things) and [irssi]("http://www.irssi.org/") for IRC client ;)

---

### Post by mcduck on 2007-01-04
> **Sukarn said:**
> Its w3m, not w3c

That's true. I've spent way too much time reading w3c :)

---

### Post by andrew.46 on 2007-08-15
Hi,

 CLI is certainly the way to go:

> **wannaBeHacker said:**
> Hey guys, I'm trying to find out if i can surf the web or check email, if so can you please tell me how, and/or link me too.Thanks-two time poopware

I see others have advised lynx, links etc. If you are keen on mutt you could do worse than try this:

[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

          Andrew

---

### Post by nanotube on 2007-08-16
for web, i highly recommend the 'elinks' browser (package elinks available in the official repos)

for email, i recommend pine (not in the repos due to some licensing nitpicks, but still good stuff) [http://www.washington.edu/pine/](http://www.washington.edu/pine/)

---

### Post by Paul133 on 2007-08-16
I second elinks and irssi. Of course, you already have nano. I know I had a CLI AIM client, but I can;t remember the name. It might have been irssi.

---

### Post by nanotube on 2007-08-17
> **Paul133 said:**
>  I know I had a CLI AIM client, but I can;t remember the name. It might have been irssi.

maybe you're thinking of "naim"?

---

### Post by st33med on 2007-08-17
Well, that will be useful if I ever screw something up and have to go on the web from the terminal.

---

### Post by RomeReactor on 2007-08-17
[Here]("http://ubuntuforums.org/showpost.php?p=3069480&postcount=10") are some other things to do with the command line.

---

### Post by nanotube on 2007-08-17
> **RomeReactor said:**
> [Here]("http://ubuntuforums.org/showpost.php?p=3069480&postcount=10") are some other things to do with the command line.

nice post! :popcorn: ;) i think that deserves to be extended and put it's own wiki page somewhere on the ubuntu wiki.

p.s. didn't know about zgv... gotta give that a try :)

p.p.s.: checked out zgv: it rocks out! :)

---

### Post by hyper_ch on 2007-08-17
well, and for torrents you could use BitTorrent or ctorrent as terminal torrent clients ;)

---

