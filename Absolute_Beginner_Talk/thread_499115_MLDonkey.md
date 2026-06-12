---
title: "MLDonkey"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-07-12
hello, I've installed MLDonkey with sudo apt-get install mldonkey-server and mldonkey-gui. it is in apps>internet>mldonkey as a graphical user interface, but I don't know how to run it in a terminal. the commands "mldonkey" or "mldonkey-server" do not work in console. I get an output: "bash: command not found". Any ideas how to run it in terminal?

---

### Post by felicity on 2007-07-12
I think you need to telnet to the server to be able to run commands on it. Check out the information on the mldonkey site [here.]("http://mldonkey.sourceforge.net/Main_Page") (the quickstart guide for example)

---

### Post by yota on 2007-07-12
try 'dpkg -L mldonkey-server' to list all files contained in the package.
There should be an /etc/init.d/mlsomething script, while the actual daemon is "mlnet".
Once you'll get it up and running try [http://sancho-gui.sourceforge.net/](http://sancho-gui.sourceforge.net/) (not available) through the repositories as a gui: it's much better than mldonkey-gui.

As a final note the version in the repositories is usually outdated; I prefer to download binaries in tar.gz format from mldonkey.sf.net instead.

---

### Post by KaiserMonkey on 2007-08-01
The command is "mlnet".

---

### Post by airtonix on 2007-11-10
and how are we supposed to edit a downloads.ini that doesnt exist? where is it the site does not tell us where this file goes.

---

