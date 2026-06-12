---
title: "Getting error &quot;E: Malformed line 2 in source list..."
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by WallRunner on 2007-02-04
[COLOR=DarkGreen][B]Hello again,

I am getting the error "E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list", and I am stumped, here is what my edgy-universe.list says:

[/B][/COLOR]```
# automatically added by gnome-app-install on 2007-01-25 18:56:49.512529
deb http://archive.ubuntu.com/ubuntu/ edgy
deb http://security.ubuntu.com/ubuntu edgy-security main universe
deb http://archive.ubuntu.com/ubuntu/ edgy-updates universe
```[COLOR=DarkGreen][B]

From,
Chris.
[/B][/COLOR]

---

### Post by taurus on 2007-02-04
Remove that line from your repos.

```
deb http://archive.ubuntu.com/ubuntu/ edgy
```

---

### Post by vloveya08 on 2007-02-04
> **WallRunner said:**
> [COLOR=DarkGreen][B]Hello again,

I am getting the error "E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list", and I am stumped, here is what my edgy-universe.list says:

[/B][/COLOR]```
# automatically added by gnome-app-install on 2007-01-25 18:56:49.512529
deb http://archive.ubuntu.com/ubuntu/ edgy
deb http://security.ubuntu.com/ubuntu edgy-security main universe
deb http://archive.ubuntu.com/ubuntu/ edgy-updates universe
```
[COLOR=DarkGreen][B]

From,
Chris.
[/B][/COLOR]

If you look at the second line of "deb", you need another "/" after "ubuntu" otherwise the URL is incorrect and the computer doesn't know where to look.  Just add it in and save it and you should be good!

---

### Post by WallRunner on 2007-02-04
[COLOR=DarkGreen][B]Thanks for the quick reply, i knew it would be something simple like that :p.

From,
Chris.
[/B][/COLOR]

---

### Post by starNIX on 2007-03-24
[email]bpregont@edgybox:/etc/apt/sources.list[/email].d$ sudo apt-get update

causes the following error:
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-multiverse.list (dist parse)

That file looks like this:
# automatically added by gnome-app-install on 2007-03-09 00:16:44.133781
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates


It looks right to me.  Any ideas?

---

### Post by taurus on 2007-03-24
> **starNIX said:**
> [email]bpregont@edgybox:/etc/apt/sources.list[/email].d$ sudo apt-get update

causes the following error:
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-multiverse.list (dist parse)

That file looks like this:
# automatically added by gnome-app-install on 2007-03-09 00:16:44.133781
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates


It looks right to me.  Any ideas?

Sorry but the second line

```
deb http://archive.ubuntu.com/ubuntu/ edgy
```
is off.  Therefore, you need to remove it.

```
gksudo gedit /etc/apt/sources.list.d/edgy-multiverse.list
```

Then, run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by starNIX on 2007-03-25
A few questions:

1.   What would cause this?

2.   Am I breaking anything else by removing this?

3.   Why is it now complaining about line 4?  

I didnt do anything to this file.  WHy is it suddenly broken?

---

### Post by starNIX on 2007-03-25
OK,  now I commented out EVERYTHING and I still get a complaint about line 2.

---

### Post by taurus on 2007-03-25
Can you post your /etc/apt/sources.list.d/edgy-multiverse.list again?

```
cat /etc/apt/sources.list.d/edgy-multiverse.list
```

---

### Post by retiman on 2007-04-13
This happened to me too.  Some program that you use to edit your sources.list has put sources in both /etc/apt/sources.list and /etc/apt/sources.list.d, so when apt-get reads em, if finds duplicate entries and gets confused I think.

I have all my repositories in sources.list, so I removed the sources.list.d directory, ran apt-get update and everything went fine.

---

