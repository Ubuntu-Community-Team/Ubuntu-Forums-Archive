---
title: "Frustrated"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by ellster456 on 2007-10-01
Is there a guide somewhere that will tell me EXACTLY how to install something? I mean seriously step-by-step, assuming that I've never touched a computer before in my entire life, that I don't know a ./configure from a slice of bread??? 

A few months ago I got Ubuntu and installed it and I like it far better than I ever did Windows, but there are several things I cannot get to install correctly, Java being first and foremost. I've tried doing what several sites have said to do but either I'm doing something wrong or they don't know what they're talking about.

---

### Post by Perfect Storm on 2007-10-01
You install things from **Synaptic Package Manager** (System --> Adminstration) or use **Add/Remove** in Application tab.
You don't need to go to diffrent homepages/sites to get what you want.

---

### Post by RomeReactor on 2007-10-01
Hi. [This community documentation page]("https://help.ubuntu.com/community/SoftwareManagement") has a very good explanation of how installing software in Ubuntu works. You'll find the [Community Documentation]("https://help.ubuntu.com/community/") pages to contain loads of useful information. There's also [Aysiu's page]("http://www.psychocats.net/ubuntu/installingsoftware") with more methods for installing software--including installing from source.

Regarding Java, if you want to enable it for Firefox, search Synaptic for **sun-java6-plugin**, and install it; or, to do it from the terminal (Applications->Accessories-Terminal):
```
sudo apt-get install sun-java6-plugin
```

---

### Post by ellster456 on 2007-10-01
Thank you both so much!

---

### Post by hyper_ch on 2007-10-01
well, as the previous posters have pointed out you will (very likely) not require to compile anything from source (yet). So forget about that "./configure, ./make, ./make install" for the time being and use the repositories. Add/Remove is a graphical frontent.
```

sudo apt-get install sun-java6-plugin

```
will do the same but from the terminal (you will see, the terminal comes in handy once you get used to it)...

For adding more repositories have a look at this page here:  [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

It will generate a sources.list that you then can replace your original with. Remember, in order to write to the sources.list you will need root access.

```

gksu gedit /etc/apt/sources.list

```

And for verifying the integrity of the repositories they use a GPG key. So if you add new ones, you will also want to import the keys, otherwise you will always get a warning message about untrusted repositories. The sources.list generator gives you already all the knowledge you need for adding the GPG keys:
```

# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

```

E.g. the medibuntu package entry looks like this:
```


# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free 

```

This means after you add it to your sources list, run those two commands:
```

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 0C5A2783

```
```

gpg --export --armor 0C5A2783 | sudo apt-key add -

```

That's it. Now update the packages available and install all the fancy new stuff ;)

---

### Post by tdrusk on 2007-10-01
> **hyper_ch said:**
> (you will see, the terminal comes in handy once you get used to it)...

I agree 100%. The terminal makes it easier for us to help you. Instead of us telling you to open this program and do all these things, you just have to copy and paste what we write.

---

