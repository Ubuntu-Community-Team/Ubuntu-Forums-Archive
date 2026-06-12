---
title: "Cannot Install Adobe Flash Player!"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by doomsdaydave11 on 2007-12-15
When I use the "sudo apt-get install flashplugin-nonfree" code in terminal, I type my pass and then it gives me this:
```

doomsdaydave11@DCOMP:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for doomsdaydave11:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
[/B]

---

### Post by doomsdaydave11 on 2007-12-15
why? I know I've tried other methods before, but I still can't view webpages with flash on them :confused: :(

---

### Post by Kingsley on 2007-12-15
Did you restart your browser before checking to see if Flash works? Try this and then restart your browser.
```
sudo apt-get remove --purge flashplugin-nonfree && sudo apt-get install flashplugin-nonfree
```

---

### Post by doomsdaydave11 on 2007-12-15
I have already restarted my browser several times, and even restarted my computer. I don't understand why I doesn't work.

---

### Post by CCNA_student on 2007-12-15
Try manually installing Adobe flash player. I found that when I tried getting Adobe flash player by using Adept or Synaptic that I kept getting bad MD5 checksums once the installer started downloading Adobe flash player. Just go to Adobe.com, download the tar.bz file, and follow the simple instructions. This worked for me.

    Sin Cere,

    CCNA_student

---

### Post by Irony on 2007-12-15
Try this instead; [http://ubuntuforums.org/showthread.php?p=3952403#post3952403](http://ubuntuforums.org/showthread.php?p=3952403#post3952403)

---

### Post by RomeReactor on 2007-12-15
> **doomsdaydave11 said:**
> I have already restarted my browser several times, and even restarted my computer. I don't understand why I doesn't work.

Hi. The flashplugin-nonfree package has a bug at the moment, where the package itself gets installed, but Firefox can't find it; see [this thread]("http://ubuntuforums.org/showthread.php?t=636397") for a temporary solution, while the update shows up in the repositories.

---

### Post by Taboo Mirage on 2007-12-15
Are you using a 64-bit architecture?

```
uname -a
```

You have have to take additional steps with ndiswrapper if this is the case.  If you are, try running this from a terminal:

```
sudo nspluginwrapper -v -a -i
```

After doing so, restart your browser.  It should work.

---

### Post by Ub1476 on 2007-12-15
Check if the plugin is in Firefox' directory:

```
cd /usr/opt/firefox/plugins
dir
```

Also check that you have enabled Flash in Firefox.

Usually it works out of the box for me with this command though:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by doomsdaydave11 on 2007-12-15
No, I am using 32-bit.

---

### Post by Taboo Mirage on 2007-12-15
> **doomsdaydave11 said:**
> No, I am using 32-bit.

In that case I recommend trying this:

```
cd ~
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
tar -zxf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/mozilla/plugins/
```
Restart browser afterwards.

---

### Post by doomsdaydave11 on 2007-12-15
Thanks for the help everyone. After trying several methods, I managed to get it to work :).

---

### Post by Oneder on 2007-12-16
> **doomsdaydave11 said:**
> Thanks for the help everyone. After trying several methods, I managed to get it to work :).
Glad you got it working.

Installed GEUbuntu several hours ago and still trying to get flash working here.

Tried everything I've seen here and over there and zilcho.](*,)]:confused:

---

### Post by maartends on 2007-12-20
I got my fix here: [https://answers.launchpad.net/ubuntu/+question/19584](https://answers.launchpad.net/ubuntu/+question/19584)

I'm working under Xubuntu...

---

