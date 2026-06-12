---
title: "Installing the latest version of Firefox on Ubuntu 6.06."
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by OmnificienT on 2007-05-30
I just got a repeater which I can use as wireless ethernet adapter, so I've only just got internet under Ubuntu, and therefore I am a total noob.

The problem is the following:
I'd like to download and install the latest version of Firefox. Now, I download the latest version from the firefox website, and I get a tarball.gz file. When I click open it will open as a archive, but I am unsure what to do next. Should I just extract it to some folder and then install it? Or do I have to use the "dpkg" command with some parameters attached to it?

Thank You,

OmnificienT

---

### Post by Simran on 2007-05-30
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Firefox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Firefox)

that guide is to install  the latest version of Firefox

Just follow the instructions, download the script and run it its all there

Simran

---

### Post by OmnificienT on 2007-05-30
And how could I do this manually?

---

### Post by aysiu on 2007-05-30
> **OmnificienT said:**
> And how could I do this manually?
Manually involves a lot of copying and pasting, but here you go:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

I'd advise using the script instead.

---

### Post by OmnificienT on 2007-05-30
Well, the script isn't working. This is the error I get:
```

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

```

I already tried sudo before the command to execute the script (sudo bash installnewfirefox.sh -install).

Does anyone happen to know what that means?

---

### Post by aysiu on 2007-05-30
> **OmnificienT said:**
> Well, the script isn't working. This is the error I get:
```

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

```

I already tried sudo before the command to execute the script (sudo bash installnewfirefox.sh -install).

Does anyone happen to know what that means?
It means you have some other application open that's accessing the package manager--Synaptic Package Manager, Adept Package Manager, Update Manager, or Add/Remove Programs.

---

### Post by OmnificienT on 2007-05-31
So how can I disable those, I did not manually start up any of those programs.

---

### Post by aysiu on 2007-05-31
That's weird.

Well, you can try pasting this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo killall dpkg
```

---

### Post by OmnificienT on 2007-05-31
Ah, thank you. That did the trick. But what does that command to exactly? dpkg are all packaging programs? That would mean that it kills all packaging programs. Am I correct?

Another thing, can't I just download firefox from the main firefox website and then install it? Because the server to which the script connects is really slow.

---

### Post by aysiu on 2007-05-31
> **OmnificienT said:**
> Ah, thank you. That did the trick. But what does that command to exactly? dpkg are all packaging programs? That would mean that it kills all packaging programs. Am I correct? *dpkg* is **the** software package manager in Ubuntu. All the other programs that appear to be package managers are just different graphical frontends for *dpkg*--Synaptic Package Manager, Adept Package Manager, Add/Remove Programs, Update Manager.

> Another thing, can't I just download firefox from the main firefox website and then install it? Because the server to which the script connects is really slow. Well the script is actually downloading from Firefox's website. But I think if you put the .tar.gz on your desktop (or in your home folder--I forget which), the script should recognize that it has already been downloaded and then not try to redownload it.

**Edit**: Looking at the script code, it appears to be trying to download to your /home/username directory, so put the .tar.gz there before running the script. ```
    echo -e "\nChanging to home directory\n"
    cd

    echo -e "\nDownloading Firefox archive from the Mozilla site\n"
    wget -c --tries=20 --read-timeout=60 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/$VERSION/linux-i686/${LOCALIZATIONS[$CHOICE]}/firefox-$VERSION.tar.gz

```

---

