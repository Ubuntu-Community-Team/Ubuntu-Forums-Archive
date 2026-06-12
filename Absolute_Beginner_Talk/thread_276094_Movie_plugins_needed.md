---
title: "Movie plugins needed"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by ausbun on 2006-10-12
When I try to use Totem to play a video taken by a Kodak digital camera, I get a message that says: "You do not have a decoder installed to handle this file. You might need to install the necessary plugins." Where do I get the necessary plugins?

BTW, Totem seems to work fine on other video.

---

### Post by Kateikyoushi on 2006-10-12
You can install the plugin with synaptic.

System >> administration >> synaptic package manager.

A little help with restricted formats [Link]("https://help.ubuntu.com/community/RestrictedFormats").

What is the extension of the video file ?

---

### Post by ausbun on 2006-10-12
It has the suffix: .MOV

---

### Post by equal on 2006-10-12
Yeah, quicktime formats fall into the grey area as far as legality goes. 

One great tool for people starting out on Ubuntu (and for people who've been using it for ages) is a program called Automatix. It automates the installation process of a lot of plugins and basic programs. Here's a quick explaination on how to install it:

Edit your sources.list. In a Terminal window, type:

```
sudo gedit /etc/apt/sources.list 
```

Paste this at the end of the file:

```
deb http://www.getautomatix.com/apt dapper main
```

Now save the file and close it.

Then enter this, one line at a time, in a terminal window:

```
wget http://www.getautomatix.com/apt/key.gpg.asc
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -
```

To finish off:

```
sudo apt-get update
sudo apt-get install automatix2
```

Then you'll find Automatix under Applications --> System Tools

Give it a try. It should take care of your codec issue, and give you a lot more too!

---

### Post by jrz on 2006-10-12
Are you saying that by installing automatix that it will see the need for a codec and find and install it automatically when that need arises?

---

### Post by sKuarecircle on 2006-10-12
No No but it will however automate the whole process, you juat click the box that says 'codecs' and it's done.trust me I am a noob and Automatix is the bomb. There are a whole bunch of other software as well that you will need on there.

> 

---

### Post by ausbun on 2006-10-12
Thanks. I'm running the Automatix now.

---

### Post by ausbun on 2006-10-13
I installed Automatix2 and used it to download some apps, like Google Earth and Picassa, but they aren't in the Applications menu and I don't know where to find them to start them?

Has this happened to anyone else?

---

### Post by dolphinsonar on 2006-10-13
Yes, I too have questions as to where things go after they are downloaded.  I theoretically understand that you can access things via the command line, IE: Applications>Accessories>Terminal, but I don't really know how to use it fully yet.  Try typing in:

```
man man
```

Its interesting if you have a minute to read stuff.

---

