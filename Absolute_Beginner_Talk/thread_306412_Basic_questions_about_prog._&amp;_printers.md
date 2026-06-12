---
title: "Basic questions about prog. &amp; printers"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by Carolyn62 on 2006-11-24
Hi,
I hope I am not being a pain, but I have a few basic questions:

I know how to download, install, and run programs in (yuk) windows, but no where can I find a basic procedure on doing this in Ubuntu.

For example: I have been trying for 3 or 4 days trying to install my printer. I finally found a way to do this on the Ubuntu forum.

> I modified a script that was originally written to install an i850. It will download the Japanese rpm drivers, convert them to deb packages, install the deb packages and setup the print queues. If the script asks for any confirmations, just type 'y'.

This script will setup a USB i860 on a debian machine.
[http://www.hildoer.com/linux/scripts..._canon_i860.sh](http://www.hildoer.com/linux/scripts..._canon_i860.sh)

Run it like this:

$ sudo ./install_canon_i860.sh 

Now as to my questions:
1. Where do I download this to, in other words what folder???
2. Is there a place where all downloaded programs are sent to???
3. Third but not least, how do I know that I can run this or any other program for that matter on dapper 6.06lt?

Your help is greatly appreciated,
Carolyn

---

### Post by CatKiller on 2006-11-24
> **Carolyn62 said:**
> I know how to download, install, and run programs in (yuk) windows, but no where can I find a basic procedure on doing this in Ubuntu.

You mean like [this one]("http://www.monkeyblog.org/ubuntu/installing/")? :)

I don't know anything about setting up a printer. Mine just worked. Sorry.

---

### Post by Carolyn62 on 2006-11-24
Hi,

It's kind of sort of what I am looking for and I saved it for ref., but this thing I am trying to download is for printers and I do not know where to put it. I apoligize for being such a dunderhead, but I am really trying.

Carolyn

---

### Post by ahildoer on 2008-01-13
> **Carolyn62 said:**
> Hi,

It's kind of sort of what I am looking for and I saved it for ref., but this thing I am trying to download is for printers and I do not know where to put it. I apoligize for being such a dunderhead, but I am really trying.

Carolyn

Carolyn,

I am the one that modified the script you are trying to run. I was not subscribed to the original post where you found my script, so I did not see your original request.

The way you download and run the script is like any other script for UNIX/Linux. For this particular script, here are the exact commands: 

[LIST=1]
[*]Click Applications -> Accessories -> Terminal. That will open a prompt.
[*]Now simply execute these commands ```
wget http://www.HildoerSystems.com/linux/scripts/install_canon_i860.sh
chmod 755 install_canon_i860.sh
sudo ./install_canon_i860.sh
```
[/LIST]

---

