---
title: "How to install programs if I get weeeird errormessages?"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by Tilulii on 2007-09-13
Okay. Total newbie on Ubuntu, like, two days newbie.

So, I downloaded a file, which is a .daa-file. Found out that a program called Poweriso can make it a ISO (hopefully) from here
[http://www.articlealley.com/article_170967_11.html](http://www.articlealley.com/article_170967_11.html)
but I can't seem to get the poweriso thingie to work. As I try to run it (Ipresume I can run programs from the terminal by just typing in their name), it just says
```
bash: poweriso: command not found

```

So not being afraid of doing stupid things that can **** up my computer totally (the way I learned computers in the first place, and actually ****** up our old 8088, in the pre-internet era, never got it fixed either :) I tried something (if you are unsure of what to do, do something):
```

elmo@sinpanssi:~/poweriso$ sudo apt-get install poweriso
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

Now the question is (this is probably not the right thing to do, 'officer, I knew it was wrong, I did it anyway'), what happened?

And what to do next?

And can't seem to find the IRC-channel for these problems. Always logging on to allkinda places, but I'm always alone there.

And can't seem to grasp the Firestarter, but first thinngs first :)

Running Ubuntu 7.04 (Feisty)

Elmo

---

### Post by por100pre1 on 2007-09-13
Is there any other package manager in use? Synaptic, available updates? Close everything else and try again.

---

### Post by Tilulii on 2007-09-13
Actually the errormessage suddenly stopped being there
Somekinda fluke
And even got the poweriso to function! Whooa, my path to being a proper nerd is laid before me! Corrupting the dark side is :)

Cheers

---

### Post by Bothered on 2007-09-13
> **Tilulii said:**
> Now the question is (this is probably not the right thing to do, 'officer, I knew it was wrong, I did it anyway'), what happened?

You probably had another package manager open, such as synaptic.

> **Tilulii said:**
> And can't seem to find the IRC-channel for these problems. Always logging on to allkinda places, but I'm always alone there.

See [here]("https://help.ubuntu.com/community/InternetRelayChat").

> **Tilulii said:**
> And can't seem to grasp the Firestarter, but first thinngs first :)

Documentation can be found [here]("http://www.fs-security.com/docs.php"), although I've found Firestarter reasonably self-explanatory.

---

### Post by Tilulii on 2007-09-14
Well, the firestarter seems easyish. I have troubles to understand about those ports and such, as I needed to open one for Azureus. I know next to nothing about stuff like this, so 'self explanatory' can be a very diffuse term indeed :)

---

### Post by Bothered on 2007-09-14
> **Tilulii said:**
> Well, the firestarter seems easyish. I have troubles to understand about those ports and such, as I needed to open one for Azureus. I know next to nothing about stuff like this, so 'self explanatory' can be a very diffuse term indeed :)

Indeed it can :-) I found it a bit better than manually messing about with iptables though.

For azureus you might want to try:

1. Launch firestarter and select the "policy" tab
2. Right click on the lower panel and select "add rule"
3. From the "name" drop down list select "BitTorrent" and click "Add"
4. Click the "Apply policy" button

---

### Post by Tilulii on 2007-09-17
Jay thanks. That is a good advice, then I do not need to have that very unpleasant port open for 'everyone' :)

Paranoid?

Well Hell yes!

---

