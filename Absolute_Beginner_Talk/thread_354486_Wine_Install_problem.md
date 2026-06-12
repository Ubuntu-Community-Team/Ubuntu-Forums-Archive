---
title: "Wine Install problem"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by sarum on 2007-02-06
Hi, I'm trying to get Wine by following these instructios:-
'to run the latest version you'll need to edit /etc/apt/sources.list......................'
'add the line .....sudo nano /etc/apt/sources.list..........save (Ctrl-O)
'then..........sudo apt-get update.........

But I then get this:-
~$ sudo apt-get update
E: Malformed line 37 in source list /etc/apt/sources.list (dist parse)

Has anyone any suggestions as to what I can do to correct it.
Thanks in anticipation Sarum.

---

### Post by bodhi.zazen on 2007-02-06
You must have a type in /etc/apt/sources.list

If you post the file we can look it over ...

If you want to post the "Malformed line" :

```
cat -n /etc/apt/sources.list | grep 37
```

---

### Post by jonnymccullagh on 2007-02-06
I would agree with bodhi, there must be a typing error in your sources.list

I am lazy and I often download and install Automatix which will create a new sources.list for you and includes Wine. You can download the deb installer for edgy (i386) here:
[http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/automatix2_1.1-2.14-6.10edgy_i386.deb]("http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/automatix2_1.1-2.14-6.10edgy_i386.deb")

Another option would be to create a sources.list using the tool here:
[http://www.ubuntu-nl.org/source-o-matic/]("http://www.ubuntu-nl.org/source-o-matic/")
and then you could just paste the list into your text editor.

The other option (which may be a bit late for you) is to add repositories using a GUI tool such as Synaptic or Adept rather than editing the sources.list file directly.

Hope this helps,
jonny

---

### Post by sarum on 2007-02-06
Thanks for your reply. I get the following:-

 cat -n /etc/apt/sources.list | grep 37
    37  deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary
So you are right a typo error as there should be a '/' after binary.
However, now when I type 'nano /etc/apt scources.list'   I get a blank nano page headed:-

File: /etc/apt/scources.list               Modified

I think I shall try jonny's suggestions with auto-matix or -o-matic. I'll post again if I'm still having troubles; so please accept my thanks now for your help.Both of you.
Cheers Sarum

---

### Post by bodhi.zazen on 2007-02-06
> **sarum said:**
> Thanks for your reply. I get the following:-

 cat -n /etc/apt/sources.list | grep 37
    37  deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary
So you are right a typo error as there should be a '/' after binary.

8)

> However, now when I type 'nano /etc/apt scources.list'   I get a blank nano page headed:-

File: /etc/apt/scources.list               Modified

LOL try:

```
sudo nano -B /etc/apt/sources.list
```

FYI You have a typo " /etc/apt/**scources**.list

The -B option creates a backup **/etc/apt/sources.list~** :D

You can also try:

```
gksudo gedit /etc/apt/sources.list
```

> I think I shall try jonny's suggestions with auto-matix or -o-matic. I'll post again if I'm still having troubles; so please accept my thanks now for your help.Both of you.
Cheers Sarum

Well, in the end the best method is in fact the one that works :p

Let us know if we can be of assistance ;)

---

### Post by sarum on 2007-02-06
Thanks again for your help. I'm not sure how I did it, but after a warning that all my packages needed reinstalling. I started again with 'nano /etc...............and went on to 'install wine.............And it has installed.
What a site this is thanks to those who help.
Cheers Sarum.

---

