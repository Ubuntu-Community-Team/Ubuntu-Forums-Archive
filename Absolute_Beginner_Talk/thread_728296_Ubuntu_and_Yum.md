---
title: "Ubuntu and Yum"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by CraigWatson on 2008-03-18
I apologise if this is in the wrong section - the sheer number of categories here are quite vast!

The question: can I setup Yum on an Ubuntu install and have it use the relevant Ubuntu repo's?

Reason: I'm a Fedora user (details on the rigs are in my signature), but I'm installing Ubuntu on my brother's laptop as my brother - unlike me - isn't technically knowledgeable and Fedora with it's Red Hat pedigree is more suited to server environments Ubuntu has quite a good desktop reputation in Linux arenas (no Ubuntu PR please, I'm quite happy with Fedora :p).

To make it easier to give support to my brother, I'd rather he have access to the commands that I'm familiar with rather than having to learn the in's and out's of a new program purely to provide support.

Cheers for any helpful answers (NB: an answer of "just use apt-get" is not considered helpful ;))

Craig

---

### Post by ExpatPaul on 2008-03-18
I would doubt it. As I understand it, the Ubuntu repositories use Debian packages, for which you need Apt-get

---

### Post by Arthur Archnix on 2008-03-18
Fedora 8 is great as a desktop. I used it and absolutely loved it. Sorry if you consider it unhelpful, but use Fedora or use Apt with Ubuntu.

---

### Post by llamakc on 2008-03-18
Create aliases for the commands.

---

### Post by handydan918 on 2008-03-18
> **llamakc said:**
> Create aliases for the commands.

Heh...
And when you're done you'll know more than most about apt-get!!

:rolleyes:

---

### Post by CraigWatson on 2008-03-18
Thanks for the replies:

[quote="Arthur Archnix"]Fedora 8 is great as a desktop. I used it and absolutely loved it. Sorry if you consider it unhelpful, but use Fedora or use Apt with Ubuntu.[/quote]

Same here, I use Fedora 8 as my main OS on both my laptop and desktop machines (dipping into XP when I need to use Fireworks CS3 which doesn't play well in Wine, and Vista when I need to provide support for people using it) but I figured it's a bit overkill for someone who hasn't got that much technical knowledge.

[quote="ExpatPaul"]I would doubt it. As I understand it, the Ubuntu repositories use Debian packages, for which you need Apt-get[/quote]

True. I may just use an extremely cut-down installation of Fedora with none of the server aspects. It's too much of a pain to have to remember what distro he's using and remember that he needs .deb's instead of .rpm's and to use **apt-get install xyz** rather than **yum install xyz** - especially when I'm using rpm's and yum on a near-daily basis!

---

### Post by kellemes on 2008-03-18
You can install the red hat package manager and yum, this way you can use RPM-repositories.
This will bypass the debian packaging system, trust me.. this is not what you want.
When in need of RPM's use [alien]("https://help.ubuntu.com/community/RPM/AlienHowto").

I'm afraid you need to dive into dpkg/apt-get/aptitude.. or find another RPM based distribution being able to use yum.

---

### Post by bodhi.zazen on 2008-03-18
+1 with fedora being a fine distro. If you are familiar with Feodra and less so with Ubuntu and you are wanting to support your brother, easiest if he learns Fedora.

The other option is for you to learn Ubuntu. 80-85 % of what you know of Fedora transfers to Ubuntu, so choice is up to you.

But, no, Ubuntu does not use yum. Try synaptic or Add/Remove those are very new user friendly, IMO at least.

---

### Post by handydan918 on 2008-03-18
I know this goes the wrong way, but apt is used with rpm's on pclos...
Interesting as a proof-of-concept, at least.

---

### Post by Duck2006 on 2008-03-18
I run fedora (3 and 4) for a wile and it was a good linux. In ubuntu as bodhi.zazen posted may be the easies way to go.

---

### Post by Abandon on 2008-03-18
Back in 2003  I used Red Hat 8 and Red Hat 9. In those day's I learned I could use apt-get (provided by Fedora website). Mind you..Fedora was not yet a distribution. The point is...oh well....memories :)

---

