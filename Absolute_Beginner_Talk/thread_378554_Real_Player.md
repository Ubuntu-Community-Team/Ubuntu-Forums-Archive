---
title: "Real Player"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by groeswenphil on 2007-03-07
Hi Group,
I've managed to download and install Real Player........and it appears to work on its own. I can't get it to work in Firefox though.

I've just found these instructions. Can anybody help?


   1. Install RealPlayer 10. (Done that)
   2. Copy nphelix.so to your Mozilla plugins directory and nphelix.xpt to your Mozilla components directory. (I get those files from Synaptic right? Then where do I find the directories where they need to go?
   3. Make sure a symbolic link to the realplay script is in your PATH. (Now I'm lost)

Note: If you installed the RealPlayer 10 RPM, these files are located in /usr/local/RealPlayer/mozilla.

---

### Post by christhemonkey on 2007-03-07
If you are using dapper you can just add the commercial repository in synaptic and then just install real player 10 easily!

Add this line to your sources.list (either in the add new repository dialog in synaptic or by editing /etc/apt/sources.list
```
deb http://archive.canonical.com/ubuntu dapper-commercial main 
```

Thenjust do this to install realplayer:

```
sudo apt-get update
sudo apt-get install realplay 
```

(or just reload repo information and search for realplayer in synaptic.)

---

### Post by groeswenphil on 2007-03-07
Please be gentle with me :( 

Add this line to your sources.list (either in the add new repository dialog in synaptic or by editing /etc/apt/sources.list

Now, I know how to get into Synaptic but how do I get to the sources.list?


```
deb http://archive.canonical.com/ubuntu dapper-commercial main 
```

Thenjust do this to install realplayer:

I can do this part :O)

```
sudo apt-get update
sudo apt-get install realplay 
```

(or just reload repo information and search for realplayer in synaptic.)[/QUOTE]
I'm sure I did this and got where I am now....Real Player runs on its own but not in Firefox.
Thanks,
Phil

---

### Post by lahook on 2007-03-07
install realplayer in /usr/lib/realplayer
it should create your symbolic links for you in /usr/lib/firefox/plugins
i hope this helps you out

---

### Post by AtrejuT on 2007-03-07
ok, what you have to do is type
```

sudo gedit /etc/apt/sources.list

```

in a command line. the editor will come up and you add the suggested lines at the bottom of the file. save and close.

go back to the terminal and do the sudo apt-get update etc. there.

good luck

atreju

---

### Post by ikg74 on 2007-03-20
I'm using Real Player 10 on ubuntu 5.04 and I just downloaded the RealPlayer10GOLD.bin from 

[http://www.real.com/linux/](http://www.real.com/linux/)

and installed it using 

```

**./RealPlayer10GOLD.bin **

```

During the installation you will be asked in which directory you want it to be installed and the setup will then fix all the symlinks to that directory correctly

When this stage installation finishes, go to the directory where your Real Player was installed and type

```

**./realplay**

```

This will start the final step of the Real Player installation necessary to successfully complete the process

To ensure the plugins have been installed correctly, check the firefox plugins folder (usually /usr/lib/mozilla-firefox/plugins/) to confirm that the file nphelix.so is present. Then check the firefox components folder (usr/lib/mozilla-firefox/components/) for the nphelix.xpt file.

If everything is where it should be then you should be able to watch real player files in your browser as well.

---

